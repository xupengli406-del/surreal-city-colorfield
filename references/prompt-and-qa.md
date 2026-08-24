# Prompt 编译与质量门

只有在场景卡和色相矩阵完成后使用本文件。

## 1. 通用编辑模板

把方括号替换为场景卡中的可见信息：

```text
Edit the provided city photo into a polished vertical 3:4 surreal colorfield collage.

Keep [landmark and key silhouette] immediately recognizable within 3 seconds; preserve [camera viewpoint / roofline / waterfront / street perspective] and do not cover [critical anchor].

Preserve exactly one impossible giant object: [object], physically [extends from / is joined to / continues from / becomes] [real architectural or spatial region]. It is dominant but does not hide the landmark's identifying structure.

Color logic: [architecture/street] remains crisp black-and-white photographic collage on [paper or neutral ground]. The entire [sky/water/wall/road] within its natural boundary becomes one flat vivid [color] matte field derived from [source in original photo]. The giant object uses [one auxiliary color] derived from [source/material/cultural color]. These are the only chromatic regions.

Add 3 to 5 small same-source [fragments/components] in graduated sizes following one arc, plus 2 to 3 thin white hand-drawn gestural strokes following [dominant movement].

High-purity matte color fields, clean cut-paper edges, bright editorial daylight, strong negative space. No gradients, no glow, no transparency, no random rainbow colors, no text, logo, watermark, border, extra giant objects, or decorative clutter.
```

## 2. 双参考图编辑

已有失败版本时，不要让模型混淆两张图：

```text
Use Image 1 only as the composition and existing surreal-object reference.
Use Image 2 only as the true landmark, geometry, and original-color reference.
Preserve the successful [composition/object connection] from Image 1, but rebuild the color logic from Image 2.
```

只提供必要的参考图。不要把一堆风格图同时输入后要求模型自行判断。

## 3. 颜色词的作用域

### 推荐

```text
the sky is a vivid high-purity cobalt-blue flat matte field
the building remains crisp black-and-white photographic collage
warm off-white paper is limited to the negative space
```

### 避免

```text
muted restrained dusty warm-ivory surreal collage
```

后一种写法会让模型把“克制”应用到整张图，连本应鲜艳的色域也一起变灰。把每个形容词绑定到具体区域。

## 4. 巨物和小元素的关系

允许：

- 巨型叶片 + 3–5 片同色小叶；
- 一架算盘 + 同一架算盘上的算珠；
- 一个信封 + 同色纸片；
- 一块织物 + 同源线迹。

不允许：

- 巨型叶片 + 月亮 + 飞船；
- 唱片 + 另一台留声机 + 金币；
- 为填空白加入与地点无关的彩球、鲸鱼、行星或花朵。

判断方法：所有小元素必须能被称作“这个巨物的一部分、碎片、痕迹或同源物”。

## 5. 单张质量门

逐项回答“是”后才能进入整组：

- 3 秒内能认出地点吗？
- 最重要的轮廓或建筑结构还在吗？
- 全图是否只有一个不可能巨物概念？
- 巨物是否与建筑、水面、道路或天空发生可见连接？
- 主色是否落在有边界的大区域，而不是只涂小物件？
- 单张是否只有 1–2 组主色？
- 大色域是否高纯度、哑光、无渐变、无透明和立体阴影？
- 小元素是否同源、3–5 个、有大小梯度和弧线节奏？
- 白色手绘线是否只有 2–3 条并服务于动势？
- 是否明亮、无文字、无水印、无无关装饰？

## 6. 整组质量门

联系表中检查：

- 九张是否像同一系列，而不是九种互不相干的画风？
- 是否至少有四个色相家族？
- 是否存在强—弱—强节奏，而非九张同样吵或同样灰？
- 是否连续三张使用同一着色区域和近似颜色？
- 黑白现实层、纸面和高纯度色域的比例是否大体一致？
- 第一张能否吸引点击，中段是否有停顿，最后一张能否收束？

## 7. 一次性纠偏表

只针对观察到的问题修改一次，其他已经成立的部分必须锁定：

| 观察到的失败 | 只修改这一项 |
|---|---|
| 彩色面积太小 | 把主色扩展到一个有来源的完整天空、水面或墙面边界 |
| 彩色区域发灰 | 将该区域改为 `vivid high-purity matte`，删除全局 `muted/dusty/restrained` |
| 地标认不出 | 恢复关键轮廓、视角和不可遮挡结构，缩小或移动巨物 |
| 巨物像贴纸 | 写明它从哪个结构延伸、变形或连接，并保留接触点 |
| 出现多个巨物 | 删除所有非同源焦点，只留一个概念 |
| 单张像彩虹 | 删到一个主色加一个辅色，小元素复用同色 |
| 色形变成 3D | 对背景区域补充 `flat matte, no gradients, no shadows on the color shapes` |
| 系列颜色重复 | 修改色相矩阵和着色区域，不在 prompt 末尾临时换色 |

如果一次纠偏后仍失败，换参考照片、换巨物连接方式或退回已通过版本，不继续无目标抽图。
