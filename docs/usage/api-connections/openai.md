# 💬 Chat Completions

## 各来源的具体说明

> 重要：大多数 API 平台只允许在创建时查看一次生成的 API 密钥。丢失了就得重新生成。请妥善保存！

### OpenAI
> 💡 **肆说**：国内需要梯子+海外支付方式。效果最好但价格也不低，GPT-4o是最强但最贵的。
使用 OpenAI 开发者平台访问各种 OpenAI 模型（gpt-4o、gpt-4.1、o3 等）。

**获取 API 密钥：**
1. 去 [OpenAI](https://platform.openai.com/) 登录
2. 用 "View API keys" 选项创建新密钥

### Claude（Anthropic）
> 💡 **肆说**：国内需要梯子+海外支付。Claude写创意文特别强，很多写卡人首选。
Claude 是 Anthropic 开发的 AI 模型家族。

**获取 API 密钥：**
1. 去 [Anthropic Console](https://console.anthropic.com/) 登录
2. 在 "Get API Key" 部分创建新密钥

### Mistral AI
> 💡 **肆说**：有免费额度，但国内需要梯子。
Mistral AI 开发开源和闭源模型。

**获取 API 密钥：**
1. 在 [La Plateforme](https://console.mistral.ai/) 创建账号
2. 选择 [计划](https://console.mistral.ai/billing/plans) 并设置支付
3. 创建 [API 密钥](https://console.mistral.ai/api-keys/)

### DeepSeek
> 💡 **肆说**：国内用户首选！国内直连，便宜好用，性价比最高。
提供 DeepSeek V3 和 DeepSeek R1 模型。

**获取 API 密钥：**
1. 在 [DeepSeek Platform](https://platform.deepseek.com/) 注册
2. 充值后在 "API keys" 部分创建密钥

### AI21
提供 Jamba 系列模型。

**获取 API 密钥：**
1. 去 [AI21 Studio](https://studio.ai21.com/) 登录
2. 在 "Settings => API Keys" 创建密钥

### Cohere
提供多种 AI 模型。

**获取 API 密钥：**
1. 去 [Cohere](https://cohere.com/) 登录
2. 在 [API Keys](https://dashboard.cohere.com/api-keys) 创建密钥

### Perplexity
> 💡 **肆说**：国内需要梯子。它的强项是联网搜索，纯聊天不是最佳选择。
提供在线功能的 Sonar 模型。

**获取 API 密钥：**
1. 去 [Perplexity](https://perplexity.ai/) 登录
2. 在 API billing 购买额度
3. 在 API keys 创建密钥

### Fireworks AI
高性能平台，支持256K上下文窗口。

**获取 API 密钥：**
1. 去 [Fireworks AI](https://fireworks.ai/) 创建账号
2. 在 [API Keys 页](https://app.fireworks.ai/settings/users/api-keys) 创建密钥

### Electron Hub
统一 OpenAI 兼容平台，一个密钥访问多个厂商模型。

**获取 API 密钥：**
1. 在 [Electron Hub](https://playground.electronhub.ai/console) 创建账号
2. 从 Console -> API Keys 生成密钥

## 自定义 OpenAI 兼容端点
> 💡 **肆说**：这个很重要！跑本地模型（LM Studio、Ollama等）就是走这个。免费+不用梯子，本地模型用户必看。

用于连接支持通用 OpenAI API 架构的任何服务器。兼容后端包括 LM Studio、LiteLLM、LocalAI 等。

**连接方法：**
1. 切换到 Chat Completion API
2. 选 Custom (OpenAI-compatible)
3. 输入端点 URL 和 API 密钥

**提示：** 如遇连接问题，试试在 URL 末尾加 `/v1`。不要加 `/chat/completions` 后缀。

## 提示词后处理（Prompt Post-Processing）

有些端点对提示词格式有特定限制。SillyTavern 提供内置转换器：
1. None - 不处理
2. 合并同角色连续消息
3. Semi-strict - 合并角色，只允许一条可选系统消息
4. Strict - 合并角色，一条可选系统消息，用户消息必须在前
5. 单用户消息 - 合并所有消息为一条

---

📖 原文链接：[Chat Completions](https://docs.sillytavern.app/usage/api-connections/openai/)
