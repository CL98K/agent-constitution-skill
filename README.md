# agent-constitution

通用行为基线随项目提供，执行流程作为可安装 Skill 复用。本 Git 仓库对应一个 Skill；多 Skill 工作区可在各 Skill 子目录分别维护仓库。

## Git 安装

将仓库克隆到平台支持的 Skill 根目录下，以 `agent-constitution` 作为安装目录名。示例使用 POSIX 路径；请按平台实际支持的扫描目录调整：

```sh
git clone https://github.com/CL98K/agent-constitution-skill.git "$HOME/.agents/skills/agent-constitution"
```

Skill 文件 `SKILL.md` 位于仓库根目录，`references/` 和 `temp/` 是随包资源，更新时在克隆目录执行 `git pull`。不要把仓库克隆到多 Skill 工作区的公共根目录，除非平台明确支持该布局；也不要仅凭克隆成功就认定已加载。

克隆后在平台的 Skill 列表或加载功能中确认能发现并读取名称为 `agent-constitution` 的 Skill。DSH 文件系统提供器的公开文档描述了项目、用户和自定义 Skill 根目录，但本仓库尚未在当前 DSH 安装上验证自动发现与该路径；如果目录未被识别，应按平台文档将仓库放入实际扫描根目录或配置自定义根目录。

## 在项目中使用

1. 将仓库根目录的 [AGENTS.md](AGENTS.md) 复制到目标项目根目录。项目已有该文件时先比较合并，不要直接覆盖。
2. 通过平台 Skill 列表或加载功能确认 `agent-constitution` 已可用。
3. 在项目中执行任务。`AGENTS.md` 提供持续适用的行为基线；多阶段、团队、恢复和异常流程按需加载 Skill 资源。

没有安装或无法加载 Skill 时，`AGENTS.md` 仍提供基础规则，Agent 应明确说明详细流程不可用。Markdown 指令执行依赖宿主和模型；需要强制门禁时，使用权限、CI 和独立验收机制。

## 文件分工

| 文件 | 职责 |
|---|---|
| [AGENTS.md](AGENTS.md) | 常驻行为原则、作用域、Skill 加载条件与缺失时的处理 |
| [SKILL.md](SKILL.md) | 模式选择、目标跟踪、协作、异常、状态 schema 和默认阈值 |
| [temp/](temp/scan-template.md) | 按场景读取的执行模板；属于分发资源，不是待清理的临时产物 |
| [自检](references/self-check.md) | 交付证据、状态、文档与协作的一致性检查 |
| [规则来源](references/incident-index.md) | 原稿历史与维护理由；历史要求不作为当前规则执行 |

## 执行规模

- `light`：咨询、短检查、小修改，做必要规划和验证，不产生状态文件。
- `standard`：多阶段或需恢复的执行，记录目标、判据、状态与关键证据。
- `team`：适合独立并行且有平台支持时启用；无成员可串行，Lead 也可实现和集成。

实现完成、检查通过和用户接受是不同结论；报告须保留实际失败和未验证项。状态 schema 与运行阈值以 Skill 主文件为单一来源。

## 维护

修改规则时同步受影响模板，使用[交付前自检](references/self-check.md)核查引用和行为一致性。运行期状态/日志默认不提交。

本 Skill 的格式依据：[AGENTS.md 开放格式](https://agents.md/)（标准 Markdown，无必填字段，支持目录作用域）与 [Agent Skills 规范](https://agentskills.io/specification)（必需名称/描述、相对资源引用和按需加载）。`temp/` 是合法附加目录，保留原有名称以避免无意义迁移。

许可证沿用仓库已有的 [Apache-2.0](LICENSE)。
