# 🗣️ MiniMax TTS
> 💡 **肆说**：MiniMax的TTS服务，国内可用！需要API密钥。

## 前提条件
1. MiniMax 账号（需 API 访问权限）
2. 有效的 API Key 和 Group ID

## 获取 API 凭证

1. 访问 [MiniMax 官网（国际版）](https://www.minimax.io/) 注册
2. 在[控制台](https://www.minimax.io/platform/user-center/basic-information)找到 GroupId
3. 在 Settings > API Keys 创建 API Key

> 注意：中国版不支持语音克隆，且只支持 `api.minimax.chat` 主机。

## 在 SillyTavern 中配置

1. Extensions > TTS > 选 "MiniMax"
2. 填入 API Key、Group ID
3. API Host 选对应区域：
   - `api.minimax.io`（国际服务器）
   - `api.minimaxi.chat`（另一国际主机）
   - `api.minimax.chat`（中国大陆）

## 模型选择
- **Speech-02-HD**：高质量（推荐）
- **Speech-02-Turbo**：快速
- **Speech-01**：旧版

## 语音参数
- Speed：0.5-2.0 / Volume：0.1-2.0 / Pitch：0.5-2.0 / 格式：MP3/WAV/FLAC

## 自定义语音
从 [MiniMax TTS 页面](https://www.minimax.io/audio/text-to-speech) 获取 Voice ID，在设置中添加。

📖 原文链接：[MiniMax TTS](https://docs.sillytavern.app/extensions/minimaxtts/)
