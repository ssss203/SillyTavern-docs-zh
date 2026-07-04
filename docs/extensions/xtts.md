# 🗣️ XTTS 语音克隆
> 💡 **肆说**：本地语音克隆方案，免费不用梯子但需要安装专用API服务器。

XTTSv2 模型的 API 服务器，在本地运行语音克隆并连接到 SillyTavern 的 TTS 扩展。

## 前提条件
1. 最新版 SillyTavern
2. [Miniconda](https://docs.conda.io/projects/miniconda/en/latest/miniconda-install.html)
3.（Windows）[Visual C++ Build Tools](https://visualstudio.microsoft.com/visual-cpp-build-tools/)
4. WAV 语音片段文件（约10秒/文件），格式：PCM, Mono, 22050Hz, 16-bit
5. 创建含 speakers 和 output 子文件夹的目录

## 安装

1. 创建 conda 环境：`conda create -n xtts` > `conda activate xtts` > `conda install python=3.10`
2. 安装：`pip install xtts-api-server pydub`
3. 安装 PyTorch（GPU版）：`pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118`
4. 启动服务器：`python -m xtts_api_server`（默认 http://localhost:8020）
5. 首次启动下载模型（约2GB）

## 连接 SillyTavern
1. TTS 服务商选 "XTTSv2"
2. 选语言
3. 确认端点指向 http://localhost:8020
4. 设置角色语音映射

## 流式传输
更新 XTTS 服务器和 SillyTavern 到最新版，启用 "Streaming" 设置。⚠️ 与 RVC 不兼容。

## 音频卡顿？
增加 "chunk size" 设置。

📖 原文链接：[XTTS with voice cloning](https://docs.sillytavern.app/extensions/xtts/)
