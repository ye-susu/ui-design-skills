---
name: design-system-use
description: 在 Figma 中创建、扩展、修改设计稿时使用本 skill。包括：根据交互稿/线框稿生成设计稿、按组件库生成界面、基于 Figma 链接生成或完善界面。无论用户是否提到「组件库」，只要任务要在 Figma 里产出或修改页面/界面/原型/设计稿，就必须先按本 skill 执行：优先复用已启用 Design System 的 Instance、Variables、Text Styles、Effect Style、Icon，并在交付前完成可执行的设计系统 QA。
compatibility: 需要可访问目标 Figma 文件及组件库。若无法访问：不得声称已复用库资产；说明限制与缺失项；可建立待替换的占位结构继续推进，但不得视为完成设计；交付说明中标注未完成原因。
---

# Design System Use

## 01. 身份与职责（Role）

你负责在 Figma 中使用已启用 Design System 产出设计稿。产出结果应可维护、可验收，并满足业务诉求。

### 职责边界

1. 交互稿、线框稿和需求说明是业务内容与流程的依据。
2. 全新设计页面及设计迭代中新增或修改的模块，保留交互稿中的模块顺序、内容分组及控件相对位置，不得自行调整。
3. 设计迭代页面中未涉及本次需求的历史模块，保持原有结构、布局和视觉样式。
4. 不得自行增加、遗漏或替换需求中的业务模块、字段、状态和文案；需求明确要求的变更除外。
5. 设计迭代页面中新增的模块及全新设计页面必须使用 Design System Instance；仅当 Design System 确实无对应组件时，才可按第 05 节 Components 第 6 条创建本地 Component。
6. 本次新增或修改的自建图层，其颜色、圆角、描边必须使用 Variables；自建文本必须使用 Text Styles，文本颜色必须绑定 Variables；用户明确要求使用阴影时，必须使用 Effect Style。
7. 不得自绘控件替代库中已有组件，不得臆造库中不存在的资产、属性或 token。
8. 设计细则按照后续章节执行，具体规则见第 05 节「设计规范」。

## 02. 工作目标（Objectives）

每次执行任务时，需满足以下目标：

1. 可对齐：设计稿对齐用户诉求，与交互稿的模块、信息层级、状态保持一致；文案按原意使用英文。
2. 可交付：设计稿满足本 skill 的交付要求；未通过质量检查或缺少交付说明时，不得视为完成。
3. 可审计：交付时必须给出复用清单、例外说明和 QA 结果；未列出则不算完成。

## 03. 核心设计原则（Core Principles）

1. 优先组件化设计，便于维护与修改。细则见第 05 节「设计规范」。
2. 设计稿文案必须使用英文；非英文来源按原意翻译。

## 04. 页面生成工作流（Workflow）

写入画布前必须完成第 1～3 步；未确认组件对应关系前，不得创建或修改页面。

1. **理解任务**：

对齐用户诉求，从需求说明、交互稿、线框稿中提取页面范围、模块、信息层级、状态与文案。

2. **读取 Design System**：

检索本次可用的组件与样式，记录可复用项与缺失项。确认本次使用的 Design System，并记录组件库名称与 fileKey；后续组件对应关系与组件来源检查均以此为准。

3. **确认组件对应关系**：

开始设计页面前，为设计迭代页面中新增的模块，以及全新设计页面中的全部模块确认组件来源：

| 页面模块 | 组件名称 | Component key | 来源组件库 | 使用方式 |
|---|---|---|---|---|
| … | … | … | … | … |

“使用方式”填写直接使用、设置 variant、Instance Swap、本次新增组件或无需组件。未找到匹配组件时，也必须在表中明确记录。

按模块的实际内容类型选择组件及 variant。结构或样式不同的内容分别确认组件对应关系，不因复用方便而统一改成同一种列表或卡片；库中没有对应组件时，按 Components 的缺失组件规则处理。

未完成组件对应关系前，不开始搭建页面。

4. **创建页面**：

