---
title: "使用 Hugo 架設靜態網站"
date: 2021-01-30T07:36:18+08:00
draft: false
tags: ["hugo", "blog"]
---
Hugo是一種用Go語言編寫的靜態網站生成器，使用Hugo構建的網站非常快速和安全。
Hugo網站可以部署在任何地方，包括 Netlify、Heroku、GoDaddy、DreamHost、GitHub Pages、GitLab Pages、Surge、Aerobatic、Firebase、Google Cloud Storage、Amazon S3、Rackspace、Azure和CloudFront，並可以與CDN很好地協作。

### 安裝 Hugo
```
brew install hugo
```
### 常用指令
> https://gohugo.io/getting-started/quick-start/
#### 建立新網站
```
hugo new site xxxx
```
#### 下載主題
> 我使用的主題

> https://github.com/reuixiy/hugo-theme-meme/blob/master/README.zh-tw.md
```=
~ $ cd blog
~/blog $ git init
~/blog $ git submodule add --depth 1 https://github.com/reuixiy/hugo-theme-meme.git themes/meme
```
#### 新建頁面
```
hugo new "xxx.md"
```
#### 設定 config 檔
可參考下載主題裡的說明（通常會有example site）
#### build
```
hugo
```
#### Local serve (Live Reload)
```
hugo server
```
#### 更新 Hugo
```
brew upgrade hugo
```
## 參考資料
1. [Hugo Documentation](https://gohugo.io/getting-started/quick-start/)
