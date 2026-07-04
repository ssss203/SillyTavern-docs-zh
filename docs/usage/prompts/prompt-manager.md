# 🎛️ 提示词管理器（Prompt Manager）
> 💡 **肆说**：提示词管理器是 Chat Completion API 用户的核心控制台，写卡会直接用到！可以精确控制发给AI的内容和顺序。

提示词管理器提供对 Chat Completion API 的提示词构建策略的更细粒度控制。

> 仅适用于 Chat Completion API。Text Completion API 用 [高级格式化](../core-concepts/advancedformatting.md)。
> 💡 **肆说**：用 OpenAI/Claude/Google 等的看这里，用本地模型的去高级格式化那边。

> 命名提示：如果预设名称跟你的角色卡名称相同，开始跟该角色聊天时会自动选中。给预设起独特的名字避免此行为。

## 快速提示词编辑
> 💡 **肆说**：这三个编辑框是你最常改的地方——主指令改AI的"总规矩"，后历史指令改"最后叮嘱"，辅助提示词改"额外要求"。

提供空间快速编辑常见提示词部分：**主指令**、**辅助提示词** 和 **后历史指令**。

## 工具提示词

### 格式模板
用于包装从世界信息和角色卡中提取的信息。特殊标记：`{0}` 用于 World Info，`{{scenario}}` 用于场景，`{{personality}}` 用于个性。

### 群聊 Nudge 模板
仅在群聊中使用，放在提示词末尾强制特定角色回复。留空禁用。

### 继续提示（Continue Nudge）
Continue 按钮按下时发给模型的指令。

### 替换空消息
文本框为空时发送此字段内容代替空白消息。

## "Prompts" 列表
> 💡 **肆说**：这里能看到发给AI的完整"配方"。拖拽可以调整顺序，关闭开关可以不让某些内容发送。调试AI回复时先来这看。

提示词管理器构成了发给 Chat Completion 模型的提示词的骨架。控制发送什么以及发送顺序。

- **固定提示词**：默认提示词不能从列表删除，但可以关闭
- **自定义提示词**：从下拉列表选择后插入，或用 "New prompt" 创建新的

## 编辑提示词

- **名称**：不发给模型，仅作参考
- **角色**：System、AI Assistant 或 User
- **触发器**：选择在哪些生成类型时发送（Normal/Continue/Impersonate/Swipe/Regenerate/Quiet）
- **位置**：Relative（按拖放顺序）或 In-Chat（在聊天历史内的特定深度）
- **深度**：In-Chat 模式下，定义在聊天历史中多深的位置发送。0=最后一条消息后，1=倒数第二条前...

---

📖 原文链接：[Prompt Manager](https://docs.sillytavern.app/usage/prompts/prompt-manager/)
