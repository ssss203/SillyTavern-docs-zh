# 作者备注（Author's Note）
> 💡 **肆说**：作者备注是写卡的核心工具之一，可以在聊天的特定位置插入"临时指令"，影响AI的回复方向。

## 这是什么？

作者备注是一个强大的自定义AI回复工具，它可以在提示词中的任何位置和任何频率插入一段文本。

## 使用方法

作者备注可以在聊天输入栏左侧的选项菜单中找到。

## 配置作者备注

### 聊天专属作者备注

面板顶部的输入框包含当前聊天的作者备注。**此内容不会自动转移到新聊天。**

### 放置选项

#### 场景之后

将作者备注放在上下文中角色定义的"场景"部分之后。

#### 聊天内

将作者备注放入聊天历史的指定深度。深度0 = 最末尾。深度4 = 最近3条消息之前。

*作者备注越靠近提示词底部，对下一次AI回复的影响越大。*
> 💡 **肆说**：所以深度0（最底部）效果最强，但太强了AI可能只听备注不听角色设定了。推荐深度3-5。

### 插入频率

频率0 = 永远不插入。频率1 = 每次都插入。频率4 = 每4次插入一次。

### 默认作者备注

面板底部的输入框包含默认作者备注，将应用于每个新聊天。

## 常见用例
> 💡 **肆说**：作者备注最常用的功能就是控制AI回复长度、风格和提醒AI遵守规则。上面这些例子直接抄去用就行。

### 提醒AI回复格式

- [Your next response must be 300 tokens in length.]
- [Write your next reply in the style of Edgar Allan Poe]

### 强化指令

- [Remember the instructions you were given at the beginning of this chat.]

### 作为临时世界信息、角色偏置或非指令模型的指令

- [{{char}} is in the library]
- [{{user}} has a fresh wound to his leg, so won't be able to run away.]

📖 原文链接：[Author's Note](https://docs.sillytavern.app/usage/core-concepts/authors-note/)
