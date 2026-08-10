# 前端基础工程（React + Vite + TypeScript）

本目录为 **结构骨架**，仅展示标准目录与最小配置，不保证可独立运行。完整可运行 starter 见 Coding / Testing 规范。

## 技术栈
- React 18 + TypeScript
- Vite 5（构建 / 开发服务器）
- Vitest（单元测试）
- ESLint + Prettier（代码质量 / 格式）

## 目录结构
```
frontend/
├── index.html              # 应用入口 HTML
├── package.json            # 依赖与脚本
├── vite.config.ts          # Vite 配置（含 @ -> src 别名）
├── tsconfig.json           # TS 严格模式配置
├── public/                 # 静态资源（不经打包）
└── src/
    ├── main.tsx            # 应用引导入口
    ├── App.tsx             # 根组件
    ├── components/         # 通用 UI 组件（纯展示，无业务耦合）
    ├── api/               # 接口请求封装（按领域分文件）
    ├── hooks/             # 自定义 React Hooks
    ├── utils/             # 纯函数工具
    ├── types/             # 全局 TS 类型 / 接口声明
    └── assets/            # 图片、样式等构建资源
```

## 约定速览
- 组件采用 **函数组件 + Hooks**，命名 `PascalCase`，文件同名。
- 一律使用 **严格模式**（`strict: true`），禁止 `any` 随意扩散。
- 路径导入优先使用 `@/` 别名，禁止深层相对路径（`../../`）。
- 详见 [Coding](../../coding/README.md)。
