# 文档规范（Documentation Standards）

本规范统一仓库内所有文档的结构、风格与维护方式，覆盖 README、Markdown 风格、API 文档、变更日志、架构决策记录（ADR）与日志。

---

## 1. 文档分层

| 类型 | 位置 | 用途 |
| --- | --- | --- |
| 仓库 README | 根 `README.md` | 仓库总览、结构索引、快速开始 |
| 模块 README | `engineering/<模块>/README.md` | 单模块结构、技术栈、本地运行 |
| 规范文档 | `engineering/{coding,agent,skill,testing,documentation}/README.md` | 编码 / agent / 技能 / 测试 / 文档规范 |
| API 文档 | `docs/api/` 或 OpenAPI | 接口契约 |
| ADR | `docs/adr/` | 架构决策及理由 |
| 日志 | `.workbuddy/memory/YYYY-MM-DD.md` | 每日工作记录（追加写） |

## 2. Markdown 风格

- 使用 **GFM**（GitHub Flavored Markdown）；标题层级从 `#` 开始不跳级。
- 中文文档用中文标点，中英文之间加半角空格（`Agent 生成的代码`）。
- 代码块必须标注语言（` ```ts ` / ` ```java ` / ` ```python `）。
- 表格用于对齐的对照信息（如命名表、框架表）。
- 行宽建议 ≤ 100，长链接用 `[描述](url)` 引用式。
- 禁止大段无结构正文；用标题、列表、表格分层。

## 3. README 结构（推荐）

每个 README 至少包含：
1. 一句话简介（这是什么）
2. 技术栈 / 依赖
3. 目录结构（树形）
4. 本地运行 / 构建步骤
5. 约定速览（指向对应规范）
6. 相关文档链接

## 4. API 文档

- 后端（Java / Python）接口须提供 **OpenAPI / Swagger** 描述（SpringDoc / FastAPI 自带）。
- 前端调用的接口在 `src/api/` 内以函数封装，函数上方注释指向接口路径与用途。
- 接口变更属于「公共契约变更」，需同步更新文档并写入变更日志。

## 5. 变更日志（Changelog）

- 采用 **Keep a Changelog** 风格，按 `Added / Changed / Fixed / Removed` 分类。
- 版本号遵循 SemVer；每个发布条目对应一个版本与日期。
- 破坏性变更必须显式标红并说明迁移步骤。

## 6. 架构决策记录（ADR）

- 任何「跨模块 / 难回退」的决策（技术选型、目录结构、规范变更）写入 `docs/adr/NNNN-<主题>.md`。
- ADR 模板：`状态 / 背景 / 决策 / 后果 / 备选方案`。
- 决策被推翻时标记 `Deprecated` 并链接新 ADR，不删除旧记录。

## 7. 日志与记忆

- 每日实质性工作追加到 `.workbuddy/memory/YYYY-MM-DD.md`（**仅追加，不覆盖**）。
- 跨项目 / 长期偏好写到用户级 `~/.workbuddy/MEMORY.md`。
- 日志只记「有长期价值」的内容（选型、约定、坑点），不记临时路径与工具报错。

## 8. 文档维护责任

- 代码与文档同步提交：改了行为就必须改对应文档，否则 CI / 评审驳回。
- 文档过期等同于 Bug；发现即修，重大过期在日志中标注。
- Agent 生成 / 修改代码时，须一并维护受影响的文档（Agent 规范第 1 节）。

---

> 配套文档：[Coding](../coding/README.md) / [Agent](../agent/README.md) / [Skill](../skill/README.md) / [Testing](../testing/README.md)
