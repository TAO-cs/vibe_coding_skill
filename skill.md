---
name: vibe-coding-standard-workflow-cn
description: 中文标准 Vibe Coding 工作流。用于将模糊项目想法或混乱代码仓库转化为文档先行、逐步实现、一步一验证、持续记录、可回退的 AI 辅助项目交付流程。适用于 AI 工具使用考核、课程设计、机器人项目、Web 项目、数据分析项目、AI 应用、自动化脚本和科研原型项目。
---

# Vibe Coding 中文标准工作流

## 使用场景

当用户需要从零启动项目、整理已有仓库、完成 AI 工具使用考核、课程设计、原型系统、机器人项目、Web 项目、数据分析项目、AI 应用或自动化工具时，使用本 Skill。

本 Skill 的目标不是直接生成完整代码，而是将项目纳入“文档先行、单步执行、持续记录、可验证、可回退”的受控交付流程。

## 核心原则

- 先文档，后代码。
- 先最小可运行版本，后功能扩展。
- 一次只执行一个可验证步骤。
- 当前步骤未验证前，不进入下一步骤。
- 技术选型必须来自设计文档，不凭空追求热门技术。
- `implementation-plan.md` 只写任务，不写代码。
- `progress.md` 是执行日志，不是设计文档。
- `architecture.md` 是当前文件结构和模块职责地图，必须保持更新。
- 出错时先判断最小修复还是版本回退，不连续盲改。
- 交付时必须能说明语言、技术、依赖、运行方式、测试方式和 AI 工具使用链路。

## 标准产物

项目应创建并维护以下文件：

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

文件职责：

- `PRD.md`：项目启动阶段的轻量想法捕获文件。
- `memory-bank/design-document.md`：正式设计文档，记录范围、非目标、用户流程、功能行为、数据状态、边界情况和验收标准。
- `memory-bank/tech-stack.md`：技术选型文档，记录语言、框架、库、工具、运行环境、测试方式和替代方案。
- `memory-bank/implementation-plan.md`：实现计划，必须 code-free，每一步小、具体、有顺序、可验证。
- `memory-bank/progress.md`：执行进度日志，记录已完成步骤、验证结果、问题和当前状态。
- `memory-bank/architecture.md`：架构记录，维护重要文件、模块职责、调用关系和重大变更。
- `AGENTS.md` / `CLAUDE.md`：Agent 工作规则，约束写代码前读取项目记忆库。
- `README.md`：项目说明、安装、运行、测试和使用说明。
- `changelog.md`：版本变化记录，推荐维护。

`PRD.md` 是启动文件。项目进入正式开发后，`memory-bank/` 是长期事实来源。

## 执行流程

### 1. 项目初拟

将用户的初始想法整理为可评估项目。若用户方向不明确，给出不超过 3 个候选方案，并推荐最稳妥、最容易跑通、最适合展示的方案。

必须明确：项目名称、目标用户、用户问题、应用场景、核心功能、推荐语言、推荐技术栈、最小可运行版本、最终展示效果、主要约束和合理假设。

### 2. 生成 PRD.md

创建轻量级 `PRD.md`，包含：项目名称、目标用户、用户问题、项目目标、主要用户流程、核心功能、关键约束、当前假设、最小可运行版本范围、暂不实现内容和待澄清问题。

PRD 只用于承接初始想法，不在此阶段写成完整技术方案。

### 3. 需求澄清

读取 `PRD.md` 后检查需求是否足以进入正式设计。重点检查项目范围、非目标、用户流程、功能行为、输入输出、数据或状态模型、异常情况和验收标准。

若仍有歧义，提出必要且集中的澄清问题。若用户要求快速推进，可基于合理假设继续，并将假设写入设计文档。

### 4. 生成 design-document.md

将澄清后的需求沉淀为 `memory-bank/design-document.md`。至少包含：项目背景、项目目标、项目范围、非目标范围、用户流程、功能行为、数据或状态模型、边界情况、异常处理和验收标准。

设计文档必须足以支撑技术选型和实现计划。

