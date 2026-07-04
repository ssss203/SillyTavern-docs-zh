# 🚀 1.12.0 迁移指南
> 💡 **肆说**：1.12.0大版本迁移指南，新安装的不用看。

SillyTavern 1.12.0（代号"Neo Server"更新）包含几项关键变更，可能影响你的使用方式。

## 数据存储更新

1.12.0 改变了 SillyTavern 处理用户数据的方式。

以前，所有持久数据跟前端部分一起存放在 `/public` 目录中，这造成了混乱和潜在的故障点，也让容器化和系统级安装变得困难。

### 变了什么？

`/public` 中的所有持久信息（设置、聊天等）被移到了一个单独的可配置路径目录，使其可移植且独立于 Web 服务器本身。需要兼容的地方（如扩展托管、全尺寸角色卡、用户图片上传等），已设置智能重定向自动从数据目录托管用户文件。

### 设置数据根目录（Data Root）

你可以通过 `config.yaml` 或 `--dataRoot` 命令行参数提供数据根目录的绝对或相对路径：

**YAML 示例：**
```
dataRoot: C:\Users\Harry\Documents\ST-Data
```

**命令行示例：**
```
node server.js --dataRoot="/Users/harry/ST-Data"
```

默认数据根路径是 `./data`（SillyTavern 仓库中的 data 目录）。

> 注意：数据根路径必须是完整的绝对路径或完整的相对路径。不能用 `~` 或 `%APP_DATA%` 这种快捷方式，因为这些是由 shell 解析的，不是操作系统。

### 迁移

#### 重要！开始之前

1. **只有你想把数据根从默认位置移走时才需要设置。** 否则跳过。在更新后首次运行服务器前设置数据根。先运行 `npm install` 让 `config.yaml` 生成新值。
2. 所有数据会被迁移到 `default-user` 账户。见下方 [用户](#用户) 部分。

#### 非容器化（裸机）安装

你什么都不用做！当 ST 服务器检测到旧存储格式（检查 `/public/characters` 目录是否存在）时，自动迁移会处理一切。移动文件时会自动在 `/backups/_migration/YYYY-MM-DD` 目录创建备份，但手动做个完整备份是好习惯。

#### 容器化（Docker）安装

1. 创建新卷，挂载到容器的 "/home/node/app/data" 路径
2. 把 config 卷中除 `config.yaml` 外的所有内容移到 data 卷的 `default-user` 子目录
3. 重建并启动容器

#### 迁移什么？

| 之前路径 | 迁移后路径 |
|---|---|
| /secrets.json | /data/default-user/secrets.json |
| /thumbnails | /data/default-user/thumbnails |
| /vectors | /data/default-user/vectors |
| /public/settings.json | /data/default-user/settings.json |
| /public/stats.json | /data/default-user/stats.json |
| /public/assets | /data/default-user/assets |
| /public/backgrounds | /data/default-user/backgrounds |
| /public/characters | /data/default-user/characters |
| /public/chats | /data/default-user/chats |
| /public/context | /data/default-user/context |
| /public/scripts/extensions/third-party | /data/default-user/extensions |
| /public/group chats | /data/default-user/group chats |
| /public/groups | /data/default-user/groups |
| /public/instruct | /data/default-user/instruct |
| /public/KoboldAI Settings | /data/default-user/KoboldAI Settings |
| /public/movingUI | /data/default-user/movingUI |
| /public/NovelAI Settings | /data/default-user/NovelAI Settings |
| /public/OpenAI Settings | /data/default-user/OpenAI Settings |
| /public/QuickReplies | /data/default-user/QuickReplies |
| /public/TextGen Settings | /data/default-user/TextGen Settings |
| /public/themes | /data/default-user/themes |
| /public/worlds | /data/default-user/worlds |
| /default/content/content.log | /data/default-user/content.log |

## 用户

1.12.0 添加了（完全可选的）多用户设置功能，允许多个用户在同一个服务器上使用各自完全隔离的 SillyTavern 实例，甚至可以同时使用。用户账户还可以设密码保护。

请参考 [多用户](../administration/multi-user.md) 文档了解更多。

---

📖 原文链接：[1.12.0 Migration Guide](https://docs.sillytavern.app/installation/st-1.12.0-migration-guide/)
