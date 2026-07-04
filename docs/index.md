# 🍺 SillyTavern 中文文档（人话版）
> 💡 **肆说**：SillyTavern中文文档首页，按需阅读。建议先从"使用指南"开始。

> 这是什么？SillyTavern（简称 ST）是一个装在你电脑或手机上的聊天界面软件，让你能跟各种 AI 大模型聊天、写故事、玩角色扮演。你可以把它想象成一个"AI聊天器"的前端界面，它本身不包含 AI，但你连上 AI 接口就能用了。

## 🎯 这个中文文档是什么？

这是 SillyTavern 官方文档的**中文人话翻译版**。目标读者是英语不太好的中国新手用户。

特点：
- 所有内容跟官方文档对齐，不删减
- 技术术语保留英文但加中文注释，比如"LLM（大语言模型）"
- 外行人不懂的说法，换成容易理解的大白话
- 代码块、命令、文件名、参数名不翻译
- 每页底部附原文链接，可点击跳转

## 📖 SillyTavern 简介

SillyTavern（简称 ST）是一个本地安装的用户界面（UI），让你可以和各种文本生成大语言模型（LLM，Large Language Model）、图像生成引擎、语音合成（TTS，Text-to-Speech）模型互动。我们的目标是让用户对 LLM 提示词（Prompt）拥有尽可能多的控制权——学习曲线确实陡，但这也是乐趣的一部分！

SillyTavern 是一个热情的开源项目，由一群 LLM 爱好者社区打造，永远免费开源。2023年2月从 TavernAI 1.2.8 分叉出来，现在已经有超过 300 名贡献者和 3 年的独立开发历史。

## 💻 安装要求

硬件要求很低：只要能运行 NodeJS 20 或更高版本的机器都行。如果你打算在本机跑 LLM 推理（推理就是让 AI 生成文字的过程），我们推荐 NVIDIA 3000 系列以上、至少 6GB 显存（VRAM）的显卡。

按你的平台选择安装指南：
- [Windows 安装](installation/windows.md)
- [Linux 和 Mac 安装](installation/linuxmacos.md)
- [Android 安装](installation/android-termux.md)
- [Docker 安装](installation/docker.md)

## 🌿 分支（Branch）说明

SillyTavern 用双分支系统开发：

- `release` - 🌟 **推荐大多数用户用这个。** 这是最稳定的分支，只有大版本更新时才推送。适合大多数用户。通常每月更新一次。
- `staging` - ⚠️ **不推荐日常使用。** 这个分支有最新功能，但随时可能出问题。只适合高级用户和爱好者。每天更新好几次。

## 🤖 除了 SillyTavern 我还需要什么？

SillyTavern 只是一个界面，你还需要一个 LLM 后端来提供推理能力。你可以用 AI Horde 开箱即聊。除此之外，我们还支持很多本地和云端 LLM 后端：OpenAI 兼容 API、KoboldAI、Tabby 等等。更多信息请看 [API 连接](usage/api-connections/index.md) 章节。

## 🃏 角色卡（Character Cards）

SillyTavern 的核心理念是"角色卡"。角色卡是一组提示词（Prompt）的集合，用来设定 LLM 的行为方式，在 SillyTavern 中进行持续性对话必须用到它。功能类似于 ChatGPT 的 GPTs 或 Poe 的机器人。角色卡的内容可以是任何东西：一个抽象场景、一个针对特定任务的助手、一个名人或虚构角色。

想快速聊个天而不选角色卡，或者只是测试 LLM 连接，直接在 [欢迎界面](usage/welcome-assistants.md) 的输入栏输入提示词就行。这会创建一个空的"助手"角色卡，你之后可以自定义。

想了解如何定义角色卡，可以看默认角色 Seraphina，或从"下载扩展和资产"菜单下载社区精选的角色卡。

你也可以从头创建自己的角色卡，参考 [角色设计](usage/core-concepts/characterdesign.md) 指南。

## ✨ 核心功能

- 高级 [文本生成设置](usage/common-settings.md)，附带大量社区预设
- [世界信息 World Info](usage/core-concepts/worldinfo.md)：创建丰富的世界观设定，或节省角色卡的 token
- [群聊](usage/core-concepts/groupchats.md)：多角色房间，角色之间可以互相聊天
- [丰富的 UI 自定义选项](usage/core-concepts/uicustomization.md)：主题颜色、背景图片、自定义 CSS 等
- [用户人设](usage/core-concepts/personas.md)：让 AI 知道你是谁，增强沉浸感
- [内置 RAG（检索增强生成）支持](usage/core-concepts/data-bank.md)：给聊天添加文档让 AI 参考
- 丰富的 [聊天命令](usage/core-concepts/slashcommands.md) 子系统和自己的 [脚本引擎](usage/st-script.md)

## 🧪 扩展插件

SillyTavern 支持扩展：
- [角色表情图（Sprites）](extensions/expression-images.md)
- [聊天记录自动摘要](extensions/summarize.md)
- 自动 UI 和 [聊天翻译](extensions/translation.md)
- [Stable Diffusion/FLUX/DALL-E 图像生成](extensions/stable-diffusion.md)
- [AI 回复的语音合成 TTS](extensions/tts.md)
- [网页搜索，给提示词添加真实世界信息](extensions/websearch.md)
- 更多扩展可从"下载扩展和资产"菜单下载

## 📜 许可证

SillyTavern 是一个免费开源项目，采用 [AGPL-3.0 许可证](https://github.com/SillyTavern/SillyTavern/blob/release/LICENSE) 发布。

---

📖 原文链接：[What is SillyTavern?](https://docs.sillytavern.app/)
