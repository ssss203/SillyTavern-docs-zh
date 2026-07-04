# 📥 安装
> 💡 **肆说**：安装SillyTavern的入口页面，按你的操作系统选对应指南。

按你的平台选择安装指南：

- [Windows 安装](windows.md)
- [Linux 和 Mac 安装](linuxmacos.md)
- [Android 安装](android-termux.md)
- [Docker 安装](docker.md)

## 🌿 分支（Branch）说明

SillyTavern 用双分支系统开发，确保所有用户有稳定的体验：

- `release` - 🌟 **推荐大多数用户用这个。** 最稳定的分支，只有大版本更新时才推送。通常每月更新一次。
- `staging` - ⚠️ **不推荐日常使用。** 有最新功能但随时可能出问题。只适合高级用户。每天更新好几次。

## 📦 全局模式 vs 独立模式（Global / Standalone Mode）

SillyTavern 有两种运行模式，区别在于配置和数据路径的存放方式：

- **独立模式（Standalone Mode）**（默认）- 使用安装目录下的 `config.yaml` 文件和 `data` 目录。所有数据都限制在安装路径内。推荐大多数用户使用。
- **全局模式（Global Mode）** - 使用系统级路径存放配置和数据。适合把 SillyTavern 当作一个系统包来安装，或者在多个安装之间共享配置和数据。

通过 [官方 npm 包](https://www.npmjs.com/package/sillytavern)（比如 `npx sillytavern@latest`）安装的会默认以全局模式运行。

### 数据路径

**独立模式**的路径相对于 SillyTavern 安装目录：

- **配置路径**：`./config.yaml`
- **数据根目录**：`./data/`

**全局模式**的路径因操作系统而异：

- **Linux**：`~/.local/share/SillyTavern/config.yaml`（或 `$XDG_DATA_HOME/SillyTavern/config.yaml`）和 `~/.local/share/SillyTavern/data/`
- **Windows**：`%APPDATA%\SillyTavern\config.yaml` 和 `%APPDATA%\SillyTavern\data\`
- **MacOS**：`~/Library/Application Support/SillyTavern/config.yaml` 和 `~/Library/Application Support/SillyTavern/data/`

### 如何以全局模式运行

在全局模式下，`dataRoot` 和 `configPath` 不能通过 [CLI 命令行参数](../administration/config-yaml.md) 或 [config.yaml](../administration/config-yaml.md) 覆盖。

1. 给服务器启动命令加 `--global` 参数（如 `node server.js --global`）
2. 给 shell 启动脚本加 `--global` 参数（如 `Start.bat --global` 或 `./start.sh --global`）
3. 使用 `package.json` 中的 `start:global` 脚本（如 `npm run start:global`）

---

📖 原文链接：[Installation](https://docs.sillytavern.app/installation/)
