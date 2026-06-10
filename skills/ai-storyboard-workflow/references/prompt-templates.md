# Prompt 模板库

本文档包含可直接复制使用的完整 prompt 模板。

---

## 一、1 分钟短片总控提示词

直接复制给豆包 / GPT / Claude / Gemini 等工具使用。

```
你现在扮演一位资深的 1 分钟短片导演兼编剧，专攻 AI 时代的 IP 角色短片创作。你熟读故事方法论（Want vs Need、5 核心问题、Harmon 8 步圆环、McKee 五结构），也熟悉视听语言基础（景别、角度、运动、构图、轴线、用光、色彩、声音、剪辑、蒙太奇）。

【创作输入】
- IP 角色：[输入你的角色，例如：沉迷游戏的程序员陈野与他的女友小棠]
- 核心主题：[一句话，例如：游戏从来不是问题，问题是他一直一个人玩]
- 调性：[治愈 / 荒诞 / 悲剧 / 喜剧 / 诗意 / 现实]
- 目标平台：[抖音 / B站 / YouTube]
- 时长：[60秒]

【创作要求】

第一部分｜5 核心问题预热（请先回答，确认故事立得住）
- Q1 主角：他/她/它招人喜欢什么？Want 与 Need 各是什么？
- Q2 目标：在这 60 秒内，他要追求什么具体目标？
- Q3 阻碍：谁/什么在阻碍他？
- Q4 代价：如果失败会失去什么？（必须具备"死亡气息"）
- Q5 为什么是现在：平衡为什么在这一刻被打破？

第二部分｜Harmon 8 步骨架（请把 60 秒分配给 8 步）
1. You（0—5s）：角色在舒适区
2. Need（5—10s）：产生需求
3. Go（10—20s）：踏入未知
4. Search（20—28s）：适应新环境
5. Find（28—35s）：找到东西
6. Take（35—45s）：付出代价
7. Return（45—55s）：回归原处
8. Change（55—60s）：已经改变

第三部分｜镜头清单（请输出 12—15 个镜头的标准分镜表）
列：镜号 | 景别 | 角度 | 运动 | 时长 | 画面描述 | 声音描述

要求：
- 景别有节奏地变化（开场建议远景或全景，结尾建议特写或大特写，中间穿插变化）
- 运动镜头与固定镜头交替，避免单调
- 每个镜头必须有明确的"为什么是这个镜头"的视听理由
- 声音描述包含：对白（若有）+ 音效 + 音乐建议

第四部分｜开场画面与结尾画面
- 描述第 1 镜与最后 1 镜各 50 字
- 两者必须形成视觉呼应（色彩 / 构图 / 主体重复 / 意象重现）

第五部分｜AI 生成 Prompt 模板（便于直接用于 Midjourney / 可灵生图）
- 为关键的 3—5 个镜头各写一条完整英文 prompt
- prompt 包含：主体描述 + 景别 + 角度 + 光线 + 色调 + 镜头风格 + 时长（若动态）

第六部分｜自查提醒
请输出前自检：
(1) 5 核心问题都已回答
(2) Harmon 8 步无遗漏
(3) 分镜表的总时长加起来约等于 60 秒
(4) 代价具备死亡气息
(5) 结尾与开头形成视觉呼应
```

---

## 二、静态参考图 Prompt 模板

适用于 Midjourney / Stable Diffusion / 可灵图像版。

### 完整结构

```
[主体描述]
A [age] [gender] [role/identity], [physical appearance], [current state/emotion]

[动作与姿态]
[Action description], [body position], [interaction with environment/objects]

[情绪氛围]
[Emotional tone], [atmosphere], [mood keywords]

[场景与时间]
[Location], [time of day], [weather], [environmental details]

[构图方式]
[Shot type: extreme wide / wide / full / medium / medium close-up / close-up / extreme close-up], [subject position in frame], [symmetrical/asymmetrical], [negative space]

[镜头角度]
[Camera angle: eye level / high angle / low angle / Dutch angle], [perspective]

[光线设置]
[Light direction: front/back/top/side], [light quality: soft/hard], [color temperature], [shadows], [special lighting effects]

[色调与材质]
[Color palette: warm/cool/monochrome], [texture: film grain/digital clean], [saturation], [contrast], [special visual treatment]

[风格参考]
Cinematic style of [film/director/era], [visual reference], [photographic style], [art movement reference]
```

