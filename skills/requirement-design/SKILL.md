---
name: requirement-design
description: >-
  根据 TAPD 看板完成需求的 UI 设计；
  创建需求 Section 和看板；
  分析交互稿并按设计时间匹配最新历史稿；
  区分无需调整页面、设计迭代页面和全新设计页面；
  使用 Design System 完成页面设计并交付 Figma 链接。
  当用户要求完成需求设计、根据交互稿出视觉稿或迭代设计稿时使用。
compatibility: 需要 Figma MCP（use_figma、get_metadata、get_screenshot、whoami），以及可访问的设计资产、交互稿和已启用的 Design System。
---

# 需求设计

## 依赖

| 时机 | 做法 |
|---|---|
| 任何 Figma 写入 | 先遵循 `figma-use` |
| 页面设计 | 遵循 `design-system-use` |
| 图标 / 流程连线 | 仅当用户当次需要 → `icon-generate` / `flow-connect` |


## 执行要求

1. 按步骤 1～7 顺序执行，不跳过步骤、不提前执行后续步骤。进入每一步前，完整阅读对应细则。
2. 每步开始实际操作前，先向用户说明步骤编号、名称和本步要做的事。
3. 每步结束时，报告实际结果和结论；按细则提供对应清单、记录或链接。不能仅回复“已完成”。
4. 当前步骤的结果完整且检查通过后，才进入下一步；先报告当前步骤完成，再说明下一步开始，可在同一条消息中反馈，无需逐步等待用户确认。
5. 步骤执行时间较长时，简要报告当前进展、已完成内容和剩余工作，不重复空泛的状态说明。
6. 无法继续时，明确当前步骤、已完成内容、阻塞原因及需要用户补充的信息；不得标记完成或跳到后续步骤。暂停条件见“完成与暂停”。
7. 反馈随实际执行发送，不得在交付时补写开始和完成记录。

## 步骤 1 — 获取看板信息

读 [board-info.md](references/board-info.md)。

进入步骤 2 前，先获取并整理完整的需求看板信息。

## 步骤 2 — 创建 Section 和需求看板

读 [create-section.md](references/create-section.md)。

## 步骤 3 — 整理页面清单

读 [page-list.md](references/page-list.md)。

## 步骤 4 — 查找并复制历史稿

读 [find-history.md](references/find-history.md)。

## 步骤 5 — 阅读设计备注并整理设计任务

读 [design-task.md](references/design-task.md)。

## 步骤 6 — 完成设计

读 [design-pages.md](references/design-pages.md)，并遵循 `design-system-use`。

## 步骤 7 — 交付

读 [delivery-checklist.md](references/delivery-checklist.md)。

## 完成与暂停

正常情况下，步骤 1–7 必须连续完成。

仅在以下情况可以暂停：

1. 缺少无法推断的必要信息；
2. Figma 或 Design System 无访问权限，或工具持续失败；
3. 用户明确要求暂停、缩小范围或只执行某一步骤。

步骤 4 完成后必须进入步骤 5；步骤 6 必须完成设计任务中明确列出的全部改动。
除步骤 5 经逐页对比确认的无需调整页面外，不得将历史稿或占位 Frame 直接作为终稿交付。

## 示例

遇到信息不完整、首次与非首次判断、页面分类或“仅改名称和文案”等边界情况时，读 [examples.md](references/examples.md)。