### 5. 生成 tech-stack.md

根据 `design-document.md` 生成 `memory-bank/tech-stack.md`。优先选择简单、稳定、易实现、易展示的技术。

必须明确：编程语言及理由、框架或不使用框架的理由、第三方库及用途、开发工具、运行环境、安装方式、启动方式、测试方式、可替代方案及不选择原因。

### 6. 建立 memory-bank

创建并维护：

```text
memory-bank/
├── design-document.md
├── tech-stack.md
├── implementation-plan.md
├── progress.md
└── architecture.md
```

规则：设计事实写入 `design-document.md`；技术事实写入 `tech-stack.md`；可执行任务写入 `implementation-plan.md`；执行日志写入 `progress.md`；文件地图和模块职责写入 `architecture.md`。

### 7. 写入 Agent 工作规则

在 `AGENTS.md` 或 `CLAUDE.md` 中写入：

```md
## 重要提示

- 写任何代码前必须完整阅读 `memory-bank/architecture.md`
- 写任何代码前必须完整阅读 `memory-bank/design-document.md`
- 写任何代码前必须完整阅读 `memory-bank/tech-stack.md`
- 写任何代码前必须完整阅读 `memory-bank/implementation-plan.md`
- 写任何代码前必须完整阅读 `memory-bank/progress.md`
- 每完成一个重大功能或里程碑后，必须更新 `memory-bank/progress.md`
- 每完成一个重大功能或里程碑后，必须更新 `memory-bank/architecture.md`
- 不允许跳过当前步骤直接执行下一步骤
- 不允许在未验证当前步骤的情况下继续扩展新功能
```

若 `AGENTS.md` 和 `CLAUDE.md` 同时存在，保持规则一致。

### 8. 生成 implementation-plan.md

根据 `design-document.md` 和 `tech-stack.md` 生成 `memory-bank/implementation-plan.md`。

计划要求：code-free、小步骤、有顺序、可独立执行、可独立验证、有完成标准、先最小可运行版本后增强功能。

每个步骤包含：步骤编号、步骤目标、涉及文件或模块、具体任务、不做什么、验证方式、完成标准。

禁止将“完成后端”“完成前端”“完善功能”“优化项目”“写完测试”等模糊表达作为独立步骤。

### 9. 功能板块与模块分类

写代码前完成板块和模块拆分。

功能板块应区分核心板块、辅助板块、展示板块、测试板块和文档板块。每个板块记录作用、输入、处理逻辑、输出、依赖关系和是否属于最小可运行版本。

模块分类应输出项目目录树、文件或组件职责、输入输出、关键函数或类、模块调用关系、测试需求和推荐开发顺序。

### 10. 执行单步实现

执行阶段一次只做 `implementation-plan.md` 中的一个步骤。

写代码前必须重新读取：

```text
memory-bank/design-document.md
memory-bank/tech-stack.md
memory-bank/implementation-plan.md
memory-bank/progress.md
memory-bank/architecture.md
```

执行时只实现当前步骤，不提前实现下一步。新增或修改文件时说明原因。完成后给出运行命令或测试方式。当前步骤未验证前，不进入下一步骤。

### 11. 单步验证

每完成一个步骤后验证：当前步骤是否完成、是否满足验收标准、是否与设计文档一致、是否影响其他模块、是否需要更新 `progress.md` 和 `architecture.md`。

通过后，向 `progress.md` 追加简洁记录，并更新 `architecture.md`。未通过时，说明问题、给出最小修复方案，并判断是否需要版本回退。

### 12. 历史记录与版本回退

优先使用 Git。若环境不支持 Git，则使用手动备份目录。

推荐版本节点：

```text
v0.1 项目结构初始化
v0.2 最小功能跑通
v0.3 核心交互或可视化完成
v0.4 测试通过
v1.0 最终展示版本
```

推荐命令：

```bash
git init
git add .
git commit -m "chore: initialize project structure"
git status
git log --oneline
git checkout -b feature/<feature-name>
git checkout main
git merge feature/<feature-name>
git tag v0.1
```

