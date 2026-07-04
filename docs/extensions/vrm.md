# 🧍 VRM 3D 模型
> 💡 **肆说**：VRM模型支持——3D角色模型。设置复杂，有VRM模型的人再看。

使用 VRM 动画模型为角色添加动态交互元素。

## 前提条件
1. 最新版 SillyTavern
2. 安装 "VRM" 扩展
3. 模型文件(.vrm)放入 `/data/<user-handle>/assets/vrm/model`，动画文件放入 `/data/<user-handle>/assets/vrm/animation`（支持 .fbx 和 .bvh，兼容 Mixamo 动画）

## 全局设置
- **Enabled** - 启用
- **Look at camera** - 眼睛看向摄像头
- **Blink** - 随机眨眼
- **TTS Lip sync** - 嘴巴跟随 TTS 声音（仅 XTTS 非流式模式）
- **Auto-send Interaction** - 点击区域自动发送消息

### 性能设置
- **Body hitboxes** - 身体碰撞检测（头/胸/手/腿等）
- **Use model cache** - 切换模型时保留内存加速
- **Use animation cache** - 缓存播放过的动画

### 场景设置
- **Light Color** - 灯光颜色
- **Light intensity** - 灯光强度百分比

## 模型设置
- Scale / Center X/Y Offset / X/Y Rotation
- 可拖动/旋转/缩放模型（左键拖动、中键/Shift+左键旋转、滚轮缩放）

## 点击区域映射
为身体各部位分配动画/消息。

## 表情分类映射
需启用 classify 扩展，为每种情绪分配表情/动画/消息。

## 斜杠命令
- `/vrmlightcolor <颜色>` - 设置灯光颜色
- `/vrmlightintensity <百分比>` - 设置灯光强度
- `/vrmmodel <模型>` - 分配模型
- `/vrmexpression <表情>` - 切换表情
- `/vrmmotion <动画> [loop] [random]` - 切换动画

## 动画自动映射
如果动画文件按特定命名（如 neutral.bvh、anger_0.fbx），重置设置时会自动映射。

📖 原文链接：[VRM](https://docs.sillytavern.app/extensions/vrm/)
