# 方案模板

复制为 `docs/plans/<plan-id>.md`。`<plan-id>` 建议：`YYYY-MM-DD-short-slug`。

锁定后禁止 Implementer 擅自改 Acceptance / Out of scope / Required tests；若必须改，先征得 Principal 明确同意，并通知 Auditor 同步更新 `audit/cases/<plan-id>.md`。

约束：遵守悟仙契约——**一次只动一块路径**、**先路径后厚度**。方向未定时用「曳光探路」格式写薄路径，禁止先写完整分层骨架。

路径块名称由**宿主仓** `project.mdc` 定义；本模板不绑定任何业务目录。

## 元数据

| 字段 | 值 |
|------|-----|
| plan-id | |
| 里程碑 / 产品锁 | 宿主文档路径 / n/a |
| 路径块（单选，名从宿主） | |
| 目标分支 | feature → 默认主干（须 Principal 明示后开/合 PR） |
| 状态 | `DRAFT` \| `LOCKED` \| `IMPLEMENTING` \| `AWAITING_AUDIT` \| `DONE` |

## 背景（为何改）

（2–5 句）

## 曳光薄路径（必填；可保留路径，非可丢原型）

1. 入口 →  
2. … →  
3. 输出 / 交付  

若仅为学习：另开 `SPIKE / THROW-AWAY` 段落，验证完再写本正式 plan，禁止把原型当产品扩。

## In scope

- …

## Out of scope（哨兵）

- …

## Acceptance（可证伪，完成后审计逐条验）

- [ ] A1: …
- [ ] A2: …

## Required tests / 验证

- [ ] T1: 命令 / 断言 / 手动步骤 — …
- [ ] T2: （若无需自动化测试：写明理由；关键逻辑须有等价验证）

## 触及文件（预估；须落在单一路径块，除非 Principal 已同意跨路径块）

- …

## 不做清单 / 非目标

- …

## 实施对照表（Implementer 开发中维护，审计必查）

| 验收 ID | 实现位置（文件/符号） | 测试 / 验证 |
|---------|----------------------|-------------|
| A1 | | |
| T1 | | |
