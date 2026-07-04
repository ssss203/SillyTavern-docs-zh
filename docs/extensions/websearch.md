# 🔎 网络搜索（Web Search）
> 💡 **肆说**：让AI能"上网查资料"，适合需要最新信息的场景。设置稍复杂，新手可以先跳过。

将网络搜索结果添加到 LLM 提示词中。

> 注意：部分 Chat Completion 来源自带网络搜索功能，此扩展可能冗余。检查 AI Response 配置面板的 "Enable web search" 开关。

## 可用来源

| 来源 | 说明 |
|------|------|
| **Selenium Plugin** | 需[服务器插件](https://github.com/SillyTavern/SillyTavern-WebSearch-Selenium)，支持 Google/DuckDuckGo |
| **Extras API** | 需 websearch 模块和 Chrome/Firefox，支持 Google/DuckDuckGo |
| **SerpApi** | 需 API 密钥，[获取](https://serpapi.com/dashboard) |
| **SearXNG** | 需实例 URL（私有或公共），[了解更多](https://docs.searxng.org/) |
| **Tavily AI** | 需 API 密钥，[获取](https://app.tavily.com/) |
| **KoboldCpp** | 需 ≥1.81.1 版本且启用 WebSearch 模块 |
| **Serper** | 需 API 密钥，[获取](https://serper.dev/) |
| **Z.AI** | 需 API 密钥，[获取](https://z.ai/manage-apikey/apikey-list/) |

## 使用方法
1. 确保最新版 SillyTavern
2. 从"下载扩展和素材"菜单安装
3. 设置 API 密钥或连接 Extras，启用扩展
4. **只有用户消息会触发搜索**
5. 用反引号包裹搜索词：``Tell me about the `latest Ryan Gosling movie`.``
6. 可选配置设置

## 设置

### 通用
- Enabled / Sources / Cache Lifetime（缓存秒数，默认一周）

### 提示词设置
- **Prompt Budget** - 插入文本最大字符数（非 token），默认1500
- **Insertion Template** - 插入模板，支持 `{{query}}` 和 `{{text}}` 宏
- **Injection Position** - 注入位置

### 搜索激活
- **Use function tool** - 用函数调用激活（需支持的 API），启用后禁用其他方式
- **Use Backticks** - 反引号激活
- **Use Trigger Phrases** - 触发词激活
- **Regular expressions** - JS 正则匹配

### 页面抓取
- Visit Links / Visit Count / Domain Blacklist / Save Target / Include Images

## 斜杠命令
```
/websearch (links=on|off snippets=on|off [query])
```

📖 原文链接：[Web Search](https://docs.sillytavern.app/extensions/websearch/)
