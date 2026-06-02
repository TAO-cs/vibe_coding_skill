# Vibe Coding 中文标准工作流 Skill

这是一个用于 AI 辅助项目交付的标准 Skill。它将模糊想法、课程项目、AI 工具考核题目或混乱仓库整理为“文档先行、逐步实现、一步一验证、持续记录、可回退”的开发流程。

## 适用场景

- AI 工具使用考核
- 课程设计和项目展示
- 机器人、Web、数据分析、AI 应用、自动化脚本、可视化系统
- 从零启动新项目
- 将已有仓库规范化为文档先行的开发流程
- 使用 Codex、Claude Code、Cursor 等 Agent 工具进行项目开发

## 文件结构

```text
vibe-coding-standard-workflow-cn/
├── skill.md
├── README.md
└── references/
    ├── prompts.md
    ├── workflow.md
    └── examples.md
```

## 核心思想

- `skill.md` 是 Skill 主入口，存放执行规则和交付约束。
- `references/prompts.md` 存放可复制的阶段提示词。
- `references/workflow.md` 解释完整工作流和文档模板。
- `references/examples.md` 给出不同类型项目的套用示例。

## 项目运行时推荐生成的产物

```text
PRD.md
memory-bank/design-document.md
memory-bank/tech-stack.md
memory-bank/implementation-plan.md
memory-bank/progress.md
memory-bank/architecture.md
AGENTS.md 或 CLAUDE.md
README.md
changelog.md
```

## 使用方式

在支持 Skills 的环境中安装本文件夹后，当用户提出“帮我用 AI 完成一个完整项目”“帮我搭建 Vibe Coding 流程”“帮我把项目规范化”“帮我做 AI 工具考核项目”等需求时，调用本 Skill。

执行时不要一次性生成全部代码，而应先生成 PRD、设计文档、技术选型和实现计划，再逐步执行一个可验证步骤。

## 推荐最小流程

1. 项目初拟
2. 生成 `PRD.md`
3. 需求澄清
4. 生成 `memory-bank/design-document.md`
5. 生成 `memory-bank/tech-stack.md`
6. 生成 `memory-bank/implementation-plan.md`
7. 建立 `progress.md` 和 `architecture.md`
8. 一次执行一个计划步骤
9. 每步验证后更新项目记忆
10. 交付 README、测试说明、技术报告和答辩材料
