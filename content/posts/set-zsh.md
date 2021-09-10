---
title: "設定 command line 為 Z-shell 環境 "
date: 2019-08-30T00:06:11+08:00
draft: false
tags: ["zsh", "command line"]
---
## 安裝z-shell
如果沒有brew的話要先安裝 `brew`

#### 安裝 `brew`
```s
$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

#### 安裝 `zsh`
```s
$  brew install zsh
```
#### 安裝 `oh-my-zsh`
```s
$ sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```
> zsh 的設定檔放在 `~/.zshrc` ，這個檔案需要我們自己產生由於我們用 `oh-my-zsh` ，所以這邊建議使用 `oh-my-zsh` 預設的 templete 比較省事

```s
$ cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc
```
#### 修改預設的 shell 為 `zsh`
```s
$ chsh -s /usr/local/bin/zsh
```

##  設定主題
### 修改 `.zshrc`
1. 切資料夾至Home `cd ~`
2. 列出所有資料(包含隱藏檔) `ls -la` 會看到名稱為 `.zshrc` 的檔案
3. 修改此檔案 `vim .zshrc`
4. 進到vim之後會看到`ZSH_THEME="bira"` 這句，代表現在套用的主題為`bira`，修改引號內的內容即可更換主題

### 有哪些主題
`cd ~/.oh-my-zsh/themes`可以看有哪些主題，[這裡](https://github.com/robbyrussell/oh-my-zsh/wiki/Themes)可以看主題長什麼樣子

### agnoster主題
如果換了agnoster主題會需要[下載字型](https://github.com/powerline/fonts)，否則會有亂碼出現，如下圖
![](https://i.imgur.com/KMAEGPC.png)

#### 下載字型
將字型clone至Home
```
git clone https://github.com/powerline/fonts.git
sudo ./fonts/install.sh
```
#### 設定字型
以 iTerm2 為例：

iTerm2 > Preference > Profiles > Text > Change Font <br>
將字型改成 `Meslo LG M DZ for Powerline`
![](https://i.imgur.com/kk87Aue.png)
![](https://i.imgur.com/sTJ70cr.png)

## Syntax Highlighting 設定

### 下載 zsh-syntax-highlighting
```s
$ brew install zsh-syntax-highlighting
```
### 設定
進vim修改 `.zshrc` 並加上以下內容：
```s
typeset -gA ZSH_HIGHLIGHT_STYLES
# 防止開新視窗style失效(可能跟globle array有相關)
ZSH_HIGHLIGHT_STYLES[alias]=fg=050,bold
ZSH_HIGHLIGHT_STYLES[builtin]=fg=050,bold
ZSH_HIGHLIGHT_STYLES[function]=fg=050,bold
ZSH_HIGHLIGHT_STYLES[command]=fg=050,bold
```
其中`fg=050`這個數字是256色碼，更改可以換顏色
> [色碼表](https://upload.wikimedia.org/wikipedia/commons/1/15/Xterm_256color_chart.svg)

### 套用
使用 `souce .zshrc` 套用
若沒有改變則：
在 .zshrc 檔中最底下將上這一段來套用：
```s
# For zsh syntax-highlighting
source /usr/local/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
```
