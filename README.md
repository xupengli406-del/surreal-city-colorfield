# Surreal City Colorfield

把城市照片做成高纯度大色域与唯一巨物的超现实拼贴系列。

这个 Skill 沉淀自一组上海城市实验：真正让画面变鲜明的，不是把整张图调得更饱和，也不是给巨物硬塞更多颜色，而是让高纯度颜色进入天空、水面、砖墙、道路等**有现实来源的大区域**；单张只保留 1–2 组主色，色彩多样性在整组之间展开。

> 地标可辨认，只有一个巨物，颜色落在空间里，单张不堆色，整组有节奏。

## 它解决什么问题

- 城市超现实图“概念有了，但画面仍然灰”；
- 为了鲜艳而在单张里强行加入很多随机颜色；
- 九张图逐张生成，最后发现全部是同一种蓝橙配色；
- 巨物像贴纸，没有和建筑、水面或道路发生关系；
- 参考图学成了照抄具体元素，而没有学到视觉语法。

## 核心方法

1. 给每张照片建立场景卡：地标锚点、区域边界、原生色、地点语义、动势。
2. 多图任务先排整组色相矩阵，安排高冲击页、安静页和夜景停顿。
3. 每张只选一个“不可能巨物”，并写清它如何从建筑或空间中延伸出来。
4. 让 1–2 组高纯度颜色占据天空、水面、墙体等完整边界，其余现实层保持黑白或低彩度。
5. 生成后先看九宫格联系表，只对明确失败做一次定点纠偏。

完整工作流见 [SKILL.md](SKILL.md)。

## 安装

### Codex / Claude Code / 兼容 Skills 的 Agent

把本仓库复制到你的 skills 目录，例如：

```bash
git clone https://github.com/xupengli406-del/surreal-city-colorfield.git ~/.codex/skills/surreal-city-colorfield
```

也可以下载 ZIP，解压后确保目录结构为：

```text
skills/
└── surreal-city-colorfield/
    ├── SKILL.md
    ├── agents/openai.yaml
    └── references/
```

不依赖固定操作系统、盘符、字体、声音、命令行工具或某个生图平台。Agent 会动态使用当前环境已有的图像生成/编辑能力；没有生图能力时，应输出场景卡、色相矩阵与可复制 prompt，并如实说明尚未生成图片。

## 使用

直接说：

```text
使用 $surreal-city-colorfield，把这 9 张杭州城市照片做成统一的超现实色形系列。先给我场景卡和色相矩阵，再生成图片。
```

或：

```text
使用 $surreal-city-colorfield 分析这组参考作品的色彩语法，但不要照搬它的具体巨物。把我的 6 张城市照片做成同一系列。
```

## 文件说明

- `SKILL.md`：核心决策、工作流、失败模式与交付标准。
- `references/scene-card-and-color-matrix.md`：单张场景卡、整组色相矩阵和强弱节奏模板。
- `references/prompt-and-qa.md`：可移植 prompt 编译器、双参考图策略、单张/整组质量门和一次性纠偏表。
- `agents/openai.yaml`：Codex 中的名称、描述与默认调用示例。

## 与 surreal-pop-collage 的关系

本项目是在 [`xupengli406-del/surreal-pop-collage`](https://github.com/xupengli406-del/surreal-pop-collage) 基础上派生的城市系列专项版本，继续遵守“现实锚点、唯一巨物、元素源于图、平涂无渐变”的核心原则；新增了：

- 彩色面积诊断，而不是只看全图平均饱和度；
- 天空/水面/墙体等区域化大色域；
- 6–12 张系列的色相矩阵与强弱节奏；
- 防止 `muted / dusty / restrained` 全局压灰的作用域规则；
- 双参考图职责拆分；
- 九宫格联系表质量门。

原项目上游为 [`2998980-hue/surreal-pop-collage`](https://github.com/2998980-hue/surreal-pop-collage)。感谢原作者提供 MIT 许可的基础方法。

## 隐私与素材

- 仓库不包含任何用户照片、生成成片、密钥、浏览器数据或本机路径。
- 使用外部城市照片时，请记录摄影者、来源与许可；公开发布前检查水印、人物隐私与平台 AI 标记要求。
- 不要照搬参考作品中的具体构图或巨物，只抽取颜色面积、现实/色形对撞和系列节奏等方法。

## License

MIT
