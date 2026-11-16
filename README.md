# agent-constitution

将通用行为基线放入项目，将执行流程作为 Skill 安装一次，供多个项目复用。

## 使用方式

1. 把本仓库完整的 [agent-constitution](agent-constitution/SKILL.md) 目录安装到 Agent 平台支持的 Skill 位置，保留 `temp/` 和 `references/`。
2. 将仓库根的 [AGENTS.md](AGENTS.md) 复制到新项目根目录。项目只需这一份入口文件；项目事实可追加到其「项目补充」。
3. 通过平台的 Skill 列表或加载功能，确认能发现并读取名称为 `agent-constitution` 的 Skill。安装目录及是否需要重启由平台决定，不能只克隆 Git 仓库就假定安装完成。
4. 在新项目中执行任务。入口规则持续适用；多阶段、团队、恢复和异常流程按需加载 Skill 资源。

尚未在各平台执行安装/自动发现测试；这里提供的是通用分发方式，不声称特定平台会自动扫描本仓库。没有安装 Skill 时，AGENTS.md 仍提供基础规则，Agent 应明确说明详细流程不可用。Markdown 指令的执行依赖宿主和模型；需要强制门禁时，使用权限、CI 和独立验收机制。

## 文件分工

| 文件 | 职责 |
|---|---|
| [AGENTS.md](AGENTS.md) | 常驻八条行为原则、作用域、加载条件与缺失时的处理 |
| [SKILL.md](agent-constitution/SKILL.md) | 模式选择、目标跟踪、协作、异常、状态 schema 和默认阈值 |
| [temp/](agent-constitution/temp/scan-template.md) | 按场景读取的执行模板；沿用目录名，属于分发资源，不是待清理临时产物 |
| [自检](agent-constitution/references/self-check.md) | 交付证据、状态、文档与协作的一致性检查 |
| [规则来源](agent-constitution/references/incident-index.md) | 原稿历史与维护理由；历史要求不作为当前规则执行 |

## 执行规模

- `light`：咨询、短检查、小修改，做必要规划和验证，不产生状态文件。
- `standard`：多阶段或需恢复的执行，记录目标、判据、状态与关键证据。
- `team`：适合独立并行且有平台支持时启用；无成员可串行，Lead 也可实现和集成。

实现完成、检查通过和用户接受是不同结论；报告须保留实际失败和未验证项。状态 schema 与运行阈值以 Skill 主文件为单一来源。

## 维护与验证

修改规则时同步受影响模板，使用 [交付前自检](agent-constitution/references/self-check.md) 核查引用和行为一致性。运行期状态/日志不属于 Skill 分发文件；默认不提交。

[2.0.1 第一轮场景验证记录](verification/2026-11-16.md) 列出 30 个场景的实际执行、模拟与未验证项，以及试跑发现的 SCAN、状态序列化和异常示例修正。第二轮补测与最小原则边界审阅见 [计划](verification/2026-11-16-round2-plan.md) 和 [结果](verification/2026-11-16-round2-results.md)，包含平台限制、未测场景及 v2.0.2 规则澄清。两轮均是有限条件下的验证记录，不保证所有模型和平台一致执行。

本次格式依据：[AGENTS.md 开放格式](https://agents.md/)（标准 Markdown，无必填字段，支持目录作用域）与 [Agent Skills 规范](https://agentskills.io/specification)（必需名称/描述、相对资源引用和按需加载）。`temp/` 为合法附加目录，保留原有名称以避免无意义迁移。

许可证沿用仓库已有的 [Apache-2.0](LICENSE)。
