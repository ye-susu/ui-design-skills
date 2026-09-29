# Flow System 组件约定

优先复用文件内已有 `Flow System` 母组件与变量；没有再创建。母组件放在独立 Section（如 `Flow System / Components`），勿与业务视觉稿重叠在一起。

## 变量（集合名 `Flow System`）


| 变量名               | 类型    | 默认值       | 用途           |
| ----------------- | ----- | --------- | ------------ |
| `color/flow`      | COLOR | `#04BF6A` | 连线、标签BG、菱形BG |
| `color/on-flow`   | COLOR | `#FFFFFF` | 标签/判断文字      |
| `radius/label`    | FLOAT | `4`       | 标签圆角         |
| `spacing/label-x` | FLOAT | `10`      | 标签左右内边距      |
| `spacing/label-y` | FLOAT | `4`       | 标签上下内边距      |


作用域按用途收窄，不要用 `ALL_SCOPES`。

## 文本样式


| 名称                              | 字体                    | 字号 / 行高 |
| ------------------------------- | --------------------- | ------- |
| `Flow System / Label Medium`    | `Noto Sans SC Medium` | 12 / 20 |
| `Flow System / Decision Medium` | `Noto Sans SC Medium` | 14 / 20 |


一律 `Noto Sans SC Medium`，不做其它中文字体回退。

## Connector Label

- 名称：`Flow System / Connector Label`
- 结构：Auto Layout 横排；底色绑 `color/flow`；圆角/内边距绑对应变量
- 文本属性：`说明`（TEXT）
- 实例：用属性覆盖文案；标签位置遵循 [routing.md](routing.md)。



## Decision Node

- 名称：`Flow System / Decision Node`
- 结构：组件内 `Rectangle` 名 `Diamond`，旋转 45° 成菱形；`cornerRadius=16`；填充绑 `color/flow`
- 文本属性：`判断条件`（TEXT）；字号 14；文字层居中对齐菱形（旋转定位见 [routing.md](routing.md)）
- 典型尺寸：外框约 `260×260`（边长 ≈ `260/√2` 的正方形旋转后对角线为 260）



## 命名


| 类型   | 命名                               |
| ---- | -------------------------------- |
| 折线   | `Flow / {起点语义} → {终点语义} / Arrow` |
| 标签实例 | `Flow / {起点语义} → {终点语义} / Label` |
| 判断实例 | `Decision / {条件简述} / Instance`   |


