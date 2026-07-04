# 🔊 文字转语音（TTS / Text-To-Speech）
> 💡 **肆说**：想让角色"说话"就看这里！配音功能，选对TTS服务体验提升巨大。

SillyTavern 有多种 TTS 选项，用于让语音为聊天内容配音。

## 配置 TTS

### TTS 服务商选择

| 服务商 | 说明 |
|--------|------|
| **AllTalk** | 免费，开源本地安装，支持多种 TTS 引擎。详见 [AllTalk 页](alltalk/) |
| **Azure TTS** | 同 Microsoft Edge 的声音，需 Azure 账号和付费订阅 |
> 💡 **肆说**：需要Azure账号+付费，国内可以直连但设置麻烦。不如直接用Edge TTS。
| **Coqui-TTS**（已弃用） | 免费，需 Extras API |
| **Edge** | 免费，通过 Azure 运行。选 "Plugin" 需安装[服务器插件](https://github.com/SillyTavern/SillyTavern-EdgeTTS-Plugin) |
> 💡 **肆说**：免费！不用梯子！微软Edge的声音，质量不错，强烈推荐新手先用这个。
| **Electron Hub** | 复用 [Electron Hub](https://electronhub.ai/) API 密钥访问云端语音 |
| **ElevenLabs** | 需付费订阅，[获取密钥](https://elevenlabs.io/) |
> 💡 **肆说**：国内需要梯子+海外支付，但效果是真的好，最自然的AI语音。
| **Google Translate** | 免费语音，每语言一个，质量参差 |
> 💡 **肆说**：免费！不用梯子！但每种语言就一个声音，质量一般。
| **Google Gemini TTS** | 需 Vertex AI 或 AI Studio 的 API 密钥 |
| **Kokoro** | 免费，用 [kokoro.js](https://www.npmjs.com/package/kokoro-js) 在浏览器本地运行，需 WebGPU |
> 💡 **肆说**：免费！不用梯子！浏览器本地跑，需要WebGPU支持，效果不错。
| **MiniMax** | 需 API 密钥，详见 [MiniMax TTS 页](minimaxtts/) |
| **Novel** | 需 NovelAI 付费订阅 |
> 💡 **肆说**：需海外付费，国内直连不行。
| **OpenAI** | 需付费 API 密钥 |
> 💡 **肆说**：国内需要梯子+海外支付。
| **Pollinations** | 免费使用 OpenAI TTS 模型，有速率限制 |
> 💡 **肆说**：免费！但需要梯子。有速率限制，偶尔会没声音。
| **Silero** | 免费，本地运行，需[专用 API 服务器](https://github.com/ouoertheo/silero-api-server) |
> 💡 **肆说**：免费！不用梯子！本地运行但需要额外装API服务器，有点折腾。
| **System** | 用操作系统 TTS 引擎，质量参差 |
| **XTTS** | 免费，需专用 API 服务器，详见 [XTTS 页](xtts/) |

### 复选框

- **Enabled** - 开启/关闭 TTS
- **Auto Generation** - 新消息到达时自动播放
- **Only narrate "quotes"** - 只播放引号内的文字
- **Ignore *text inside asterisks*** - 忽略星号内的文字（即使有引号）
- **Narrate only the translated text** - 只播放翻译后的文字
- **Apply regex** - 发送前用正则过滤文字

示例文字：`*Cohee approaches you with a faint "nya"* "Good evening, senpai", she says.`

| 忽略星号 | 只播引号 | 输出 |
|---------|---------|------|
| 关 | 关 | 全部文字 |
| 关 | 开 | "nya"... "Good evening, senpai" |
| 开 | 关 | "Good evening, senpai", she says. |
| 开 | 开 | "Good evening, senpai" |

### 按钮
- **Apply** - 设置 TTS API 或编辑语音映射后必须点击
- **Refresh** - 重新加载语音列表
- **Available voices** - 弹窗预览所有可用语音

## 使用 TTS

1. 勾选 "Enable"
2. 可选勾选 "Auto-generation" 自动播放
3. 可点消息右上角喇叭图标按需播放
4. 点右下角 "Stop" 按钮停止播放

### 语音映射（Voice Map）
必须设置语音映射，否则 TTS 不知道每个角色用什么声音。打开角色聊天，从下拉列表选择 TTS 服务商提供的语音。有些服务商需手动填写语音列表。

📖 原文链接：[TTS](https://docs.sillytavern.app/extensions/tts/)
