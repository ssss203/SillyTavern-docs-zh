# 🔮 Google Gemini
> 💡 **肆说**：Google的AI模型，有免费额度！AI Studio方式最简单，国内需要梯子。

Gemini 是 Google 的多模态大语言模型（LLM），可通过 Google Vertex AI 和 Google AI Studio 访问。

## Google AI Studio
> 💡 **肆说**：最简单的方式，有免费额度，注册就能用。国内需要梯子。

最快最简单的方式，不需要 Google Cloud 项目。

### 步骤1：创建密钥
1. 去 [Google AI Studio](https://aistudio.google.com/apikey) 用 Google 账号登录
2. 点击 "Get API Key"，接受条款
3. 点击 "Create API Key" 生成密钥
4. 复制密钥

### 步骤2：填入 SillyTavern
1. API 连接页面选 Chat Completion
2. 选 Google AI Studio
3. 输入密钥，点击 Connect

## Google Vertex AI
> 💡 **肆说**：企业级服务，设置复杂，新手别碰。除非你需要GCP的特定功能。

Vertex AI 是 Google Cloud Platform (GCP) 提供的服务。

### 服务账号方式

**前置条件：** 需要 GCP 账号、项目、已启用账单。

1. 启用 Vertex AI API
2. 创建服务账号（IAM -> Service Accounts），赋予 Vertex AI User 角色
3. 生成 JSON 密钥文件（.json 会自动下载）
4. 在 SillyTavern 中选 Google Vertex AI，切换到 Service Account 认证
5. 把整个 JSON 文件内容粘贴到 "Service Account JSON Content" 文本框
6. 点击 "Validate JSON" 验证
7. 点击 Connect

### Express 模式

最快方式，用 API 密钥直接使用，无需服务账号。

1. 去 Vertex AI Studio，点击 "Try it free"
2. 接受条款
3. 创建 API Key
4. 在 SillyTavern 选 Google Vertex AI，切换到 Express Mode (API Key)
5. 粘贴密钥，点击 Connect

---

📖 原文链接：[Google Gemini](https://docs.sillytavern.app/usage/api-connections/google/)
