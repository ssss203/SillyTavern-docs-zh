# 数据银行 / RAG（Data Bank）
> 💡 **肆说**：数据银行是"给AI塞参考资料"的高级功能，适合想让AI参考大量外部文本（小说、维基等）的场景。新手可以先跳过，等有需求再看。

检索增强生成（Retrieval-Augmented Generation，简称 RAG）是一种为大语言模型（LLM）提供外部知识源的技术。它通过访问模型训练数据之外的信息来帮助提高 AI 回答的准确性。

SillyTavern 提供了一套工具，用于从多种来源构建多功能知识库（Knowledge Base），以及在 LLM 提示词中使用收集到的数据。

## 访问数据银行

内置的聊天附件扩展（Chat Attachments，在 1.12.0 及更高版本的发布中默认包含）在"魔法棒"菜单中添加了一个新选项 — 数据银行（Data Bank）。这是你在 SillyTavern 中管理 RAG 可用文档的中心。

## 关于文档

数据银行存储文件附件，也称为文档（Documents）。文档分为三种可用范围：

1. 全局附件 — 在每个聊天中可用，无论是单人还是群组。
2. 角色附件 — 仅对当前选择的角色可用，包括在群组中回复时。*附件保存在本地，不会随角色卡导出！*
3. 聊天附件 — 仅在当前打开的聊天中可用。聊天中的每个角色都可以从中获取信息。

##### 注意

虽然不属于数据银行的正式部分，你甚至可以将文件附加到单个消息上。使用"魔法棒"菜单中的"附加文件"选项，或消息操作行中的回形针图标。

什么可以成为文档？几乎任何可以用纯文本形式表示的东西！

示例包括但不限于：

- 本地文件（书籍、科学论文等）
- 网页（维基百科、文章、新闻）
- 视频转录文本

各种扩展和插件也可以提供收集和处理数据的新方式，下面会详细介绍。

## 数据源

要向任何范围添加文档，点击"添加"并选择一个可用的来源。

### 记事本

从头创建文本文件，或编辑现有附件。

### 文件

从电脑硬盘上传文件。SillyTavern 为常用文件格式提供内置转换器：

- PDF（仅文本）
- HTML
- Markdown
- ePUB
- TXT

你还可以附加任何非标准扩展名的文本文件，如 JSON、YAML、源代码等。如果所选文件类型没有已知的转换方式，且文件无法作为纯文本文档解析，文件上传将被拒绝，即不允许原始二进制文件。

##### 注意

