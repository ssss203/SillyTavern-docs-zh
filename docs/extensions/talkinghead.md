# 🗣️ TalkingHead（已弃用）
> 💡 **肆说**：让角色头像"说话"——嘴会跟着语音动。纯视觉增强功能。

> ⚠️ TALKINGHEAD 支持已在 SillyTavern 1.12.13 中移除。此页面仅作历史参考。

## 这是什么？

Talking Head Anime 3 Demo 的 AITuber 实现。功能包括：
- 从单张静态图片生成随机 Live2D 风格动作
- 与任何 TTS 输出同步对口型

## 硬件要求
- CPU 模式约 1 FPS
- GPU 模式（RTX3060）约 9-10 FPS
- ifacialmocap_puppeteer 需 iOS 11.0+ 且有 TrueDepth 前置摄像头的设备

## 输入图片要求
- 分辨率 512x512
- 必须有 alpha 通道（透明背景）
- 只含一个角色，直立正面
- 头部大致在顶部中间 128x128 区域
- 背景像素 alpha 须为 0

📖 原文链接：[talkinghead](https://docs.sillytavern.app/extensions/talkinghead/)
