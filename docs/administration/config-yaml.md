# ⚙️ 配置文件（config.yaml）
> 💡 **肆说**：config.yaml是SillyTavern的核心配置文件，一般不需要手动改。除非你知道自己在干嘛。

`config.yaml` 是 SillyTavern 服务器的主配置文件，包含网络、安全和后端相关设置。修改后需重启服务器生效。

主要配置项包括：数据存储、日志、网络（端口/监听/IPv4/IPv6）、SSL、安全（IP白名单/主机白名单/私有地址白名单）、用户认证、速率限制、请求代理、CORS、浏览器启动、性能、缩略图、备份、扩展、Git 后端、API 集成设置（OpenAI/MistralAI/Ollama/Claude/Google Gemini/DeepL）等。

也可通过命令行参数和环境变量覆盖配置。

📖 原文链接：[Configuration File](https://docs.sillytavern.app/administration/config-yaml/)
