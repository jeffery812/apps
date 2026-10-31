# apps

[English](README.md) | **简体中文**

我所有 App 的介绍页和隐私政策，通过 GitHub Pages 发布。每个 App 一个目录。

- 仓库：<https://github.com/jeffery812/apps>
- 网站：<https://jeffery812.github.io/apps/>

## App 列表

| App | 介绍页 | 隐私政策 | App Store |
| --- | --- | --- | --- |
| STHLM Rail | [sthlm-rail/](https://jeffery812.github.io/apps/sthlm-rail/) | [privacy.html](https://jeffery812.github.io/apps/sthlm-rail/privacy.html) | [id1084180460](https://apps.apple.com/se/app/stockholm-rail/id1084180460?l=en-GB) |

## 目录结构

```
apps/
├── README.md
├── index.html            # 所有 App 的列表
├── 404.html              # 全站共用的 404 页面，GitHub Pages 只认根目录下的这个
└── sthlm-rail/
    ├── index.html        # 介绍页
    ├── privacy.html      # 隐私政策
    └── images/           # 截图、图标
```

## 约定

- **目录名**用产品名，小写，单词之间用 `-` 连接，不带平台后缀（`sthlm-rail`，而不是 `sthlm-rail-ios`）。目录名就是网址的一部分，发布后不要再改，否则 App Store Connect 里填的隐私政策网址会失效。
- **每个 App 至少有两个页面**：`index.html`（介绍）和 `privacy.html`（隐私政策）。
- **只用相对路径**引用图片和页面（`images/icon-180.png`、`privacy.html`），整个目录挪到别处也能直接用。
- **页面是纯静态 HTML**，不需要构建步骤。字体和图标从 Google Fonts、unpkg 加载，其他内容都写在页面里。
- **所有页面都用英文。**
- **README 有英文（`README.md`）和中文（`README.zh-CN.md`）两个版本**，改其中一个时要同步另一个。
- **隐私政策的内容要跟 App 的实际行为一致**，包括所用的 SDK、上报的事件、数据保留期限。App 改了数据处理方式时，先更新 `privacy.html` 和页面上的"Last updated"日期，再发版本，同时检查 App Store Connect 里的隐私标签。

## 添加一个新 App

1. 新建目录 `<app-name>/`，放入 `index.html`、`privacy.html` 和 `images/`。
2. 在本 README（中英文两个版本）的 App 列表、根目录的 `index.html` 和 `404.html` 的 App 列表里各加一项。
3. 本地预览，确认没有坏链接（见下文）。
4. 提交并推送，GitHub Pages 一般一两分钟后更新。
5. 在 App Store Connect 中，把该 App 的隐私政策网址设为 `https://jeffery812.github.io/apps/<app-name>/privacy.html`。如果需要，再把技术支持网址或营销网址设为介绍页地址。

## 本地预览

```bash
cd /Users/zhihuitang/repo/Documents/apps
python3 -m http.server 8000
```

然后打开 <http://localhost:8000/sthlm-rail/>。直接双击打开 HTML 文件也能看，但用本地服务器预览更接近线上效果。

## 发布设置

第一次需要在 GitHub 上设置一次：仓库的 **Settings → Pages → Build and deployment**，Source 选 **Deploy from a branch**，分支选 `main`，目录选 `/ (root)`。

以后如果改用自己的域名，在根目录加一个 `CNAME` 文件，再在域名服务商那里配置 DNS。各 App 的路径不用变。
