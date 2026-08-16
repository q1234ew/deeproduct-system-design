# 来源与致谢

## 方法来源

`deeproduct-system-design` 的初始方法体系来自对开源项目 [DeepSeek Harness](https://github.com/deepseek-ai/deepseek-harness) 工程实践的学习和总结，尤其受到以下公开内容启发：

- 项目根目录和各子目录的 `AGENTS.md` 分层工程规则；
- “一切皆插件”的系统组合方式；
- Service Definition、Provider、Consumer 组成的能力设计；
- 可逆副作用、异步所有权、提交点和静止式销毁等生命周期原则；
- 以持久事实为权威来源，并从事实派生投影和用户界面的状态设计；
- 在真正产生副作用的位置执行权限、验证和资源限制；
- 让单元测试、真实组合测试、快照、端到端测试和运行时不变量匹配不同影响面；
- 将当前系统说明、设计决策、操作指南和事故记录分别归档的文档治理方式。

这些思想主要来自 DeepSeek Harness 的 [`AGENTS.md`](https://github.com/deepseek-ai/deepseek-harness/blob/master/AGENTS.md)、[架构文档](https://github.com/deepseek-ai/deepseek-harness/blob/master/docs/architecture.md)、[测试文档](https://github.com/deepseek-ai/deepseek-harness/blob/master/docs/testing.md)及其包级开发说明。

## 本 Skill 的演化

本 Skill 没有把 DeepSeek Harness 的 Cordis API、包结构、事件名称、构建配置或 CI 规则作为通用要求。它将其中可复用的工程思想重新组织为产品系统设计流程，并扩展到 SaaS、工作流、第三方集成、数据平台、Web 应用和 Agent 系统。

本仓库中的工作流、参考指南、领域扩展、模板和评估标准为独立整理的通用内容。DeepSeek Harness 是重要的方法来源和案例，而不是运行时依赖。

## 致谢

感谢 [DeepSeek AI](https://www.deepseek.com/) 团队和 [DeepSeek Harness contributors](https://github.com/deepseek-ai/deepseek-harness/graphs/contributors) 公开项目代码、架构文档、工程规则和设计记录，使这些方法能够被学习、讨论和进一步泛化。

同时感谢 [Cordis](https://github.com/cordiverse/cordis) 项目及其贡献者。DeepSeek Harness 的插件化和组合设计建立在 Cordis 之上，本 Skill 关于能力边界、可替换实现和可逆注册的认识也受到了这些实践的启发。

DeepSeek Harness 采用 [MIT License](https://github.com/deepseek-ai/deepseek-harness/blob/master/LICENSE)。本项目是独立的社区方法整理，不是 DeepSeek AI 或 Cordis 的官方项目，也不代表其认可或背书。相关项目名称和商标归各自所有者。
