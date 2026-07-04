# 🎵 动态音频（Dynamic Audio）
> 💡 **肆说**：给聊天加背景音乐和环境音，沉浸感加成。可以暂时跳过。

为 SillyTavern 聊天添加沉浸式背景音乐和环境音效。

## 前提条件
- 最新版 SillyTavern
- 从"下载扩展和素材"菜单安装 "Dynamic Audio" 扩展

## 设置

1. **连接素材仓库**：Extensions > Assets > Connect，下载想要的 BGM 和环境音
2. **启用扩展**：Extensions > Dynamic Audio，启用并调节音量
3. **表情联动 BGM**：启用后 BGM 跟随角色表情变化（需角色文件夹内有 BGM）

## 为角色导入音乐

1. 进入角色文件夹，如 `\SillyTavern\data\<user-handle>\characters\Seraphina`
2. 创建 `bgm` 子文件夹
3. 导入音乐文件，命名格式：`[情绪]_[编号].mp3`，如 `anger_0.mp3`、`joy_0.mp3`
4. 同情绪可多个音轨：`neutral_1.mp3`、`neutral_2.mp3`
5. 无情绪检测时随机播放 neutral 音轨

## 更改默认 BGM
替换/添加 `\SillyTavern\data\<user-handle>\assets\bgm` 中的音乐文件。

## 更改环境音
环境音文件名对应背景图片名（空格替换为短横线）。如 `bedroom-clean.mp3` 对应 "bedroom clean.jpg" 背景。

📖 原文链接：[Dynamic Audio](https://docs.sillytavern.app/extensions/dynamic-audio/)
