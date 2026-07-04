# ⚠️ Extras 安装（已停止维护）
> 💡 **肆说**：Extras已停止维护，不需要安装了。

Extras 项目已于 2024 年 4 月停止维护。大部分功能已在 SillyTavern 主程序中提供。

## 使用 Colab（推荐）
1. 打开[官方 Extras Colab](https://colab.research.google.com/github/SillyTavern/SillyTavern/blob/release/colab/GPU.ipynb)
2. 选择 Extra 选项，可选 `use_cpu`（不需要 GPU）
3. 推荐 `secure` 选项生成 API 密钥
4. 点击开始按钮，等待加载
5. 找到 `trycloudflare.com` 链接（不是 localhost 那个）
6. 在 ST 扩展面板粘贴 API URL 并连接

## 本地安装（MiniConda 推荐）
1. 安装 Miniconda 和 git
2. `conda create -n extras` > `conda activate extras` > `conda install python=3.11 git`
3. `git clone https://github.com/SillyTavern/SillyTavern-extras` > `cd SillyTavern-extras`
4. `pip install -r requirements.txt`（基本功能）/ `pip install -r requirements-rvc.txt`（语音克隆）
5. 启动：`python server.py --enable-modules=YOUR,MODULE,LIST`

### 模块列表
| 模块名 | 功能 |
|--------|------|
| `caption` | 图片描述 |
| `summarize` | 文本摘要 |
| `classify` | 情绪分类 |
| `sd` | Stable Diffusion |
| `silero-tts` | Silero TTS |
| `edge-tts` | Edge TTS |
| `chromadb` | 向量存储 |
| `coqui-tts` | Coqui TTS |
| `rvc` | 实时语音克隆 |

📖 原文链接：[Extras Installation](https://docs.sillytavern.app/extensions/extras/installation/)
