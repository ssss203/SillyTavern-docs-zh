# 🌐 远程连接
> 💡 **肆说**：想在手机上用电脑跑的SillyTavern？看这个。但绝对不要直接暴露到公网！

最常见的场景是：电脑跑 ST 服务器，手机通过同一 WiFi 网络访问。

> ⛔ **绝对不要用端口转发把 ST 服务器暴露在公网上！** 用 VPN 或隧道服务（如 Cloudflare Zero Trust、ngrok、Tailscale）。参考 [VPN 和隧道](../administration/tunneling.md) 指南。
> 💡 **肆说**：真的！用VPN或隧道服务代替，端口转发等于把你电脑的SillyTavern裸奔到互联网上。

## 允许远程连接

默认 ST 只接受本机连接。要允许其他设备连接，在 `config.yaml` 中设 `listen: true`。

```
listen: true
```

启动后看到 `SillyTavern is listening on IPv4: 0.0.0.0:8000` 表示成功。

## 访问控制

启用远程连接后，必须配置至少一种访问控制方式，否则服务器不会启动。

### 白名单方式

编辑 `config.yaml` 的 `whitelist` 部分，添加允许的 IP 地址。

允许所有局域网设备：
```
whitelist:
  - ::1
  - 127.0.0.1
  - 10.0.0.0/8
  - 172.16.0.0/12
  - 192.168.0.0/16
```

### 禁用白名单

设 `whitelistMode: false` 并重启服务器。

### HTTP 基本认证

在 `config.yaml` 中启用：
```
basicAuthMode: true
basicAuthUser:
  username: "MyUsername"
  password: "MyPassword"
```

## 连接到你的 SillyTavern

1. 获取 ST 主机的 IP（Windows: `ipconfig`）
2. 在远程设备浏览器输入：`http://192.168.0.5:8000`（用你的实际 IP）

## HTTPS

用 `--ssl` 标志启动：
```
node server.js --ssl
```

证书文件放在 `certs` 文件夹，或用 `--keyPath` 和 `--certPath` 指定路径。

---

📖 原文链接：[Remote connections](https://docs.sillytavern.app/usage/remoteconnections/)
