# 🎯 提示词（Prompts）
> 💡 **肆说**：提示词就是发给AI的完整"输入包"，理解它的构成对写卡和调试至关重要。写卡必读！

当你给 AI 发消息时，你写的文字会和其他文字组合成一条完整的"提示词"（也叫"请求"或"上下文"）发给 AI。

提示词可以包含多种类型的文字：
- [主指令](#主指令system-prompt) - 告诉 AI 如何生成回复
- [角色定义](../core-concepts/characterdesign.md) - 定义 AI 扮演的角色
- [人设定义](../core-concepts/personas.md) - 定义你的身份
- [世界信息](../core-concepts/worldinfo.md) - AI 所处世界的信息
- [数据银行](../core-concepts/data-bank.md) 的相关文档
- [摘要](../../extensions/summarize.md) - 过去对话的总结
- [网页搜索](../../extensions/websearch.md) 结果
- 之前的对话消息
- **你发给 AI 的消息**
- [后历史指令](#后历史指令post-history-instructions) - 生成回复前的最后指令

## 查看提示词
> 💡 **肆说**：AI回复不满意？先看提示词！点消息上的提示词图标能看到AI到底收到了什么，十有八九问题出在这。

查看发给 AI 的最终提示词非常有用，能理解 AI 为什么那样回复。查看方式：
- 用 AI 回复消息上的提示词明细图标
- 用 Prompt Inspector 扩展
- 查看 ST 终端窗口的日志
- 查看浏览器开发者工具的控制台

## 更改提示词构建方式

- **Text Completion API**：用 [高级格式化](../core-concepts/advancedformatting.md) 面板
- **Chat Completion API**：用 [提示词管理器](prompt-manager.md)

## 主指令（System Prompt / Main Prompt）
> 💡 **肆说**：主指令就是"总规矩"，告诉AI要扮演谁、怎么回复。写卡会直接改这个。

主指令定义模型应遵循的通用指令，设定对话的基调和上下文。

默认主指令是：
```
Write {{char}}'s next reply in a fictional chat between {{char}} and {{user}}.
```
`{{char}}` 和 `{{user}}` 占位符会被替换为你定义的角色和人设名字。

### 调整主指令

常见调整原因：
- **提供额外指令**：比如让 AI 解释推理过程、遵循特定规则
- **明确 AI 的角色**：比如让 AI 当旁白、故事讲述者或向导
- **改变对话上下文**：比如让 AI 当 AI 助手、文字冒险游戏或写作伙伴

> AI 更容易遵循"应该做什么"的指令，而不是"不该做什么"。
> 💡 **肆说**：这条超重要！告诉AI"用第三人称写"比告诉AI"不要用第一人称"有效得多。

### 消息历史的影响

对话已有历史时，更改主指令的效果有限。建议：
- 用 [作者备注](../core-concepts/authors-note.md) 在消息历史附近插入当前指令
- 通过开新对话来测试主指令更改
- 编辑消息历史去除不需要的行为示例

### 去掉"虚构聊天"上下文

```
Write {{char}}'s next reply in a conversation with {{user}}.
```

或完全去掉角色概念：
```
You are {{char}}, a helpful assistant. You provide useful information and help {{user}} with their questions.
```

### AI 当旁白/故事讲述者

创建一个名为"Narrator"或"AI"的角色，调整主指令：
```
You are {{char}}, a skilled and versatile storyteller. Narrate the story.
```

## 后历史指令（Post-History Instructions, PHI）
> 💡 **肆说**：后历史指令是AI看到的最后一条指令，所以AI会特别重视它。适合放"一定要记住"的规则。

后历史指令在主指令和用户消息之后发送给 AI。因为是 AI 生成回复前收到的最后指令，AI 通常会给予更高优先级，可以覆盖主指令。

要使用每个角色专属的后历史指令，添加到角色的后历史指令字段并启用"Prefer Char. Instructions"。

---

📖 原文链接：[Prompts](https://docs.sillytavern.app/usage/prompts/)
