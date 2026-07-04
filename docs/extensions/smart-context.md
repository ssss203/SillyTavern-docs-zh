# 🧠 智能上下文 Smart Context（已弃用）
> 💡 **肆说**：已弃用！别用了！需要类似功能去看聊天向量化或数据银行。

> ⚠️ 此扩展已不再维护，不建议使用。建议考虑[聊天向量化](chat-vectorization/)作为替代。

## 这是什么？

Smart Context 使用 [ChromaDB](https://www.trychroma.com/) 让 AI 角色获取正常上下文窗口外的信息。将整个聊天记录放入向量数据库，每次输入新消息时搜索匹配关键词的消息放入上下文。

## 设置
1. 更新 SillyTavern 至 1.10.6+
2. 安装 "Smart Context" 扩展
3. 安装/更新 Extras
4. 运行 Extras：`python server.py --enable-modules=chromadb`

## 配置概念
- **Chat History Preservation** - 保留最近N条自然聊天
- **Memory Injection Amount** - 最多插入N条记忆
- **Individual Memory Length** - 每条记忆最大字符数

## 注入策略
- **Replace oldest history** - 替换最老消息，不易溢出上下文
- **Add to Bottom** - 在聊天记录后添加，影响更大但易溢出
- **Custom Depth** - 自定义深度和模板

📖 原文链接：[Smart Context](https://docs.sillytavern.app/extensions/smart-context/)
