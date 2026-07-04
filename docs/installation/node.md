# 📦 更新 Node.js
> 💡 **肆说**：手动安装Node.js的指南，一般安装脚本会自动处理，不需要单独看。

保持 Node.js 运行时更新很重要，涉及安全和性能。以下是各操作系统更新 Node.js 的步骤。

推荐使用最新的 LTS（Long Term Support，长期支持）版本，可在 [Node.js 官网](https://nodejs.org/en/about/previous-releases) 查看。

## 检查当前 Node.js 版本

1. 打开终端或命令提示符
2. 输入：`node -v`

## nvm（Node Version Manager，Node版本管理器） - 跨平台

如果你装了 `nvm`：

**Unix/Linux/macOS：**
```
nvm install --lts
nvm use --lts
```

**Windows：**
```
nvm install lts
nvm use lts
```

## Windows - 常规安装

1. 去 [Node.js 下载页](https://nodejs.org/en/download/)
2. 下载 Windows LTS 安装程序
3. 运行安装程序按提示完成

## Windows - SillyTavern Launcher

1. 打开 SillyTavern Launcher
2. 进入 `Toolbox / App Installer / Core Utilities / Install Node.js`

或手动用 winget：`winget install --id=OpenJS.NodeJS.LTS -e`

## Android - Termux

```
pkg update
pkg upgrade nodejs-lts
```

别忘了按 `Y` 确认更新提示。

## macOS - 常规安装

1. 去 [Node.js 下载页](https://nodejs.org/en/download/)
2. 下载 macOS LTS 安装程序
3. 运行 `.pkg` 文件按提示完成

## macOS - Homebrew

```
brew update
brew upgrade node
```

## Linux - 包管理器

方法因发行版而异。官方仓库的 Node.js 版本可能不是最新的，推荐使用 [nvm](https://github.com/nvm-sh/nvm) 或 [NodeSource 仓库](https://github.com/nodesource/distributions)。

## Docker

无需操作。预构建的 Docker 镜像已包含最新版 Node.js。

---

📖 原文链接：[How to update Node.js](https://docs.sillytavern.app/installation/updating/node/)