全新设计时新建根 Frame；修改现有页面时使用任务指定的 Frame。历史稿可作为迭代基础，但不得未经调整直接作为终稿交付；经对比确认属于无需调整的页面除外。

5. **填充内容**：

按页面结构插入 Instance，并填入文案、Icon 与 Image。

6. **绑定样式与布局**：

完成 Variables / Styles 绑定，并设置 Auto Layout 与 Constraints。

7. **QA 与交付**：

按 QA 与设计规范检查并修复问题，输出交付说明。

## 05. 设计规范

### Layout Rules

#### 页面结构

1. 根 Frame 通常包含 StatusBar、NavBar、Content，以及按需出现的 BottomButton、Tabbar、Toast、Loading、Floating 等。
2. 图层顺序：Content 在最底层；StatusBar、NavBar、BottomButton、Tabbar、Toast、Loading、Floating 等叠在 Content 之上。
3. 根 Frame 默认 `360×800`。内容未超出时保持 `800` 高；内容超出 `800` 时，根 Frame 高度随 Content 增高。用户指定其他尺寸时从其指定。

#### Auto Layout

1. 根 Frame 不使用 Auto Layout；
2. Agent 创建的布局容器仅在 Content 及其内部使用 Auto Layout，Design System Instance 保留组件自身的布局设置；
3. Content 左右 Padding 默认 `16`。
4. Auto Layout 子元素（含文本）默认宽度 `Fill container`，高度 `Hug contents`。
5. 例外项：
  - 图标、头像、固定比例图片等：`Fixed`。
  - 标签、徽标等短内容：宽度 `Hug contents`。
  - 同一行文本与图标、按钮等并列：文本宽、高均为 `Hug contents`。
  - Design System 的 Instance 保留组件自身尺寸规则；可设置其在父级中的 Fill/Hug/Constraints，不修改 Instance 内部布局。
  - Toast、Loading、Floating 等不进入普通文档流，使用绝对定位 + Constraints。
6. 除第 4 条默认规则与第 5 条例外外，不另行设置宽高。

#### Constraints

1. StatusBar、NavBar：`Left + Right + Top`。
2. BottomButton、Tabbar：`Left + Right + Bottom`。
3. Content：`Left + Right + Top`；有底栏(BottomButton、Tabbar 等)时，Content 不与底栏在布局上重叠。
4. Toast、Loading：`Center + Center`。
5. Floating：`Right + Bottom`。

### Components

1. 只有来自当前指定并已启用的 Design System 组件库的组件，才能记为 Design System Instance。
2. Design System 中有对应组件时，页面控件必须使用其 Instance，不得自行绘制。
3. 组件来源检查仅适用于设计迭代页面中新增的模块，以及全新设计页面。
4. 无需调整页面和设计迭代页面中保留的历史模块，不纳入本次组件来源检查。
5. 历史稿或设计资产其他页面中的本地 Component，不得直接用于本次新增模块。
6. Design System 中确实没有对应组件时，才可创建本地 Component；标记为“本次新增组件”，不得命名为 `DS / …`。
7. 插入或复制 Design System Instance 后，保留其原组件名称，不添加任何前缀。
8. 使用组件前先查看组件属性，组件属性支持配置不同类型、尺寸、样式、状态、级别等。
9. 相同场景使用相同组件与 variant。
10. 禁止 detach Instance。
11. Design System 中已有完整组件时，禁止使用其子组件重新拼装。如 Tabs 中的 item。
12. 禁止对 Instance 的内部 layout 和视觉样式进行调整；父级中的 Fill / Hug / Constraints 除外。
13. 用途与结构相同的自建模块，重复使用时须先做成 Component 再引用；禁止复制普通 Frame 重复使用。

### Variables

1. 自建图层颜色、圆角、描边必须调用已有 Variables。
2. 优先使用 global 层 token，global 层 token 无法满足需求，可使用 base 层。
3. Design System 中没有语义合适的 Variables 时，记入缺失项，不写死裸值。

### Typography

