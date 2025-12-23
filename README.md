# JDChain 部署指南文档站点 / JDChain Deployment Guide Documentation Site

[![部署到 Vercel](https://vercel.com/button)](https://vercel.com/import/project?template=https://github.com/hhongli1979-coder/https-gitee.com-JD-opensource-jdchain)

这是一个 JDChain 区块链部署指南的文档站点，可以部署到 Vercel 等静态托管平台。

*This is a documentation site for JDChain blockchain deployment guide that can be deployed to static hosting platforms like Vercel.*

## 📖 关于 JDChain / About JDChain

JDChain 是京东集团自主研发的企业级区块链底层框架，支持多种共识算法和智能合约，适用于供应链、溯源、金融等多个场景。

*JDChain is an enterprise-level blockchain framework independently developed by JD.com, supporting multiple consensus algorithms and smart contracts, suitable for supply chain, traceability, finance and other scenarios.*

## 🌐 在线访问 / Online Access

部署后，您可以通过浏览器访问完整的部署指南。

*After deployment, you can access the complete deployment guide through your browser.*

## 🚀 快速部署到 Vercel / Quick Deploy to Vercel

> 📖 **新手？** 查看 [快速开始指南 (QUICKSTART.md)](./QUICKSTART.md) 了解 5 分钟快速部署流程！
> 
> *New here? Check out the [Quick Start Guide (QUICKSTART.md)](./QUICKSTART.md) for a 5-minute deployment walkthrough!*

### 方法 1: 使用 Vercel CLI

```bash
# 安装 Vercel CLI
npm i -g vercel

# 在项目目录中运行
vercel
```

### 方法 2: 通过 Vercel Dashboard

1. 访问 [Vercel](https://vercel.com)
2. 导入此 GitHub 仓库
3. Vercel 会自动检测配置并部署

### 方法 3: 使用 Vercel 按钮

点击上方的 "Deploy to Vercel" 按钮，一键部署。

## 📁 项目结构 / Project Structure

```
.
├── docs/
│   └── index.html          # 主文档页面 / Main documentation page
├── DEPLOYMENT.md           # 详细部署指南 / Detailed deployment guide
├── vercel.json            # Vercel 配置 / Vercel configuration
└── README.md              # 本文件 / This file
```

## 📚 文档内容 / Documentation Content

本文档站点包含以下内容：

- ✅ JDChain 快速开始指南
- ✅ 构建和编译说明
- ✅ 部署步骤详解
- ✅ 系统要求
- ✅ 网络拓扑说明
- ✅ 命令行工具使用
- ✅ SDK 集成指南
- ✅ 故障排查指南

*This documentation site includes:*
- ✅ *JDChain quick start guide*
- ✅ *Build and compilation instructions*
- ✅ *Detailed deployment steps*
- ✅ *System requirements*
- ✅ *Network topology explanation*
- ✅ *Command line tool usage*
- ✅ *SDK integration guide*
- ✅ *Troubleshooting guide*

## 🔧 本地开发 / Local Development

```bash
# 克隆仓库
git clone https://github.com/hhongli1979-coder/https-gitee.com-JD-opensource-jdchain.git
cd https-gitee.com-JD-opensource-jdchain

# 使用任何 HTTP 服务器运行
# 例如使用 Python
python -m http.server 8000

# 或使用 Node.js
npx serve .

# 访问 http://localhost:8000/docs/
```

## ⚠️ 重要说明 / Important Notes

**本仓库提供的是文档站点，而非 JDChain 区块链本身。**

JDChain 是一个企业级区块链平台，需要完整的基础设施部署：
- ☑️ 对等节点（Peer Nodes）
- ☑️ 网关节点（Gateway Nodes）
- ☑️ 共识服务
- ☑️ 数据存储

**This repository provides a documentation site, not JDChain blockchain itself.**

*JDChain is an enterprise-level blockchain platform that requires complete infrastructure deployment:*
- ☑️ *Peer Nodes*
- ☑️ *Gateway Nodes*
- ☑️ *Consensus Service*
- ☑️ *Data Storage*

### 实际部署 JDChain / Actual JDChain Deployment

要部署实际的 JDChain 节点，您需要：

1. 克隆 JDChain 源代码仓库：
   ```bash
   git clone https://github.com/blockchain-jd-com/jdchain.git
   ```

2. 按照 [DEPLOYMENT.md](./DEPLOYMENT.md) 中的说明构建和部署

3. 部署到支持 Java 应用的服务器环境（如阿里云、腾讯云、AWS 等）

*To deploy actual JDChain nodes, you need to:*
1. *Clone the JDChain source code repository*
2. *Follow the instructions in DEPLOYMENT.md to build and deploy*
3. *Deploy to server environments that support Java applications (such as Alibaba Cloud, Tencent Cloud, AWS, etc.)*

## 🔗 相关链接 / Related Links

- **JDChain GitHub**: https://github.com/blockchain-jd-com/jdchain
- **京东链官网**: https://ledger.jd.com/
- **京东智臻链官网**: https://blockchain.jd.com/
- **支持邮箱**: jdchain-support@jd.com

## 📄 许可证 / License

请参考 [LICENSE](./LICENSE) 文件。

*Please refer to the [LICENSE](./LICENSE) file.*

## 🤝 贡献 / Contributing

欢迎提交问题和拉取请求来改进本文档站点！

*Issues and pull requests are welcome to improve this documentation site!*

---

© 2025 JDChain Deployment Guide Documentation | 京东区块链
