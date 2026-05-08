## Why（变更理由）

<!--
说明本次变更的动机。这个变更解决什么问题？为什么是现在？

硬限制：50 ≤ 字符数 ≤ 1000（OpenSpec zod schema 会 validate）
- 太短：会收到 `Why section must be at least 50 characters` error
- 太长：会收到 `Why section should not exceed 1000 characters` error

建议结构：现状痛点 → 为什么现在处理 → 预期收益（各 1-2 句）
-->

## What Changes（变更内容）

<!--
描述将发生什么变化。具体说明新增能力、修改或移除内容。

对于有明确前后对比的行为变更，使用 From/To 格式（markdown 无 inline diff）：

**<Section or Behavior Name>**
- From: <当前状态 / 需求>
- To: <未来状态 / 需求>
- Reason: <为什么需要此变更>
- Impact: <breaking / non-breaking，谁受影响>

多个变更可重复此 block；纯新增或纯删除可用简单列表描述。
-->

## Capabilities（能力）

### 新增能力
<!--
引入的能力。将 <name> 替换为 kebab-case 标识符。
命名规则见 openspec/specs/README.md：使用复合名词（至少 2 个词），
例如 `user-auth`、`data-export`、`api-rate-limiting`，不用纯单词。
每个能力创建 specs/<name>/spec.md
-->
- `<name>`: <此能力涵盖内容的简要描述>

### 修改的能力
<!--
需求正在变更的现有能力（不仅是实现变更）。
仅在 spec 级行为变更时列出此处。每个需要 delta spec 文件。
使用 openspec/specs/ 中的现有 spec 名称。如无需求变更则留空。
-->
- `<existing-name>`: <什么需求正在变更>

## Impact（影响）

<!-- 受影响的代码、API、依赖、系统 -->
