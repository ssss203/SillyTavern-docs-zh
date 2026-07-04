# 🐱 TabbyAPI
> 💡 **肆说**：本地跑Exl2格式模型的API，速度很快但需要不错的显卡。免费！不用梯子！新手先看KoboldCpp或Ollama。

基于 FastAPI 的应用，使用 Exllamav2 后端生成文本，支持 Exl2、GPTQ 和 FP16 模型。

## 快速开始

1. 按 [安装指南](https://github.com/theroyallab/tabbyAPI/wiki/01.-Getting-Started) 安装
2. [创建 config.yml](https://github.com/theroyallab/tabbyAPI/wiki/02.-Server-options) 设置模型路径等
3. 启动 TabbyAPI
4. 在 SillyTavern 的 Text Completion API 选 TabbyAPI
5. 复制终端中的 API 密钥到 ST，确认 API URL 正确（默认 `http://127.0.0.1:5000`）

## TabbyAPI Loader 扩展

官方扩展，可直接从 ST 加载/卸载模型：
1. 在扩展标签页进入 Download Extensions & Assets
2. 粘贴 `https://raw.githubusercontent.com/theroyallab/ST-repo/main/index.json` 到 Assets URL
3. 下载 Tabby Loader
4. 在 TabbyAPI Loader 中填入 Admin Key，刷新模型列表

---

📖 原文链接：[TabbyAPI](https://docs.sillytavern.app/usage/api-connections/tabbyapi/)
