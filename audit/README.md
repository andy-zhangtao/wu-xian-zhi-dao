# 审计目录（Audit）

本目录是**方案执行偏移监控**的唯一落地处（拷入宿主仓后使用）。  
主体见 [`agent.md`](../agent.md)：**Principal 只出需求并拍板**；方案/代码/审计均由硅基完成。

禁止 Auditor 改产品代码；禁止 Implementer 自填 PASS；禁止把审计表甩给 Principal 填写。

## 目录约定

| 路径 | 谁写 | 用途 |
|------|------|------|
| `audit/README.md` | 流程维护 | 总则（本文件） |
| `audit/_TEMPLATE.md` | 同上 | 单次审计规则模板 |
| `audit/cases/<plan-id>.md` | **Auditor** | 本次验收规则与结论 |
| `docs/plans/<plan-id>.md` | **Implementer** | 锁定方案 |

`<plan-id>` 与方案文件同名。

## 审计要点（四轴，缺一不可）

### A. 方案符合度（Plan fidelity）

- 方案中每条 **Acceptance** 是否有对应实现证据（文件路径 + 符号/行为）
- 是否出现方案 **Out of scope** 中的改动 → `SCOPE_DRIFT`
- 是否擅自改写方案语义（未获批准就改 `docs/plans/`）→ `PLAN_MUTATION`

### B. 测试 / 验证充分性（Test sufficiency）

- 方案 **Required tests** 是否全部存在且指向正确行为
- 新增/修改的核心逻辑是否有单测或方案批准的等价验证
- 仅有烟雾、没有逻辑断言 → `TEST_GAP`（除非方案明确声明且 Principal 已批准）

### C. 方案与代码一致性（Plan ↔ code）

- 方案描述的行为与代码实际行为是否一致（含边界与失败路径）
- 注释/文案宣称与代码是否矛盾 → `PLAN_CODE_MISMATCH`
- 「做了更好的扩展」但方案未写 → 一律算偏移，不算加分

### D. 悟仙四问（Wuxian / 审法四问）

对照 `.cursor/rules/wuxian-contract.mdc` 与 Skill「审法四问」：

1. 知识是否唯一？  
2. 是否一次一轴？  
3. 决策是否可逆？  
4. 是否显式而非巧合？  

并检查：可测性、改到之处的破窗、是否违反「先路径后厚度」。任一项阻断 → `WUXIAN_VIOLATION`，不得 PASS。

## 裁决等级

| VERDICT | 含义 | 后续 |
|---------|------|------|
| `PASS` | 四轴相对 LOCKED plan 无阻断项 | Conductor 可报 `READY_FOR_PR`；**开/合 PR 须 Principal 明示** |
| `FAIL` | 存在阻断项 | Implementer 只修审计点；修完再次申请审计 |
| `BLOCKED` | 缺方案、缺 case、或无法取到 diff | 硅基先补齐产物；不得要求 Principal 写代码 |

阻断项类型：`SCOPE_DRIFT` | `PLAN_MUTATION` | `MISSING_ACCEPTANCE` | `TEST_GAP` | `PLAN_CODE_MISMATCH` | `WUXIAN_VIOLATION`

## 何时创建 / 更新 case

1. **方案锁定后**：Auditor 立即创建 `audit/cases/<id>.md`（从 `_TEMPLATE.md` 展开）。结论 `PENDING`。
2. **Implementer 申请审计后**：Auditor 只读对照方案 + diff + 验证，更新证据表与 `VERDICT`。
3. **FAIL 修复后再次申请**：同一 case 追加一轮，不新开 id（除非 Principal 要求新切片）。

## 禁止事项

- 无 `docs/plans/<id>.md` 就开始写业务代码
- Implementer 自评 `PASS` 或自己改写 `audit/cases/` 结论
- Auditor 为了变绿而修改产品代码或放宽验收项
- 把「建议优化」写进 PASS 条件（优化另开 plan）
- 跳过第四轴（悟仙四问）
