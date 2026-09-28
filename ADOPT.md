# 采用指南（宿主仓库）

把本仓规范接到任意项目时，按「契约必带、流水线可选、业务本地补」三层处理。

## 最小采用（仅质量护栏）

复制到宿主仓：

- `.cursor/rules/wuxian-contract.mdc`
- `.cursor/rules/output-style.mdc`（对 Principal 的表达：张涛输出文风）
- （可选）三个工序 Skill：`曳光探路` / `审法四问` / `破窗重塑`
- 根目录 `AGENTS.md` 中引用契约与输出文风即可

## 完整采用（宪法 + Conductor 流水线）

再复制：

| 来源 | 宿主路径 |
|------|----------|
| `agent.md` | 仓库根 |
| `AGENTS.md` / `CLAUDE.md` | 仓库根（按宿主合并） |
| `.cursor/rules/plan-first.mdc` | `.cursor/rules/` |
| `.cursor/rules/audit-handoff.mdc` | `.cursor/rules/` |
| `.cursor/rules/output-style.mdc` | `.cursor/rules/`（若最小采用已拷可跳过；取代旧的 `plain-language.mdc`） |
| `.cursor/skills/conductor` 等六个 Skill | `.cursor/skills/` |
| `docs/plans/_TEMPLATE.md` | `docs/plans/` |
| `audit/README.md`、`audit/_TEMPLATE.md` | `audit/` |

然后**必须**在宿主仓新增本地文件（**不要** PR 回本上游）：

1. `.cursor/rules/project.mdc`（或等价名）  
   - 声明技术栈默认值（可逆）  
   - 声明目录轴（一次一轴的路径表）  
2. 按需改写 `plan-first.mdc` 中的「产品路径」列表，使其匹配宿主目录。  
3. 可选：`docs/PRD*.md`、`docs/TECH-SPEC*.md`、`docs/milestones/`。

## 禁止事项

- 把宿主产品的定价、上架、品牌、框架默认值写进对本仓的 PR，当作「通用默认」。  
- 用本仓示例目录冒充宿主真实结构而不改 `project.mdc`。  
- 启用流水线后仍跳过独立审计或要求 Principal 填审计表。

## 升级

从本仓 `main` 拉取契约与 Skills 更新时：保留宿主 `project.mdc` 与产品锁；解决冲突时以悟仙契约与 `agent.md` 语义为准。
