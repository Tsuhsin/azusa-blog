---
title: "使用 ssh key 連接 Github"
date: 2021-02-02T19:20:48+08:00
draft: false
tags: ["ssh", "github"]
---
當需要從本地推檔案到 Github 上時若沒有設定 ssh key 可能會發生 `permission deny` （使用 ssh 連線）或需要每次都需要打你  Github 帳密（使用http連線）的狀況，為了能夠方便地推檔案上  Github 我們需要設定 ssh key。

> 所有生成的 ssh key 都會在 `~/.ssh` 裡
## 連接單一 Github 帳號

### 生成 ssh key
```=zsh
$ ssh-keygen -t rsa -b 4096 -C "你的 Github email"
```
接下來一路 Enter 到底就可以了，這時 `.ssh` 裡面就可以看到 `id_rsa` 和 `id_rsa.pub` 這兩個檔案，前者是私鑰、後者是公鑰（後面有.pub的）


### 把公鑰設定在 Github 上
先將剛剛生成的公鑰 `id_rsa.pub` 複製起來
```=zsh
$ cat id_rsa.pub
```
登入你的 Github ，到 Setting > SSH and GPG keys 這個頁面，點下 `New SSH key` 將複製好的公鑰貼上，點 `add SSH key` 就設定完成。（ title 那裡可以自己取名）
![](https://i.imgur.com/Yw0ZBH8.png)

## 連接多個 Github 帳號
### 生成 ssh key
`ssh-keygen` 之後看到這句時
```
Enter file in which to save the key (/Users/azusa2658/.ssh/id_rsa):
```
先不要 Enter，將預設的`id_rsa`後加上你的 GitHub 帳號名
例如：`id_rsa_sandy`

```=zsh
# Github帳號 1
$ ssh-keygen -t rsa -b 4096 -C "sandy@gmail.com"
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/azusa2658/.ssh/id_rsa): /Users/azusa2658/.ssh/id_rsa_sandy

# Github帳號 2
$ ssh-keygen -t rsa -b 4096 -C "cindy@gmail.com"
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/azusa2658/.ssh/id_rsa): /Users/azusa2658/.ssh/id_rsa_cindy
```
### 添加私鑰到 ssh-agent
```=zsh
$ eval "$(ssh-agent -s)"
$ ssh-add ~/.ssh/id_rsa_sandy
$ ssh-add ~/.ssh/id_rsa_cindy
```
### 設定 config 檔
在 `~/.ssh` 下新增一個 config 檔，內容如下（請自行修改`host` 和 `IdentityFile`）
```=
host sandy.github.com
    Hostname github.com
    User sandy
    IdentityFile ~/.ssh/id_rsa_sandy

Host cindy.github.com
    HostName github.com
    User cindy
    IdentityFile ~/.ssh/id_rsa_cindy
```

### 修改相對應 Repository 的遠端連結網址
```
# Github帳號 1
~/sandy-blog
$ git remote set-url origin git@sandy.github.com:sandy/sandy-blog.git

# Github帳號 2
~/cindy-blog
$ git remote set-url origin git@cindy.github.com:cindy/cindy-blog.git
```
> 這邊 `git@` 後接的主機名分别是 `sandy.github.com` 和 `cindy.github.com`，不再是預設的 `github.com` 了
> 之後 clone repository 時也要注意，修改為相應的主機名

最後將相應的公鑰加到相對應 GitHub 帳號就完成了～

## 參考資料
1. [Connecting to GitHub with SSH](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh)
2. [使用 SSH 連接到 GitHub（多帳號）](https://io-oi.me/tech/ssh-with-multiple-github-accounts/)
3. [git 配置多個SSH-Key](https://my.oschina.net/stefanzhlg/blog/529403)

