---
title: "Git 本地端 push 到遠端 (Github)"
date: 2021-02-02T18:00:00+08:00
draft: true
tags: ["git", "github"]
---
### 前置作業
進 command line 先在本地建一個專案資料夾 (local repository)並進資料夾
```s
$ mkdir test-repo
$ cd test-repo
```
接著設定git
```s
$ git init
```
這時就可以做第一個 commit (一定要有commit才能推到遠端)
```s
$ git add .
$ git commit -m "git init"
```
### 將本地repo推到遠端
Github 那邊要先建一個一樣名稱的repository (這次舉例資料夾名稱為test-repo)

之後回到 command line 這裡，將本地跟遠端連結
```s
$ git remote add origin git@github.com:Tsuhsin/test-repo.git
```
網址是剛剛建好的 repo 的網址 (直接複製ssh)
![](https://i.imgur.com/pRgCTVG.jpg)

最後push上去就大功告成了
```s
$ git push -u origin master
```

