# 🗣️ AllTalk TTS V2
> 💡 **肆说**：本地TTS方案，免费不用梯子但需要折腾安装。支持多种TTS引擎。

AllTalk 是基于 Coqui XTTS、F5-TTS、VITS、Piper 等多种 TTS 模型引擎的语音克隆系统，可产生高质量语音（零样本语音克隆或内置语音）。

## 主要特性
- **多引擎支持**：轻松切换 Coqui XTTS、VITS、Piper、Parler、F5 和自定义引擎
- **语音转换（RVC）**：增强的检索式语音克隆
- **旁白功能**：分别为旁白和角色指定不同语音
- **DeepSpeed 和低显存模式**：资源有限环境下的性能优化

## 安装方式

- **独立安装**（推荐）：[独立安装指南](https://github.com/erew123/alltalk_tts/wiki/Install-%E2%80%90-Standalone-Installation)
- **自动安装**（Windows）：通过 SillyTavern-Launcher 的 Home > Toolbox > App Installer > Voice Generation > Install AllTalk V2
- **手动安装**：[手动安装指南](https://github.com/erew123/alltalk_tts/wiki/Install-%E2%80%90-Manual-Installation-Guide)
- **Google Colab**：[Colab 安装](https://github.com/erew123/alltalk_tts/wiki/Google-COLAB)

## 在 SillyTavern 中使用

1. 加载 AllTalk 后，在 TTS 页面选择 AllTalk
2. 确保选择正确的服务器版本
3. 如果 ST 先于 AllTalk 加载，重新加载 TTS 扩展页
4. 可选启用 DeepSpeed 和低显存模式

> TGWUI 用户需在 TGWUI 聊天界面禁用 "Enable TGWUI TTS"，否则会有重复语音。

## 故障排除
参考 [AllTalk Wiki](https://github.com/erew123/alltalk_tts/wiki/SillyTavern-Extension) 获取最新信息。

📖 原文链接：[AllTalk TTS V2](https://docs.sillytavern.app/extensions/alltalk/)
