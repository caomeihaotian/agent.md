# AGENTS.md 中文模板

`AGENTS.md` 是给 AI 编程代理阅读的项目说明文件。

你可以把它理解为“写给 agent 的 README”：它提供一个固定、清晰、可预期的位置，用来告诉 Codex、Copilot、Claude Code 等代码代理如何理解项目、如何修改代码、如何运行测试，以及与你协作时应该遵守哪些沟通和工程规范。

本仓库用于保存我个人可复用的中文 agent 自定义指令，尤其适合“软件开发人员 + 大学计算机教师”的双重身份场景。

## 为什么需要 AGENTS.md

普通 README 通常面向人类开发者，关注项目介绍、安装、运行和贡献方式。

`AGENTS.md` 则更适合写给 AI 编程代理，重点包括：

- 项目的技术栈、目录结构和常用命令
- 修改代码前需要阅读哪些上下文
- 测试、格式化、构建和验证要求
- 代码风格、抽象边界和禁止事项
- 沟通偏好、解释深度和教学场景要求
- Git、提交、PR、敏感信息等协作规范

这些内容越具体，agent 越容易稳定地按你的方式工作。

## 本仓库包含什么

- [codex-custom-instructions.md](codex-custom-instructions.md)：适合放入 Codex 全局自定义指令的中文模板。
- `README.md`：说明这个模板仓库的用途、使用方式和推荐写法。

## 快速使用

### 作为 Codex 全局自定义指令

打开 [codex-custom-instructions.md](codex-custom-instructions.md)，复制其中适合你的部分，放入 Codex 的全局自定义指令中。

全局指令适合放这些内容：

- 你的身份和沟通偏好
- 默认语言和回答结构
- 通用编码要求
- 通用测试与验证要求
- 代码审查偏好
- 教学和文档偏好
- Git 与安全边界

### 作为项目级 AGENTS.md

在具体项目根目录创建 `AGENTS.md`，只放与该项目强相关的内容。

项目级指令适合放这些内容：

- 技术栈和主要模块
- 安装、运行、测试、构建命令
- 目录约定
- 代码风格和本项目特殊规则
- 不要修改的文件或目录
- 发布、提交、PR 或 CI 要求

建议做法是：

- 全局自定义指令：写“我是谁、我偏好什么、通用工程习惯”。
- 项目 `AGENTS.md`：写“这个项目怎么跑、怎么测、哪里不能碰”。

这样可以减少重复，也能避免不同项目的规则互相干扰。

## 最小示例

下面是一份简化版 `AGENTS.md` 示例：

```md
# Project Instructions

## 开发环境

- 使用 `pnpm install` 安装依赖。
- 使用 `pnpm dev` 启动本地开发服务。
- 修改前先阅读相关模块和测试，不要只根据文件名猜测行为。

## 测试要求

- 修改业务逻辑后运行 `pnpm test`。
- 修改类型、导入路径或公共接口后运行 `pnpm lint` 和 `pnpm typecheck`。
- 新增行为应补充测试，至少覆盖正常路径和关键边界条件。

## 编码规范

- 优先遵循现有代码风格。
- 保持改动范围小，避免无关重构。
- 不要引入大型依赖，除非收益明确并先说明原因。

## PR 要求

- PR 标题格式：`[模块名] 简短说明`。
- 提交前确认测试、格式化和类型检查通过。
```

## 适合我的扩展方向

由于我的身份同时包含软件开发和高校教学，本模板会特别关注：

- 工程质量：可维护性、可测试性、边界条件、协作流程。
- 教学表达：概念边界、学生常见误区、讲授顺序、练习设计。
- 代码审查：优先发现正确性、安全性、回归风险和测试缺口。
- 文档产出：README、实验指导、课程材料、作业反馈和技术说明。

## 推荐文件结构

```text
agent.md/
├── README.md
└── codex-custom-instructions.md
```

后续可以继续扩展为：

```text
agent.md/
├── README.md
├── codex-custom-instructions.md
├── templates/
│   ├── AGENTS.basic.md
│   ├── AGENTS.frontend.md
│   ├── AGENTS.backend.md
│   └── AGENTS.teaching.md
└── examples/
    ├── dotnet.AGENTS.md
    ├── python.AGENTS.md
    └── node.AGENTS.md
```

## 编写原则

- 写具体规则，不写空泛口号。
- 写可执行命令，不写“运行相关测试”这类模糊表达。
- 写项目真实约定，不照搬不适用的模板。
- 写 agent 容易犯错的地方，例如生成文件、锁文件、迁移脚本、生产配置。
- 规则要保持短小、明确、可维护。

## 参考来源

- [agentsmd/agents.md](https://github.com/agentsmd/agents.md)
- [agents.md 官网](https://agents.md/)
- [OpenAI Codex](https://github.com/openai/codex)
- [GitHub Copilot custom instructions](https://docs.github.com/en/copilot/how-tos/copilot-on-github/customize-copilot/add-custom-instructions)