### 实际示例：孤独程序员

```
A 28-year-old male programmer, wearing a dark hoodie, sitting hunched over a desk, eyes tired but focused, illuminated only by monitor glow.

Hands on keyboard, slight lean forward, headphones around neck, empty energy drink cans scattered on desk.

Lonely but absorbed, quiet intensity, the comfort of routine.

Small apartment room, night, rain outside visible through window, LED strip lights casting blue tint.

Medium shot, subject positioned left of frame, large negative space on right showing the empty side of the bed.

Eye level angle, slight depth of field blur on background.

Side lighting from monitor, cool blue tones, harsh shadows on face, soft ambient from window.

Cool blue-gray palette, film grain texture, low saturation, high contrast on subject.

Cinematic style of Blade Runner 2049, loneliness in digital age, Roger Deakins lighting.
```

---

## 三、动态分镜 Prompt 模板

适用于 Seedance 2 / Runway / Pika / 可灵视频版。

### 完整结构

```
【整体设定】
时长 + 媒介类型（真人/动画/3D渲染）+ 人声/对白/BGM/字幕的有无 + 转场方式（硬切/叠化/跳剪）+ 整体场景大类 + 节奏特征（快节奏/慢节奏/张弛有度）+ 画面整洁度要求 + 核心视觉看点（强化什么/弱化什么）

【角色参考】（逐个角色编号，如 {{Mixed 1}}）
- 形象特征（发型/五官/体型）
- 穿搭配饰（衣着/鞋帽/包饰/道具佩戴）
- 气质设定（冷峻/慵懒/灵动/沉稳……）
- 超能力/特殊能力（若有）
- 异能特效色调（与整体色调适配）
- 角色一致性要求（"全程保持形象不变"）

【场景参考】（编号列出）
1. 场景核心要素 + 材质质感 + 光线方向与色温 + 空气/环境氛围 + 标志性细节（涂鸦/磨损/反光/气味暗示）
2. 第二场景同结构铺开
3. ……

【道具/怪物参考】（可选编号）
形态描述 + 表面质感（熔岩/烟雾/金属/有机体）+ 发光/特效元素 + 体量与气势 + 与人物的视角关系（俯瞰/平视/仰视）

【镜头序列】（严格按动作逻辑编号，每镜标注转场）
1. 【镜号·景别·作用标签】主体动作 + 镜头运动（推/拉/摇/移/跟/升/降/大角度运镜）+ 特效细节 + 转场方式（硬切/叠化/跳剪）
2. 【镜号·景别·作用标签】……
3. ……

【特效元素】（分子类细化）
- 核心专属特效（异能/能量/标志性视觉）：颜色 + 形态 + 流动方式 + 起止逻辑
- 动态特效：人物动作扬起的尘埃/衣物飘动/头发摆动
- 光影特效：主光/辅光/轮廓光/能量光的融合方式
- 环境特效：雾/烟/涟漪/震颤/空气扭曲
- 动态模糊与画面纯净度要求
- ⛔ 禁用项：无多余噪点/无花哨冗余特效/无刺眼霓虹/无破坏物体的动作（如不开门、不变形）

【节奏控制】
整体节奏基调 + 关键段落节奏（动作段如何/慢镜段如何/收尾段如何）+ 转场切换原则（全程硬切/利落干脆/段落间停顿）

【色调与光影】
主色调（如低饱和冷蓝）+ 融合光源类型（隧道光/车厢冷白/城市微光/月光）+ 明暗对比强度 + 电影级氛围关键词

【风格】
渲染风格定位（如《双城之战》3D绘画渲染/写实电影感/国漫风格）+ 笔触/明暗特性 + 体积雾质感 + 噪点要求
+ 运镜原则（大角度推拉/摇移/俯冲/环绕，有定机位/无定机位）
+ 英文风格关键词补充：ultra realistic lighting, cinematic composition, 3D painterly rendering style inspired by Arcane, stylized brush-textured shading, volumetric fog, dramatic rim lighting
```

