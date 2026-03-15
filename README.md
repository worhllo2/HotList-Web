# 今日热榜

**微博热搜、今日头条、知乎日报、虎扑步行街、36氪、澎湃新闻、哔哩哔哩热榜，知乎、IT资讯、虎嗅网、人人都是产品经理热榜百度、抖音热点豆瓣小组精选等聚合API免费接口**

### 使用说明

https://www.vvhan.com/article/zhihu-baidu-weibo-api-kaiyuan


### 第一步：准备工作

1. **Fork 仓库**：先将 [uxiaohan/HotList-Web](https://github.com/uxiaohan/HotList-Web) 项目 Fork 到你自己的 GitHub 账号下。
2. **本地检查（可选）**：该项目通常使用 `pnpm` 或 `npm` 管理依赖。

### 第二步：在 Cloudflare 控制台操作

1. 登录 [Cloudflare Dashboard](https://dash.cloudflare.com/)。
2. 在左侧菜单栏选择 **Workers 和 Pages**。
3. 点击 **创建应用程序 (Create application)**，然后选择 **Pages** 选项卡。
4. 点击 **连接到 Git (Connect to Git)**。
5. 选择你的 GitHub 账号，并在列表中找到刚才 Fork 的 `HotList-Web` 仓库，点击 **开始设置**。

### 第三步：配置构建设置

在“设置构建和部署”页面，按照以下信息填写（Cloudflare 通常会自动识别，但请务必核对）：

* **项目名称**：可以自定义（如 `hotlist`）。
* **生产分支**：`main`。
* **框架预设**：选择 **Vite**（如果选项里有 Vue 也可以选 Vue，它们本质是一样的）。
* **构建命令 (Build command)**：`npm run build` 或 `pnpm run build`。
* **构建输出目录 (Build output directory)**：`dist`。
* **根目录 (Root directory)**：保持默认（即 `/`）。

### 第四步：保存并部署

1. 点击 **保存并部署**。
2. Cloudflare 会开始拉取代码、安装依赖并运行构建。
3. 等待几分钟，部署完成后，你会获得一个以 `.pages.dev` 结尾的免费域名（例如 `hotlist.pages.dev`）。

---

### ⚠️ 可能遇到的问题及解决方案

#### 1. 环境变量 (API 地址)

`HotList-Web` 作为一个前端项目，需要调用后端接口来获取热点数据。

* **检查代码**：查看项目中是否有 `.env` 文件。如果项目默认使用了作者的公开 API，则直接部署即可运行。
* **自定义 API**：如果你想使用自己的后端接口，请在 Cloudflare Pages 项目的 **设置 -> 环境变量** 中添加对应的变量名。

#### 2. Node.js 版本报错

如果构建失败并提示 Node 版本过低，请在 Cloudflare Pages 的 **设置 -> 环境变量** 中添加：

* **变量名**：`NODE_VERSION`
* **值**：`18` 或更高（如 `20`）。

#### 3. 路由 404 问题

由于这是一个单页应用（SPA），如果你点击了某个链接后刷新页面出现 404，请在项目的 `public` 目录下创建一个名为 `_redirects` 的文件，内容如下：

```text
/* /index.html  200

```

然后重新推送代码到 GitHub，Cloudflare 会自动触发更新。

---

**部署完成后，你可以通过“自定义域”功能绑定你自己的域名。如果你还想通过 Cloudflare Worker 代理它的 API 请求，可以参考你之前问过的 Worker 反代教程。**

### API接口

https://api.vvhan.com/article/wbHot.html

# 动动小手 点个Star

### 页面截图

![今日热榜](https://i0.wp.com/uxiaohan.github.io/v2/2024/09/1725265210.png)

## Stargazers over time

![Stargazers over time](https://starchart.cc/uxiaohan/HotList-Web.svg?variant=adaptive)
