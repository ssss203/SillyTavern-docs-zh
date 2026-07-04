# 🌐 聊天翻译（Chat Translation）
> 💡 **肆说**：想让AI用中文回复但API只支持英文？开翻译扩展就行！推荐用Google或DeepL。

## 概述

聊天翻译扩展可以使用多种翻译服务商，在不同语言之间实时翻译聊天消息。支持手动和自动翻译模式。

## 使用方式

- **Translate Chat** 按钮：一次性翻译整个聊天记录
- **Translate Input** 按钮：只翻译当前输入的文字
- **Translate Message** 图标：点击翻译该条消息，再点恢复原文
- **Auto-mode**：自动翻译用户输入、AI 回复，或两者都翻译
- **/translate** 斜杠命令：`/translate [target=language_code] text`

## 配置

在 **Extensions** 面板的 **Chat Translation** 中配置。

#### 翻译服务商（Provider）
选择翻译服务。如有 API Key 图标就点它输入密钥。

#### 目标语言（Target Language）
选择你想用什么语言写消息或阅读 AI 回复。

#### 自动模式（Auto-mode）
- **None**：不自动翻译
- **Translate responses**：自动翻译 AI 回复
- **Translate inputs**：自动翻译用户输入为英文
- **Translate both**：两者都翻译

#### 清除翻译
**Clear Translations** 按钮移除所有翻译，原文保留。

### 配置示例：中文用户与英文 AI 聊天
1. Auto-mode 设 "Translate both"
2. Target Language 设 "Chinese (Simplified)"
3. 选语言自动检测好的服务商（如 Google/DeepL）

## 翻译服务商

| 服务商 | 特点 |
|--------|------|
| [Libre Translate](https://libretranslate.com/) | 自托管，开源，有云端版 |
| [Google Translate](https://cloud.google.com/translate) | 语言多，准确度高 |
> 💡 **肆说**：免费方案，国内可能需要梯子。
| [Lingva Translate](https://lingva.ml/) | Google 前端替代，注重隐私 |
| [DeepL](https://www.deepl.com/) | 翻译质量高，尤其欧洲语言 |
> 💡 **肆说**：翻译质量最好，国内需要梯子。
| [DeepLX](https://github.com/OwO-Network/DeepLX) | 自托管 DeepL 代理 |
| [Bing Translator](https://www.bing.com/translator) | 微软翻译 |
> 💡 **肆说**：国内可用！免费，质量还行。
| [Yandex Translate](https://translate.yandex.com/) | 俄语/东欧语言好 |

### DeepL 特殊配置
德/法/意/西/荷/日/俄语支持正式度等级，通过 `config.yaml` 的 `deepl.formality` 配置。

## 技术说明

- 支持 UTF-8、特殊字符、emoji
- 大消息自动分块
- 保留格式和嵌入图片
- 缓存翻译结果

### AI 输入语言
`internal_language` 默认硬编码为 'en'，发给 AI 的消息始终翻译成英文。

### 中文变体映射
- Libre Translate：zh-CN→zh，zh-TW→zt
- DeepL/DeepLX：两种→ZH
- Bing：zh-CN→zh-Hans，zh-TW 不变

### 文本长度限制
Yandex 5000 / DeepLX 1500 / Bing 1000 / Google 5000 字符

📖 原文链接：[Chat Translation](https://docs.sillytavern.app/extensions/translation/)
