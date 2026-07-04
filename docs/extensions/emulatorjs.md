# 🎮 EmulatorJS 模拟器
> 💡 **肆说**：在SillyTavern里玩复古游戏，纯娱乐功能，跟AI聊天无关。

在 SillyTavern 聊天中直接玩复古主机游戏。

## 安装
- 前提：最新版 SillyTavern + ROM 文件
- 从扩展下载器安装，或用链接：`https://github.com/SillyTavern/SillyTavern-EmulatorJS`

## 使用
1. 打开 EmulatorJS 扩展菜单
2. 点击 "Add ROM file"（ROM 保存在浏览器存储中）
3. 输入名称和核心（如未自动检测），需要的话加 BIOS 文件
4. 点击 "Play" 启动

## 评论模式
利用多模态模型让 AI 角色看到你的游戏画面并提供评论。

### 要求
- 支持 [ImageCapture](https://developer.mozilla.org/en-US/docs/Web/API/ImageCapture) 的浏览器（Chrome 可用，Firefox 需开启配置，Safari 不行）
- 支持 multimodal 的 Chat Completion API

### 启用
1. 设置评论间隔（0=不评论）
2. 选角色聊天并启动游戏
3. AI 会定期根据截图写评论

### 为何没有评论？
评论在以下情况暂停：模拟器暂停、浏览器窗口失焦、输入框有内容、正在生成回复、TTS 正在播放。

📖 原文链接：[EmulatorJS](https://docs.sillytavern.app/extensions/emulatorjs/)
