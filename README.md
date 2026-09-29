# Maxwell's Blog

基于 Hexo 8.1.2 与 Butterfly 5.7.0 的静态博客。

- 在线地址：https://maxwell0339.github.io/
- 源码分支：`main`
- 发布方式：推送后由 GitHub Actions 构建，并发布到 GitHub Pages
- Node.js：建议使用 `.nvmrc` 指定的 24 版本

## 本地预览

```bash
npm ci
npm run server
```

打开 <http://localhost:4000>。修改站点或主题配置后，需要重启预览服务。

## 写文章

```bash
npm run new -- "文章标题"
```

编辑 `source/_posts/` 下生成的 Markdown 文件。例如：

```yaml
---
title: 文章标题
date: 2026-09-29 20:00:00
tags:
  - 学习笔记
categories:
  - 技术实践
description: 一两句话介绍文章内容。
cover: /img/notes.svg
---
```

正文使用 Markdown 编写。可以用 `<!-- more -->` 划分摘要和正文。图片放到 `source/img/`，使用 `/img/文件名` 引用。未来时间的文章不会提前发布。

## 发布

先在本地检查构建：

```bash
npm run build
```

确认内容后提交并推送：

```bash
git add .
git commit -m "docs(blog): add a new post"
git push origin main
```

在仓库的 [Actions 页面](https://github.com/Maxwell0339/Maxwell0339.github.io/actions) 查看发布结果。构建产物在 `public/`，无需提交这个目录。

GitHub 仓库 **Settings → Pages → Build and deployment → Source** 应选择 **GitHub Actions**。发布使用 GitHub 提供的短期令牌，不需要配置个人令牌或上传 SSH 私钥。

## 常用配置

| 文件或目录 | 用途 |
| --- | --- |
| `_config.yml` | 标题、作者、域名、语言、文章链接 |
| `_config.butterfly.yml` | 导航、侧栏、配色、搜索、深色模式 |
| `source/index.md` | 网站首页 |
| `source/homepage/index.html` | 独立学术主页 |
| `source/archives/index.md` | 文章归档页 |
| `source/_posts/` | 文章正文 |
| `source/about/index.md` | 关于页面 |
| `source/projects/index.md` | 项目页面 |
| `source/css/custom.css` | 自定义样式 |
| `source/css/homepage.css` | 独立学术主页样式 |
| `source/img/` | 封面、头像与图标 |
| `.github/workflows/pages.yml` | 自动构建和发布 |

学术主页位于 `/homepage/`，内容直接编辑 `source/homepage/index.html`：替换姓名、简介、动态、教育经历、论文和学术服务等文字即可。若要使用个人照片，请先将图片放入 `source/img/`，再修改页面中头像 `<img>` 的 `src`。页面样式集中在 `source/css/homepage.css`，修改后运行 `npm run build` 预览构建结果。

本地搜索、文章目录、代码复制、分类、标签及深色模式已启用。评论区尚未接入服务；若需要，可在 Butterfly 配置中接入 Giscus 等服务。

## 主题选择

| 主题 | 特点 | 官方预览与文档 |
| --- | --- | --- |
| **Butterfly（当前使用）** | 卡片布局、侧栏丰富、可选功能多 | <https://butterfly.js.org/> |
| NexT | 布局简洁，以长文阅读为主 | <https://theme-next.js.org/> |
| Fluid | 大幅封面、留白舒适 | <https://hexo.fluid-dev.com/> |

主题通过 npm 安装，并由 `package-lock.json` 记录依赖版本。自定义配置独立于主题包，后续升级无需修改主题源码。

## 参考

- [Hexo 官方 GitHub Pages 部署文档](https://hexo.io/docs/github-pages)
- [Butterfly 官方安装文档](https://butterfly.js.org/posts/21cfbf15/)
