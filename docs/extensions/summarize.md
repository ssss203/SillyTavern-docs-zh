# 📝 自动摘要（Summarize）
> 💡 **肆说**：聊天太长AI记不住？摘要功能会自动总结之前的对话，相当于"长期记忆"。但别完全信任，可能漏细节。

## 这是什么？

自动为聊天事件创建和使用摘要。可理解为长期记忆，但要持保留态度——可能丢失细节或产生幻觉，建议关注并手动修正。

## 通用配置

- **Current summary** - 显示/修改当前摘要，更新时嵌入聊天文件元数据
- **Restore Previous** - 回滚到上一版摘要
- **Pause** - 阻止自动更新
- **Popup window** - 分离为可移动面板
- **Injection Template** - 注入包装方式，用 `{{summary}}` 宏
- **Injection Position** - 注入位置，同作者备注选项

## 支持的摘要来源

### Main API
由当前 AI 后端提供，无需额外设置。

子模式：
1. **Raw, blocking** - 只用摘要提示词+聊天记录，提示词差异大
2. **Raw, non-blocking** - 同上但不阻塞聊天生成
3. **Classic, blocking** - 附加在常规提示词末尾，推荐用于 llama.cpp

#### 设置项
1. Summary Prompt - 提示词，可含 `{{words}}` 宏
2. Target summary length - `{{words}}` 的值
3. API response length - 覆盖响应长度
4. Max messages per request - 限制消息数（仅raw）
5. No WI/AN - 省略世界信息和作者备注
6. Update every X messages - 间隔消息数
7. Update every X words - 间隔单词数

### Extras API
辅助摘要模型（BART），上下文小（约1024 token），能力有限。

📖 原文链接：[Summarize](https://docs.sillytavern.app/extensions/summarize/)
