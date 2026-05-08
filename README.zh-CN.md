# openspec-schemas

[English](./README.md) · [繁體中文](./README.zh-TW.md) · [简体中文](./README.zh-CN.md)

社区贡献的 [OpenSpec](https://github.com/Fission-AI/OpenSpec) schema。每条 schema 都是一个自包含的包，你可以复制到项目的 `openspec/schemas/` 目录中，并通过 `--schema <name>` 按需选用。

## 本仓库中的 Bridges

| Bridge | 用途 | 状态 |
|--------|---------|--------|
| [`superpowers-bridge`](./superpowers-bridge/) | 将 OpenSpec 的 artifact 治理与 [obra/superpowers](https://github.com/obra/superpowers) 执行技能（头脑风暴、制定计划、通过子代理进行 TDD、代码审查、完成工作）桥接起来。添加了以证据为先的 `retrospective` artifact，填补了 Superpowers 原生不覆盖的空白。 | v1 |

## 为什么单独建一个仓库？

[OpenSpec PR #970](https://github.com/Fission-AI/OpenSpec/pull/970) 最初提议将 `sdd-plus-superpowers` 作为内置 schema。经过维护者审查后，集成工作移到了社区仓库——与 [github/spec-kit's community extension catalog](https://speckit-community.github.io/extensions/) 相同的模式，将第三方工具集成排除在核心之外。

优势：
- OpenSpec 核心不承受 Superpowers 的发布节奏
- Bridge 可以独立迭代
- 其他社区 schema 可以作为同级加入本仓库

## 安装

每个 bridge 目录都有独立的 `README.md`，包含一键安装的复制粘贴 Claude Code 提示，以及手动 bash 替代方案。参见 [`superpowers-bridge/README.md#install`](./superpowers-bridge/README.md#install)。

## 路线图

计划中的内容请参见 [`docs/roadmap.md`](./docs/roadmap.md)。

## 许可证

MIT —— 参见 [LICENSE](./LICENSE)。
