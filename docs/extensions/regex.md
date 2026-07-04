# 🔤 正则表达式（Regex）
> 💡 **肆说**：写卡前期不用管，等你有"自动替换文字"的需求再看。比如自动去掉AI回复里的某些格式标签。

## 这是什么？

Regex 扩展让你自动检测文本中的特定模式（称为"序列"）并应用替换操作。与 Quick Replies/STscript 配合使用非常强大，也可简单用于从聊天中移除某些词。

## 前提条件
Regex 是内置扩展，无需额外安装。设置在 **Extensions** 面板中。

## 常见用途
查找替换特定词、为词添加 markdown 样式、向 STscript 返回布尔值。

## 脚本列表
- 顶部按钮创建新脚本：**Global**（全局，所有角色适用）或 **Scoped**（仅当前角色）
- **Import** 导入其他实例导出的脚本
- 拖拽排序、开关切换、编辑、移动到 scoped/global、导出、删除

## 编辑器
- **Test Mode** - 打开对比视图，实时调试
- **Name** - 脚本名称，也是斜杠命令/STscript 的目标名
- **Find Regex** - 正则表达式，可用 SillyTavern 宏
- **Replace With** - 替换内容。`{{match}}` 插入完整匹配，`$1`/`$2` 等插入捕获组
- **Trim Out** - 匹配后先删除的文本
- **Affects** - 选择影响范围：User Input / AI Response / Slash Commands / World Info / Reasoning
- **Run on Edit** - 编辑消息后也运行

### 深度设置
Min/Max Depth 控制影响聊天历史中的哪些消息（0=最后一条）。

### 标志（Flags）
`/pattern/flags` 格式。常用：`i`(不区分大小写)、`g`(全局匹配)、`s`(单行)、`m`(多行)、`u`(unicode)

### 临时性（Ephemerality）
默认直接修改聊天 JSONL 文件（不可逆）。勾选后可限制为只改显示或只改提示词。

📖 原文链接：[Regex](https://docs.sillytavern.app/extensions/regex/)
