---
name: icon-generate
description: 基于 iconfont、IconPark、Lucide、Tabler、Phosphor、Iconoir 生成在 Figma 中可编辑的图标。 在用户要求生成/设计/输出/搜索图标时使用。
compatibility: 需要 Figma MCP（use_figma）与网络检索。写入前加载 figma-use。
---

# icon-generate

## 工作流

1. 解析需求
2. 检索图标
3. 写入与命名
4. 放入 Frame
5. 交付需求

具体规则见「规则详情」

输入输出示例见 [examples.md](examples.md)。

## 规则详情


| 主题   | 规则                                                                |
| ---- | ----------------------------------------------------------------- |
| 解析需求 | 明确语义、风格、尺寸、fileKey                                                |
| 图标来源 | 搜索 `6` 个图标库；有命中的源各写 1 个 component；取源细节见 [sources.md](sources.md)。 |
| 风格   | 默认线性；当用户指定面性、填充时输出面性；若该源无面性则用线性替代，并在交付中说明。                        |
| 尺寸   | 默认尺寸 `24*24`；当用户指定其它尺寸以`24*24`等比缩放。                               |
| 描边   | 描边粗细 `2`，可编辑描边，端点为 `none` ，转角为 `round`。                           |
| 颜色   | `#333`；镂空白`#fff`。                                                 |
| 圆角   | 有垂直正交拐角 → `Rectangle` + 可调整`cornerRadius`；纯曲线保持路径。                |
| 命名   | `{source}-{slug}-{size}` slug 取英文语义。                              |
| 画板   | 新建 Frame `icons-{语义}`，放入图标 component。                             |
| 交付   | 画板名 + 链接/node id · 已写组件名 · 跳过的源及原因。                               |




## 交付前自检

- [ ] 每个命中项生成一个 `{source}-{slug}-{size}` 图标组件。
- [ ] 线性 stroke=2；颜色 `#333`（镂空白除外）。
- [ ] 垂直正交拐角可调 cornerRadius。   
- [ ] 跳过项已说明。