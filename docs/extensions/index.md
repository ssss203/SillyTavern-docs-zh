# 🧩 扩展功能（Extensions）
> 💡 **肆说**：扩展就像SillyTavern的"插件市场"，想要新功能就来这装。内置的已经够用了，不用急着装太多。

SillyTavern 自带很多扩展功能，可以在"扩展面板"里开启或关闭。扩展功能可以添加新功能、改变现有功能的行为，或者为 AI 提供额外内容。更多扩展可以通过扩展面板中的"下载扩展和素材"菜单安装。

## 扩展面板

在顶部栏选择 **Extensions** 就能打开或关闭扩展面板。

- **Manage extensions**：激活、停用和更新扩展
- **Download Extensions & Assets**：从 SillyTavern 仓库安装更多扩展、角色、音效和背景
- **Notify on extension updates**：勾选后当已安装扩展有更新时会通知你
- **Install extension**：从 Git 仓库 URL 导入第三方扩展

## 内置扩展

这些扩展已经内置在 SillyTavern 中，不需要额外安装。可以在扩展面板中启用或禁用。

- [**聊天翻译（Chat Translation）**](translation/)：把聊天消息翻译成其他语言
- [**图片描述（Image Captioning）**](captioning/)：从图片生成文字描述，让 AI 能"看到"并回应对话中的视觉内容
- [**图片生成（Image Generation）**](stable-diffusion/)：使用本地或云端的 Stable Diffusion、FLUX 或 DALL-E API 来生成图片
- [**角色表情图（Expression Images）**](expression-images/)：AI 角色的图片（也叫"sprites"/精灵图），显示在聊天窗口旁边或后面
- [**自动摘要（Summarize）**](summarize/)：自动生成聊天记录的摘要
- [**聊天向量化（Chat Vectorization）**](chat-vectorization/)：从聊天记录中找到相关消息并加入上下文
- [**文字转语音（Text To Speech）**](tts/)：通过 ElevenLabs、Silero、系统 TTS、[AllTalk](alltalk/)、[XTTS](xtts/) 等为聊天消息配音
- [**快捷回复（Quick Reply）**](../usage/st-script/#quick-replies-script-library-and-auto-execution)：一键回复消息、运行命令和 STscript 等
- **Token 计数器（Token Counter）**：把文字转换成 token 并计算数量

## 可安装扩展

你**必须**安装了 git 才能下载扩展。如果没装，请按照 [Git 安装页面](https://git-scm.com/downloads) 的指引操作。

你可以在应用内直接浏览所有可用扩展：进入 **Extensions** => **Download Extensions & Assets** 菜单，点击 **Load Asset List** 按钮。要安装某个扩展，点击 **Download** 按钮。要了解扩展详情，点击名称旁边的 **Link** 按钮打开其 GitHub 页面。

> ⚠️ 扩展不是 Extras。Extras 项目已于 2024 年 4 月停止维护。你不需要安装 Extras 就能使用扩展。

| 扩展名 | 功能说明 |
|--------|---------|
| [Blip](blip/) | 用可变速度动画显示角色消息文字，并伴随音效 |
| [Dynamic Audio](dynamic-audio/) | 为聊天添加沉浸式背景音乐和环境音 |
| [EmulatorJS](emulatorjs/) | 在 SillyTavern 聊天中直接玩复古主机游戏 |
| [Live2D](live2d/) | 支持 Live2D 模型，可自定义表情、动画和交互 |
| [Objective](objective/) | 为 AI 设置一个聊天中要达成的目标 |
| [RVC](rvc/) | 为语音合成模块添加实时语音克隆功能 |
| [Speech Recognition](speech-recognition/) | 用浏览器或 API 将语音转文字 |
| [VRM](vrm/) | 支持 VRM 模型，可自定义表情、动画和交互 |
| [Web Search](websearch/) | 将网络搜索结果加入 LLM 提示词 |
| [Regex](regex/) | 用正则表达式自动查找替换文本模式 |

更多扩展见 GitHub 官方仓库，可通过"下载扩展和素材"菜单安装。

## 第三方扩展

使用第三方扩展可能会产生意外副作用，也存在安全风险。在通过 **Install extension** 导入扩展前，请确保你信任该来源。我们不对第三方扩展造成的任何损害负责。

要安装第三方扩展，进入 **Extensions** => **Install Extension** 菜单，粘贴扩展仓库的 URL。可选指定分支和安装目标。扩展会自动下载并加载。

📖 原文链接：[Extensions](https://docs.sillytavern.app/extensions/)