导入 Microsoft Office（DOCX、PPTX、XLSX）和 LibreOffice 文档（ODT、ODP、ODS）需要安装并加载[服务器插件](https://github.com/SillyTavern/SillyTavern-Office-Parser)。请参阅插件的 README 页面获取安装说明。

### 网页

通过 URL 抓取网页文本。HTML 文档随后通过 [Readability](https://github.com/mozilla/readability) 库处理，仅提取可用文本。

某些网页服务器可能会拒绝抓取请求、受 Cloudflare 保护或严重依赖 JavaScript 运行。如果你在某个特定网站上遇到问题，请通过浏览器手动下载页面并使用文件上传器附加。

### YouTube

通过 ID 或 URL 下载 YouTube 视频的转录文本，可以是上传者创建的也可以是 Google 自动生成的。某些视频可能禁用了转录文本，年龄限制视频的解析也不可用，因为需要登录。

脚本以视频的默认语言加载。可选地，你可以指定两个字母的语言代码来尝试获取特定语言的转录文本。此功能并非总是可用，可能会失败，请谨慎使用。

### 网页搜索

##### 注意

此来源需要安装并正确配置[网页搜索](https://docs.sillytavern.app/extensions/websearch/)扩展。详见链接页面了解更多详情。

执行网页搜索并从搜索结果页面下载文本。这类似于网页来源但是全自动的。选择的搜索引擎将继承自扩展设置，请提前设置好。

开始时，指定搜索查询、要访问的最大链接数和输出类型：一个合并文件（按扩展规则格式化）或每个页面的单独文件。你也可以选择保存页面片段。

### Fandom

##### 注意

此来源需要安装并加载[服务器插件](https://github.com/SillyTavern/SillyTavern-Fandom-Scraper)。请参阅插件的 README 页面获取安装说明。

通过 ID 或 URL 从 [Fandom](https://www.fandom.com/) 维基抓取文章。由于某些维基非常大，使用过滤正则表达式限制范围可能很有用，它将针对文章标题进行测试。如果未提供过滤器，则所有页面都将被导出。你可以将它们保存为每页单独的文件，或合并为单个文档。

### Bronie 解析器扩展（第三方）

##### 注意

此来源来自第三方，与 SillyTavern 团队**无关**。此来源需要你安装 Bronya Rand 的 [Bronie 解析器扩展](https://github.com/Bronya-Rand/Bronie-Parser-Extension)以及需要解析器工作的服务器插件。

Bronya Rand 的 Bronie 解析器扩展允许使用第三方抓取器，例如将 miHoYo/HoYoverse 的 [HoYoLab](https://wiki.hoyolab.com/) 抓取到 SillyTavern 中，类似于其他数据源。

目前，Bronya Rand 的 Bronie 解析器扩展支持以下内容：

- miHoYo/HoYoverse 的 HoYoLab（用于原神/崩坏：星穹铁道）通过 [HoYoWiki-Scraper-TS](https://github.com/Bronya-Rand/HoYoWiki-Scraper-TS)

开始时，按照其[安装指南](https://github.com/Bronya-Rand/Bronie-Parser-Extension?tab=readme-ov-file#installation)安装 Bronya Rand 的 Bronie 解析器扩展，并将支持的服务器插件安装到 SillyTavern 中。重启 SillyTavern，进入*数据银行*菜单。点击 `+ 添加`，你应该会看到最近安装的抓取器已添加到可用的来源列表中。

## 向量存储（Vector Storage）
> 💡 **肆说**：向量存储就是"智能搜索"——AI不读整篇文档，而是根据当前聊天内容自动找最相关的段落塞进上下文，省token。

所以，你已经建立了一个关于特定主题的全面信息库。接下来呢？

要使用文档进行 RAG，你需要使用兼容的扩展将相关数据插入到 LLM 提示词中。

向量存储（Vector Storage），与 SillyTavern 捆绑提供，是此类扩展的参考实现。它使用嵌入（Embeddings，也叫向量）来搜索与正在进行的聊天相关的文档。

##### 有趣的事实

1. 嵌入是由专业语言模型产生的数字数组，抽象地表示一段文本。更相似的文本在其各自向量之间的距离更短。

2. 向量存储扩展使用 [Vectra](https://github.com/Stevenic/vectra) 库来跟踪文件嵌入。它们以 JSON 文件存储在用户数据目录的 `/vectors` 文件夹中。每个文档在内部由其自己的索引/集合文件表示。

由于向量功能默认禁用，你需要打开扩展面板（顶部栏的"堆叠方块"图标），然后导航到"向量存储"部分，在"文件向量化设置"下勾选"为文件启用"复选框。

向量存储本身不产生任何向量，你需要使用兼容的嵌入提供者（Embedding Provider）。

## 向量提供者

##### 警告

嵌入只有在使用生成它们的相同模型检索时才可用。更改嵌入模型或来源时，需要重新计算向量。

### 本地来源
> 💡 **肆说**：本地来源免费！不用梯子！推荐用本地（Transformers）或Ollama，零成本。

这些来源免费且无限制，使用你的 CPU/GPU 计算嵌入。

1. 本地（Transformers）— 在 Node 服务器上运行。SillyTavern 将自动从 HuggingFace 下载兼容的 ONNX 格式模型。默认模型：[jina-embeddings-v2-base-en](https://huggingface.co/Cohee/jina-embeddings-v2-base-en)。

2. WebLLM — 需要安装扩展和支持 [WebGPU](https://caniuse.com/webgpu) 的浏览器。直接在浏览器中运行，可以使用硬件加速。自动从 HuggingFace 下载支持的模型。从此处安装扩展：[https://github.com/SillyTavern/Extension-WebLLM](https://github.com/SillyTavern/Extension-WebLLM)。

3. Ollama — 从 [https://ollama.com/](https://ollama.com/) 获取。在 API 连接菜单中设置 API URL（在文本补全下，默认：`http://localhost:11434`）。必须先下载兼容模型，然后在扩展设置中设置其名称。示例模型：[mxbai-embed-large](https://ollama.com/library/mxbai-embed-large)。可选地，勾选将模型保留在内存中的选项。

4. llama.cpp 服务器 — 从 [ggerganov/llama.cpp](https://github.com/ggerganov/llama.cpp) 获取，使用 `--embedding` 标志运行服务器可执行文件。从 HuggingFace 加载兼容的 GGUF 嵌入模型，例如 [nomic-ai/nomic-embed-text-v1.5-GGUF](https://huggingface.co/nomic-ai/nomic-embed-text-v1.5-GGUF)。

5. vLLM — 从 [vllm-project/vllm](https://github.com/vllm-project/vllm) 获取。先在 API 连接菜单中设置 API URL 和 API 密钥。

6. Extras（已弃用）— 在 [Extras API](https://github.com/SillyTavern/SillyTavern-extras) 下使用 SentenceTransformers 加载器运行。默认模型：[all-mpnet-base-v2](https://huggingface.co/sentence-transformers/all-mpnet-base-v2)。此来源不再维护，最终将在未来被移除。

### API 来源
> 💡 **肆说**：API来源大多需要梯子和付费，不过嵌入计算很便宜，几分钱的事。最省事的是OpenAI。

所有这些来源都需要各自服务的 API 密钥，通常有使用费用，但一般来说计算嵌入相当便宜。

1. OpenAI
2. Cohere
3. Google AI Studio
4. Google Vertex AI
5. TogetherAI
6. MistralAI
7. NomicAI
8. OpenRouter
9. Electron Hub
10. Chutes
11. NanoGPT
12. SiliconFlow
13. Cloudflare Workers AI

## 向量化设置

选择嵌入提供者后，别忘了配置其他定义文档处理和检索规则的设置。

##### 注意

分割、向量化和从附件中检索信息需要一些时间。虽然文件的初始摄取可能需要一段时间，但 RAG 搜索查询通常足够快，不会产生明显的延迟。

### 消息附件

这些设置控制直接附加到消息上的文件。

适用以下规则：

1. 只有适合 LLM 上下文窗口的消息才能检索其附件。
2. 当向量存储扩展禁用时，文件附件及其附带的消息会完整插入到提示词中。
3. 当文件向量化启用时，文件将被分割成块，只插入最相关的片段，节省上下文空间并帮助模型保持专注。

- 大小阈值（KB）— 设置分块拆分阈值。只有大于指定大小的文件才会被分割。
- 块大小（字符）— 设置单个块的目标大小（以文本字符计，不是模型令牌！）。
- 块重叠（%）— 设置块大小中相邻块之间共享的百分比。这允许块之间更平滑的过渡，但也可能引入一些冗余。
- 检索块数 — 设置要检索的最相关文件块的最大数量。它们将按原始顺序插入。

### 数据银行文件

这些设置控制数据银行文档的处理方式。

适用以下规则：

1. 当文件向量化禁用时，不使用数据银行。
2. 否则，当前范围内的所有可用文档（见上文）都会被考虑用于查询。只检索所有文件中最相关的块。同一文件的多个块按原始顺序插入。
3. 插入的块将在适应聊天消息之前保留上下文的一部分。

- 大小阈值（KB）— 设置分块拆分阈值。
- 块大小（字符）— 设置单个块的目标大小。
- 块重叠（%）— 设置相邻块之间共享的百分比。
- 检索块数 — 设置要检索的文件块的最大数量。此配额在所有文件之间共享。
- 注入模板 — 定义检索到的信息如何插入到提示词中。你可以使用特殊的 `{{text}}` 宏来指定检索文本的位置，以及任何其他宏。
- 注入位置 — 设置提示词注入的位置。与作者备注和世界信息的规则相同。

### 共享设置

- 查询消息 — 用于查询文档块的最新聊天消息数量。
- 分数阈值 — 调整以允许根据相关性分数裁剪块的检索（0 = 完全不匹配，1 = 完美匹配）。较高的值允许更准确的检索并防止完全随机的信息进入上下文。合理的值范围在 0.2（更宽松）和 0.5（更聚焦）之间。
- 块边界 — 分割文件为块时优先使用的自定义字符串。如果未指定，默认按（依次）双换行、单换行和单词间空格分割。
- 仅在自定义边界上分块 — 如果启用，分块仅在指定的块边界上发生。否则，分块也会在默认边界上发生。
- 处理前将文件翻译成英文 — 如果启用，将使用[聊天翻译](https://docs.sillytavern.app/extensions/translation/)扩展中配置的翻译 API 在处理前将文件翻译成英文。这在使用仅支持英文文本的嵌入模型时很有用。
- 包含在世界信息扫描中 — 如果你希望注入的内容激活知识书条目，请勾选。
- 全部向量化 — 强制摄取所有未处理文件的嵌入。
- 清除向量 — 清除文件嵌入，允许重新计算其向量。

##### 注意

"聊天向量化"设置请参见[聊天向量化](https://docs.sillytavern.app/extensions/chat-vectorization/)。

## 结论

恭喜！你的聊天体验现在已通过 RAG 的力量得到了增强。它的能力只受你的想象力限制。一如既往，不要害怕实验！

---

📖 原文链接：[Data Bank (RAG)](https://docs.sillytavern.app/usage/core-concepts/data-bank/)
