# 审计验收规则：`<plan-id>`

> 由 Auditor 在方案锁定后创建。Implementer 不得改写本文件的验收标准与最终 VERDICT。

## 元数据

| 字段 | 值 |
|------|-----|
| plan | `docs/plans/<plan-id>.md` |
| status | `PENDING` \| `AUDIT_REQUESTED` \| `PASS` \| `FAIL` \| `BLOCKED` |
| created | YYYY-MM-DD |
| last_audit | — |

## 本方案专属验收规则

从方案 Acceptance / Required tests / Out of scope 展开（Auditor 填写，一条一行，可证伪）：

### Acceptance → 证据

| ID | 验收陈述（摘自方案） | 期望证据 | 结果 | 证据（路径/测试名） |
|----|----------------------|----------|------|---------------------|
| A1 | | 代码行为 / 测试 | PENDING | |
| A2 | | | PENDING | |

### Required tests / 验证

| ID | 要求（摘自方案） | 符号/命令/步骤 | 结果 | 备注 |
|----|------------------|----------------|------|------|
| T1 | | | PENDING | |

### Out of scope 哨兵

| 禁止项 | 是否出现在 diff | 结果 |
|--------|-----------------|------|
| | 否/是 | PENDING |

## 通用四轴（必须勾完）

- [ ] A 方案符合度：无 `MISSING_ACCEPTANCE` / `SCOPE_DRIFT` / `PLAN_MUTATION`
- [ ] B 测试/验证充分性：无 `TEST_GAP`
- [ ] C 一致性：无 `PLAN_CODE_MISMATCH`
- [ ] D 悟仙四问：无 `WUXIAN_VIOLATION`

### D 审法四问记录

| 问 | 结论（通过/风险/违规） | 证据 |
|----|------------------------|------|
| 知识唯一 | | |
| 一次一轴 | | |
| 可逆 | | |
| 非巧合 | | |

## 裁决

```text
VERDICT: PENDING
SCOPE_DRIFT: (none)
PLAN_MUTATION: (none)
MISSING_ACCEPTANCE: (none)
TEST_GAP: (none)
PLAN_CODE_MISMATCH: (none)
WUXIAN_VIOLATION: (none)
NOTES:
```

## 审计轮次日志

### Round 1 — YYYY-MM-DD

- 请求方：implementer
- 范围：`git diff` / 相关路径
- 结论：…
