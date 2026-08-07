# RealWorld 项目中文教程（2026-08-07）

## 项目用途

RealWorld（又称 Conduit）是一个标准化的全栈博客示例项目。它把用户注册、登录、文章发布、编辑、评论、标签、收藏和关注作者等常见需求组合成一个完整应用，并通过统一的业务模型和 API 规范，帮助开发者使用不同技术栈实现同一个产品。

`github-daily-explorer` 用来持续记录项目学习和工程实验。本教程适合用来理解前后端分离、REST API、身份认证、数据库迁移、测试与部署；它不是生产环境配置的替代品，实际命令应以所选 RealWorld 实现的 README 为准。

## 实际使用场景

- 教学：用真实业务模块练习全栈开发，而不是只编写孤立的示例页面。
- 技术选型：使用相同需求比较 React、Vue、Angular 以及不同后端框架的实现方式。
- API 联调：验证登录、文章 CRUD、评论、收藏等接口的请求格式和错误处理。
- 作品集：展示从数据模型、接口设计、前端交互到上线的完整开发流程。
- 工程实践：加入单元测试、端到端测试、代码检查和持续集成，模拟团队项目。

## 本地部署

### 1. 获取仓库和参考实现

```bash
git clone https://github.com/baibai971101/github-daily-explorer.git
cd github-daily-explorer
git clone https://github.com/gothinkster/realworld.git
cd realworld
```

RealWorld 上游仓库包含多个前端和后端实现。请选择一个具体实现目录并先阅读其中的 README，确认运行时版本、数据库、环境变量和启动脚本。

### 2. 安装并配置

以 Node.js 实现为例：

```bash
npm install
cp .env.example .env  # 仅在项目提供模板时执行
# 编辑 .env，填写数据库地址、JWT 密钥等配置
npm run dev            # 使用项目实际提供的脚本
```

如果前端和后端是两个目录，请分别安装依赖并启动：

```bash
# 后端终端
cd backend
npm install
npm run dev

# 前端新终端
cd frontend
npm install
npm run dev
```

前端 API 地址应通过项目指定的环境变量配置。启动后，注册测试账号，依次验证登录、创建文章、评论、收藏和退出登录。

## Docker 部署

如果所选实现提供 Docker 配置，优先使用官方文件：

```bash
docker compose build
docker compose up -d
docker compose ps
docker compose logs -f
```

确认数据库迁移已完成、端口映射正确，并通过健康检查或 API 请求验证后端。停止服务：

```bash
docker compose down
```

不要把数据库密码、JWT 密钥等敏感信息硬编码进镜像或提交到 Git；使用环境变量或云平台的 Secret 管理功能。

## 云端生产部署步骤

1. 准备数据库：创建托管数据库和最小权限账号，配置备份与迁移策略。
2. 部署后端：将后端部署到 Render、Railway、Fly.io、云服务器或 Kubernetes，并配置生产环境变量。
3. 部署前端：执行 `npm run build`，把生成目录部署到 Vercel、Netlify 或 CDN。
4. 配置网络：将前端 API 地址指向后端 HTTPS 域名，并把 CORS 限制为正式前端域名。
5. 验证功能：测试健康检查、注册登录、文章增删改查、评论、收藏、关注和错误响应。
6. 维护上线服务：启用日志、监控、数据库备份和依赖安全扫描，定期更新运行时与依赖版本。

## 推荐学习顺序

先阅读 API 规范，再追踪“注册登录”和“发布文章”的完整请求链路；随后研究数据库模型、认证中间件、前端状态管理和测试；最后补充 Docker、CI/CD、监控与安全配置。

上游参考仓库：https://github.com/gothinkster/realworld

具体目录结构、依赖版本和部署命令可能随实现而异，请以对应实现的官方文档为准。