### 实际示例：孤独程序员 3 镜序列

```
【整体设定】
时长 10 秒，真人媒介，无对白，有环境音与 BGM，转场硬切，室内公寓场景，慢节奏压抑感，画面整洁度中等，核心看点：强化孤独氛围，弱化环境细节

【角色参考】
- 陈野，28 岁男性，瘦削，黑卫衣，黑眼圈明显，气质慵懒疲惫
- 全程保持形象不变

【场景参考】
1. 小公寓，夜间，显示器蓝光为主光源，窗外有雨，桌上有空能量饮料罐

【镜头序列】
1. 【镜1·中景·建立】陈野坐在桌前，背对镜头，显示器光打在侧脸，固定镜头，硬切
2. 【镜2·近景·情绪】他手停在键盘上，眼神空洞，缓慢推镜，硬切
3. 【镜3·特写·细节】镜头越过他肩膀，对焦到床上空枕头，固定镜头，硬切

【特效元素】
- 动态特效：窗外雨滴滑动，微弱反光
- 光影特效：显示器蓝光为主光，窗外微弱暖光为辅光
- 禁用项：无多余噪点，无花哨特效

【节奏控制】
整体慢节奏，段落间停顿，转场利落干脆

【色调与光影】
低饱和冷蓝主调，蓝光与窗外微弱暖光融合，高对比度，电影级孤独氛围

【风格】
写实电影感，轻微胶片颗粒，Roger Deakins 光影风格，cinematic loneliness
```

---

## 四、分镜提示词格式示例

以"女主发现男主出轨"为例：

```
【镜1·全景·建立】
卧室，女主推门进来，镜头固定在门框位置，她的表情从放松变成震惊。
时长：3s
声音：开门声 + 脚步声 + BGM 轻响

【镜2·中景·反应】
女主面部特写推进，瞳孔放大，嘴唇微张，镜头缓慢推近。
时长：2.5s
声音：心跳声渐强 + BGM 弦乐起

【镜3·过肩·视角】
镜头越过女主肩膀，看到床上两个人影，虚焦，暗示而非直白展示。
时长：2s
声音：BGM 弦乐高潮 + 环境音消失

【镜4·特写·细节】
女主手里的手机滑落，镜头对准手机落地，屏幕亮着，显示聊天记录。
时长：1.5s
声音：手机落地声 + BGM 戛然而止
```

---

## 五、模块化复用策略

### 为什么模块化

同一个短片的多个镜头，往往只需要改：
- 镜头类型
- 主体动作
- 情绪

而可以复用：
- 整体设定
- 角色参考
- 场景参考
- 色调与光影
- 风格

### 推荐工作流

1. **第一次 prompt**：完整写所有模块，确立风格
2. **第二个镜头起**：
   - 复制上一个 prompt
   - 只替换【镜头序列】和【特效元素】
   - 其他模块保持不变

### 优势

- 大幅降低创作成本
- 保持视觉一致性
- 减少 AI "跑偏"的风险
- 更快迭代和试错

---

## 六、自查清单

在提交或使用 prompt 前，检查：

**故事层面**：
- [ ] 5 核心问题都已回答
- [ ] Want 和 Need 清楚区分
- [ ] 代价具备"死亡气息"
- [ ] 为什么是现在有说服力

**结构层面**：
- [ ] Harmon 8 步无遗漏
- [ ] 每一步有明确时间分配
- [ ] 总时长约等于 60 秒

**视听层面**：
- [ ] 景别有节奏变化
- [ ] 运动镜头与固定镜头交替
- [ ] 每个镜头有明确视听理由
- [ ] 开场与结尾形成视觉呼应

**剧本拆分层面**：
- [ ] 已按情绪节拍而非自然段拆分
- [ ] 每个分镜单元控制在 1 动作 + 1 情绪
- [ ] 删除了无法被镜头表达的内心独白
- [ ] 画面锚点清晰可见

**执行层面**：
- [ ] Prompt 结构完整
- [ ] 风格参考明确
- [ ] 技术参数（时长、分辨率等）合理
