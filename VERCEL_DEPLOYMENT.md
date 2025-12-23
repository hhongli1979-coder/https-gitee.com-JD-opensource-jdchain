# Vercel 部署指南 / Vercel Deployment Guide

本文档说明如何将 JDChain 部署指南文档站点部署到 Vercel。

*This document explains how to deploy the JDChain deployment guide documentation site to Vercel.*

## 🌟 为什么选择 Vercel / Why Vercel?

- ✅ 免费托管静态网站 / Free static website hosting
- ✅ 自动 HTTPS / Automatic HTTPS
- ✅ 全球 CDN 加速 / Global CDN acceleration
- ✅ 自动部署（Git 集成）/ Automatic deployment (Git integration)
- ✅ 简单易用 / Simple and easy to use

## 📋 前置要求 / Prerequisites

- GitHub 账户 / GitHub account
- Vercel 账户（可以使用 GitHub 登录）/ Vercel account (can login with GitHub)

## 🚀 部署方法 / Deployment Methods

### 方法 1: 通过 Vercel Dashboard（推荐）

#### 步骤 1: 登录 Vercel

1. 访问 https://vercel.com
2. 点击 "Sign Up" 或 "Log In"
3. 使用 GitHub 账户登录

#### 步骤 2: 导入项目

1. 在 Vercel Dashboard 中，点击 "New Project"
2. 选择 "Import Git Repository"
3. 选择此仓库：`hhongli1979-coder/https-gitee.com-JD-opensource-jdchain`
4. 如果看不到仓库，点击 "Adjust GitHub App Permissions" 来授权访问

#### 步骤 3: 配置项目

Vercel 会自动检测到 `vercel.json` 配置文件。

**项目设置：**
- **Framework Preset**: Other
- **Root Directory**: `./` (保持默认)
- **Build Command**: 留空（静态站点不需要构建）
- **Output Directory**: 留空
- **Install Command**: 留空

#### 步骤 4: 部署

1. 点击 "Deploy"
2. 等待部署完成（通常 30 秒以内）
3. 部署成功后，Vercel 会提供一个 URL（例如：`your-project.vercel.app`）

### 方法 2: 使用 Vercel CLI

#### 步骤 1: 安装 Vercel CLI

```bash
npm install -g vercel
```

#### 步骤 2: 登录

```bash
vercel login
```

按照提示完成登录。

#### 步骤 3: 部署

在项目根目录运行：

```bash
vercel
```

首次部署时，CLI 会询问几个问题：
- **Set up and deploy**: 选择 "Y"
- **Which scope**: 选择您的账户
- **Link to existing project**: 选择 "N"（首次部署）
- **What's your project's name**: 输入项目名称或按回车使用默认名称
- **In which directory is your code located**: 按回车使用当前目录

部署完成后，CLI 会显示部署的 URL。

#### 步骤 4: 生产环境部署

```bash
vercel --prod
```

### 方法 3: 一键部署按钮

在 README.md 中提供了 "Deploy to Vercel" 按钮：

