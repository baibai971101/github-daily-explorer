# RealWorld 项目中文教程

## 项目简介

RealWorld 是一个全栈示例项目，旨在为不同的前端框架（如 React、Vue、Angular 等）和后端实现（如 Node.js、Django、Rails 等）提供统一的 **增删改查（CRUD）** 示例。它遵循 **Conduit** 规范，展示了典型的博客系统功能，包括用户注册、登录、文章发布、评论、标签、关注等。

本仓库 `github-daily-explorer` 将 RealWorld 作为每日技术探索的实验平台，帮助开发者在同一代码库中快速尝试不同技术栈、工具链或部署方式。

## 实际用途

- **学习参考**：通过完整的项目结构，帮助新手了解全栈开发的最佳实践。
- **技术对比**：可以在此项目中集成不同框架或库，比较它们的性能、开发体验等。
- **每日实验**：记录每日的技术实验、探索过程以及成果，形成持续学习的记录。
- **部署演示**：展示如何在本地、Docker、Kubernetes 或云平台（如 Vercel、Render）上部署完整的 RealWorld 应用。

## 部署步骤

### 1. 本地运行（Node.js 示例）
```bash
# 克隆仓库
git clone https://github.com/baibai971101/github-daily-explorer.git
cd github-daily-explorer

# 进入 RealWorld 示例（本仓库仅提供演示脚本，实际代码请参考上游仓库）
git clone https://github.com/gothinkster/realworld.git
cd realworld

# 安装依赖（以 backend 为例）
cd backend
npm install
npm run dev   # 启动后端，默认 http://localhost:3000

# 前端
cd ../frontend
npm install
npm run dev   # 启动前端，默认 http://localhost:8080
```

### 2. Docker 部署
在仓库根目录创建 `docker-compose.yml`（已在本仓库提供示例），然后执行：
```bash
docker compose up -d
```
这将启动后端和前端容器，分别映射到 3000 和 8080 端口。

### 3. Kubernetes（示例）
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: realworld-backend
spec:
  replicas: 1
  selector:
    matchLabels:
      app: realworld-backend
  template:
    metadata:
      labels:
        app: realworld-backend
    spec:
      containers:
        - name: backend
          image: node:18-alpine
          command: ["sh", "-c", "npm install && npm run start"]
          ports:
            - containerPort: 3000
```
将上述部署文件保存为 `backend-deployment.yaml` 并使用 `kubectl apply -f backend-deployment.yaml` 部署。

### 4. 云平台（Vercel 示例）
1. 在 Vercel 新建项目，连接到本仓库的 `frontend` 目录。
2. 设置构建命令 `npm install && npm run build`，输出目录 `dist`（或对应框架的输出目录）。
3. 部署完成后即可通过 Vercel 提供的域名访问前端，后端可自行部署到 Render、Fly.io 等平台。

## 贡献指南

- Fork 本仓库，提交 Pull Request 改进教程或添加新的部署方案。
- 在 `issues` 中提出想要实验的技术栈或工具，作者会在每日探索中进行实现。
- 请遵守上游 RealWorld 项目的开源许可证（MIT），在引用时注明来源。

---

*祝你玩得开心，持续探索！*