# UI Design Skills

一组用于 Figma UI 设计的 Agent Skills，包含设计系统使用、图标生成、流程连线和需求设计，帮助 Agent 以明确的规范与流程完成设计工作。

## Skills

### design-system-use · 设计系统使用

指导 Agent 使用已有设计系统生成设计稿，规范组件、样式、变量、布局的用法，并在交付前完成质量检查。

### icon-generate · 图标生成

从 iconfont、IconPark、Lucide、Tabler、Phosphor 和 Iconoir 中检索图标，在 Figma 中生成可编辑的图标组件，统一尺寸、描边、颜色和命名。

### flow-connect · 流程连线

根据交互流程，在 UI 稿中绘制流程连线、标签和判断节点。

### requirement-design · 需求设计

根据需求链接完成需求设计，包括整理需求信息、创建设计看板、分析页面、匹配历史稿、完成UI设计和交付检查，并在每个步骤开始与完成时反馈进展。

## Skills 之间的关系

```t
requirement-design
├── 页面设计阶段必须遵循 design-system-use
├── 需要新增或补充图标时使用 icon-generate
└── 需要绘制页面流程时使用 flow-connect
```

`design-system-use`、`icon-generate` 和 `flow-connect` 也可以独立使用。

## 使用前提

- 支持 Agent Skills 的 Codex 或兼容 Agent 环境；
- 可访问目标 Figma 文件及相关设计资产；
- 已连接能够读取和写入 Figma 的 MCP 工具；
- 使用 `requirement-design` 时，需要能够访问对应的 TAPD 看板、交互稿和 Design System；
- 使用 `icon-generate` 时，需要允许网络检索图标资源。

这套 Skills 根据个人工作流程整理而来，并非通用方案。使用前，请根据自身项目的流程、设计系统和工具环境进行调整。

## 安装

将需要的 Skill 文件夹完整复制到 Agent 的 Skills 目录。不要只复制 `SKILL.md`，否则配套的参考文件和示例会缺失。

以个人 Skills 目录为例：

```bash
mkdir -p ~/.agents/skills
cp -R skills/requirement-design ~/.agents/skills/
cp -R skills/design-system-use ~/.agents/skills/
cp -R skills/icon-generate ~/.agents/skills/
cp -R skills/flow-connect ~/.agents/skills/
```

不同 Agent 或不同版本的 Skills 目录可能不同，请以当前环境的说明为准。安装后重新打开会话，确认四个 Skill 已被发现。

## 使用示例

### 按 Design System 生成页面

```text
请根据这个交互稿完成视觉设计，并使用当前文件已启用的 Design System。
```

### 生成图标

```text
请使用 icon-generate，在这个 Figma 文件中生成 24×24 的线性“审批记录”图标。
```

### 绘制流程连线

```text
请使用 flow-connect，根据交互稿为这些视觉稿页面绘制流程连线。
```

### 完成需求设计

```text
看板链接：<TAPD 需求链接>
设计资产：<Figma 设计资产链接>
输出位置：XXX 页

请使用 requirement-design 完成这个需求。
```

## 目录结构

```text
ui-design-skills/
├── README.md
└── skills/
    ├── design-system-use/
    │   └── SKILL.md
    ├── icon-generate/
    │   ├── SKILL.md
    │   ├── sources.md
    │   └── examples.md
    ├── flow-connect/
    │   ├── SKILL.md
    │   ├── components.md
    │   ├── routing.md
    │   └── examples.md
    └── requirement-design/
        ├── SKILL.md
        └── references/
```

## License

如仓库根目录包含 `LICENSE` 文件，则本项目按照该文件所列条款授权。
