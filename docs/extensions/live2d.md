# 🎭 Live2D
> 💡 **肆说**：Live2D支持——就是让角色动起来那种。设置复杂，有Live2D模型的人再看。

使用 Live2D 动画模型为角色添加动态交互元素。

## 前提条件
1. 最新版 SillyTavern
2. 安装 "Live2D" 扩展
3. 将模型文件夹放入 `/data/<user-handle>/assets/live2d`（`***.model.json` 须在模型文件夹根目录）
   - 也可放入角色专属文件夹如 `/data/<user-handle>/characters/Shizuku/live2d/`

## 扩展设置

### 全局设置
- **Enabled** - 启用/禁用（禁用后用普通 sprites）
- **Follow Cursor** - 模型跟随光标
- **Auto-send Interaction** - 点击映射区域自动发送交互消息

### 调试设置
- **Reset Model Before Animation** - 每次动画前重载模型
- **Show Model Frames** - 显示模型框架和点击区域

### 模型选择
从列表选择模型分配给角色，设置按角色和模型保存。

### 模型设置
- Model Scale - 模型大小
- Center X/Y Offset - 水平/垂直偏移
- 可拖动模型，设置自动保存

### 模型说话
- 选择嘴巴Y轴参数ID
- 调整嘴巴动画速度和每字符时间

### 模型动画
- **Starter animation** - 开始聊天时播放
- **Default animation** - 角色发消息时播放

### 点击区域映射
为模型各区域分配动画/消息。

### 表情分类映射
需启用 classify 扩展，为每种检测到的情绪分配表情/动画。

📖 原文链接：[Live2D](https://docs.sillytavern.app/extensions/live2d/)
