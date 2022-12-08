# Edge Tunnel （正在开发）

一个无比简单安全，基于 edge 的 tunnel 。

**v2ray-heroku 由于 heroku 取消免费，项目已经死了。

> 项目正在开发，基本可用，会有 bug。。
> **请定期按照 github 的提示，只同步到自己的项目。只需要在乎下图红框的提示，其他提示不要点击**。
> ![sync](./doc/sync.jpg)

> 本项目纯属技术性验证，探索最新的 web standard。不给予任何保证。请大家酌情使用。如果有兴趣想一起进行技术探讨可以联系我。💕

## Edge Tunnel server --- Deno deploy

Edge tunnel 的服务使用了 [Deno deploy](https://deno.com/deploy).

### 风险提示

`Deno deploy` 采用 [fair use policy](https://deno.com/deploy/docs/fair-use-policy), 翻译成中文就是`看良心使用`。 违反可能会封号。
按照我的理解，本项目应该是违反 fair use policy。请大家**酌情使用**。

> 这里十分感谢 Deno deploy 严肃对待 web standard， 支持 HTTP request & response streaming，让 edge tunnel 成为可能。

> 这里没有使用 deno websocket，其实技术上可以把 v2ray 移植过来。但是我暂时没有看明白 VLESS 协议内容.

## Edge Tunnel server --- Cloudflare Worker （敬请期待）

这个需要等 Cloudflare 发布下面的技术。
https://blog.cloudflare.com/introducing-socket-workers/

### 如何部署服务

请查看下面教程。

[Deno deploy Install](./doc/edge-tunnel-deno.md)

## Edge Tunnel 客户端

> 由于看不懂 VLESS 协议内容, 所以无法使用常用的客户端软件.

### 安装

请转到本项目 [releases](https://github.com/zizifn/edgetunnel/releases),选择正确的平台，下载最新客户端.

项目使用https://github.com/vercel/pkg, 所以支持下面平台.

1. **platform** alpine, linux, linuxstatic, win, macos, (freebsd)
2. **arch** x64, arm64, (armv6, armv7)

## 启动

解压并且修改安装文件的 `config.json` 文件.

```json
{
  "port": "1081", // 本地 HTTP 代理的端口
  "address": "https://****.deno.dev/", // deno deploy URL
  "uuid": "****" // 你 deno deploy 设置的用户
}
```

然后,在解压目录下，打开命令行, 输入下面命令.

> Edge Tunnel Client 会在本地启动一个 http 代理.

> 如果 window 系统提示，是否允许网络权限，请把所有允许。
> ![firewall](./doc/firewall.jpg)

```ps
.\edgetunnel-win-x64.exe run --config .\config.json
```

![client-log](./doc/client-log.jpg)

> 请不要关闭关闭命令行. 如果关闭,代理会自动退出.

### 验证代理是否正常

再次开启一个新的命令行，测试 proxy 是否启动正常。。**注意自己 proxy 的端口**。

```bash
curl -v https://www.google.com --proxy http://127.0.0.1:1081
```

如果有返回结果，并且 edge tunnel 命令行有提示，说明一切成功。

```
proxy to www.google.com:443 and remote return 200
```

## 配置代理服务 （重要）

> 不像 v2rayN 可以在自动配置代理，本客户端目前需要手动配置代理才能工作。 下面三种方式可供参考。

### 浏览器 switchyomega 设置

具体安装和配置,请查看官网.
https://proxy-switchyomega.com/proxy/

除了端口（port）和下图可能不一样。其他都应该是一样的。

> 端口是你在 config.json 自己配置的

![switchyomega2](./doc/switchyomega2.jpg)

### 系统全局 proxy 配置

你也可以配置 proxy 到系统级别。

### 其他软件 proxy 设置

> 电报客户端一直不停的发送 HTTP 请求，所以代理电报可能会快速消耗资源和免费额度。

> 下面以电报为例，其他软件也是一样的。具体方式请用搜索引擎。

路径， setting--> Advance-->Conntction type--> Use Custom proxy
![tel](./doc/tel.jpg)
