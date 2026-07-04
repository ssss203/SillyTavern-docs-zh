# 聊天文件管理
> 💡 **肆说**：聊天记录可以导出备份、创建分支（检查点），写长篇故事时检查点功能很实用，后悔了可以回到之前的节点。

本页面描述了管理AI聊天文件的方式。

## 单聊 vs 群聊

使用角色卡最简单的方式是单聊；只需点击角色卡开始聊天。当你有几个角色卡后，还可以创建包含多个角色的[群聊](groupchats.md)。

## 聊天导入

**从Character.AI导入聊天：** 使用CAI Tools浏览器扩展：https://github.com/irsat000/CAI-Tools

其他可导入聊天的程序：TavernAI、Text Generation WebUI（oobabooga）、Agnai、KoboldAI Lite、RisuAI

## 导出为 .jsonl

点击"管理聊天文件"时，每个条目都有导出按钮，可导出为可重新导入的格式。包含所有元数据（不含图片和文件附件）。

## 导出为 .txt

可通过"下载聊天为纯文本文档"按钮导出纯文本版本。无法重新导入。

## 检查点

"检查点"是当前聊天的克隆，复制到某一点的所有消息。从消息的三个点按钮创建：

- "创建分支"：克隆并切换到它
- "创建检查点"：克隆、命名但不切换

从汉堡菜单"返回父聊天"可回到主聊天。

## 重命名聊天

默认以日期时间命名。点击铅笔图标可更改。注意会断开检查点链接。

📖 原文链接：[Chat File Management](https://docs.sillytavern.app/usage/core-concepts/chatfilemanagement/)
