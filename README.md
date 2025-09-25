# Claude Code Hub

> 一个现代化的 AI API 代理服务，提供智能负载均衡、用户管理和使用统计功能。

[![TypeScript](https://img.shields.io/badge/TypeScript-5.9-blue)](https://www.typescriptlang.org/)
[![Next.js](https://img.shields.io/badge/Next.js-15.4-black)](https://nextjs.org/)
[![React](https://img.shields.io/badge/React-19.1-blue)](https://reactjs.org/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind%20CSS-4.1-38bdf8)](https://tailwindcss.com/)
[![pnpm](https://img.shields.io/badge/pnpm-9.15-ffbf00)](https://pnpm.io/)

## ✨ 核心特性

- 🔄 **智能代理** - 基于 Hono 的高性能 API 代理，支持流式响应 (SSE)
- ⚖️ **负载均衡** - 智能分发请求到多个上游提供商，支持权重配置
- 👥 **用户管理** - 多用户支持，细粒度的权限和配额控制
- 🔑 **密钥管理** - 用户密钥生成、管理和权限控制
- 📊 **使用统计** - 详细的请求统计、成本分析和可视化图表
- 🎨 **现代界面** - 基于 shadcn/ui 的响应式管理面板
- 💾 **数据持久化** - PostgreSQL + Drizzle ORM 的可靠数据存储

## 🏗️ 技术栈

### 前端
- **Next.js 15** - 使用 App Router 的全栈框架
- **React 19** - 最新的 React 特性支持
- **TypeScript** - 类型安全的开发体验
- **Tailwind CSS v4** - 实用优先的 CSS 框架
- **shadcn/ui** - 高质量的 React 组件库

### 后端
- **Hono** - 轻量级、高性能的 Web 框架
- **Drizzle ORM** - 类型安全的 SQL ORM
- **PostgreSQL** - 生产级关系型数据库
- **Node.js** - 稳定的 JavaScript 运行时

## 🚀 快速开始

### 环境要求

- **pnpm** ≥ 9.15.0
- **Node.js** ≥ 18
- **PostgreSQL** ≥ 12

### 安装与运行

1. **克隆仓库**
   ```bash
   git clone https://github.com/your-username/claude-code-hub.git
   cd claude-code-hub
   ```

2. **安装依赖**
   ```bash
   pnpm install
   ```

3. **配置环境变量**

   复制环境变量模板：
   ```bash
   cp .env.example .env.local
   ```

   编辑 `.env.local` 文件：
   ```bash
   # 应用配置
   NODE_ENV=development

   # 管理员令牌
   ADMIN_TOKEN=your-secure-admin-token

   # 数据库连接
   DATABASE_URL=postgres://user:password@localhost:5432/claude_code_hub
   ```

4. **初始化数据库**
   ```bash
   # 生成迁移文件
   pnpm run db:generate

   # 执行数据库迁移
   pnpm run db:migrate
   ```

5. **启动开发服务器**
   ```bash
   pnpm dev
   ```

   应用将在 http://localhost:13500 启动

### 生产部署

1. **构建应用**
   ```bash
   pnpm run build
   ```

2. **启动生产服务器**
   ```bash
   pnpm run start
   ```

## 📁 项目结构

```
src/
├── app/                          # Next.js App Router
│   ├── v1/[...route]/           # API 代理路由 (Hono)
│   ├── dashboard/               # 管理面板页面
│   ├── login/                   # 登录页面
│   └── layout.tsx               # 根布局
├── actions/                     # Server Actions
│   ├── users.ts                 # 用户相关操作
│   ├── keys.ts                  # 密钥管理
│   ├── providers.ts             # 供应商管理
│   └── statistics.ts            # 统计数据
├── repository/                  # 数据访问层
│   ├── user.ts                  # 用户数据访问
│   ├── key.ts                   # 密钥数据访问
│   ├── provider.ts              # 供应商数据访问
│   └── message.ts               # 消息记录
├── types/                       # TypeScript 类型定义
│   ├── user.ts                  # 用户类型
│   ├── key.ts                   # 密钥类型
│   ├── provider.ts              # 供应商类型
│   └── statistics.ts            # 统计类型
├── components/                  # 共享 UI 组件 (shadcn/ui)
├── lib/                         # 工具函数和配置
│   ├── config/                  # 环境配置
│   ├── constants/               # 常量定义
│   ├── validation/              # 数据验证
│   └── utils.ts                 # 通用工具
└── drizzle/                     # 数据库 schema 和迁移
```

## 🎯 主要功能

### 1. API 代理服务

智能代理 AI API 请求，支持：
- 多上游提供商负载均衡
- 基于权重的请求分发
- 流式响应 (Server-Sent Events)
- 请求认证和速率限制
- 自动故障转移

### 2. 用户管理系统

- **多用户支持** - 支持管理员和普通用户角色
- **配额控制** - 每日消费限额和请求频率限制
- **权限管理** - 细粒度的功能权限控制

### 3. 密钥管理

- **密钥生成** - 自动生成安全的 API 密钥
- **生命周期管理** - 支持密钥过期和禁用
- **使用统计** - 实时监控密钥使用情况

### 4. 供应商管理

- **多供应商支持** - 管理多个 AI 服务提供商
- **负载均衡配置** - 支持权重、速率限制等参数
- **健康检查** - 自动检测和切换不可用的供应商

### 5. 数据分析

- **实时统计** - 请求量、成本、响应时间等指标
- **可视化图表** - 基于 Recharts 的交互式图表
- **历史数据** - 支持不同时间范围的数据查看

## 🔧 开发命令

```bash
# 开发
pnpm dev                    # 启动开发服务器 (Turbopack)

# 构建
pnpm run build             # 构建生产版本
pnpm run start                 # 启动生产服务器

# 代码质量
pnpm run lint              # ESLint 检查
pnpm run typecheck         # TypeScript 类型检查

# 数据库
pnpm run db:generate       # 生成迁移文件
pnpm run db:migrate        # 执行数据库迁移
pnpm run db:push           # 推送 schema 到数据库
pnpm run db:studio         # 启动 Drizzle Studio
```

## 🎨 UI 组件

项目使用 [shadcn/ui](https://ui.shadcn.com/) 组件库，提供：

- 一致的设计语言
- 高度可定制的组件
- 无障碍访问支持
- 深色模式支持

### 添加新组件

```bash
pnpm dlx shadcn@latest add [component-name]
```

## 📊 数据库设计

核心数据表：

- **users** - 用户信息和配额设置
- **keys** - API 密钥管理
- **providers** - 上游服务提供商配置
- **message_request** - 请求记录和统计
- **model_prices** - 模型定价信息

## 🔒 安全特性

- **密钥加密存储** - 敏感信息加密保存
- **请求认证** - 基于 JWT 的身份验证
- **速率限制** - 防止 API 滥用
- **权限控制** - 基于角色的访问控制
- **输入验证** - 使用 Zod 进行严格的数据验证

## 🚀 部署指南

### Docker 部署

```bash
# 构建镜像
docker build -t claude-code-hub .

# 运行容器
docker run -p 3000:3000 -e DATABASE_URL=your-db-url claude-code-hub
```

### 生产环境建议

- 使用反向代理 (Nginx/Caddy)
- 配置 HTTPS
- 设置数据库连接池
- 启用日志收集
- 配置监控和告警

## 🤝 贡献指南

1. Fork 本仓库
2. 创建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 开启 Pull Request

### 代码规范

- 使用 TypeScript 严格模式
- 遵循 ESLint 规则
- 提交前运行类型检查和 lint
- 使用有意义的提交消息

## 📝 许可证

本项目采用 MIT 许可证 - 查看 [LICENSE](LICENSE) 文件了解详情。

## 🆘 支持与反馈

- 🐛 [报告问题](https://github.com/your-username/claude-code-hub/issues)
- 💡 [功能建议](https://github.com/your-username/claude-code-hub/discussions)
- 📧 邮件: your-email@example.com

---

<p align="center">
  用 ❤️ 构建，为 AI 应用开发者服务
</p>