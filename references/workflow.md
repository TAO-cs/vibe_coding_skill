# Workflow Reference

## 1. Bootstrap

先将用户想法整理为 `PRD.md`。PRD 只负责捕获初始想法，包括项目名称、目标用户、用户问题、用户流程、核心功能、约束、假设和最小可运行版本。

## 2. Design

基于 PRD 进行需求澄清，形成 `memory-bank/design-document.md`。设计文档必须明确范围、非目标、用户流程、功能行为、数据或状态模型、异常情况和验收标准。

## 3. Tech Stack

基于设计文档生成 `memory-bank/tech-stack.md`。技术选型必须简单、稳定、可运行、易展示，并明确语言、框架、库、工具、运行环境和测试方式。

## 4. Memory Bank

建立长期项目记忆：

```text
memory-bank/
├── design-document.md
├── tech-stack.md
├── implementation-plan.md
├── progress.md
└── architecture.md
```

`memory-bank/` 是正式开发阶段的事实来源。

## 5. Implementation Plan

`implementation-plan.md` 必须 code-free。每个步骤都要小、具体、可验证，包含目标、涉及文件、任务、不做什么、验证方式和完成标准。

## 6. Execution Loop

每次写代码前读取完整 `memory-bank/`。只执行当前一步，不提前做下一步。完成后验证，验证通过再更新 `progress.md` 和 `architecture.md`。

## 7. Recovery

优先使用 Git 建立 checkpoint。若出现小错误，最小修复；若多文件混乱或稳定版本被破坏，回退到最近稳定版本。

## 8. Delivery

最终交付应包含可运行项目、README、测试说明、进度记录、架构记录、技术报告和答辩材料。
