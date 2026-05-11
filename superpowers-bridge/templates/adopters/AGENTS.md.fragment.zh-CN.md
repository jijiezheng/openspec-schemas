<!-- Source: superpowers-bridge/templates/adopters/AGENTS.md.fragment.md -->
<!-- 将此部分复制到项目 AGENTS.md 中，以便 Agent 正确路由后续工作。-->
<!-- 如有定制可修改 schema 名称和桥接仓库 URL；否则保持不变。-->

## 工作流路由（会话启动时阅读）

本仓库使用 [`superpowers-bridge`](https://github.com/jijiezheng/openspec-schemas/tree/main/superpowers-bridge) 桥接 OpenSpec 与 Superpowers。集成规则（语言、制品路径、PRECHECK）遵循该桥接的 README；本节为 Agent 提供路由指引。

### 入口路由

| 观察到的触发词 | 应对方式 |
|---|---|
| 用户开始"设计讨论 / 头脑风暴" | 运行口头的 `superpowers:brainstorming`，但**不要**写入 `docs/superpowers/specs/`。当对话符合以下 5 条标准时，提升为 `/opsx-propose` |
| 用户直接调用 `/opsx-propose` | 遵循 schema 流程；各步骤的制品说明会自动注入 |
| 用户明确说是 bug 修复 / 笔误 / 配置调整 / 文档更新 | 直接 PR——**不要**发起 change（见下方跳过规则） |
| 用户处于变更中途 | 用 `/opsx:continue`、`/opsx:apply`、`/opsx:verify` 或 `/opsx:archive` 推进 |

### 何时不用 opsx（直接 PR）

| 场景 | 直接 PR？ |
|---|---|
| 新功能 / 新能力 / 架构变更 / 破坏性变更 | ❌ 使用 opsx |
| Bug 修复（无契约变更）/ 补测试 / linter 调整 / 非破坏性升级 / 笔误 / 文档 / 配置值微调 | ✅ 直接 PR |

原则：**流程仪式与风险成正比**。外部契约 / schema / 跨系统集成 / 合规要求 → opsx。其他情况 → 直接 PR。

### 口头头脑风暴 → opsx 提升标准

在提升之前，以下 5 条必须全部满足（缺任一条 → 继续头脑风暴，**绝不**写入 `docs/superpowers/specs/`）：

1. **范围已锁定**——一句话描述包含什么 / 不包含什么
2. **主要设计分歧已解决**——已权衡各方案；待定项有负责人和影响范围说明
3. **跨系统依赖已梳理**——每项依赖明确：就绪 / 可 mock / 确实未知
4. **验收条件可陈述**——具体通过条件（如 `./mvnw clean verify` 通过 + N 项交付物）
5. **对话正在收敛**——最近几轮是确认而非新的"那如果...呢"

5 条全部满足时 → 主动提议"可以进入 `/opsx-propose` 了？"——等待用户确认，绝不自动触发。

### 前门反模式（不要这样做）

- 允许头脑风暴写入 `docs/superpowers/specs/`
- 允许 writing-plans 写入 `docs/superpowers/plans/`
- 在有未解决阻塞性 TBD 时提升为 opsx
- 为 bug 修复 / 笔误发起 change

详细说明：[superpowers-bridge README §Entry & exit gates](https://github.com/jijiezheng/openspec-schemas/blob/main/superpowers-bridge/README.zh-CN.md#%E5%85%A5%E5%8F%A3%E4%B8%8E%E5%87%BA%E5%8F%A3%E9%97%B8%E9%97%A8)。
