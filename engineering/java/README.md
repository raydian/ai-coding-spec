# Java 端基础工程（Spring Boot 3 + Maven）

本目录为 **结构骨架**，仅展示标准分层目录与最小配置，不保证可独立运行。完整约定见 Coding / Testing 规范。

## 技术栈
- Spring Boot 3.3（Java 17）
- Maven 构建
- Spring Validation（参数校验）
- JUnit 5 + Spring Boot Test（测试）

## 目录结构
```
java/
├── pom.xml                              # Maven 依赖与构建
├── src/main/java/com/example/demo/
│   ├── DemoApplication.java             # 启动类（@SpringBootApplication）
│   ├── controller/                      # 控制器层：接收请求、参数校验、返回 DTO
│   ├── service/                         # 业务层：核心逻辑，事务边界
│   ├── repository/                      # 数据访问层：JPA / MyBatis Mapper
│   ├── model/                           # 实体 / DTO / 枚举
│   └── config/                          # 配置类（Bean、拦截器、WebMvc 等）
├── src/main/resources/
│   ├── application.yml                  # 主配置
│   └── application-{env}.yml            # 环境配置
└── src/test/java/com/example/demo/     # 测试代码（镜像主代码包结构）
```

## 分层约定速览
- **Controller** 不做业务，只做参数接收、`@Validated` 校验、调用 Service、包装响应。
- **Service** 承载业务逻辑与 `@Transactional` 边界，禁止在 Service 直接写 SQL。
- 包名全小写、逆向域名（`com.example.demo`）；类名单词首字母大写。
- 详见 [Coding](../../coding/README.md)。
