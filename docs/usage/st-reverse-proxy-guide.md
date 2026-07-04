# 反向代理
> 💡 **肆说**：你不是服务器管理员，扫一眼就行。这个是给想要公网部署SillyTavern的人看的，非常技术性。

##### 注意

本节**不**指OpenAI/Claude反向代理。专指**HTTP/HTTPS反向代理**。

Termux设置太复杂？厌倦在每台设备上更新安装ST？想要整理你的聊天和角色？本指南将介绍如何在你的PC上托管SillyTavern，让你可以在任何地方连接。

##### 警告

本指南**不适合**初学者。技术性很强。

## 重要警告

##### Windows用户

本指南不适用于Windows用户。建议使用Linux VM或WSL2。

##### Linux用户

你必须具备以下知识：Linux控制台命令、DNS记录、公网IP地址、[Docker](https://www.docker.com/)

**你需要为自己购买域名并为SillyTavern页面配置CNAME。建议在[Cloudflare](https://www.cloudflare.com/)上添加或购买域名。**

## 安装

### Linux（裸机SillyTavern）

使用[Traefik](https://traefik.io/traefik/)进行反向代理。详细步骤包括：

1. 获取私有IP和公网IP
2. 安装Docker
3. 创建docker文件夹结构和配置
4. 配置Cloudflare DNS记录
5. 配置Traefik（traefik.yml、docker-compose.yaml、config.yml）
6. 运行Docker Compose
7. 编辑SillyTavern的config.yaml启用listen模式和基本认证

### Linux（Docker SillyTavern）

类似步骤，但SillyTavern运行在Docker容器中，通过Traefik标签配置路由。

## 更新Cloudflare DNS

[DDClient](https://ddclient.net/)允许你将公网IP同步到Cloudflare，在ISP更改IP时仍可访问ST实例。

📖 原文链接：[Reverse proxying](https://docs.sillytavern.app/usage/st-reverse-proxy-guide/)
