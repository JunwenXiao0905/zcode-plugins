# ECC 精选开发套件（ZCode 插件）

本仓库是一个 [ZCode](https://zcode.ai) 本地插件市场（marketplace），目前收录一个插件：

## ecc-dev — ECC 精选开发套件 v0.1.0

从 [affaan-m/ECC](https://github.com/affaan-m/ECC)（everything-claude-code，311 skills / 71 agents / 97 commands）按个人技术栈裁剪迁移而来的 ZCode 插件：

- **19 个子代理**：planner / architect / tdd-guide / code-reviewer / security-reviewer / docs-lookup / e2e-runner / refactor-cleaner / doc-updater / database-reviewer / build-error-resolver（通用 + Go/Java 版）/ 六语言 reviewer（Go、Python、TypeScript、Java、React、Vue）
- **30 个技能**：语言栈（Python/FastAPI、Go、Java/Spring Boot/MyBatis、PostgreSQL）、工程流程（TDD、代码审查、安全审查、验证循环、API 设计、数据库迁移、E2E）、前端（React/Vue/Vite）、基建（Docker/部署）、写作与研究（article-writing、market-research）
- **rules 归并**：ECC 的 12 个 rules 文件（1270 行）已去重归并进对应技能与 AGENTS.md，不随插件分发

裁剪依据：Python(FastAPI)/TypeScript(React+Vue/Vite)/Go/Java(Spring Boot+MyBatis) 的 Web 开发；不依赖 hooks；上下文固定开销约为 ECC 全量的 1/15。

### 安装

在 ZCode 客户端：**插件市场 → 添加 → 添加插件市场**，粘贴本仓库地址：

```
https://github.com/JunwenXiao0905/zcode-plugins
```

然后在 **个人 → junwen-plugins** 中找到 **ECC 精选开发套件**，点击安装。

### 主要改造（相对 ECC 上游）

- agent frontmatter 剥除 `model:` 字段（Claude 模型名在 ZCode 无对应，继承会话模型）
- `docs-lookup` 改用内置 WebSearch/WebFetch（去除 Context7 MCP 依赖）
- 清洗全部 `~/.claude/` 路径与 "Claude Code" 字样；修复 `tdd-workflow` 对未分发脚本的悬空引用
- 详见本人知识库《ECC迁移ZCode插件落档》

## 来源与许可

- 上游 [affaan-m/ECC](https://github.com/affaan-m/ECC) 以 [MIT](./LICENSE) 许可发布，本仓库的技能/子代理内容为其衍生作品，同样以 MIT 许可发布
- 上游同步：sparse clone 后对在用文件逐一 diff，遵循落档文档中的取舍清单
