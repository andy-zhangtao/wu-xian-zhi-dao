# 《悟仙之道》

把《程序员修炼之道》（*The Pragmatic Programmer*）压缩成 **AI 可执行的护栏与工序**：薄契约始终生效，短 Skill 按需触发；可选 **Conductor 流水线**（plan → 独立审计）约束 Bot 行动。

目标：缓解「开始简单，越开发越难维护」——尤其是 AI 高速生成带来的熵增。

**本仓库与任何具体业务无关。** 技术栈、改动块怎么划、商业规则由宿主项目在本地补充（见 [`ADOPT.md`](./ADOPT.md)）。

## 结构

```text
悟仙之道/
├── agent.md                           # 工作流宪法（Principal / Conductor / …）
├── AGENTS.md                          # Agent 入口指南
├── ADOPT.md                           # 宿主仓采用步骤
├── CLAUDE.md                          # → AGENTS.md
├── .cursor/
│   ├── rules/
│   │   ├── wuxian-contract.mdc        # 始终生效的契约
│   │   ├── output-style.mdc           # 张涛输出文风（排障 + 教程/文案）
│   │   ├── plan-first.mdc             # 无 LOCKED plan 不改产品路径
│   │   └── audit-handoff.mdc          # 独立审计交接
│   └── skills/
│       ├── conductor/                 # 默认调度 / 对 Principal 喉舌
│       ├── plan-implementer/          # 方案 + 代码
│       ├── plan-auditor/              # 只读审计
│       ├── 曳光探路/                  # Tracer Bullets
│       ├── 审法四问/                  # 生成后四问
│       └── 破窗重塑/                  # 小步重构
├── docs/plans/_TEMPLATE.md            # 方案模板
├── audit/                             # 审计总则与 case 模板
└── LICENSE
```

## 怎么用

### 方式一：最小采用（仅契约 + 文风）

复制 `.cursor/rules/wuxian-contract.mdc` 与 `.cursor/rules/output-style.mdc`（可选再加三个工序 Skill）。

### 方式二：完整流水线

按 [`ADOPT.md`](./ADOPT.md) 拷入宪法、门禁、六大 Skill、plan/audit 模板，并在宿主仓写本地 `project.mdc`（改动块划分 + 栈）。

### 方式三：按任务唤起 Skill

| 时机 | Skill |
|------|--------|
| 默认调度 / 新需求 | `conductor` |
| 新功能、方向未定 | `曳光探路` |
| AI 大段生成之后 / 审计第四项 | `审法四问` |
| 感到难维护、重复增多 | `破窗重塑` |
| 写方案与实现 | `plan-implementer` |
| 独立裁决 | `plan-auditor` |

## 设计原则

| 形态 | 职责 |
|------|------|
| **契约** | 每次生成都不能踩的线（否决权） |
| **宪法** | 谁写什么、何时可改代码、如何向 Principal 交差 |
| **Skill** | 有步骤的正确顺序（工序） |

不要做成一本厚 Skill 替代契约；也不要只写鸡汤法则却没有验收动作。  
不要把某一产品的目录、定价、框架写进本仓默认正文。

## 与原书的对应（摘要）

- DRY / 知识唯一 → 契约第 1 条  
- 正交性 → 契约第 2 条（一次一块）  
- 可逆决策 → 契约第 3 条  
- 不靠巧合编程 → 契约第 4 条  
- 为测试而设计 → 契约第 5 条  
- 破窗理论 → 契约第 6 条 / Skill「破窗重塑」  
- 曳光弹 → Skill「曳光探路」  

## 许可

MIT。理念源自 Hunt & Thomas《程序员修炼之道》，本仓库是面向 AI 编码场景的实践提炼，而非原书原文转载。
