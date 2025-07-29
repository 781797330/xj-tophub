# 信笺TopHub - 智能信息聚合平台

[![CI/CD Pipeline](https://github.com/781797330/xj-tophub/workflows/信笺TopHub%20CI/CD%20Pipeline/badge.svg)](https://github.com/781797330/xj-tophub/actions)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Version](https://img.shields.io/badge/version-1.0.0-green.svg)](https://github.com/781797330/xj-tophub/releases)

## 项目简介

信笺TopHub是一款现代化的智能信息聚合平台，类似于Folo和tophub.today，旨在为用户提供个性化的信息阅读体验。通过RSS和API采集各类信息源，结合AI技术进行内容分析和智能推荐，支持PC端、移动端和小程序多端同步。

## 核心特性

- 🚀 **智能信息聚合** - 支持RSS、API等多种信息源采集
- 🤖 **AI内容分析** - 基于Spring AI的智能标签生成和内容分类
- 📊 **个性化推荐** - 协同过滤和内容推荐算法
- 📱 **多端同步** - PC端、移动端、微信小程序全覆盖
- 🎯 **每日卡片** - 个性化日报推送
- 👤 **用户画像** - 智能用户行为分析
- 🔒 **安全可靠** - JWT认证、数据加密、权限控制

## 技术架构

### 后端技术栈
- **框架**: Spring Boot 3.x + Spring Cloud
- **数据库**: MySQL 8.0 + MongoDB 7.0 + Redis 7.2
- **AI框架**: Spring AI
- **消息队列**: RabbitMQ
- **搜索引擎**: Elasticsearch
- **监控**: Prometheus + Grafana + ELK Stack
- **容器化**: Docker + Docker Compose

### 前端技术栈
- **PC端**: React 18 + TypeScript + Vite + TailwindCSS + shadcn/ui
- **移动端**: React Native + TypeScript
- **小程序**: 微信小程序原生开发
- **状态管理**: Redux Toolkit
- **UI组件**: shadcn/ui + Lucide React

## 项目结构

```
xj-tophub/
├── backend/                    # 后端微服务
│   ├── user-service/          # 用户管理服务
│   ├── content-service/       # 内容管理服务
│   ├── ai-service/           # AI分析服务
│   ├── recommendation-service/ # 推荐服务
│   ├── notification-service/  # 通知服务
│   ├── gateway/              # API网关
│   └── common/               # 公共模块
├── frontend/                  # 前端应用
│   ├── web/                  # PC端React应用
│   ├── mobile/               # 移动端React Native应用
│   └── miniprogram/          # 微信小程序
├── database/                 # 数据库脚本
│   ├── mysql/               # MySQL初始化脚本
│   └── mongodb/             # MongoDB初始化脚本
├── monitoring/              # 监控配置
│   ├── prometheus/          # Prometheus配置
│   ├── grafana/            # Grafana仪表板
│   └── elk/                # ELK Stack配置
├── scripts/                # 部署脚本
├── tests/                  # 测试用例
│   ├── unit/              # 单元测试
│   ├── integration/       # 集成测试
│   └── performance/       # 性能测试
└── docs/                  # 项目文档
```

## 快速开始

### 环境要求

- Java 17+
- Node.js 18+
- Docker & Docker Compose
- MySQL 8.0+
- MongoDB 7.0+
- Redis 7.2+

### 本地开发

1. **克隆项目**
```bash
git clone https://github.com/781797330/xj-tophub.git
cd xj-tophub
```

2. **启动基础服务**
```bash
docker-compose up -d mysql mongodb redis
```

3. **初始化数据库**
```bash
# MySQL
mysql -h localhost -u root -p < database/mysql/init.sql
mysql -h localhost -u root -p < database/mysql/schema.sql
mysql -h localhost -u root -p < database/mysql/data.sql

# MongoDB
mongo < database/mongodb/init.js
mongo < database/mongodb/collections.js
```

4. **启动后端服务**
```bash
cd backend
mvn clean install
mvn spring-boot:run -pl user-service
mvn spring-boot:run -pl content-service
mvn spring-boot:run -pl ai-service
mvn spring-boot:run -pl recommendation-service
mvn spring-boot:run -pl notification-service
mvn spring-boot:run -pl gateway
```

5. **启动前端应用**
```bash
cd frontend/web
npm install
npm run dev
```

6. **访问应用**
- 前端应用: http://localhost:5173
- API网关: http://localhost:8080
- 监控面板: http://localhost:3000

### Docker部署

```bash
# 开发环境
docker-compose up -d

# 生产环境
docker-compose -f docker-compose.production.yml up -d
```

## API文档

API文档通过Swagger自动生成，启动服务后访问：
- http://localhost:8080/swagger-ui.html

主要API端点：
- `/api/auth/*` - 用户认证
- `/api/users/*` - 用户管理
- `/api/articles/*` - 文章管理
- `/api/sources/*` - 信息源管理
- `/api/recommendations/*` - 推荐服务
- `/api/notifications/*` - 通知服务

## 功能特性

### 🔐 用户系统
- 用户注册/登录
- JWT身份认证
- 用户资料管理
- 权限控制

### 📰 内容管理
- RSS信息源管理
- 文章自动采集
- 内容去重和清洗
- 全文搜索

### 🤖 AI智能分析
- 内容自动标签
- 情感分析
- 关键词提取
- 内容分类

### 📊 个性化推荐
- 协同过滤算法
- 内容推荐算法
- 用户画像分析
- 实时推荐

### 📱 多端支持
- 响应式Web界面
- React Native移动应用
- 微信小程序
- 数据同步

### 🔔 通知系统
- 每日卡片推送
- 邮件通知
- 站内消息
- 推送通知

## 监控和运维

### 监控指标
- 应用性能监控 (APM)
- 系统资源监控
- 业务指标监控
- 日志聚合分析

### 部署方式
- Docker容器化部署
- Kubernetes集群部署
- CI/CD自动化部署
- 蓝绿部署策略

## 测试

```bash
# 运行单元测试
mvn test

# 运行集成测试
mvn test -Dtest=*IntegrationTest

# 运行性能测试
./tests/performance/scripts/run-performance-test.sh

# 前端测试
cd frontend/web
npm test
```

## 贡献指南

1. Fork 项目
2. 创建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 打开 Pull Request

## 开发规范

- 遵循阿里巴巴Java开发手册
- 使用ESLint和Prettier格式化代码
- 编写单元测试和集成测试
- 提交信息遵循Conventional Commits规范

## 许可证

本项目采用 MIT 许可证 - 查看 [LICENSE](LICENSE) 文件了解详情

## 联系方式

- 项目主页: https://github.com/781797330/xj-tophub
- 问题反馈: https://github.com/781797330/xj-tophub/issues
- 邮箱: admin@tophub.com

## 致谢

感谢以下开源项目的支持：
- [Spring Boot](https://spring.io/projects/spring-boot)
- [React](https://reactjs.org/)
- [TailwindCSS](https://tailwindcss.com/)
- [shadcn/ui](https://ui.shadcn.com/)
- [Docker](https://www.docker.com/)

---

⭐ 如果这个项目对你有帮助，请给它一个星标！