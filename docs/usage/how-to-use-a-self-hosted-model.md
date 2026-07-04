# 🖥️ 自建 AI 模型指南
> 💡 **肆说**：想免费无限用AI？自己跑模型！但需要有6GB+显存的显卡。没有好显卡就老实用云端API吧。

本指南帮助你用 SillyTavern 连接本地 AI（我们开始用正确的术语：LLM，Large Language Model，大语言模型）。

## 硬件要求

- 有几千个免费 LLM 可以下载
- 跑未压缩的 LLM 需要怪兽级 GPU（你大概率没有）
- 可以用**量化（Quantization，压缩模型格式）**降低显存需求，如 GPTQ 或 AWQ。模型能力稍降但显存需求大减
- **GGUF**（之前叫 GGML）是普通人的首选格式，可以不用 GPU，只用 CPU 和内存运行。比 GPU 慢约15倍，但模型能力一样好
> 💡 **肆说**：GGUF是普通人的首选！CPU也能跑，不需要高端显卡。只是比GPU慢一些。
- 模型大小以参数量命名：7B、13B、30B、70B 等。可以理解为"大脑大小"，越大越聪明但越吃资源
- 量化程度有 8-bit、5-bit、4-bit 等。越低越省资源但模型越退化。3-bit 和 2-bit 基本没法用了
- **上下文大小**（对话能多长不丢内容）也影响显存/内存需求

## 下载 LLM

最常见的地方是 HuggingFace。推荐看 bartowski 的 GGUF 模型：[https://huggingface.co/bartowski](https://huggingface.co/bartowski)

- GGUF 格式只需要 .gguf 文件（通常 4-11GB）
- .safetensors 文件如果文件名有编号需要全部下载

## 安装 LLM 服务器

### 用 KoboldCpp（无需安装，GGUF 模型）
> 💡 **肆说**：最简单的本地方案，下载一个文件、选模型、点启动，完事。

1. 访问 [https://koboldai.org/cpp](https://koboldai.org/cpp) 下载
2. 启动 KoboldCpp，用 Browse 选择 GGUF 模型
3. 调整上下文大小（默认最大 4K）
4. 点击 Launch
5. 在 SillyTavern 选 Text Completion -> KoboldCpp，URL 设为 `http://127.0.0.1:5001/`
6. 点击 Connect

### 用 Oobabooga

1. `git clone https://github.com/oobabooga/text-generation-webui`
2. 运行 `start_windows.bat`
3. 选择 GPU 类型
4. 把模型文件放入 `text-generation-webui/user_data/models`
5. 编辑 `CMD_FLAGS.txt`，写入 `--api`
6. 重启 Oobabooga
7. 在浏览器访问 `http://127.0.0.1:5000/docs` 确认 FastAPI 页面加载
8. 在 Oobabooga 加载模型
9. 在 SillyTavern 选 Text Completion -> Default (Oobabooga)，URL 设 `http://127.0.0.1:5000/`

---

📖 原文链接：[Self-hosted AI models](https://docs.sillytavern.app/usage/how-to-use-a-self-hosted-model/)
