# 😊 角色表情图（Expression Images / Sprites）
> 💡 **肆说**：给角色加上表情图，聊天时AI会根据情绪自动切换图片，氛围感拉满！就是找图/画图比较费劲。

## 这是什么？

表情图是 AI 角色的图片（也叫 sprites/精灵图），显示在聊天窗口旁边或后面，可根据 AI 回复情绪自动切换。

## 添加角色表情图

1. 打开扩展面板展开 "Character Expressions"，看到图片占位符网格
2. 点击每张左上角 "Upload image"，选择对应情绪的图片
3. 图片保存到 `/data/<user-handle>/characters/(角色名)/`

### 导入 ZIP
用 "Upload sprite pack (ZIP)" 按钮导入。ZIP 须扁平结构、文件名正确。

## 手动切换
点击表情图或用 `/expression-set (name)` 命令。

## 自动切换

### 分类模块（classify）
小型情绪解析模型检测 AI 输出情绪，返回最可能的一种，前端显示对应图片。

### 本地设置（Local）
1. 分类来源选 "Local"
2. 从 HuggingFace 下载模型（约100MB）
3. 默认28种标签，要改用6种模型在 `config.yaml` 改 `extensions.models.classification`

### LLM 设置
1. 连接 API → 导入表情图 → 分类来源选 "Main API"
2. 提示词策略：Limited Context（仅末条消息）或 Full Context（完整记录）

### WebLLM 设置
安装 [WebLLM 扩展](https://github.com/SillyTavern/Extension-WebLLM) → 分类来源选 "WebLLM"

### Extras 设置（已弃用）
`python server.py --enable-modules=classify` → 分类来源选 "Extras"

## 自定义表情
在扩展设置中创建，可起任意名。只有 LLM/WebLLM 分类来源会自动使用自定义表情。

## 图片格式
任何格式，最常用透明背景 PNG。

## 默认表情
- Choose a Fallback Expression：无图时显示备选
- [No Fallback]：不显示
- [Default emojis]：内置 emoji 风格图

## 每表情多图
勾选 "Allow multiple sprites per expression"，自动选中时随机选一张。命名如 `joy.png`、`joy-1.png`。

## 精灵图文件夹覆盖
同名角色共用表情图，要不同图片集用 Sprite Folder Override：输入文件夹名或 `/costume 文件夹名`。

📖 原文链接：[Character Expressions](https://docs.sillytavern.app/extensions/expression-images/)
