# 🔌 API 连接
> 💡 **肆说**：这是你用SillyTavern之前必须搞定的——连上AI模型才能聊天。先看这个页面了解全貌，再选适合你的API。

SillyTavern 可以连接多种 LLM API。以下是各自的特点、优缺点和使用场景。

## ELI5（Explain Like I'm 5，像跟5岁小孩解释）：Chat Completions 对比 Text Completions

当你用 ST 发消息时，你的聊天、角色描述和其他提示词会被组合成一条"提示词"（Prompt）发给模型。API"类型"决定了这条提示词如何构建。

### Chat Completions（聊天补全）
把提示词构建成用户、助手和系统之间的一系列消息，营造"聊天"的感觉。

### Text Completions（文本补全）
把提示词转成一条长字符串，模型只是尝试接着往下写。大多数有推荐的"指令模板"（Instruct Template）帮助它们像聊天一样回复。

## 本地 API
> 💡 **肆说**：免费！不用梯子！但需要有张显卡（6GB显存起步）而且设置比较折腾。

- 在你自己的电脑上运行，免费使用，无内容过滤
- 安装过程可能复杂（SillyTavern 开发团队不提供支持）
- 需要从 HuggingFace 单独下载模型（5-50GB 每个）

### KoboldCpp
易用 API，支持 CPU 卸载和流式输出。单文件运行。支持 GGUF 模型。比纯 GPU 加载器慢。

### llama.cpp
KoboldCpp 和 Ollama 的原始来源。支持 GGUF 模型。轻量级 CLI。

### Ollama
最易安装使用。精美模型目录一键下载。支持 GGUF 模型。

### Oobabooga TextGeneration WebUI
一体化 Gradio UI。最广泛格式支持（AWQ/Exl2/GGML/GGUF/GPTQ/FP16）。一键安装器。

### TabbyAPI
轻量级 Exllamav2 API。支持 Exl2/GPTQ/FP16。有官方 ST 扩展。不推荐低显存用户。

## 云端 LLM API
> 💡 **肆说**：花钱但省心，AI也更强。大部分国内用需要梯子。

- 作为云服务运行，你的电脑不需要资源
- 比大多数本地 LLM 更强
- 但都有内容过滤，大部分需付费

### AI Horde - 开箱即用，社区志愿者 GPU
> 💡 **肆说**：免费但质量随机，纯公益，适合先试试水。
### OpenAI (ChatGPT) - 设置简单，按量付费
### Claude (Anthropic) - 创意写作风格
### Google AI Studio / Vertex AI - 有免费额度
### Mistral AI - 高效模型，有免费额度
### OpenRouter - 统一 API 访问所有主要 LLM，按 token 付费
### DeepSeek - 最新模型，便宜
> 💡 **肆说**：国内用户福音！便宜好用，国内直连不用梯子，写卡效果不错。
### NovelAI - 无内容过滤，需付费
### DreamGen - 无审查创意写作模型
### Pollinations - 无需设置，免费
> 💡 **肆说**：免费！不用梯子！无需设置直接用，但质量有限。

各 API 详细设置指南见左侧导航栏对应页面。

---

📖 原文链接：[API Connections](https://docs.sillytavern.app/usage/api-connections/)
