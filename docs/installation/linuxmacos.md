# 🐧 Linux / Mac 安装
> 💡 **肆说**：Linux/Mac用户看这个，需要用终端命令。

## 手动 Git 安装

MacOS / Linux 的所有操作都在终端（Terminal）中完成。

1. 安装 git 和 nodeJS（方法因操作系统而异）
2. 克隆仓库：
   - 稳定版：`git clone https://github.com/SillyTavern/SillyTavern -b release`
   - 开发版：`git clone https://github.com/SillyTavern/SillyTavern -b staging`
3. `cd SillyTavern` 进入安装目录
4. 用以下命令之一运行启动脚本：
   - `./start.sh`
   - `bash start.sh`

## 通过 SillyTavern Launcher 安装

### Linux 用户

1. 打开你喜欢的终端，安装 git
2. 下载 SillyTavern Launcher：`git clone https://github.com/SillyTavern/SillyTavern-Launcher.git`
3. 进入目录：`cd SillyTavern-Launcher`
4. 启动安装：`chmod +x install.sh && ./install.sh`，选择你想安装的内容
5. 安装完成后启动：`chmod +x launcher.sh && ./launcher.sh`

### Mac 用户

1. 打开终端，安装 Homebrew：`/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`
2. 安装 git：`brew install git`
3. 下载 SillyTavern Launcher：`git clone https://github.com/SillyTavern/SillyTavern-Launcher.git`
4. 进入目录：`cd SillyTavern-Launcher`
5. 启动安装：`chmod +x install.sh && ./install.sh`，选择你想安装的内容
6. 安装完成后启动：`chmod +x launcher.sh && ./launcher.sh`

---

📖 原文链接：[Linux/MacOS Install](https://docs.sillytavern.app/installation/linuxmacos/)
