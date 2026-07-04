# 🔍 聊天向量化（Chat Vectorization）
> 💡 **肆说**：高级功能！让AI从超长聊天记录里自动找回相关内容，适合聊了几千条消息的老玩家。新手先跳过。

> 免责声明：不保证更好体验或记忆改善，需理解向量数据库含义后使用。

在聊天记录中搜索与最近消息相关的消息，临时调整到开头或末尾。这是一种 RAG（检索增强生成）：
- **Retrieval**：用最近消息检索相关过去消息
- **Augmented**：插入过去消息增强上下文
- **Generation**：指示模型使用过去消息

### 术语
- **向量**：一组数字，表示文字特征
- **向量化**：计算文字的向量
- **向量搜索**：比较向量找相关结果

## 设置
⚠️ 与提示词缓存不兼容，必须二选一。

启用：Extensions > Vector Storage > Enabled for chat messages

## 准备消息
每条消息计算向量存储。大消息分块（默认400字符）。

控制：Vectorize All / View Stats / Purge Vectors

## 查找相关消息
- 最近2条→查询向量（可改 Query messages）
- 相关性≥25%（可改 Score threshold）
- 调整最相关3条（可改 Insert#）
- 最近5条不调整（可改 Retain#）

## 调整位置
主提示词后（默认）/ 前 / 聊天末尾@Depth 2

## 向量摘要（实验性）
⚠️ 不是聊天摘要！向量化前先提取要点让搜索更精准。

📖 原文链接：[Chat Vectorization](https://docs.sillytavern.app/extensions/chat-vectorization/)
