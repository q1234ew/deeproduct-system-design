# Deeproduct System Design

`deeproduct-system-design` 是一个遵循 [Agent Skills](https://agentskills.io/) 规范的产品系统设计 Skill。它帮助 AI 基于产品目标和项目证据完成新系统设计、现有架构评审、能力演进与轻量技术决策，并主动抑制无依据的过度设计。

这套方法最初从开源项目 [DeepSeek Harness](https://github.com/deepseek-ai/deepseek-harness) 的分层 Agent 工程规则、插件架构、能力设计、生命周期管理、持久状态、测试证据和文档治理实践中总结并泛化，但核心流程不依赖 Agent、Cordis、特定框架、编程语言或云平台。领域指南覆盖 SaaS、工作流、第三方集成、数据平台、Web 应用和 Agent 系统。

> [!NOTE]
> 本项目是独立的社区方法整理，不是 DeepSeek AI 或 Cordis 的官方项目。详细的方法来源、演化范围和贡献者致谢见 [`ACKNOWLEDGEMENTS.md`](ACKNOWLEDGEMENTS.md)。

## 设计目标

- **证据驱动**：区分事实、推断、假设和提案，先理解现有系统再提出结构。
- **产品导向**：从用户结果、约束和非目标出发，而不是从架构模式出发。
- **责任清晰**：明确能力、状态、资源和异步操作的所有者。
- **生命周期完整**：覆盖提交、失败、取消、恢复、重试和清理，而不只描述成功路径。
- **安全可执行**：把验证、授权和限制放在真正产生副作用的位置。
- **适度设计**：没有当前需求或生产消费者时，不引入公共抽象、微服务、事件溯源或插件系统。
- **可验证交付**：让测试、运行时信号和发布策略匹配实际影响面。

## 适用场景

| 模式 | 使用时机 | 典型产出 |
|---|---|---|
| `greenfield` | 从零设计产品或系统 | 完整产品系统设计 |
| `review` | 评审已有代码库或架构 | 架构事实、重点发现与渐进改进方案 |
| `evolution` | 增加能力或重构现有系统 | 目标设计、兼容策略和阶段计划 |
| `lightweight` | 小型产品、原型或局部技术决策 | 精简设计记录 |

它适合需要讨论以下问题的任务：

- 领域和系统责任如何划分；
- 一项能力是否值得抽象；
- 哪份状态是权威事实，哪些只是投影或缓存；
- 长期任务如何取消、恢复和回收；
- 权限、凭据、租户隔离和外部调用在哪里执行；
- 如何验证真实装配路径并安全发布。

它不替代 PRD、UI 设计或具体编码 Skill。PRD 回答“为什么做、为谁做、做什么”，本 Skill 主要回答“系统如何组织、演进和验证”。

## 安装

### Pi 或兼容 Agent Skills 的工具

克隆仓库：

```bash
git clone https://github.com/q1234ew/deeproduct-system-design.git
cd deeproduct-system-design
```

链接到全局 Skills 目录：

```bash
mkdir -p ~/.agents/skills
ln -s "$PWD" ~/.agents/skills/deeproduct-system-design
```

重新启动 Agent 会话后即可自动发现。Pi 用户也可以显式调用：

```text
/skill:deeproduct-system-design review this repository's architecture
```

Pi 还支持直接加载路径：

```bash
pi --skill /absolute/path/to/deeproduct-system-design
```

> Skill 可以指导 Agent 读取代码、运行工具和修改文件。请在使用前检查 `SKILL.md` 及其引用内容。

## 使用示例

### 评审已有系统

```text
/skill:deeproduct-system-design review
请基于代码事实评审当前系统，找出最重要的三个责任、状态或生命周期问题，并给出渐进式改进方案。
```

### 设计 SaaS 能力

```text
/skill:deeproduct-system-design evolution
我们要增加团队工作区、成员邀请、角色和配额，请设计系统并避免不必要的分布式架构。
```

### 设计审批与第三方同步

```text
/skill:deeproduct-system-design
审批通过后需要同步第三方平台，请设计幂等、重试、取消、故障恢复和凭据管理。
```

### 做一个轻量决策

```text
/skill:deeproduct-system-design lightweight
这个小型内部工具是否需要事件总线？请基于当前消费者和故障需求给出决策。
```

## 工作方式

Skill 按以下流程工作：

1. 选择 `greenfield`、`review`、`evolution` 或 `lightweight` 模式；
2. 收集产品目标、代码和运行时装配证据；
3. 划分责任、能力及当前消费者；
4. 设计权威状态、生命周期和失败恢复；
5. 定位信任边界、安全控制和资源限制；
6. 判断真正需要的扩展点和兼容承诺；
7. 为风险匹配测试、运行时证据和发布方案；
8. 使用最小适用模板输出结果。

遇到证据不足时，它应说明被阻塞的决策、所需的最小证据和安全的临时选择，而不是虚构确定性。

## 方法结构

```text
deeproduct-system-design/
├── SKILL.md                     # 工作流、规则和按需加载入口
├── AGENTS.md                    # 本仓库维护规则
├── ACKNOWLEDGEMENTS.md          # 方法来源、演化范围与致谢
├── LICENSE                      # MIT License
├── references/
│   ├── core/                    # 通用产品系统设计方法
│   │   ├── problem-framing.md
│   │   ├── capability-design.md
│   │   ├── state-and-lifecycle.md
│   │   ├── boundaries-and-security.md
│   │   ├── extensibility.md
│   │   ├── verification.md
│   │   └── decision-documentation.md
│   └── domains/                 # 按系统类型选择性加载
│       ├── saas-and-multitenancy.md
│       ├── workflow-systems.md
│       ├── integration-platforms.md
│       ├── data-platforms.md
│       ├── web-applications.md
│       └── agent-systems.md
├── assets/                      # 系统设计、评审和轻量模板
└── evals/                       # 作者评估用例与评分规则
```

`SKILL.md` 保持简洁，Agent 只在任务相关时加载具体领域文档。这种渐进式披露可减少无关上下文，并避免把 Agent 系统的方法强行套到普通产品中。

## 输出模板

仓库提供三类模板：

- [`assets/system-design-template.md`](assets/system-design-template.md)：完整新系统设计；
- [`assets/architecture-review-template.md`](assets/architecture-review-template.md)：已有系统评审；
- [`assets/lightweight-design-template.md`](assets/lightweight-design-template.md)：局部或早期决策。

模板不是必填清单。不适用的部分应被省略，而不是用通用文字填满。

## 领域扩展

Skill 根据任务按需组合领域指南：

- SaaS：租户、成员、角色、配额和计费；
- 工作流：状态转换、幂等、重试、补偿和人工介入；
- 集成平台：Webhook、凭据、第三方故障和数据同步；
- 数据平台：Schema、血缘、质量、回填和服务投影；
- Web 应用：前后端状态、协议、响应式数据和 UI 组合；
- Agent 系统：模型输入、工具执行、会话生命周期、成本和评估。

例如，多租户 AI 工作流产品可以组合通用方法、SaaS、工作流和 Agent 指南，而普通后台不需要加载 Agent 规则。

## 评估方法

`evals/` 用于评估 Skill 自身，不会作为默认运行说明加载。

建议在缺少成熟架构指令的外部项目中分别运行：

1. 不加载 Skill 的基线回答；
2. 显式执行 `/skill:deeproduct-system-design` 的回答。

使用 [`evals/rubric.md`](evals/rubric.md) 比较问题理解、证据质量、责任划分、状态与生命周期、安全、演进、验证、可执行性和领域适配，并对以下情况扣分：

- 无依据引入复杂架构；
- 把推断写成事实；
- 创建没有生产消费者的公共抽象；
- 只在 UI、Prompt 或 Schema 中限制危险操作；
- 忽略不可逆迁移和回滚；
- 小问题强行套用完整模板。

当前评估案例覆盖小型 SaaS、工作流集成和已有系统评审。

## 来源与致谢

本 Skill 的初始设计方法来自对 [DeepSeek Harness](https://github.com/deepseek-ai/deepseek-harness) 公开工程实践的学习，重点包括“一切皆插件”、Definition / Provider / Consumer 能力设计、可逆副作用、异步生命周期所有权、持久事实与投影、执行点安全控制，以及按影响面选择验证证据。

感谢 [DeepSeek AI](https://www.deepseek.com/)、[DeepSeek Harness contributors](https://github.com/deepseek-ai/deepseek-harness/graphs/contributors)、[Cordis](https://github.com/cordiverse/cordis) 及其贡献者公开这些代码、文档和设计实践。本 Skill 对相关思想进行了通用化整理，不复制其项目专属 API 和工程约束，也不代表相关项目的官方立场或背书。完整说明见 [`ACKNOWLEDGEMENTS.md`](ACKNOWLEDGEMENTS.md)。

## 参与改进

修改方法时请遵循 [`AGENTS.md`](AGENTS.md)：

- 通用原则放入 `references/core/`；
- 特定系统规则放入 `references/domains/`；
- 工作流和路由规则留在 `SKILL.md`；
- 新增长期质量标准时同步更新评估 Rubric；
- 优先删除重复和无证据的规则，而不是持续扩充检查表。

提交前至少检查 Skill Frontmatter、相对链接、Markdown 格式，并在一个没有等价项目指令的外部代码库完成对照评估。

## License

本项目采用 [MIT License](LICENSE)。