回退原则：小范围错误优先最小修复；多文件混乱或稳定版本被破坏时优先回退；回退前记录当前问题和最近修改；回退后先验证稳定版本。

常用回退命令：

```bash
git restore <file>
git restore .
git reset --hard HEAD
git checkout <commit-id>
```

`git reset --hard` 会丢弃未提交修改，执行前必须确认。

### 13. 报错修复

报错处理流程：识别类型、定位文件与行号、判断是否由最近修改引入、给出最小修复方案、判断是否需要重构、判断是否需要回退、给出验证命令、更新 `progress.md`，必要时更新 `architecture.md`。

禁止在未定位原因前连续大改代码。

### 14. 模块测试

每个核心模块完成后进行模块测试。测试内容包括功能概述、输入输出、正常用例、异常用例、边界用例、自动化测试方式、运行命令和通过标准。

优先使用项目技术栈中简单稳定的测试工具。例如 Python 项目可使用 `pytest` 或 `unittest`。

### 15. 集成测试

多个模块完成后进行集成测试。重点检查模块调用关系、文件导入路径、参数传递、数据格式、主流程完整性、循环依赖、命名一致性、异常情况和与 `design-document.md` 的一致性。

集成测试必须给出测试流程、测试用例、重点接口、问题清单、修复建议和最终验收标准。

### 16. 项目优化

最小可运行版本通过后再优化。优化分为：必须优化、推荐优化、有时间再优化、当前不建议优化。

优先处理影响稳定性、运行和验收的问题；其次处理展示效果、用户体验、日志、异常处理、参数配置、测试和文档；避免引入复杂度高、风险高、收益不明确的功能。

### 17. 文档整理

交付前整理 `README.md`、使用说明、测试说明、技术报告、`changelog.md`、`progress.md`、`architecture.md`、答辩稿和 FAQ。

文档必须简洁、可提交、可复现，并说明语言、技术、依赖、运行方式、测试方式和 AI 工具使用链路。

### 18. 技术报告与答辩材料

技术报告包含：项目背景、项目目标、需求分析、技术选型、系统设计、模块设计、核心技术或算法、实现过程、测试方案与结果、AI 工具使用过程、项目亮点、不足与改进、总结。

答辩材料包含：3 分钟讲稿、5 分钟讲稿、展示流程、项目亮点话术、常见问题与回答。

答辩表述重点：不是简单让 AI 替用户写代码，而是使用 AI 完成项目初拟、需求分析、技术选型、模块拆分、代码实现、调试修复、模块测试、集成测试、版本记录、文档整理和技术报告撰写的完整工程流程。

## 非协商规则

- 不在需求不清楚时直接写代码。
- 不一次性生成整个项目。
- 不跳过设计文档和技术选型。
- 不让 `implementation-plan.md` 包含代码。
- 不执行未验证的下一步。
- 不把 `progress.md` 写成设计文档。
- 不让 `architecture.md` 过期。
- 不只保留最终代码，必须保留进度、架构、变更和回退记录。
- 不在代码出错后盲目连续修改，必须先判断最小修复还是版本回退。
- 不引入超出最小可运行版本太多的复杂功能。

## 最小交付标准

项目至少达到以下状态才算完成：

- `memory-bank/design-document.md` 已完成。
- `memory-bank/tech-stack.md` 已完成。
- `memory-bank/implementation-plan.md` 已完成，且无代码内容。
- `memory-bank/progress.md` 记录了主要执行过程。
- `memory-bank/architecture.md` 记录了当前文件结构和模块职责。
- 最小可运行版本可以启动。
- 核心功能通过验证。
- README 能说明安装、运行和测试方式。
- 有基本测试记录。
- 有项目总结或技术报告。
- 有版本回退或备份方案。

## 执行风格

- 使用中文。
- 输出简洁、明确、可执行。
- 优先表格和清单，但避免过度碎片化。
- 对用户已给出的信息不要重复追问。
- 信息不足时先提出关键问题；时间紧时基于假设推进。
- 始终优先稳定、可运行、可展示。
