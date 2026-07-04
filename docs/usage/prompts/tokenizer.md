# 🔢 分词器（Tokenizer）
> 💡 **肆说**：分词器就是"怎么数token"的工具。选"Best match"就行，ST会自动匹配最适合你API的分词器。

分词器（Tokenizer）是把文本拆分成更小单元（称为 token）的工具。一个 token 大约对应 3~4 个字符。

SillyTavern 提供"Best match"选项，根据 API 供应商自动匹配分词器。

## Text Completion API（可覆盖）

1. NovelAI Clio: NerdStash
2. NovelAI Kayra: NerdStash v2
3. Text Completion: API 分词器或 Llama 分词器
4. KoboldAI Classic / AI Horde: Llama 分词器
5. KoboldCpp: 模型 API 分词器

可设置的覆盖选项：None(每个token约3.3字符)、Llama、Llama 3、NerdStash、NerdStash v2、Mistral V1、Mistral Nemo、Yi、Gemma、DeepSeek、API 分词器。

## Chat Completion API（不可覆盖）

1. OpenAI: tiktoken
2. Claude: WebTokenizers
3. OpenRouter: 按模型选对应分词器
4. Google AI Studio: Gemma
5. 其他: 首次使用时需一次性下载

## Token 填充（Token Padding）
> 💡 **肆说**：因为不同分词器数出来的token数不一样，ST会预留一点"余量"防止超限。如果你发现AI总是截断回复，可以试试调大这个值。

由于分词可能不准确，SillyTavern 分配一部分上下文大小作为填充，避免添加超出模型容量的聊天条目。如果发现提示词被截断，调整填充值。

---

📖 原文链接：[Tokenizer](https://docs.sillytavern.app/usage/prompts/tokenizer/)
