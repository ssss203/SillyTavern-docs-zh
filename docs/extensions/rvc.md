# 🎤 语音克隆（RVC / Retrieval-based Voice Conversion）
> 💡 **肆说**：AI语音克隆——用少量音频就能模仿任何人的声音。做角色配音很酷但设置复杂。

RVC 是一种将一段音频的语音特征转移到另一段音频的技术。你看过那些"总统玩X"视频吗？就是用 RVC 做的。用 RVC 扩展，你的角色可以用任何声音说话。

RVC 不是 TTS：它更像语音转语音。RVC 等待 TTS 生成音频后，进行第二遍处理将 TTS 音频转换为克隆语音。

## 前提条件
- 安装 ffmpeg 并加入 PATH
- TTS 必须已启用且正常工作
- 安装 "RVC" 扩展
- 在 Extensions > RVC 中启用

## rvc-python 设置（推荐）

1. 按 [rvc-python 安装指南](https://github.com/daswer123/rvc-python?tab=readme-ov-file#installation) 安装（推荐 CUDA 版）
2. 创建 `rvc_models` 目录，每个模型一个子文件夹（含 .pth 和可选 .index）
3. 启动 API：`python -m rvc_python api -p 5050 -l -md models_path`
4. 在 RVC 设置中填入 API URL（默认 http://localhost:5050）
5. 设置语音映射

## Extras 设置（已弃用）

1. 将 .pth 和 .index 放入 `\SillyTavern-extras\data\models\rvc\模型名\`
2. `pip install -r requirements-rvc.txt`
3. 启动：`python server.py --enable-modules=rvc,edge-tts`（可选加 `--cuda`）
4. 设置语音映射，选择 rmvpe 提取方法

### 表情联动语音
为每种分类表情准备单独的 .pth 和 .index 文件，启用 classify 模块：
`python server.py --enable-modules=rvc,classify`

📖 原文链接：[RVC](https://docs.sillytavern.app/extensions/rvc/)
