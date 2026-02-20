# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

这是一个基于 Jekyll 的静态博客网站（工具集合网），forked from [Hux Blog](https://github.com/Huxpro/huxpro.github.io)。主要用于发布在线工具集合和相关文章。

- **站点配置**: `_config.yml`
- **域名**: itzhouq.cn（通过 CNAME 配置）
- **部署**: GitHub Pages，推送到 master 分支自动触发部署

## 常用命令

### 本地开发预览

```bash
# 启动 Jekyll 本地服务器（推荐）
npm run start
# 或
bundle exec jekyll serve

# 同时监听 Less/JS 文件变化并自动编译
npm run dev
```

### 构建前端资源

```bash
# 编译 Less 和压缩 JS（生成 .min 文件）
grunt
# 或
npm run dev  # 监听模式
```

### 创建新文章

```bash
# 使用 Rake 任务创建新文章
rake post title="文章标题" subtitle="副标题"

# 文章会创建在 _posts/ 目录下，文件名格式：YYYY-MM-DD-title.md
```

### 部署

```bash
# 推送到 GitHub 触发自动部署
git push origin master

# 推送带 tag
npm run push
```

## 项目结构

```
├── _config.yml          # Jekyll 站点配置
├── _layouts/            # 页面布局模板
│   ├── default.html     # 默认布局
│   ├── post.html        # 文章页布局（含目录、评论）
│   ├── page.html        # 页面布局
│   └── keynote.html     # 演示文稿布局
├── _includes/           # 可复用的组件片段
│   ├── head.html        # HTML 头部（meta、CSS、OG标签）
│   ├── nav.html         # 导航栏
│   ├── footer.html      # 页脚
│   ├── intro-header.html # 页头大图
│   └── ...
├── _posts/              # 博客文章（.md 或 .markdown）
├── css/                 # 编译后的 CSS
├── js/                  # JavaScript 文件
├── less/                # Less 源文件（修改样式从此处）
│   └── hux-blog.less    # 主样式文件
├── img/                 # 图片资源
├── pwa/                 # Progressive Web App 配置
├── index.html           # 首页（文章列表）
├── about.html           # 关于页面
├── archive.html         # 归档页面
├── 404.html             # 404 页面
├── Gruntfile.js         # Grunt 构建配置
├── Rakefile             # Rake 任务（创建文章）
├── package.json         # npm 脚本
└── Gemfile              # Ruby 依赖
```

## 开发注意事项

### 样式修改

- **源文件**: `less/hux-blog.less` 及 `less/` 目录下的其他 .less 文件
- **编译后**: `css/hux-blog.css` 和 `css/hux-blog.min.css`
- 修改 Less 文件后需要运行 `grunt` 或 `npm run dev` 编译

### 文章 Front Matter

文章需要包含以下 front matter：

```yaml
---
layout: post
title: "文章标题"
subtitle: "副标题"
date: YYYY-MM-DD HH:MM:SS
author: "作者名"
header-img: "img/post-bg-xxx.jpg"  # 头图
tags:
    - 标签1
    - 标签2
---
```

### 标签和分类

- 文章通过 `tags` 字段指定标签
- 标签页会自动生成（基于 `tags` 目录）
- 特色标签在 `_config.yml` 中 `featured-condition-size` 配置

### 评论系统

- Disqus: 在 `_config.yml` 中配置 `disqus_username`
- 网易云跟帖: 设置 `netease_comment: true`

### 侧边栏目录

文章页自动生成目录（TOC），如需禁用：
```yaml
---
no-catalog: true
---
```

## GitHub Actions

自动部署流程在 `.github/workflows/jekyll.yml`：
- 推送到 `master` 分支触发
- Ruby 3.1 + Jekyll 构建
- 输出到 `_site` 目录并部署到 GitHub Pages

## PWA 支持

- Service Worker: `sw.js`
- Manifest: `pwa/manifest.json`
- 在 `_config.yml` 中 `service-worker: true` 启用
