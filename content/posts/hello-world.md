---
title: "Hugo 架站"
date: 2021-01-30T07:36:18+08:00
draft: false
---

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
可參考下載得住提的說明（通常會有example site）
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
