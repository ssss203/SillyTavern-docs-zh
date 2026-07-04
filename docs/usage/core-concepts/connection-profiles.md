# 连接配置（Connection Profiles）
> 💡 **肆说**：如果你只用一个API，这个可以跳过。如果你经常切换不同模型/API，保存配置能省很多事。

保存连接配置以快速切换不同的API、模型和格式化模板。当你使用多个API连接或需要在不同配置之间切换时很有用。

## 访问连接配置

从SillyTavern 1.12.6起默认启用为内置扩展，在API连接菜单中找到。

## 保存的内容

### 通用

- API类型、模型和服务器URL | 密钥 | 设置预设 | 以此开始回复 | 自定义停止字符串 | 推理格式化

### 文本补全API

- 系统提示词及其状态 | 指令模式状态和模板 | 上下文模板 | 分词器

### 聊天补全API

- 提示词后处理 | 代理预设

## 管理连接配置

- 保存：设置所需设置 → 点击"创建" → 提供唯一名称
- 查看详情：点击"信息"按钮
- 恢复：点击"重新加载"按钮
- 删除：点击"删除"按钮（不可逆）

## 斜杠命令

1. `/profile [name]` - 切换到配置或获取当前配置名
2. `/profile-create [name]` - 保存当前设置为新配置
3. `/profile-list` - 返回可用配置名数组
4. `/profile-get [name]` - 获取配置详情
5. `/profile-update` - 用当前设置更新选定配置

📖 原文链接：[Connection Profiles](https://docs.sillytavern.app/usage/core-concepts/connection-profiles/)
