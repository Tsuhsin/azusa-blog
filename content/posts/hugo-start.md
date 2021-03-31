---
title: "使用 Hugo 架設靜態網站"
date: 2021-01-30T07:36:18+08:00
draft: false
tags: ["hugo", "blog"]
---
Hugo是一種用Go語言編寫的靜態網站生成器，使用Hugo構建的網站非常快速和安全。

Hugo網站可以部署在任何地方，包括 Netlify、Heroku、GoDaddy、DreamHost、GitHub Pages、GitLab Pages、Surge、Aerobatic、Firebase、Google Cloud Storage、Amazon S3、Rackspace、Azure和CloudFront，並可以與CDN很好地協作。

### 安裝 Hugo
```s
$ brew install hugo
```
### 建立新網站
```s
$ hugo new site my-blog
```
### 下載主題
> 我使用的 [主題](https://github.com/reuixiy/hugo-theme-meme/blob/master/README.zh-tw.md)
```s
~ $ cd my-blog
~/my-blog $ git init
~/my-blog $ git submodule add --depth 1 https://github.com/reuixiy/hugo-theme-meme.git themes/meme
```

### 設定 config 檔
可參考下載主題裡的說明（通常會有example site）

### 新建頁面
```s
$ hugo new "posts/first.md"
```
### 基本 hugo 指令
#### build
```s
$ hugo
```
#### Local serve (Live Reload)
```s
$ hugo server -D
```
#### 更新 Hugo
```s
$ brew upgrade hugo
```
## 參考資料
1. [Hugo Documentation](https://gohugo.io/getting-started/quick-start/)
2. [Hugo 主題 MemE 文檔](https://io-oi.me/tech/documentation-of-hugo-theme-meme/)
