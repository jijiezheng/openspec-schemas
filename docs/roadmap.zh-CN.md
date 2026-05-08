# 路线图

[English](./roadmap.md) · [繁體中文](./roadmap.zh-TW.md) · [简体中文](./roadmap.zh-CN.md)

本仓库作为副项目积极维护。下面的路线图勾勒了计划内容，但不是合约——项目可能会根据实际使用情况调整。

## v1 — 已发布

- [x] **`superpowers-bridge`** — 桥接 OpenSpec ↔ obra/superpowers + 原生 `retrospective` artifact

## v1.x — 后续待办

这些项目在 `~/.claude/plans/pr-quizzical-oasis.md`（实施计划）中追踪：

- [ ] **`workflow-retrospective` skill 打包** — 目前 retrospective 流程嵌入在 schema instruction 中（决策 3）。如果真实用户需要在 schema 流程外交互调用 `/workflow-retrospective`，则重新打包为 Claude Code 插件
- [ ] **端到端 CI 集成测试** — 当前 CI 只运行 `openspec schema validate`。往返测试（`/opsx:new` 到 `/opsx:archive`）可以捕获回归，但需要在 CI 中有 Superpowers
- [ ] **Verify artifact 5 个优化点** — 列在 v1.1 待办 A 中（模板清晰度、design 可选处理、worktree origin、通过标准、TDD 备注）

## 等待 OpenSpec 核心

这些无法在社区 schema 中解决：

- [ ] **`requires_skills:` schema 字段** — 将用引擎验证的声明替换提示 PRECHECK
- [ ] **`post_apply` phase** — 让 `verify` 和 `retrospective` 成为真正的 post-apply hooks，而不是存在时序错位的 artifacts（类似于 spec-kit 的 `after_implement`）

## 未来 bridge 候选

当有实际需求时：

- [ ] **`obra-bridge`** — 更广泛地集成其他 obra/* 工具（如果用户社区增长）
- [ ] **领域特定 schemas** — 例如，带有更强 schema 验证 artifacts 的 `data-pipeline` schema 变体

想推荐一个 bridge？在本仓库开 issue：https://github.com/JiangWay/openspec-schemas/issues
