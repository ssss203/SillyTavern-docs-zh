# 🎨 图片生成（Image Generation / Stable Diffusion）
> 💡 **肆说**：想给聊天配图就看这个！内置功能不用额外装。

使用本地或云端的 Stable Diffusion、FLUX 或 DALL-E API 在聊天中生成图片。内置扩展，无需额外安装。

## 快速开始
1. 打开扩展面板 > Image Generation > 选择来源
2. 配置 API 连接
3. 在聊天中输入描述，通过魔杖菜单或 `/imagine` 命令生成图片

## 支持的来源
> 💡 **肆说**：Pollinations 免费！不用梯子！适合先试试效果。想要高质量图就上本地SD或DALL-E。

| 来源 | 说明 |
|------|------|
| **Stable Diffusion Web UI (AUTOMATIC1111)** | 本地，需 SD Web UI 运行且开启 `--api` |
| **Stable Diffusion WebUI Forge** | 本地，AUTOMATIC1111 的优化分支 |
| **ComfyUI** | 本地，基于节点的工作流，灵活度最高 |
| **DALL-E** | 云端，OpenAI API，付费 |
| **Pollinations** | 云端，免费 |
> 💡 **肆说**：免费！不用梯子！质量还行，先拿这个入门。
| **Stability AI** | 云端，付费 API |
| **Together AI** | 云端，付费 |
| **Draw Things** | 本地 macOS/iOS 应用 |
| **Forge Classic (Horde)** | AI Horde 众包网络，免费 |

## 基本设置

### 模型选择
从下拉列表选择检查点模型。点刷新按钮更新列表。

### 提示词
- **Prompt** - 正向提示词
- **Negative Prompt** - 反向提示词
- 可使用宏如 `{{char}}`、`{{user}}` 等

### 生成参数
- **Steps** - 采样步数
> 💡 **肆说**：步数越高图越细但越慢，一般20-30够用，超50基本没区别了。
- **Sampler** - 采样器
- **CFG Scale** - 提示词相关性
> 💡 **肆说**：就是"听不听你话"的旋钮，7-12是安全区。太高(>20)图会崩，太低(<5)AI就放飞自我了。
- **Width / Height** - 图片尺寸
- **Seed** - 随机种子（-1为随机）

### 图片风格（Styles）
可在提示词前后添加预设文本。创建多个风格快速切换。

## ComfyUI 工作流
ComfyUI 支持自定义 JSON 工作流。可在工作流中使用占位符（如 `%prompt%`、`%negative_prompt%`、`%seed%` 等），SillyTavern 会自动替换。还支持自定义占位符和宏。

## 斜杠命令
- `/imagine [提示词]` - 生成图片
- `/imagine-style [风格名]` - 切换图片风格

📖 原文链接：[Image Generation](https://docs.sillytavern.app/extensions/stable-diffusion/)
