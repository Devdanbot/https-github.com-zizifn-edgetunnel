# Deno deploy Install

## 风险提示

`Deno deploy` 采用 [fair use policy](https://deno.com/deploy/docs/fair-use-policy), 翻译成中文就是`看良心使用`。 违反可能会封号。

## Fork 本项目到自己 Github 下

![fork](./fork.jpg)

**请定期按照 github 的提示，同步 code 到自己的项目**。
![sync](./sync.jpg)

## 登录 Deno deploy

用 Github 账户登录 https://deno.com/deploy

> 相关免费策略，https://deno.com/deploy/pricing

## New Project

请在配置过程中 **记住 UUID**, 并且选择正确的部署入口文件。`apps\deno-vless\src\main.ts`
![deno-link](./deno-link.jpg)

### 流程演示

> GIF 仅仅是流程演示，具体入口文件，请看上图。

https://raw.githubusercontent.com/zizifn/edgetunnel/main/doc/deno-deploy.gif

![deno-deploy](./deno-deploy.gif)

如果 UUID 忘记 或者入口文件有变化，也可以在 deno 管理界面修改项目的配置。

https://raw.githubusercontent.com/zizifn/edgetunnel/main/doc/deno-deploy2.gif
![deno-deploy2](./deno-deploy2.gif)

其他更多配置，比如使用量，请自行探索。

## 项目地址

点击 View 项目会自动打开。一开始返回 `404`. 不要慌张, 把你设置的 `UUID` 添加到 URL 后面。

下面是示例，请把 URL 和 UUID 换成自己的。
`https://xxxxxx.deno.dev/015897c1-663d-4b2a-9f90-053b189cdc47`。

如果出现下面的界面，都代表一切正常。

![index](./index.jpg)
