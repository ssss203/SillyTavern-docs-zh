# 🔧 服务器插件（Server Plugins）
> 💡 **肆说**：服务器插件开发文档，做角色卡暂时跳过。

在 NodeJS 环境中运行，可添加 UI 扩展无法实现的功能（如新 API 端点）。需在 config.yaml 中设置 `enableServerPlugins: true`。插件通过 Express router 注册路由，路径为 `/api/plugins/{id}/{route}`。⚠️ 插件不受沙箱保护，只安装你信任的开发者的插件。

📖 原文链接：[Server Plugins](https://docs.sillytavern.app/for-contributors/server-plugins/)
