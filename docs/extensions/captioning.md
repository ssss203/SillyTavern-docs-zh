# 🖼️ 图片描述（Image Captioning）
> 💡 **肆说**：让AI能"看懂"你发的图，自动生成图片描述塞进上下文。不常用到但偶尔很有用。

自动为聊天中的图片生成文字描述，让 AI 能"看到"并回应视觉内容。内置扩展，无需额外安装。

## 快速开始
1. Extensions 面板 > Image Captioning > 选来源（Local/Multimodal）
2. 从 Extensions 弹出菜单选 "Generate Caption" > 选图片
3. 带描述的图片插入消息，点 Send

## 来源选择

| 来源 | 说明 |
|------|------|
| **Multimodal** | 云端(OpenAI/Claude/Google等)或本地(Ollama/llama.cpp/KoboldCpp等)，支持自定义提示词 |
| **Local** | 用 transformers.js 在本地运行，零设置 |
| **Horde** | AI Horde 众包网络，免费但响应时间不稳定 |

## 描述配置
- **Caption Prompt**：自定义提示词，默认 "What's in this image?"
- **Ask every time**：每次都要求输入提示词
- **Message Template**：消息模板，用 `{{caption}}` 宏。默认 `[{{user}} sends {{char}} a picture that contains: {{caption}}]`
- **Auto-captioning**：自动为粘贴/附加的图片生成描述
- **Edit captions before saving**：保存前编辑描述

## 斜杠命令 /caption
```
/caption [quiet=true|false] [mesId=number] [prompt]
```
示例：
```
/caption
/caption Describe the main colours
/caption mesId=5 quiet=true
/caption mesId=10 Describe image keywords | /imagine
```

## Multimodal 来源
先在 API Connections 设置好连接，再在 Captioning 选择使用。

支持：OpenAI、Claude、Google AI Studio、Ollama、KoboldCpp、llama.cpp、vLLM、OpenRouter、Groq、MistralAI 等几十种 API。

### 次要端点
可为多模态描述设置独立的次要端点 URL，支持 KoboldCpp/llama.cpp/Ollama/oobabooga/vLLM。

## Local 来源
在 `config.yaml` 的 `extensions.models.captioning` 改 HuggingFace 模型 ID。默认 `Xenova/vit-gpt2-image-captioning`。

📖 原文链接：[Image Captioning](https://docs.sillytavern.app/extensions/captioning/)
