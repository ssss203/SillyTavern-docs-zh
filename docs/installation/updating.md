# 🔄 更新 SillyTavern
> 💡 **肆说**：更新SillyTavern的方法，保持最新版能获得最新功能和bug修复。

找到你的操作系统，按说明更新。

> 以下假设你已经安装并运行过 SillyTavern 至少一次。安装说明看 [安装页面](index.md)。

## Linux/Termux 或 MacOS

你一定是用 git 安装的，直接在 SillyTavern 目录里 `git pull` 就行：

- `cd SillyTavern` 进入目录
- `git pull` 获取更新
- `./start.sh` 或 `bash start.sh` 启动

## Windows

先试试用安装目录下的 `UpdateAndStart.bat`。如果失败，继续往下看。

### 方式1 - Git

我们一直推荐用 git 安装，原因很简单：用 `git clone` 安装的话，更新只需要在 ST 文件夹的命令行里输入 `git pull`。如果你装了 GitHub Desktop，也可以用 Repository 菜单的 Pull 功能。更新会自动安全地应用。

#### "我之前是用 Zip 安装的，想转 Git 怎么办？"

明智的选择！既然你是用 Zip 安装的，需要新建一个 Git 安装。按照 [Windows 安装指南](windows.md) 操作。用 git 在**不同文件夹**安装新的 SillyTavern 后，回来继续看下面第4步。

### 方式2 - Zip

如果你坚持用 Zip 安装，更新流程如下：

1. 下载新的发布版 zip
2. 解压到**你当前 ST 安装目录外面**的文件夹
3. 按你操作系统的常规流程安装 NodeJS 依赖
4. 按需从旧安装复制文件/文件夹

#### 更新 ≥1.12.0

从旧安装复制 `/data` 目录和 `config.yaml` 文件到新安装。如果你有服务器范围的扩展想保留，也复制 `/public/scripts/extensions/third-party` 目录。

#### 从 <1.12.0 更新到 >1.12.0

1.12.0 包含自动迁移程序。以下步骤仅在迁移中断或出错时才需要：

5. 运行新安装至少一次，创建 `/data/default-user` 目录
6. 按需从旧 `/public` 转移文件到新 `/data/default-user`

**注意：不要复制整个 /public/ 文件夹！** 那样会破坏新安装。

需要复制的文件夹/文件：
```
Assets
Backgrounds
Characters
Chats
Context
Groups
Group chats
Instruct
movingUI
KoboldAI Settings
NovelAI Settings
OpenAI Settings
QuickReplies
TextGen Settings
Worlds
User
settings.json
secrets.json
```

7. 复制后粘贴到新安装的 `/data/default-user` 文件夹（secrets.json 放根目录）
8. 重新启动 SillyTavern
9. 一切正常后可以安全删除旧 ST 文件夹

### 常见更新问题

#### "There are unresolved conflicts in the working directory."

这意味着你修改了默认文件，而这些文件在远程仓库中被更新了（比如设置了预设）。修复方法：

```
git merge --abort
git reset --hard
git pull --rebase --autostash
```

谨慎使用，可能造成数据丢失。确保有备份。

#### 文件修改阻止 git pull

- 如果你修改了 SillyTavern 系统文件，`git pull` 可能失败
- 通常是因为默认预设文件或 `package-lock.json`
- 试试移动/删除冲突文件后再 `git pull`
- 另一个方案：`git pull --rebase --autostash`

#### 启动时报 Error: Cannot find module "***"

- 这意味着 SillyTavern 添加了新的 npm 包依赖
- 在 SillyTavern 目录运行 `npm install`
- 没用的话删除 node_modules 文件夹重装

**Windows：**
```
rmdir /s /q node_modules
npm cache clean --force
npm install
```

**Unix/Linux：**
```
rm -rf node_modules
npm cache clean --force
npm install
```

## Docker

1. 终端进入 docker 目录：`cd SillyTavern/docker`
2. 删除容器：`docker compose down`
3. 删除镜像缓存：`docker rmi ghcr.io/sillytavern/sillytavern:latest`（如果是 staging 分支换成 `sillytavern:staging`）
4. 重建容器：`sudo docker compose up -d`

### 常见 Docker 更新问题

#### 更新后所有数据没了！

你需要按照 [Docker 迁移指南](st-1.12.0-migration-guide.md) 更新卷映射。

#### 权限拒绝

这是 Linux 问题。两种解决方式：
1. 简单方法：命令前加 `sudo`
2. 正确方法：修复你的权限设置

---

📖 原文链接：[How to Update SillyTavern](https://docs.sillytavern.app/installation/updating/)
