# Ocean 节点管理脚本

这个 Bash 脚本用于安装和卸载 Ocean 节点。它提供了一个简单的界面来管理多个 Ocean 节点的部署和移除。

## 功能

1. 安装 Ocean 节点
2. 卸载 Ocean 节点

## 前置条件

- 安装 Docker 和 Docker Compose
- 安装 curl（用于获取公共 IP 地址）
- 安装 openssl（用于生成私钥）

## 使用方法

1. 确保脚本具有执行权限：
   ```
   chmod +x main.sh
   ```

2. 运行脚本：
   ```
   ./main.sh
   ```

3. 根据提示选择安装或卸载节点。

### 安装节点

选择安装选项后，您需要提供以下信息：

- 节点起始索引
- 节点结束索引
- 节点数据的基础目录
- 确认或提供公共 IP 地址或 FQDN

脚本将为每个节点创建一个 Docker Compose 文件，并启动相应的容器。

### 卸载节点

选择卸载选项后，您需要提供以下信息：

- 节点起始索引
- 节点结束索引
- 节点数据的基础目录

脚本将停止并移除指定范围内的所有节点容器，并删除相关目录。

## 注意事项

- 脚本会自动为每个节点生成一个私钥，或使用已存在的私钥文件。
- 每个节点都会有自己的 Typesense 实例。
- 端口号是根据节点索引自动分配的，起始于 10000。
- 确保您有足够的系统资源来运行多个节点。
- 在生产环境中使用前，请确保正确配置了安全设置。

## 配置

脚本中包含了预设的 RPC 端点配置，支持以下网络：

- Ethereum Mainnet
- Optimism
- Polygon
- Oasis Sapphire
- Oasis Sapphire Testnet
- Ethereum Sepolia Testnet
- Optimism Sepolia Testnet

如需修改或添加其他网络，请编辑脚本中的 `RPCS` 环境变量。

## 故障排除

- 如果遇到端口冲突，请确保指定的端口范围内没有其他服务在运行。
- 确保您有足够的磁盘空间来存储节点数据。
- 如果节点无法启动，检查 Docker 日志以获取更多信息。

## 贡献

欢迎提交问题报告和改进建议。如果您想贡献代码，请先开 issue 讨论您的想法。
