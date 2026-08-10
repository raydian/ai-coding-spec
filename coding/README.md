# 编码规范（Coding Standards）

适用范围：本仓库下所有前端（React + Vite + TS）、Java（Spring Boot 3 + Maven）、Python（FastAPI）工程，以及由 AI 编码智能体（Agent）生成的代码。

目标：让人类与 Agent 产出的代码风格一致、可评审、可维护、可测试。

---

## 1. 通用原则

1. **可读性优先于聪明**：代码是写给人看的，机器只是顺便执行。
2. **单一职责**：函数 / 类 / 模块只做一件事，并做好。
3. **显式优于隐式**：不靠魔法，错误与边界要明确表达。
4. **杜绝重复（DRY）**：重复三次以上的逻辑必须抽取。
5. **类型即文档**：能用静态类型表达的不靠注释补。
6. **提交原子化**：一次提交只解决一个问题，可独立回滚。

## 2. 命名约定

| 元素 | TypeScript | Java | Python |
| --- | --- | --- | --- |
| 变量 / 字段 | `camelCase` | `camelCase` | `snake_case` |
| 常量 | `UPPER_SNAKE_CASE` | `UPPER_SNAKE_CASE` | `UPPER_SNAKE_CASE` |
| 函数 / 方法 | `camelCase` | `camelCase` | `snake_case` |
| 类 / 接口 / 类型 | `PascalCase` | `PascalCase` | `PascalCase` |
| 文件（组件/类） | `PascalCase.tsx` | `PascalCase.java` | `snake_case.py` |
| 文件（其他） | `kebab-case.ts` | — | `snake_case.py` |

- 命名要表意，禁止 `data`、`temp`、`obj`、`a/b/c` 等无意义名。
- 布尔量用 `is/has/can/should` 前缀（`isActive`、`hasPermission`）。
- 集合用复数（`users`、`items`）。

## 3. 格式与工具

| 栈 | 格式化 | Lint | 配置 |
| --- | --- | --- | --- |
| 前端 | Prettier | ESLint | `.prettierrc` / `.eslintrc` |
| Java | Spotless / 手动 | Checkstyle（可选） | `pom.xml` 插件 |
| Python | Ruff format | Ruff lint | `pyproject.toml [tool.ruff]` |

- **提交前必须本地通过 lint/format**，CI 中再次校验，不通过则阻断合并。
- 行宽：前端 100、Java 120、Python 100。
- 禁止 `// eslint-disable` / `# noqa` 绕过，确需跳过须写明原因并升级评审。

## 4. 注释与文档

1. **好代码少注释**：只在「为什么」而非「做什么」上注释。
2. 禁止描述代码本身（`// i++ 自增`）的废话注释。
3. 复杂业务逻辑、算法取舍、临时 workaround 必须写「原因 + 责任人 + 到期日」。
4. 公共 API / 导出的函数必须有简短 Docstring / JSDoc / JavaDoc。
5. 架构级、跨模块决策写入 ADR（见 Documentation），不在代码里长篇大论。

## 5. 错误处理

- **不吞异常**：空 `catch {}`、吞掉错误返回 `null` 一律禁止。
- 前端：统一错误边界 + 全局错误提示，异步请求必须有 `try/catch` 与加载态。
- Java：Controller 统一 `@RestControllerAdvice` 返回结构化错误；业务异常自定义、不抛 `RuntimeException` 裸异常。
- Python：定义 `app/core/exceptions.py` 业务异常层次，在 `main.py` 注册 handler。
- 对外错误信息脱敏，堆栈与内部细节不返回给客户端。

## 6. Git 提交约定（Conventional Commits）

```
<type>(<scope>): <subject>
```

- `type`：`feat` / `fix` / `refactor` / `test` / `docs` / `chore` / `perf` / `style`
- `scope`：模块名（如 `frontend`、`java`、`python`、`agent`）
- `subject`：祈使句、不超过 50 字、不加句号

示例：
```
feat(python): 新增图像推理接口 /image/generate
fix(frontend): 修复上传组件在 Safari 下的进度丢失
```

- 禁止超大提交（单提交 > 400 行需拆分）。
- 禁止把 `debug`、密钥、`.env` 提交进仓库。

## 7. 安全基线

- 密钥一律走环境变量 / 配置中心，禁止硬编码。
- 外部输入必须校验（前端轻校验 + 后端强校验，不可信任前端）。
- SQL / 命令拼接使用参数化，禁止字符串拼接。
- 输出到 HTML / 日志的内容做转义，防注入。

## 8. Agent 生成代码的额外要求

- Agent 产出须符合本规范第 2–7 节，并在 PR 描述注明「由 Agent 生成 / 修改范围」。
- Agent 不得修改它未被告知要改的文件（最小变更原则）。
- 生成代码必须附带对应测试（见 Testing），否则视为未完成。

---

> 配套文档：[Agent](../agent/README.md) / [Skill](../skill/README.md) / [Testing](../testing/README.md) / [Documentation](../documentation/README.md)
