# 🐳 Docker 安装
> 💡 **肆说**：Docker方式安装，适合有运维经验的人，新手别碰。

以下说明假设你已经安装了 Docker，能通过命令行管理容器，并熟悉 Docker 的基本操作。

## 使用 GitHub Container Registry（推荐）

使用预构建镜像是最快最简单的方式。

### Docker Compose（推荐）

从 [GitHub 仓库](https://github.com/SillyTavern/SillyTavern/blob/release/docker/docker-compose.yml) 下载 `docker-compose.yml` 文件，在文件所在目录运行：

```
docker compose up
```

这会从 GitHub Container Registry 拉取最新的发布版镜像并启动容器，自动创建所需的卷（Volume）。

你可以编辑该文件进行自定义：
- 默认端口是 8000，你可以修改 `ports` 部分
- 把 `image` 标签改为 `staging` 来使用开发版
- 如果想用环境变量调整服务器配置，查看 [环境变量](../administration/config-yaml.md) 页面

### Docker CLI（高级）

你需要两个必需的目录映射和一个端口映射。

#### 容器变量

##### 卷映射（Volume Mappings）
- `CONFIG_PATH` - SillyTavern 配置文件在你主机上的存放目录
- `DATA_PATH` - SillyTavern 用户数据（包括角色卡）在你主机上的存放目录
- `PLUGINS_PATH` -（可选）SillyTavern 服务器插件在你主机上的存放目录
- `EXTENSIONS_PATH` -（可选）全局 UI 扩展在你主机上的存放目录

##### 端口映射
- `PUBLIC_PORT` - 暴露流量的端口。这是必需的，因为你要从容器外部访问。**不要在没实现安全措施的情况下暴露到互联网。**

##### 其他设置
- `SILLYTAVERN_VERSION` - 在 [GitHub Packages 页面](https://github.com/SillyTavern/SillyTavern/pkgs/container/sillytavern) 查看可用的镜像版本标签。"latest" 会保持最新发布版，"staging" 指向每日构建版。

#### 运行容器

1. 打开命令行
2. 在你想存放配置和数据的目录运行：

```
SILLYTAVERN_VERSION="latest" PUBLIC_PORT="8000" CONFIG_PATH="./config" DATA_PATH="./data" PLUGINS_PATH="./plugins" EXTENSIONS_PATH="./extensions" docker run \
  --name="sillytavern" \
  -p "$PUBLIC_PORT:8000/tcp" \
  -v "$CONFIG_PATH:/home/node/app/config:rw" \
  -v "$DATA_PATH:/home/node/app/data:rw" \
  -v "$EXTENSIONS_PATH:/home/node/app/public/scripts/extensions/third-party:rw" \
  -v "$PLUGINS_PATH:/home/node/app/plugins:rw" \
  ghcr.io/sillytavern/sillytavern:"$SILLYTAVERN_VERSION"
```

默认在前景运行。想后台运行加 `-d` 标志。

## 自行构建 Docker 镜像

### Linux

1. 按 [Docker 安装指南](https://docs.docker.com/engine/install/) 安装 Docker。**不要**安装 Docker Desktop。
2. 按 Docker [安装后指南](https://docs.docker.com/engine/install/linux-postinstall/) 中的"以非 root 用户管理 Docker"操作。
3. 用包管理器安装 [Git](https://git-scm.com/download/linux)。
   - Debian/Ubuntu：`sudo apt install git`
   - Arch：`sudo pacman -S git`
   - Fedora：`sudo dnf install git`
4. 克隆仓库：
   - 稳定版：`git clone https://github.com/SillyTavern/SillyTavern && cd SillyTavern/docker`
   - 开发版：`git clone https://github.com/SillyTavern/SillyTavern -b staging && cd SillyTavern/docker`
5. 在 docker 目录执行：`docker compose up -d`
6. 浏览器打开 [http://localhost:8000](http://localhost:8000/)

### Windows

在 Windows 上用 Docker 真的**很**复杂。不仅要开启 WSL（Windows Subsystem for Linux），还要配置虚拟化（Intel VT-d/AMD SVM），不同电脑厂商设置方法不同，有些系统根本没有这选项。强烈建议按 [Windows 安装](windows.md) 指南操作。

1. 按 [Docker Desktop 安装指南](https://docs.docker.com/desktop/setup/install/windows-install/) 安装
2. 安装 [Git for Windows](https://git-scm.com/download/win)
3. 克隆仓库（同上）
4. 在 docker 目录执行：`docker compose up -d`
5. 浏览器打开 [http://localhost:8000](http://localhost:8000/)

### macOS

1. 按 [Docker Desktop 安装指南](https://docs.docker.com/desktop/setup/install/mac-install/) 安装
2. 用 Homebrew 安装 git：`brew install git`
3. 克隆仓库（同上）
4. 在 docker 目录执行：`docker compose up -d`
5. 浏览器打开 [http://localhost:8000](http://localhost:8000/)

## 配置 SillyTavern

配置文件（config.yaml）在 `config` 文件夹内。配置方法跟不用 Docker 时一样，但保存修改需要用管理员权限运行 `nano` 或代码编辑器。

修改后别忘了重启容器！在 docker 目录执行：

```
docker compose restart sillytavern
```

## 找到用户数据

数据文件夹在 `data` 文件夹内。备份很简单，但恢复或添加内容可能需要管理员权限。

## 运行服务器插件

在 Docker 中运行插件（如 [HoYoWiki-Scraper-TS](https://github.com/Bronya-Rand/HoYoWiki-Scraper-TS)）跟非 Docker 方式基本一样，只需稍微修改 Docker Compose 脚本。

1. 用编辑器打开 `docker-compose.yml`，在 `volumes` 下添加：
   ```
   volumes:
     - "./config:/home/node/app/config"
     - "./data:/home/node/app/data"
     - "./plugins:/home/node/app/plugins"
   ```
2. 在 docker 目录下创建 `plugins` 文件夹
3. 按插件的安装说明操作
4. 用管理员权限编辑 `config.yaml`（在 config 目录内），启用 `enableServerPlugins`：
   ```
   enableServerPlugins: true
   ```
5. 重启容器：`docker compose restart sillytavern`

## 非 root 用户模式

默认容器以 root 运行。如果你想让挂载卷中的文件属于特定用户，可以启用非 root 模式。

### 方式1：PUID/PGID（推荐）

设置 `PUID` 和 `PGID` 环境变量为所需的 UID/GID。入口点会更新目录权限然后以该用户运行服务器。

Docker Compose 示例：
```
services:
  sillytavern:
    environment:
      - PUID=1000
      - PGID=1000
```

### 方式2：Docker `--user` 标志

用 Docker 的 `--user` 标志指定用户运行容器。此模式下容器无法自动修复权限，需确保挂载卷已被指定 UID/GID 可写。

## 容器健康检查（Healthcheck）

Docker 镜像内置了健康检查机制，监控 SillyTavern 服务器的响应能力。适用于容器编排系统（如 Docker Compose、Kubernetes、Docker Swarm）。

### 工作原理

1. 启用后，SillyTavern 服务器定期将时间戳写入 `heartbeat.json` 文件
2. 健康检查脚本验证心跳文件是否存在且最近更新
3. 如果心跳文件缺失或太旧（超过2个间隔），容器标记为不健康

### 配置

由 `SILLYTAVERN_HEARTBEATINTERVAL` 环境变量控制（或 config.yaml 中的 `heartbeatInterval`）：
- **默认：** `0`（禁用）
- **推荐：** 使用 Docker 健康检查时设 `30` 秒

默认 `docker-compose.yml` 已包含健康检查配置。

### 查看健康状态

```
docker inspect --format='{{.State.Health.Status}}' sillytavern
```

或 `docker ps` 查看 STATUS 列。

### 禁用健康检查

将环境变量设为 `0` 并注释掉 `docker-compose.yml` 中的 `healthcheck` 部分。

## Docker 常见问题

### SELinux 权限问题

启用了 SELinux 的 Linux 发行版可能阻止容器访问挂载卷。可以在卷挂载后添加 `:z` 或 `:Z` 后缀：
- `:z` 用于多个容器共享的卷
- `:Z` 用于仅当前容器使用的卷

### 白名单问题

Docker Desktop（Windows/Mac）和 Docker CE（Linux）的区别：Docker CE 不支持 `host.docker.internal` 主机名，需要手动添加 Docker 网关 IP 到白名单。

1. 获取 Docker 容器 IP：`docker network inspect docker_default`
2. 复制 Gateway IP
3. 编辑 `config.yaml`，在 `whitelist` 部分添加该 IP
4. 重启容器

---

📖 原文链接：[Docker Installation](https://docs.sillytavern.app/installation/docker/)
