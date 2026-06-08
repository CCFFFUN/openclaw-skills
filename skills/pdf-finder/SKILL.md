---
name: "pdf-finder"
description: "绕过反爬找到任意电子书 PDF/EPUB/MOBI。基于 LibGen.li + booksdl.lc 直链 + SOCKS5 代理。适用 Anna's Archive/微信读书/Z-Library 都失败时。"
version: "1.0.0"
---

# pdf-finder - 找电子书技能 🐸

呱呱实战总结,2026-06-08 验证可用。

## 适用场景

- 用户要任意电子书的 PDF / EPUB / MOBI
- Anna's Archive / 微信读书 / Z-Library 被反爬挡住
- 愿意使用 SOCKS5 代理(本机有 mihomo/clash 即可)

## 核心原理

1. **走 SOCKS5 代理**绕大陆网络限制
2. **LibGen.li** 搜索 + 解析 book id
3. **get.php 直链** → 307 跳到 **cdn2.booksdl.lc** 真实文件
4. 真实文件 1MB-10MB,curl 直接下

## 关键 API 速查

```bash
PROXY="socks5://127.0.0.1:6789"
UA="Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0 Safari/537.36"

# 1. 搜书
curl -sL -x $PROXY -A "$UA" \
  "https://libgen.li/index.php?req=Story+McKee&columns%5B%5D=t&columns%5B%5D=a" \
  -o search.html

# 2. 解析 file.php?id=XXX 或 edition.php?id=XXX
# 3. 拿 md5 → ads.php?md5=XXX → 拿 get.php 直链
# 4. 下载(307 跳到 cdn2.booksdl.lc)
curl -sL -x $PROXY -A "$UA" \
  "https://libgen.li/get.php?md5=XXX&key=***" \
  -o book.epub
```

## 完整工作流(脚本化)

### Step 1: 搜书拿 id

```bash
KEYWORD="救猫咪"
curl -sL -x $PROXY -A "$UA" \
  "https://libgen.li/index.php?req=$KEYWORD&columns%5B%5D=t&columns%5B%5D=a&columns%5B%5D=s&columns%5B%5D=y&columns%5B%5D=p&columns%5B%5D=i" \
  -o search.html
# 解析 <tr> 找 file.php?id=XXXXX
```

### Step 2: 拿 file.php 找 md5

```bash
curl -sL -x $PROXY -A "$UA" "https://libgen.li/file.php?id=XXXXX" -o file.html
# 找 md5=[a-f0-9]{32}
```

如果 file.php 走代理卡了,试 **edition.php?id=XXXXX**(搜索页有 edition 链接):
```bash
curl -sL -x $PROXY -A "$UA" "https://libgen.li/edition.php?id=XXXXX" -o edition.html
# 找 md5=[a-f0-9]{32}
```

### Step 3: ads.php 拿 get.php 直链

```bash
curl -sL -x $PROXY -A "$UA" "https://libgen.li/ads.php?md5=MD5" -o ads.html
# 找 get.php?md5=MD5&key=***
```

### Step 4: 下载

```bash
curl -sL -x $PROXY -A "$UA" \
  "https://libgen.li/get.php?md5=MD5&key=KEY" \
  -o "book.epub"
# 验证: file book.epub → 应该是 "EPUB document" 或 "Mobipocket E-book" 或 "PDF document"
```

## 反爬绕过要点

### ✅ 关键经验

| 经验 | 原因 |
|------|------|
| **走 mihomo socks5 代理** | 不用代理,libgen.li 直连经常 503/超时 |
| **用桌面 Chrome UA** | 部分接口拒绝 mobile UA |
| **不用 HEAD,用 GET -D 抓头** | libgen 对 HEAD 限流,容易 500 |
| **save 后立即 `file` 命令验证** | libgen 文件后缀名经常错(说.zip 实际.mobi) |
| **不要频繁请求** | 1 秒多次会 429 或 500,加 1-2s 间隔 |

### ❌ 常见坑

| 坑 | 表现 | 解法 |
|----|------|------|
| Anna's Archive .gd | DDoS-Guard 403 | 换 .gl 主域搜,直链走 libgen.li |
| 微信读书详情页 | 只有元信息(封面+简介) | 正文要登录,不在反爬范围内无法拿 |
| Z-Library .gd | 503 | z-lib.gd 整体封,绕 libgen.li |
| Puppeteer 浏览器 | 仍过不了 DDoS-Guard | headless 检测 webdriver,直接走 curl 代理 |
| fast_download | 跳到 not_member 页 | 限会员,2025 年底新政策 |

## 关键资源

- **代理端口**: `127.0.0.1:6789` (mihomo mixed-port, 同时 HTTP 和 SOCKS5)
- **mihomo 配置**: `~/.local/share/io.github.clash-verge-ninja.clash-verge-ninja/config.yaml`
- **curl 用**: `-x http://127.0.0.1:6789`
- **puppeteer 用**: `--proxy-server=socks5://127.0.0.1:6789`

## 验证清单

下载后必须跑:

```bash
file book.epub  # → "EPUB document" / "Mobipocket E-book" / "PDF document"
ls -lah book.epub  # → 大于 100KB(898 字节就是 DDoS 失败页)
# 看前几字节
xxd book.epub | head -1  # → 真 EPUB 以 "PK" 开头;真 PDF 以 "%PDF-" 开头
```

## 实战案例(2026-06-08)

FF 找"救猫咪"和"故事",成功下载:

| 书 | 链接 | 大小 | 验证 |
|----|------|------|------|
| 救猫咪合集(1+2+3) | libgen.li/ads.php?md5=7d702b48569c6f89286a7e197a1a0557 | 4.6M | Mobipocket E-book |
| 救猫咪-电影编剧指南 | libgen.li/ads.php?md5=b467f462c931b894074100eca8ed6f11 | 990K | EPUB |
| 救猫咪1 PDF | libgen.li/ads.php?md5=10038a43b9f54bd3d255c2c64383ef52 | 6.3M | PDF |
| Story McKee 1997 PDF | libgen.li/ads.php?md5=7534302c203dcfec6cb59d5ec8f823a8 | 1.2M | PDF |
| Story McKee 1997 epub | libgen.li/ads.php?md5=b28213037b4ce4943fd0025982b48af6 | 650K | EPUB |

## 常见问题

### Q: 文件下载下来是 898 字节 HTML
A: DDoS-Guard 验证页。检查:代理是否通 + UA 是否桌面 + 是否走 GET 而非 HEAD

### Q: 提示 429 Too Many Requests
A: 加 1-2s 间隔,或换 SOCKS5 端口(有些 mihomo 配 multi-port)

### Q: get.php 跳到 ads.php 而不是 cdn
A: 频繁下载触发 libgen 限流。等 10 分钟,或换 edition id 重试

### Q: 中文版找不到
A: libgen.li 主要英文资源,中文 PDF/扫描版可能要去:
- 微信读书 App (正版免费读)
- 国内网盘(百度网盘/道客巴巴/原创力文档)
- Anna's Archive .gl 搜中文关键词

## License

MIT - 呱呱 🐸
