# ⚙️ 高级格式化
> 💡 **肆说**：这个页面主要是给 Text Completion API 用户看的。如果你用的是 Chat Completion（比如 OpenAI/Claude），去提示词管理器那边调就行。

这些设置让你对 Text Completion API 的提示词构建策略有更多控制。

> 大部分设置不适用于 Chat Completion API，它们由提示词管理器控制。
> 💡 **肆说**：再说一遍，用Chat Completion API的可以直接跳过这个页面。

- **系统提示词**：定义模型的通用指令
> 💡 **肆说**：系统提示词是"告诉AI它是谁、要干嘛"的总指令，写卡会直接用到。
- **上下文模板**：AI 模型需要以特定方式提供角色数据的转换规则
- **分词器**：把文本拆成 token 的工具
- **自定义停止字符串**：JSON 格式的停止字符串数组

## 重置模板

可以通过 UI 或手动删除数据文件恢复默认模板。

## 后端定义模板

有些 Text Completion 来源可以自动选择模型作者推荐的模板。需要：
1. 启用"派生模板"选项
2. 选择支持的后端（llama.cpp 或 KoboldCpp）
3. 模型正确报告元数据
4. 报告的聊天模板哈希匹配已知 SillyTavern 模板

## 开始回复前缀（Start Reply With）

- **Text Completion API**：预填充提示词最后一行，强制模型从该点继续
- **Chat Completion API**：在提示词末尾添加助手角色消息。部分后端不支持

---

📖 原文链接：[Advanced Formatting](https://docs.sillytavern.app/usage/core-concepts/advancedformatting/)
