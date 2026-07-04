# 💻 Windows 安装
> 💡 **肆说**：Windows用户看这个，最简单的安装方式。

> ⛔ **不要安装到 Windows 管控的文件夹**（如 Program Files、System32 等）
> ⛔ **不要用管理员权限运行 Start.bat**
> ⛔ **Windows 7 无法安装**，因为跑不了 NodeJS 20

## 方式一：通过 Git 安装

1. 安装 [NodeJS](https://nodejs.org/en)（推荐最新 LTS 长期支持版）
2. 安装 [Git for Windows](https://gitforwindows.org/)
3. 打开 Windows 资源管理器（`Win+E`）
4. 找到或创建一个不受 Windows 管控的文件夹（如 `C:\MySpecialFolder`）
5. 在该文件夹的地址栏输入 `cmd`，按回车，打开命令提示符
6. 在黑色命令行窗口输入以下命令之一并回车：
   - 稳定版：`git clone https://github.com/SillyTavern/SillyTavern -b release`
   - 开发版：`git clone https://github.com/SillyTavern/SillyTavern -b staging`
7. 克隆完成后，双击 `Start.bat`，NodeJS 会自动安装所需依赖
8. 服务器启动后，SillyTavern 会在浏览器中弹出

## 方式二：通过 SillyTavern Launcher 安装

1. 键盘按 **`WINDOWS + R`** 打开运行对话框，输入以下命令安装 git：
   ```
   cmd /c winget install -e --id Git.Git
   ```
2. 键盘按 **`WINDOWS + E`** 打开文件资源管理器，进入你想安装的文件夹，在地址栏输入 `cmd` 回车，然后运行：
   ```
   git clone https://github.com/SillyTavern/SillyTavern-Launcher.git && cd SillyTavern-Launcher && start installer.bat
   ```

## 方式三：通过 GitHub Desktop 安装

（这种方式只能在 GitHub Desktop 里用 git，如果你想也在命令行用 `git`，还需要安装 [Git for Windows](https://gitforwindows.org/)）

1. 安装 [NodeJS](https://nodejs.org/en)（推荐最新 LTS 版）
2. 安装 [GitHub Desktop](https://central.github.com/deployments/desktop/desktop/latest/win32)
3. 打开 GitHub Desktop，点击 "Clone a repository from the internet...."（注意：这步**不需要**创建 GitHub 账号）
4. 点击 URL 标签页，输入 `https://github.com/SillyTavern/SillyTavern`，点击 Clone。你可以修改 Local path 来改变安装位置
5. 用 Windows 资源管理器进入克隆的文件夹。默认路径是：`C:\Users\[你的用户名]\Documents\GitHub\SillyTavern`
6. 双击 `start.bat` 文件（注意：`.bat` 后缀可能被系统隐藏，文件名可能只显示 "Start"，双击它就行）
7. 双击后会弹出一个大的黑色命令行窗口，SillyTavern 开始安装所需依赖
8. 安装完成后，如果一切正常，命令行窗口会显示启动信息，浏览器中会打开 SillyTavern
9. 连接任意 [支持的 API](../usage/api-connections/index.md) 就可以开始聊天了！

---

📖 原文链接：[Windows Installation](https://docs.sillytavern.app/installation/windows/)
