# 🧠 推理（Reasoning）
> 💡 **肆说**：推理功能让AI"先想想再回答"，适合需要逻辑推理的场景。用 DeepSeek R1 或 Claude 的思维链时才需要关注。

在语言模型中，推理（也叫模型思考）指的是模仿人类逐步分析的思维链（CoT，Chain-of-Thought）技术。SillyTavern 提供多项功能使推理模型的使用更高效一致。

## 常见问题

1. 使用推理模型时，模型的内部推理过程会消耗你的回复 token 额度，即使推理不在最终输出中显示。如果回复不完整或为空，尝试调高 AI 回复配置面板中的最大回复长度。推理模型通常需要 1024 到 4096 token 的限制。
> 💡 **肆说**：所以用推理模型时要把最大回复长度调高，不然AI想完了token也用完了，实际输出就几行。建议设到2048以上。

## 配置

大部分推理相关设置在"高级格式化"面板的 Reasoning 部分配置。

推理块在聊天中显示为可折叠的消息区域。默认折叠以节省空间。

## 添加推理

### 手动
通过消息编辑菜单添加。点击  添加推理区域。

### 通过命令
用 `/reasoning-set` STscript 命令：
```
/reasoning-set at=0 这是第一条消息的推理。
```

### 通过后端
支持的来源：Claude、DeepSeek、Google AI Studio、Google Vertex AI、OpenRouter、xAI (Grok)、AI/ML API、Z.AI、Pollinations、MistralAI、Electron Hub、Chutes、NanoGPT、Moonshot。

在 AI 回复配置面板启用"Request model reasoning"。

### 通过解析
在高级格式化面板启用"Auto-Parse"自动从模型输出解析推理。回复必须包含配置的前缀和后缀序列包裹的推理区域。

## 推理效果等级（Reasoning Effort）

影响推理可能使用的 token 数量。各等级对应不同来源的具体参数值，详见原文表格。

---

📖 原文链接：[Reasoning](https://docs.sillytavern.app/usage/prompts/reasoning/)
