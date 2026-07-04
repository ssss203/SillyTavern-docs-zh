# 🎯 CFG（无分类器引导，Classifier-Free Guidance）
> 💡 **肆说**：CFG是高级功能，可以控制"AI多听你的话"。新手先跳过，等你有经验了再回来玩。

## 这是什么？

CFG 是一种让提示词的某些部分变得更突出或更不突出的方法。

### 支持的后端 API
Oobabooga textgen WebUI、NovelAI 和 TabbyAPI。

> 警告：CFG 因为要处理多条提示词，会增加显存使用！如果显存不够，考虑减小上下文大小或关闭 CFG。
> 💡 **肆说**：显存不够的别开，本地跑模型容易爆显存。

## 配置

四个下拉菜单：
- **Chat CFG** - 仅限当前聊天的 CFG 比例和提示词
- **Character CFG** - 限定到指定角色
- **Global CFG** - 全局覆盖
- **CFG 高级设置** - 组合以上三个的提示词并设置插入深度

> 指引比例（Guidance Scale）设为1时 CFG 关闭。

## 概念

### 这不是 Stable Diffusion 的 CFG 吗？
LLM 的 CFG 工作方式不同，基于"提示词混合"原理。CFG 公式取正面和负面提示词，混合它们之间的差异，然后生成回复。

### 我需要 CFG 提示词吗？
不需要！只要把指引比例调到1以上就会有效果。

### 什么算好的 CFG 提示词？
比如角色"John"应该一直开心但有时会悲伤。负面提示词设 `[John's feelings: sad, depressed]`，正面提示词设 `[John's feelings: happy, joyful]`。

### 指引比例
- 1 = 关闭
- >1 = 正常效果
- <1 = 反转效果（负面提示词变主要）

建议从1.5开始，根据输出上下调整。

---

📖 原文链接：[CFG](https://docs.sillytavern.app/usage/prompts/cfg/)
