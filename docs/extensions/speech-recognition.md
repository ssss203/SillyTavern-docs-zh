# 🎙️ 语音识别（Speech Recognition）
> 💡 **肆说**：可以暂时跳过，知道有就行。等你有需要再看。

将语音转录为文字。

## 前提条件
- 最新版 SillyTavern
- 安装 "Speech Recognition" 扩展

## 浏览器设置
1. Extensions > Speech Recognition > 选 "Browser"
2. 选择消息模式：
   - **Append**：追加到当前输入框
   - **Replace**：替换当前输入
   - **Auto send**：检测到语音结束后自动发送
3. 可选启用消息映射（语音快捷短语）
4. 选择语言
5. 点麦克风按钮开始/停止录音

## API 来源设置
支持 OpenAI、MistralAI、Groq、Chutes、Z.AI 等提供语音转文字 API 的服务商。
1. 在 Chat Completion API 设置中提供 API 密钥
2. 选对应 API 来源

## Extras 设置（已弃用）
需 ffmpeg。启用 whisper-stt 或 vosk-stt 模块：
```
python server.py --enable-modules=whisper-stt
python server.py --enable-modules=vosk-stt
```
Whisper 更准确。

## 流式设置（已弃用）
`python server.py --enable-modules=streaming-stt`
可选设置触发词防止随机噪声被转录。

📖 原文链接：[Speech Recognition](https://docs.sillytavern.app/extensions/speech-recognition/)
