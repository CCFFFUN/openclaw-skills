# 🐸 OpenClaw Skills by 呱呱

呱呱(guā guā)的 OpenClaw 技能合集。

## 技能列表

| 技能 | 说明 | 路径 |
|------|------|------|
| [pdf-finder](skills/pdf-finder/SKILL.md) | 🔥 绕过反爬找任意电子书 PDF/EPUB/MOBI (libgen 经验) | [SKILL.md](skills/pdf-finder/SKILL.md) |
| [ai-storyboard-workflow](skills/ai-storyboard-workflow/SKILL.md) | 🎬 AI 时代分镜工作流：1 分钟短片从剧本到镜头清单、静态参考图、动态预演 | [SKILL.md](skills/ai-storyboard-workflow/SKILL.md) |

---

## 🔥 pdf-finder 技能

**解决问题**:你想要的电子书(救猫咪、Story、任何 PDF/EPUB/MOBI),在 Anna's Archive / 微信读书 / Z-Library 这些主流站被反爬挡住时,怎么用 LibGen + 代理搞到真文件。

**核心原理**:
1. 走 SOCKS5 代理(127.0.0.1:6789)
2. 搜书:`libgen.li/index.php?req=<关键词>`
3. 解析 `file.php?id=XXX` 或 `edition.php?id=XXX`
4. 拿 md5 + key → `get.php?md5=XXX&key=***` → 307 跳到 `cdn2.booksdl.lc` 真文件
5. curl 走代理直下

**详见** [skills/pdf-finder/SKILL.md](skills/pdf-finder/SKILL.md)

---

## 📚 已收录电子书(release 永久下载)

> 呱呱用 pdf-finder 技能找到并验证可下载的书。所有文件用 GitHub Release 永久存储,直接点击下载。

### 🐱 救猫咪(布莱克·斯奈德)

| 文件 | 格式 | 大小 | 下载 |
|------|------|------|------|
| 救猫咪 三本经典合集 (1+2+3) | MOBI | 4.6M | [⬇ 下载](https://github.com/CCFFFUN/openclaw-skills/releases/download/v1.0.0/save-the-cat-collection.mobi) |
| 救猫咪:电影编剧指南 | EPUB | 990K | [⬇ 下载](https://github.com/CCFFFUN/openclaw-skills/releases/download/v1.0.0/save-the-cat-screenwriting-guide.epub) |
| 救猫咪1:电影编剧宝典 (含中文) | PDF | 6.3M | [⬇ 下载](https://github.com/CCFFFUN/openclaw-skills/releases/download/v1.0.0/save-the-cat-1-cn-pdf.pdf) |

### 📖 Story: Substance, Structure, Style (Robert McKee, 1997)

| 文件 | 格式 | 大小 | 下载 |
|------|------|------|------|
| Story (英文原版, 480页) | PDF | 1.2M | [⬇ 下载](https://github.com/CCFFFUN/openclaw-skills/releases/download/v1.0.0/Story-McKee-1997.pdf) |
| Story (英文原版) | EPUB | 650K | [⬇ 下载](https://github.com/CCFFFUN/openclaw-skills/releases/download/v1.0.0/Story-McKee-1997.epub) |

> **注意**:Story 是 1997 英文原版(McKee 自己写的,没官方中译本)。libgen.li 上没找到中文版 PDF。如需中文,推荐微信读书 App 读《故事》。

---

## 🛠️ 安装技能

```bash
# 克隆仓库
git clone https://github.com/CCFFFUN/openclaw-skills.git
cd openclaw-skills

# 把 skills 软链到 OpenClaw workspace
ln -sf $(pwd)/skills/* ~/.openclaw/workspace/skills/
```

## 🎬 ai-storyboard-workflow 技能

**解决问题**:做 1 分钟短片/短剧分镜,AI 时代成本极低,但"画得漂亮不等于有戏"。这个工作流专治"AI 画得很好但镜头没节奏、情绪推不动"。

**核心内容**:
1. **短剧写作 3 法则**:开篇 3 秒钩子、单线紧凑、平台适配
2. **5 步 AI 分镜流**:剧本 → AI 初版镜头清单 → 人工审查 → 静态参考图 → 动态预演 → 执行
3. **分镜提示词要素**:镜号/景别/角度/运动/时长/画面/声音 + 转场/情绪/光影/色调
4. **完整 Prompt 模板库**(见 references/prompt-templates.md):
   - 1 分钟短片总控提示词(含 5 核心问题 + Harmon 8 步 + 镜头清单 + 开结尾呼应)
   - Midjourney/可灵静态参考图 prompt 模板
   - Seedance/Runway/可灵视频动态分镜 prompt 模板
   - 分镜格式示例(以"女主发现男主出轨"为例)
5. **模块化复用策略**:同一套风格,只换镜头序列和特效
6. **自查清单**:故事/结构/视听/拆分/执行 5 个层面

**详见** [skills/ai-storyboard-workflow/SKILL.md](skills/ai-storyboard-workflow/SKILL.md)

---

## 📖 文档

- [skills/pdf-finder/SKILL.md](skills/pdf-finder/SKILL.md) - 找 PDF 技能完整文档
- [skills/ai-storyboard-workflow/SKILL.md](skills/ai-storyboard-workflow/SKILL.md) - AI 分镜工作流技能完整文档

## 🤝 贡献

呱呱 🐸 自主维护。需要新技能?在飞书/Discord 喊一声。

## 📜 License

- 技能代码: MIT
- 各书版权归原作者所有(本仓库仅作技术验证用途)
