# 图标源检索参考

由 [SKILL.md](SKILL.md) 在检索时按需阅读。优先使用机器可读的公开接口；失败则跳过该源并记录原因。

## 前缀与 slug


| 库        | 前缀         | slug  |
| -------- | ---------- | ----- |
| iconfont | `iconfont` | 取英文语义 |
| IconPark | `iconpark` | 同上    |
| Lucide   | `lucide`   | 同上    |
| Tabler   | `tabler`   | 同上    |
| Phosphor | `phosphor` | 同上    |
| Iconoir  | `iconoir`  | 同上    |


## Iconify

搜索：

```text
https://api.iconify.design/search?query={q}&prefix={prefix}&limit=20
```

下载：

```text
https://api.iconify.design/{prefix}:{name}.svg?height=24&width=24
```

将 `currentColor` 换成 `#333`。

建议带浏览器 UA；Python `urllib` 若 403，改用 `curl`。


| 库           | prefix                            | 线性             | 面性                        |
| ----------- | --------------------------------- | -------------- | ------------------------- |
| Lucide      | `lucide`                          | 默认 stroke      | 无官方 filled → 使用线性替代       |
| Tabler      | `tabler`                          | `name`         | 有则用 `name-filled`         |
| Phosphor    | `ph`                              | `name`（常为填充勾线） | `name-fill`               |
| Iconoir     | `iconoir`                         | `name`         | 有则用 `name-solid`，无则使用线性替代 |
| IconPark 镜像 | `icon-park-outline` / `icon-park` | outline        | 面性优先 npm `filled`（见下）     |




### Phosphor

`ph:name` 的 regular 多为填充式描边，不是可调粗细的 stroke。线性任务可导入。若强要求真 stroke，优先 Lucide/Tabler/Iconoir。面性用 `ph:name-fill`。

### Tabler 面性

该语义没有 `*-filled` → 使用线性替代。

### Iconoir 面性

仅当存在 `*-solid`；无则使用线性替代。

## IconPark

**线性：** Iconify `icon-park-outline:{kebab}`，或 `@icon-park/svg` 的 `theme: 'outline'`。

**面性：** `@icon-park/svg` 的 `theme: 'filled'`。若结果几乎全是 stroke、无实心填充，视为无有效面性 → 用线性替代。避免直接交未处理的 Iconify `icon-park` 双色。

生成 filled 可：

```bash
npm install @icon-park/svg
```



## iconfont

没有稳定的任意图标公共 CDN 公式。可用搜索 API（可能需要登录 cookie）：

```text
https://www.iconfont.cn/api/icon/search.json
```

使用返回的 `show_svg`。名称尽量匹配「线性」「面性」。多为填充勾线——导入可编辑路径，能设 stroke 则设 2，勿 flatten。鉴权失败 → 跳过 `iconfont`。

## 选择图标优先级

1. 名称与语义完全匹配
2. 风格匹配（线性 / 面性）
3. 真 stroke（线性）或官方面性（面性）
4. 结构简单、单色；直角几何易拆成 Rectangle

语义含糊时选常见 UI 字形（返回 → `arrow-left` / `back`）。

## 跳过表


| 情况                    | 处理              |
| --------------------- | --------------- |
| 搜索无结果                 | 跳过该源            |
| 面性任务且无官方 filled/solid | 使用线性替代          |
| iconfont 鉴权/网络失败      | 跳过 iconfont     |
| Lucide 面性任务           | 使用线性替代          |
| SVG 导入失败              | 再试一个备选；仍失败则跳过该源 |


