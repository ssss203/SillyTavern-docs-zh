# 📱 Android 安装（通过 Termux）
> 💡 **肆说**：在Android手机上直接跑SillyTavern！不需要电脑，但设置有点折腾。

SillyTavern 可以在 Android 设备上通过 Termux 原生运行。

## 安装 Termux

**不要从 Google Play 商店安装 Termux**，那个版本已不再维护。请用 F-Droid（推荐）或 GitHub Releases 获取最新版。

1. 从 [F-Droid](https://f-droid.org/en/packages/com.termux/) 或 [GitHub Releases](https://github.com/termux/termux-app/releases) 下载 Termux
2. 安装下载的 APK 文件
3. 打开 Termux，运行第一条命令：
   ```
   termux-change-repo
   ```
4. 选择 "Mirror group"，选离你最近的服务器。你可以用 [Unexpected Keyboard](https://play.google.com/store/apps/details?id=juloo.keyboard2&hl=en) 的滑动手势来操作
5. 更新 Termux：
   ```
   pkg update && pkg upgrade
   ```

## 安装依赖

安装必需的包：

```
pkg install git nodejs-lts nano
```

如果你是 32 位 Android，看下面的 [常见错误](#常见错误) 章节。

## 安装 SillyTavern

克隆 SillyTavern 仓库（[如何选择分支](index.md)）：

- **稳定版：**
  ```
  git clone https://github.com/SillyTavern/SillyTavern -b release
  ```
- **开发版：**
  ```
  git clone https://github.com/SillyTavern/SillyTavern -b staging
  ```

## 运行 SillyTavern

进入目录并运行启动脚本：

```
cd ~/SillyTavern
bash start.sh
```

更新 SillyTavern：

```
cd ~/SillyTavern
git pull --rebase --autostash
```

看下面的 [别名设置](#可选设置命令别名) 来简化这些操作。

## 常见错误

### Unsupported platform: android arm LEtime-web

32 位 Android 需要一个 npm 无法安装的外部依赖。运行以下命令安装：

```
pkg install esbuild
```

然后继续上面的安装步骤。

### 性能优化

关于一般的性能提示，参考 [FAQ 性能优化](../usage/faq.md) 部分。

由于 Android 设备硬件限制，你可能需要调整以下 [config.yaml](../administration/config-yaml.md) 设置来优化内存、存储和 CPU 使用：

```
performance:
  # 避免加载所有角色数据，等到需要时再加载
  lazyLoadCharacters: true
  # 禁用磁盘缓存以减少存储占用
  useDiskCache: false
backups:
  chat:
    # 可选：禁用自动聊天备份以节省存储
    enabled: false
```

用 Termux 自带的 `nano` 编辑器修改 `config.yaml`：`nano ~/SillyTavern/config.yaml`

## 可选：设置命令别名

你可以创建常用命令的快捷方式，让操作更方便。

1. 打开编辑器修改 `.bashrc`：
   ```
   nano ~/.bashrc
   ```
2. 添加以下行来创建别名：
   ```
   # 更新 Termux 包
   alias pkgup="pkg update && pkg upgrade"
   # 启动 SillyTavern
   alias st='cd ~/SillyTavern && bash start.sh'
   # 更新 SillyTavern
   alias stup='cd ~/SillyTavern && git pull --rebase --autostash'
   ```
3. 保存文件并退出编辑器（在 nano 中按 `CTRL + X`，然后 `Y`，然后回车）
4. 让更改生效：
   ```
   source ~/.bashrc
   ```

现在你可以用这些快捷命令了：
- `st` 启动 SillyTavern
- `stup` 更新 SillyTavern
- `pkgup` 更新 Termux 包

## 延伸阅读

以下指南不是 SillyTavern 团队维护的：
- Termux 安装指南（ArroganceComplex#2659）：[https://rentry.org/STAI-Termux](https://rentry.org/STAI-Termux)
- 用 Material Files 访问 Termux 文件：[https://www.learntermux.tech/2020/10/Termux-File-Manager.html](https://www.learntermux.tech/2020/10/Termux-File-Manager.html)
- 防止 Termux 进程深度休眠：[https://wiki.termux.com/wiki/Termux-wake-lock](https://wiki.termux.com/wiki/Termux-wake-lock)

---

📖 原文链接：[Android (Termux) Installation](https://docs.sillytavern.app/installation/android-(termux)/)
