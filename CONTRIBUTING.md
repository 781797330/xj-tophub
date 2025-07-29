# 贡献指南

感谢您对信笺TopHub项目的关注！我们欢迎所有形式的贡献，包括但不限于：

- 🐛 报告Bug
- 💡 提出新功能建议
- 📝 改进文档
- 🔧 提交代码修复
- ✨ 添加新功能

## 开发环境设置

### 环境要求

- Java 17+
- Node.js 18+
- Docker & Docker Compose
- MySQL 8.0+
- MongoDB 7.0+
- Redis 7.2+

### 本地开发

1. **Fork并克隆项目**
```bash
git clone https://github.com/your-username/xj-tophub.git
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
# 启动各个微服务
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

## 代码规范

### Java代码规范

- 遵循阿里巴巴Java开发手册
- 使用Lombok减少样板代码
- 所有公共方法必须有JavaDoc注释
- 单元测试覆盖率不低于80%

### 前端代码规范

- 使用TypeScript进行类型检查
- 遵循ESLint和Prettier配置
- 组件命名使用PascalCase
- 文件名使用kebab-case

### 提交信息规范

使用Conventional Commits规范：

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

类型说明：
- `feat`: 新功能
- `fix`: Bug修复
- `docs`: 文档更新
- `style`: 代码格式调整
- `refactor`: 代码重构
- `test`: 测试相关
- `chore`: 构建过程或辅助工具的变动

示例：
```
feat(user): 添加用户头像上传功能

- 支持JPG、PNG格式
- 自动压缩和裁剪
- 添加上传进度显示

Closes #123
```

## 提交流程

1. **创建Issue**
   - 对于Bug报告，请使用Bug模板
   - 对于功能请求，请使用Feature模板
   - 详细描述问题或需求

2. **创建分支**
```bash
git checkout -b feature/your-feature-name
# 或
git checkout -b fix/your-bug-fix
```

3. **开发和测试**
```bash
# 运行测试
mvn test  # 后端测试
npm test  # 前端测试

# 代码检查
mvn checkstyle:check  # 后端代码检查
npm run lint          # 前端代码检查
```

4. **提交代码**
```bash
git add .
git commit -m "feat: 添加新功能描述"
git push origin feature/your-feature-name
```

5. **创建Pull Request**
   - 填写PR模板
   - 关联相关Issue
   - 等待代码审查

## 代码审查

所有代码变更都需要经过代码审查：

- 至少需要一个维护者的批准
- 所有CI检查必须通过
- 代码覆盖率不能降低
- 必须更新相关文档

## 发布流程

1. **版本号规范**
   - 使用语义化版本号 (Semantic Versioning)
   - 格式：MAJOR.MINOR.PATCH
   - 例如：1.0.0, 1.1.0, 1.1.1

2. **发布步骤**
   - 更新CHANGELOG.md
   - 创建版本标签
   - 触发自动部署

## 社区准则

- 尊重所有贡献者
- 保持友好和专业的交流
- 欢迎新手参与
- 及时回应Issue和PR

## 获得帮助

如果您在贡献过程中遇到问题，可以通过以下方式获得帮助：

- 在GitHub上创建Issue
- 发送邮件至：admin@tophub.com
- 加入我们的开发者群组

## 致谢

感谢所有为信笺TopHub项目做出贡献的开发者！

您的贡献将被记录在项目的贡献者列表中。