1. 自建文本必须使用 Text Style，文本颜色绑定 Variables。
2. 按信息层级选择 Text Style，标题优先使用 Strong 样式。

### Icon

1. 优先使用 Design System 中的 Icon。
2. 库中无合适 Icon 时，按照 Design System 风格自绘。
3. 当以上均无法实现时，使用占位图层，并在交付例外项中列出。
4. 禁止使用 Emoji 、Image 充当 Icon。
5. 组件支持 Swap Instance 时，通过 Swap 替换 Icon，保持原尺寸与样式。

### Image

1. 交互稿或用户已提供图片时，优先复用对应素材，不自行替换图片承载的商品、活动等业务内容。
2. 需要新增通用配图或用户明确要求替换时，再生成符合场景的图片。
3. 所需素材无法获取时，使用名为 Image 的占位图层，并说明缺失项；不得将占位视为素材已完成。

### Effects

自建图层默认不使用阴影；用户明确要求使用阴影时，必须使用 Design System 中的 Effect Style。

### Naming

1. 根 Frame 沿用交互稿页面名称：Figma 链接源页面名或图片上的页面标题，不翻译为英文。
2. 自建图层禁止 `Frame 1`、`Rectangle 23`、`Group 9` 等无意义名称。

## 06. 质量检查（QA）

交付前必须完成检查，发现问题先修复，通过检查再交付。
用于设计迭代页面时，页面结构和 Design System 检查只覆盖本次新增或明确修改的内容。未涉及本次需求的历史模块不检查、不替换，也不得为满足当前 Design System 规范而重新搭建。
全新设计页面检查全部页面与图层；组件来源检查按照 Components 第 3～4 条执行。

### 对照检查

- [ ] 需求：页面范围、模块、状态与交互稿/用户诉求一致；界面文案为英文。
- [ ] 设计迭代页面中，修改范围之外的页面结构、布局、样式和模块与历史稿保持一致。
- [ ] Layout：根 Frame 不使用 Auto Layout；Content 及其内部承担布局的容器使用 Auto Layout；resizing 符合默认规则或例外项。
- [ ] Page Structure：根 Frame 已含任务所需关键层，图层顺序正确。
- [ ] Size：根 Frame 尺寸符合默认规范或用户指定。
- [ ] Constraints：关键层 Constraints 符合规范；Content 与底栏不重叠。
- [ ] 组件来源：设计迭代页面中新增的模块及全新设计页面中的全部模块，均已使用已确认的 Design System Instance；库中无对应组件时已按规范处理。无需调整页面和设计迭代页面中保留的历史模块，不纳入本次组件来源检查。
- [ ] Instance：无 detach；已有完整组件时不使用子组件重新拼装；不修改 Instance 内部 layout 和视觉样式。
- [ ] 组件化：重复自建模块已 Component 化。
- [ ] Variables：自建图层的颜色、圆角和描边均已绑定 Variables；缺失项不得作为完成项交付。
- [ ] Typography：自建文本已绑定 Text Style；颜色已绑定 Variables。
- [ ] Icon / Image：已填入真实 Icon / Image；不使用 Emoji；缺失已占位并声明。
- [ ] Effects：自建图层默认无阴影；用户明确要求阴影时，已使用 Design System 的 Effect Style。
- [ ] Naming：根 Frame 与交互稿页面名称一致（不译英）；无默认、无意义的图层名。
- [ ] 响应式：已在当前宽度及 440 宽度下检查，无溢出/重叠/截断。

## 07. 交付说明

完成 Figma 操作与 QA 后，以中文输出交付报告。
```markdown
## 交付报告

- 页面/Frame：
- 复用的组件及来源组件库：组件名称、组件库名称、fileKey
- 使用的变量与样式：
- 根 Frame：layoutMode、宽高
- QA 结果：对照检查通过项/总项；detach 数；Text Style 缺失数；Variables 未绑定数；响应式测试宽度与问题数
- 缺失与例外：
- 未通过项与处理：

```
