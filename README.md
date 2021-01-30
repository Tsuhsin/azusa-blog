# azusa-blog

## 目錄結構
```
.
├── content                # 存放編譯後的可執行檔案
│   └── post               # 文章位置
├── public                 # 編譯後的資料
├── static                 # 放置 images css 等靜態檔
└── themes                 # 版型存放位置
│   └── theme-name
│       ├── exampleSite    # 初始化用，可複製此資料夾至專案根目錄
│       └── layouts        # theme 模板檔 👈 可客製化的地方
└── config.toml            # 主要的 config 檔
```

## 安裝
```
brew install hugo
```
## 更新 Hugo
```
brew upgrade hugo
```
## 新建頁面
```
hugo new "xxx.md"
```
## build
```
hugo
```
## Local serve (Live Reload)
```
hugo server
```
