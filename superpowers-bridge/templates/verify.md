# 验证报告

> 此文件由 `openspec-verify-change` skill 在 apply 完成后产生，用以确认实现
> 与 specs / design / tasks 的一致性。失败的检查须返回对应 artifact 修正后
> 再重新运行 verify。

**变更**: `<change-name>`
**验证时间**: `YYYY-MM-DD HH:mm`
**验证者**: `<谁 / 哪个 agent>`

---

## 1. 结构验证 (`openspec validate --all --json`)

- [ ] 所有 items `"valid": true`

**结果**：

```text
<贴上 openspec validate --all 的输出摘要>
```

若有失败项目，列出 id + 问题：

| Item | 类型 | 问题 |
|---|---|---|
| — | — | — |

---

## 2. 任务完成 (`tasks.md`)

- [ ] 所有 `- [ ]` 已变为 `- [x]`

**未完成任务**（若有）：

| Task | 未完成原因 | 是否阻塞归档 |
|---|---|---|
| — | — | — |

---

## 3. Delta Spec 同步状态

对每个 `openspec/changes/<name>/specs/` 下的 capability 目录，与
`openspec/specs/<capability>/spec.md` 比对：

| Capability | 同步状态 | 备注 |
|---|---|---|
| — | ✓ 已同步 / ✗ 待同步 / N/A | — |

---

## 4. Design / Specs 一致性抽查

抽样比对 `design.md` 的决策是否反映在 `specs/*.md` 的 Requirements 与
Scenarios 中：

| 抽样项 | design 描述 | specs 对应 | 差距 |
|---|---|---|---|
| — | — | — | — |

**漂移警告**（非阻塞）：

- <若有，列出；无则填「无」>

---

## 5. 实现信号

- [ ] 工作目录内无非暂存的文件
- [ ] 所有相关 commit 已推送

**Commit 范围**（若知道）：`<from-sha>..<to-sha>`

---

## 6. 前门路由泄露检测（warning，非阻塞）

设计产出不应落在 `docs/superpowers/specs/`(brainstorm artifact 的
output redirection 会把它导到 `openspec/changes/<name>/brainstorm.md`)。

检测:

```bash
ls docs/superpowers/specs/*.md 2>/dev/null
```

- [ ] 无文件，或存在的文件是 schema 安装前的合法残留

**泄露清单**（若有）：

| 文件 | 内容是否已捕获进变更 | 建议动作 |
|---|---|---|
| — | — | — |

> 不会挡住 archive。新的 schema-installed cycle 产生的泄露，应搬进
> `openspec/changes/<name>/brainstorm.md` 或 `design.md` 后删原文件。

---

## 7. 推迟的手动 dogfood 与自动化测试等价性

对 plan.md 中标记 `[~]` deferred 的手动 dogfood / smoke task，逐项列出
等价的自动化测试覆盖。若没有等价自动化测试，该项应视为**真正的 gap**
而非合理 deferral，建议在 retrospective Misses 中记录。

| 推迟的 dogfood（plan §） | 等价自动化测试 | 覆盖评估 | 真正 gap? |
|---|---|---|---|
| 例:§11.3 `compose up + curl /actuator/health` | `LinebcIntegrationApplicationTests`（Testcontainers，24秒） | Spring context 启动 + Flyway 跑完 + 主要 bean 注入 | ❌ 已等价覆盖 |
| — | — | — | — |

> **判读规则**:
> - 「等价」= 自动化测试的断言集合是手动 dogfood 预期断言的超集
> - 「覆盖评估」= 列出实际被触及的层（context / DB schema / wiring / HTTP path 等）
> - 任何「真正 gap = ✅」的列，总体判定仍可「通过」，但须在 retrospective 留 follow-up 条目

> **何时可以整节空白**：plan.md 完全没有 `[~]` 标记的行时，本节不需要填（空白即通过）。
> 只要 plan.md 出现任何 `[~]`，本节必须逐项列出，否则总体判定应降为「不通过」。

---

## Overall Decision

- [ ] ✅ 通过 — 可进入 finishing-a-development-branch 与归档
- [ ] ⚠️ 有警告通过 — 可进入后续步骤但需注意：`<说明>`
- [ ] ❌ 不通过 — 返回失败的 artifact 修正后重新运行 verify

**下一步**：

<说明下一个动作>

(End of file - total 131 lines)