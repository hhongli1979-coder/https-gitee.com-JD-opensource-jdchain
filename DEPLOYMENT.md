# JDChain 部署指南 / JDChain Deployment Guide

[English](#english) | [中文](#chinese)

---

<a name="chinese"></a>
## 中文部署指南

### 快速开始

#### 1. 克隆代码

```bash
git clone https://github.com/blockchain-jd-com/jdchain.git jdchain
cd jdchain
```

#### 2. 选择分支

这里仅以 master 分支为例，正常情况下 master 分支可能难以构建成功。

**注意事项：**
- 不推荐使用 develop 分支，子模块代码可能未对齐
- 切换推荐到具体已发布的版本分支

```bash
git checkout master
```

#### 3. 设置执行权限

```bash
chmod +x build/*.sh
```

### 构建选项

#### 完整构建

执行完整的构建，包括执行"集成测试"和"预留"两个部分：

```bash
build/build.sh --update
```

**参数说明：**
- `--skipTests`: 跳过集成测试部分
- `--update`: 从远程仓库更新子模块（注意：采用此参数会导致子模块本地仓库丢失尚未提交的代码）
- 不附带此参数的情况下不会更新子模块仓库

#### 跳过测试的构建

跳过子模块代码更新和集成测试，直接编译和备份：

```bash
build/build.sh --skipTests
```

#### 首次拉取构建

首次代码拉取，跳过集成测试和预编译：

```bash
build/build.sh --update --skipTests
```

### 构建产物

构建完成后会在以下位置生成部署包：

- **deploy 模块**: `deploy-gateway` 和 `deploy-peer` 目录的 `target` 中
- **网关安装部署包**: `jdchain-gateway-<version>.zip`
- **节点安装部署包**: `jdchain-peer-<version>.zip`

### 部署使用

#### 快速部署

使用源码构建生成的部署安装包，或者下载官方部署安装包，参照快速部署文档可快速部署运行 JD Chain 网络。

**部署步骤：**

1. 解压部署包到目标目录
2. 配置网络参数
3. 启动节点和网关
4. 验证网络连接

### 数据上链

#### 命令行工具

京东链命令行工具集，即 `jdchain-cli`，可快速执行数据上链和链上数据查询。

**基本使用：**

```bash
# 数据上传
jdchain-cli tx upload --data <your-data>

# 数据查询
jdchain-cli query --key <data-key>
```

#### SDK 使用

JD Chain 提供了 Java 和 Go 版本的 SDK。

**Java SDK:**
```xml
<dependency>
    <groupId>com.jd.blockchain</groupId>
    <artifactId>sdk-samples</artifactId>
    <version>${jdchain.version}</version>
</dependency>
```

实际项目开发中 Java 可参照示例代码。

**Go SDK:**
Go 语言 SDK 参照 framework-go 仓库。

### 系统要求

- **Java**: JDK 8 或更高版本
- **Maven**: 3.6.0 或更高版本
- **操作系统**: Linux / macOS / Windows
- **内存**: 建议 4GB 以上
- **磁盘**: 建议 10GB 以上可用空间

### 网络拓扑

JD Chain 网络由以下组件构成：

```
┌─────────────┐
│   Client    │
└──────┬──────┘
       │
       v
┌─────────────┐
│   Gateway   │ (网关节点)
└──────┬──────┘
       │
       v
┌─────────────┐
│   Peer 1    │ (共识节点1)
├─────────────┤
│   Peer 2    │ (共识节点2)
├─────────────┤
│   Peer 3    │ (共识节点3)
├─────────────┤
│   Peer N    │ (共识节点N)
└─────────────┘
```

### 故障排查

#### 构建失败

如果构建失败，请检查：
1. Java 版本是否正确
2. Maven 配置是否正确
3. 网络连接是否正常
4. 子模块是否正确更新

#### 启动失败

如果节点启动失败，请检查：
1. 端口是否被占用
2. 配置文件是否正确
3. 日志文件查看详细错误信息

### 更多资源

- **文档**: [docs](https://github.com/blockchain-jd-com/jdchain/tree/master/docs)
- **京东链官网**: https://ledger.jd.com/
- **京东智臻链官网**: https://blockchain.jd.com/
- **服务邮箱**: jdchain-support@jd.com

JD Chain 功能开发，使用问题等欢迎在 Issues 中讨论，也欢迎广大开发者积极参与 JD Chain 社区及代码开发活动！

---

<a name="english"></a>
## English Deployment Guide

### Quick Start

#### 1. Clone the Repository

```bash
git clone https://github.com/blockchain-jd-com/jdchain.git jdchain
cd jdchain
```

#### 2. Select Branch

Using the master branch as an example. Note that the master branch may be difficult to build successfully under normal circumstances.

**Important Notes:**
- The develop branch is not recommended as submodule code may not be aligned
- It is recommended to switch to a specific released version branch

```bash
git checkout master
```

#### 3. Set Execution Permissions

```bash
chmod +x build/*.sh
```

### Build Options

#### Full Build

Execute a complete build, including "integration tests" and "reserve" sections:

```bash
build/build.sh --update
```

**Parameters:**
- `--skipTests`: Skip the integration test section
- `--update`: Update submodules from remote repository (Warning: using this parameter will cause the loss of uncommitted code in submodule local repositories)
- Without this parameter, submodule repositories will not be updated

#### Build Without Tests

Skip submodule code updates and integration tests, compile and backup directly:

```bash
build/build.sh --skipTests
```

#### First-Time Build

For the first code pull, skip integration tests and pre-compilation:

```bash
build/build.sh --update --skipTests
```

### Build Artifacts

After the build is complete, deployment packages will be generated:

- **Deploy modules**: In the `target` directories of `deploy-gateway` and `deploy-peer`
- **Gateway deployment package**: `jdchain-gateway-<version>.zip`
- **Peer node deployment package**: `jdchain-peer-<version>.zip`

### Deployment

#### Quick Deployment

Use the deployment installation package generated from source code build, or download the official deployment installation package, and refer to the quick deployment documentation to quickly deploy and run a JD Chain network.

**Deployment Steps:**

1. Extract the deployment package to the target directory
2. Configure network parameters
3. Start nodes and gateway
4. Verify network connectivity

### Data Upload to Chain

#### Command Line Tool

JD Chain command line toolkit, `jdchain-cli`, can quickly execute data uploads to the chain and query data on the chain.

**Basic Usage:**

```bash
# Data upload
jdchain-cli tx upload --data <your-data>

# Data query
jdchain-cli query --key <data-key>
```

#### SDK Usage

JD Chain provides Java and Go SDKs.

**Java SDK:**
```xml
<dependency>
    <groupId>com.jd.blockchain</groupId>
    <artifactId>sdk-samples</artifactId>
    <version>${jdchain.version}</version>
</dependency>
```

Refer to sample code for Java development in actual projects.

**Go SDK:**
Refer to the framework-go repository for Go language SDK.

### System Requirements

- **Java**: JDK 8 or higher
- **Maven**: 3.6.0 or higher
- **Operating System**: Linux / macOS / Windows
- **Memory**: 4GB or more recommended
- **Disk**: 10GB or more available space recommended

### Network Topology

JD Chain network consists of the following components:

```
┌─────────────┐
│   Client    │
└──────┬──────┘
       │
       v
┌─────────────┐
│   Gateway   │ (Gateway Node)
└──────┬──────┘
       │
       v
┌─────────────┐
│   Peer 1    │ (Consensus Node 1)
├─────────────┤
│   Peer 2    │ (Consensus Node 2)
├─────────────┤
│   Peer 3    │ (Consensus Node 3)
├─────────────┤
│   Peer N    │ (Consensus Node N)
└─────────────┘
```

### Troubleshooting

#### Build Failures

If the build fails, please check:
1. Java version is correct
2. Maven configuration is correct
3. Network connection is normal
4. Submodules are correctly updated

#### Startup Failures

If node startup fails, please check:
1. Ports are not occupied
2. Configuration files are correct
3. Check log files for detailed error information

### Additional Resources

- **Documentation**: [docs](https://github.com/blockchain-jd-com/jdchain/tree/master/docs)
- **JD Chain Official Website**: https://ledger.jd.com/
- **JD Blockchain Official Website**: https://blockchain.jd.com/
- **Support Email**: jdchain-support@jd.com

For JD Chain feature development and usage questions, please discuss in Issues. We welcome developers to actively participate in the JD Chain community and code development activities!
