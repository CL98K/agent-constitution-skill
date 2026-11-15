# 任务状态文件模板

> 仅为 `standard` 与 `team` 模式建立。触发条件、路径、身份冲突和恢复规则见 `../SKILL.md`。状态字段的唯一规范来源是 `../SKILL.md` §7；本模板只给出可填写的骨架。

```yaml
session_id: <稳定会话标识；无平台标识时为本会话生成并固定使用的 UUID>
objective: <对用户目标忠实的摘要；可选附简短原话引用>
accept:
  - id: A1
    criterion: <可观察的验收条件>
    source: user # user | derived
    status: pending # pending | passed | failed | unverified
    evidence:
      - <证据或未验证原因>
scope:
  - <本任务范围>
constraints:
  - <适用约束>
mode: standard # standard | team
state: running # running | waiting_user | paused | exception | done | aborted
flow: unverified # pass | fail | unverified
done: []
doing:
  - <当前工作>
blocked: []
risk: []
next:
  - <下一步>
updated_at: <含时区的时间>
retry_total: 0
teammates: [] # team 模式按需列 id、task、status、evidence、retry_count
```

## 填写提示

- 必须字段及取值按 `../SKILL.md` §7；不要在本模板或日志中另创状态 schema。
- `accept` 逐条记录来源、执行者检查状态和证据。`passed` 表示检查通过，不代表用户已验收。
- `flow` 是流程自检状态，与验收条件状态分开；证据不足时用 `unverified`。
- 仅记录平台实际提供的团队信息；单 Agent 执行时 `teammates` 可为空。
- 状态文件可按最新进度更新。切换目标前按主 Skill 归档旧目标摘要；不得覆盖身份不符的既有状态文件。

## 示意例

以下为完全虚构的结构示意，不是实际任务状态或验收证据：

```yaml
session_id: example-session-uuid
objective: 登录表单提交前校验邮箱格式
accept:
  - id: A1
    criterion: 非法邮箱会阻止提交并显示错误
    source: user
    status: unverified
    evidence: [尚未运行测试]
scope: [登录表单与相关测试]
constraints: [不改无关文件]
mode: standard
state: running
flow: unverified
done: []
doing: [检查现有校验实现]
blocked: []
risk: []
next: [确认可用的针对性测试]
updated_at: 2026-11-15T23:00:00+08:00
retry_total: 0
teammates: []
```
