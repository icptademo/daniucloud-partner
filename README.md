# 国际云渠道笔记

中文笔记，用 Jekyll 写成，发布为 GitHub 项目站点。地址是 <https://icptademo.github.io/daniucloud-partner>。

文章只讨论如何成为并运营国际云开户与充值的代理和渠道：代理合作、渠道分销、技术联运、方案共建，以及返佣对账、白标、下级代理和接待客户时的合规边界。控制台步骤在 [《国际云实战笔记》](https://icptademo.github.io)，本站不重复。

事实以 [大牛云代理招商](https://www.daniucloud.com/partners) 为准，并对照首页和价格说明。不在文章里编写返佣比例、到账承诺或服务等级。联系用官网表单或 Telegram [@yanhuacloud](https://t.me/yanhuacloud)。不要在仓库 issue 里粘贴密码、验证码或密钥。

## 发布到 GitHub Pages

这是项目站点，不是用户站点。`_config.yml` 里必须保持：

```yaml
url: https://icptademo.github.io
baseurl: /daniucloud-partner
```

`baseurl` 少了或不对，样式、文章和 RSS 都会指向错误地址。不要添加 `CNAME`，除非以后改用独立域名并同时改这两项。

仓库管理员需要做一次设置：

1. 打开仓库的 **Settings → Pages**。
2. **Build and deployment** 的 **Source** 选 **Deploy from a branch**。
3. **Branch** 选 `main`，文件夹选 `/ (root)`，保存。

保存后等 GitHub Pages 用 Jekyll 构建。完成后访问 <https://icptademo.github.io/daniucloud-partner>。RSS 在 `/daniucloud-partner/feed.xml`，站点地图在 `/daniucloud-partner/sitemap.xml`。

`.github/workflows/jekyll.yml` 只在推送到 `main` 和拉取请求上检查 `jekyll build` 能否通过，并确认生成的链接带有 `/daniucloud-partner`。它不会把站点部署出去。不要把发布来源改成 GitHub Actions，除非另外准备部署工作流。

本站只用 GitHub Pages 允许的插件：`jekyll-feed`、`jekyll-seo-tag`、`jekyll-sitemap`。

## 本地预览

需要 Ruby 3.2 或与之接近的版本。

```bash
bundle config set --local path 'vendor/bundle'
bundle install
bundle exec jekyll serve
```

浏览器打开 <http://127.0.0.1:4000/daniucloud-partner/>。`Gemfile` 使用 `github-pages` gem，尽量和 GitHub Pages 的构建一致。

## 写一篇新笔记

在 `_posts/` 新增 `YYYY-MM-DD-english-slug.md`。固定链接来自文件名，例如 `2026-11-12-compliant-account-opening.md` 对应 `/daniucloud-partner/2026/11/compliant-account-opening/`。

```yaml
---
layout: post
title: "中文标题"
description: "给首页、RSS 和搜索结果用的一两句话。"
date: 2026-11-12 10:00:00 +0800
categories: [合规接待]
tags: [开户合规]
---
```

分类使用 `_data/categories.yml` 里已有的名称。新标签在 `_data/tag_slugs.yml` 加一条英文锚点，标签页才有稳定地址。站内链接写成 `{{ '/路径/' | relative_url }}`，不要写死以 `/` 开头却不含项目目录的地址。

不写购买或转让他人账号，不写返佣百分比。比例、结算日和退款扣减只提示读者写进合作条件。