[![Deploy to Vercel](https://vercel.com/button)](https://vercel.com/import/project?template=https://github.com/hhongli1979-coder/https-gitee.com-JD-opensource-jdchain)

点击按钮后：
1. 登录 Vercel（如果尚未登录）
2. Vercel 会 fork 仓库到您的 GitHub 账户
3. 自动配置并部署项目
4. 提供部署 URL

## 🔧 配置说明 / Configuration

项目使用 `vercel.json` 进行配置：

```json
{
  "version": 2,
  "name": "jdchain-deployment-guide",
  "builds": [
    {
      "src": "docs/**",
      "use": "@vercel/static"
    }
  ],
  "routes": [
    {
      "src": "/",
      "dest": "/docs/index.html"
    },
    {
      "src": "/(.*)",
      "dest": "/docs/$1"
    }
  ]
}
```

### 配置说明：

- **version**: Vercel 配置版本
- **name**: 项目名称
- **builds**: 指定如何构建项目（静态文件）
- **routes**: URL 路由规则
  - 根路径 `/` 重定向到 `/docs/index.html`
  - 其他路径转发到 `docs` 目录

## 🌐 自定义域名 / Custom Domain

### 添加自定义域名

1. 在 Vercel Dashboard 中打开您的项目
2. 进入 "Settings" → "Domains"
3. 输入您的域名（例如：`jdchain.yourdomain.com`）
4. 按照提示配置 DNS 记录：
   - **A Record**: 指向 Vercel 的 IP
   - 或 **CNAME**: 指向您的 Vercel 部署域名

### DNS 配置示例

如果您使用的是 `jdchain.yourdomain.com`：

```
Type: CNAME
Name: jdchain
Value: your-project.vercel.app
```

等待 DNS 传播（通常几分钟到几小时），然后您就可以通过自定义域名访问站点了。

## 🔄 自动部署 / Automatic Deployment

Vercel 支持自动部署：

### Git 集成

- ✅ 推送到 `main` 分支 → 自动部署到生产环境
- ✅ 推送到其他分支 → 自动创建预览部署
- ✅ Pull Request → 自动创建预览部署

### 配置自动部署

1. Vercel Dashboard → 项目设置
2. "Git" 选项卡
3. 配置：
   - **Production Branch**: `main`（或您的主分支名称）
   - **Ignored Build Step**: 留空

每次推送代码，Vercel 都会自动重新部署。

## 📊 监控和分析 / Monitoring and Analytics

### 部署日志

在 Vercel Dashboard 中：
1. 选择项目
2. 点击 "Deployments"
3. 选择特定的部署
4. 查看详细的构建和部署日志

### 访问分析

Vercel 提供基本的访问分析：
1. 项目 Dashboard
2. "Analytics" 选项卡
3. 查看访问统计、地理位置等信息

## 🐛 故障排查 / Troubleshooting

### 部署失败

如果部署失败：

1. **检查部署日志**
   - 在 Vercel Dashboard 中查看详细错误信息

2. **验证配置文件**
   - 确认 `vercel.json` 格式正确
   - 验证文件路径

3. **检查文件权限**
   - 确保所有文件都已提交到 Git
   - 检查 `.gitignore` 是否排除了必要的文件

### 404 错误

如果访问页面出现 404：

1. **检查路由配置**
   - 验证 `vercel.json` 中的路由规则
   - 确认文件路径正确

2. **检查文件位置**
   - 确认 `docs/index.html` 存在
   - 检查文件名大小写

### 样式或资源未加载

1. **检查资源路径**
   - 使用相对路径而非绝对路径
   - 确认所有资源文件都已提交

2. **检查 MIME 类型**
   - Vercel 会自动设置，但可以在 `vercel.json` 中配置

## 🔒 安全建议 / Security Best Practices

1. **启用 HTTPS**
   - Vercel 自动启用 HTTPS
   - 确保所有资源使用 HTTPS

2. **设置安全头**
   - 可以在 `vercel.json` 中配置安全响应头

3. **保护敏感信息**
   - 不要在前端代码中硬编码 API 密钥
   - 使用环境变量

## 📝 更新文档 / Updating Documentation

要更新文档：

1. 克隆仓库或编辑文件
2. 修改 `docs/index.html` 或其他文件
3. 提交并推送到 GitHub
4. Vercel 自动检测变更并重新部署

```bash
git add .
git commit -m "Update documentation"
git push origin main
```

## 💡 最佳实践 / Best Practices

1. **保持文档简洁**
   - 静态文件应该轻量化
   - 优化图片和资源

2. **使用版本控制**
   - 所有更改都通过 Git 管理
   - 使用有意义的提交信息

3. **测试变更**
   - 使用分支进行测试
   - 利用 Vercel 的预览部署功能

4. **监控性能**
   - 定期检查页面加载速度
   - 使用 Vercel Analytics

## 🆘 获取帮助 / Getting Help

如果遇到问题：

- **Vercel 文档**: https://vercel.com/docs
- **Vercel 支持**: https://vercel.com/support
- **社区论坛**: https://github.com/vercel/vercel/discussions

## 🎉 部署成功！ / Deployment Success!

完成部署后，您应该能够：

- ✅ 通过 Vercel 提供的 URL 访问文档站点
- ✅ 查看完整的 JDChain 部署指南
- ✅ 自动部署代码更新
- ✅ 使用自定义域名（可选）

恭喜！您已经成功将 JDChain 部署指南文档站点部署到 Vercel！

*Congratulations! You have successfully deployed the JDChain deployment guide documentation site to Vercel!*

---

如有任何问题或建议，欢迎提交 Issue 或 Pull Request。

*For any questions or suggestions, feel free to submit an Issue or Pull Request.*
