# 🦎 KoboldCpp
> 💡 **肆说**：跑本地模型最简单的方式之一，下载一个文件就能跑。免费！不用梯子！但需要有显卡。

KoboldCpp 是一个独立的 GGML 和 GGUF 模型 API。

用这个 [VRAM 计算器](https://huggingface.co/spaces/NyxKrage/LLM-Model-VRAM-Calculator) 查看你的模型需要多少 RAM/VRAM。

## NVIDIA GPU 快速开始

1. 下载最新版：[https://github.com/LostRuins/koboldcpp/releases](https://github.com/LostRuins/koboldcpp/releases)
2. 启动 KoboldCpp，可能有 Microsoft Defender 弹窗，点 "Run Anyway"
3. 在 Quick Launch 标签页选择模型和上下文大小
4. 选择 "Use CuBLAS"，确保 GPU ID 旁黄字匹配你的 GPU
5. 不要勾选 "Low VRAM"（即使你显存低）
6. 除非 NVIDIA 10 系列或更旧 GPU，取消勾选 "Use QuantMatMul (mmq)"
7. GPU Layers 已自动填充
8. 在 Hardware 标签页勾选 "High Priority"
9. 点击 Save 保存配置
10. 点击 Launch 等待模型加载

加载成功后会显示：
```
Load Model OK: True
Starting Kobold API on port 5001 at http://localhost:5001/api/
```

在 SillyTavern 中用 `http://localhost:5001` 作为 API URL 连接即可。

## GPU 层（GPU Layers）优化

看终端输出中 `CUDA0 buffer size` 来了解用了多少显存。算出剩余显存能多加载几层，然后重启 KoboldCpp 调整 GPU Layers 数值。

**计算方法：** 剩余显存 / 每层占用 = 可增加的层数

---

📖 原文链接：[KoboldCpp](https://docs.sillytavern.app/usage/api-connections/koboldcpp/)
