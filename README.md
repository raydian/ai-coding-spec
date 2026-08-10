# ai-coding-spec

AI 驱动编码的**基础核心工程 + 规范集**仓库。目标是为前端、Java、Python 三套基础工程提供统一、可落地的开发规范，并沉淀 Agent / 技能 / 测试 / 文档的工程标准。

> 本仓库的工程目录为**结构骨架**，仅展示标准目录与最小配置；各规范的详细内容集中在与 `engineering/` 同级的对应英文目录的 `README.md`。

## 目录结构

```
ai-coding-spec/
├── README.md                  # 本文件：总览与索引
├── engineering/               # 基础工程目录（前端 / Java / Python 骨架）
│   ├── frontend/              # 前端基础工程骨架（React + Vite + TypeScript）
│   ├── java/                  # Java 端基础工程骨架（Spring Boot 3 + Maven）
│   └── python/                # Python 基础工程骨架（FastAPI）
├── coding/                    # 编码规范（Coding）
├── agent/                     # Agent 规范（Agent）
├── skill/                     # 技能规范（Skill）
├── testing/                   # 测试规范（Testing）
└── documentation/             # 文档规范（Documentation）
```

> 规范目录使用英文名称；`docs/` 名称保留给 API 文档与 ADR（`docs/api`、`docs/adr`），见 Documentation 规范。

## 基础工程栈

| 模块 | 技术栈 | 状态 |
| --- | --- | --- |
| 前端 | React 18 + Vite 5 + TypeScript + Vitest | 骨架（结构展示） |
| Java | Spring Boot 3.3 + Maven + Java 17 | 骨架（结构展示） |
| Python | FastAPI + Pydantic v2 + Uvicorn + pytest | 骨架（结构展示） |

各模块的目录布局、最小配置与本地运行说明见其 `README.md`。

## 规范文档索引

1. [Coding](coding/README.md) — 三栈通用的代码风格与提交约定。
2. [Agent](agent/README.md) — Agent 的职责边界、安全护栏与质量门禁。
3. [Skill](skill/README.md) — 技能的创建、结构与安全审计标准。
4. [Testing](testing/README.md) — 分层测试、框架选型与覆盖率要求。
5. [Documentation](documentation/README.md) — 文档结构、API 文档、ADR 与日志约定。

## 协作原则

- 人类与 Agent 产出的代码都必须遵守上述五份规范。
- 规范之间互相引用，改动任一规范须同步更新相关文档。
- 任何跨模块决策写入 ADR（见 Documentation）。

---

_由 WorkBuddy 依据需求脚手架生成，工程目录为结构展示，重点为五类规范文档。_
