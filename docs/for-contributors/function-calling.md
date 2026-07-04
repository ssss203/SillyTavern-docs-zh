# 🔧 函数调用（Function Calling）
> 💡 **肆说**：开发者文档，做角色卡暂时跳过。

允许扩展添加动态功能，让 LLM 使用结构化数据触发特定功能。仅 Chat Completion API 支持，需在 AI Response 配置中启用。支持递归限制（默认5轮）和交错思考。使用 `registerFunctionTool()` 注册工具，`unregisterFunctionTool()` 注销。

📖 原文链接：[Function Calling](https://docs.sillytavern.app/for-contributors/function-calling/)
