# 📋 上下文模板（Context Template）
> 💡 **肆说**：这个只对 Text Completion API 有用。Chat Completion 用户跳过，用提示词管理器代替。

> 仅适用于 Text Completion API。Chat Completion API 用 [提示词管理器](prompt-manager.md)。

AI 模型通常需要你以特定方式提供角色数据。SillyTavern 包含多种预制的转换规则，你也可以自定义。

在"高级格式化"面板编辑。

## Story String（故事字符串）

这是提示词前言的模板，是向文本补全和指令模型添加角色卡信息的主要方式。

支持的 Handlebars 参数：
1. `{{anchorBefore}}` - "Before Story String" 位置的提示词
2. `{{anchorAfter}}` - "After Story String" 位置的提示词
3. `{{description}}` - 角色描述
4. `{{scenario}}` - 角色场景
5. `{{personality}}` - 角色个性
6. `{{system}}` - 系统提示词
7. `{{persona}}` - 人设描述
8. `{{char}}` - 角色名
9. `{{user}}` - 人设名
10. `{{wiBefore}}`/`{{loreBefore}}` - "Before Char Defs" 的世界信息
11. `{{wiAfter}}`/`{{loreAfter}}` - "After Char Defs" 的世界信息
12. `{{mesExamples}}` - 示例对话（指令格式化）
13. `{{mesExamplesRaw}}` - 示例对话（原始格式）

> 警告：如果以上任何参数从模板中缺失，它们就不会被发送！
> 💡 **肆说**：这就是说如果你删了模板里的 {{description}}，角色描述就不会发给AI了！改模板要小心。

## 示例分隔符

用作示例对话块之间的分隔标题。`<START>` 标签会被替换为该字段内容。

## Chat Start

在故事字符串和示例对话之后、第一条消息之前插入的分隔符。

## 名称作为停止字符串

将角色和人设名称添加到停止字符串列表。建议开启以防止模型冒充。

---

📖 原文链接：[Context Template](https://docs.sillytavern.app/usage/prompts/context-template/)
