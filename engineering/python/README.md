# Python 基础工程（FastAPI）

本目录为 **结构骨架**，仅展示标准目录与最小配置，不保证可独立运行。完整约定见 Coding / Testing 规范。

## 技术栈
- FastAPI（异步 Web 框架）
- Pydantic v2 + pydantic-settings（数据校验与配置）
- Uvicorn（ASGI 服务器）
- pytest + httpx（测试）
- Ruff（Lint / Format）

## 目录结构
```
python/
├── pyproject.toml         # 依赖、构建与工具配置（ruff/pytest）
├── requirements.txt       # 等价依赖清单（便于 pip 安装）
├── app/
│   ├── main.py            # 应用入口：创建 FastAPI 实例、挂载路由
│   ├── api/               # 路由层（按资源分模块，router）
│   ├── models/            # Pydantic 模型 / ORM 模型
│   ├── services/          # 业务逻辑层
│   └── core/              # 配置、依赖注入、常量、异常处理
└── tests/                 # 测试代码（镜像 app 结构）
```

## 约定速览
- 路由（`api/`）只做请求解析与响应封装，业务下沉到 `services/`。
- 配置集中在 `core/config.py`，通过 `pydantic-settings` 读取环境变量。
- 模块导入使用绝对导入（`from app.api import ...`），避免相对导入混乱。
- 类型注解 100% 覆盖函数签名；详见 [Coding](../../coding/README.md)。
