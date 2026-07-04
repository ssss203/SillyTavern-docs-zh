# ✍️ NovelAI
> 💡 **肆说**：需海外付费，国内直连不行。NovelAI的特色是没内容审查+擅长写小说，但贵且上下文窗口小。

NovelAI 是付费订阅服务，提供无限月访问其高质量文本生成、图像生成和语音合成模型。注册：[https://novelai.net/](https://novelai.net/)

免费试用只有 50 次生成。出现 "Not eligible for this model" 错误表示试用已用完。
> 💡 **肆说**：50次连试手感都不够，想认真用得付费。

## 获取 API 密钥

1. 点击左侧栏顶部齿轮图标
2. 选 User Settings 下的 Account
3. 选 Get Persistent API Token
4. 点击复制图标

## 模型

有 Opus 订阅用 Erato，否则用 Kayra。

## 设置

- **回复长度**：每条消息最大 150 token（NovelAI 限制）
> 💡 **肆说**：150 token超短的！大概就两三句话，写长篇基本要一直按继续。
- **上下文长度**：取决于模型和订阅等级（3072-8192 token）
- **前言（Preamble）**：插入聊天上方修改写作风格。推荐格式：`[ Style: chat, detailed, sensory ]`

## NovelAI 使用技巧

- 在高级格式化中设 Context Template 为 NovelAI、Tokenizer 为 Best match
- 取消勾选 Instruct Mode
- 角色描述可用散文体或属性列表格式
- 避免使用 W++ 格式（浪费 token）
> 💡 **肆说**：W++格式早就过时了，用自然语言写角色描述效果更好更省token。
- 不要长期使用 Instruct 模块，只在需要时用花括号 `{}` 调用
- 回复被截断时用 Continue 功能或开启 Auto-continue

---

📖 原文链接：[NovelAI](https://docs.sillytavern.app/usage/api-connections/novelai/)
