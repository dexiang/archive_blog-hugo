---

title: Hexo 指南
categories: 
  - tech
tags:
  - hexo
date: 2017-01-20 15:08:26

---


其實目前官網的文件非常詳細，這裡就不多做介紹了。

## 安裝 Hexo ##

```
$ npm install hexo-cli -g
```

## 建立 & 初始化 ##

```
$ hexo init <folder>
$ cd <folder>
$ npm install
```

建立後會有以下資料夾 & 檔案

```
.
├── _config.yml # 網站設定檔
├── package.json
├── scaffolds # 鷹架資料夾
├── scripts # 腳本資料夾
├── source
|   ├── _drafts
|   └── _posts
└── themes # 主題
```

<!-- more -->

## 配置 ##

※ [官方設定檔文件](https://hexo.io/zh-tw/docs/configuration.html "Hexo Configuration")

## 常用指令 ##

```
# 查看幫助
hexo help
# 新建文章
hexo new "postName"
# 新建頁面
hexo new page "pageName"
# 產生靜態網頁
hexo generate
# 本機預覽
hexo server
# 部署
hexo deploy
# 清除暫存，執行前建議使用
hexo clean

```

> ### 簡寫 ###
> ```
> hexo n == hexo new
> hexo g == hexo generate
> hexo s == hexo server
> hexo d == hexo deploy
> ```

## 部署到 Git ##

透過 Git 發佈，安裝 Git 套件

```
$ npm install hexo-deployer-git --save
```

修改 `_config.yml` 設定值

```
# Deployment
deploy:
  type: git
  repo: git@github.com:dexiang/dexiang.github.io.git
  branch: master
  message:
```

設定好以後就可以部署了

```
$ hexo deploy
```

> GitHub Page
>

## Domain Name 設定 ##

首先當然要先有 Domain Name 啦～ 設定好以後，可透過 CNAME 設定到部落格上。

另外在每次 deploy 到 Github 上時，CNAME 會一直被覆蓋，怎麼辦呢？

安裝 CNAME，在 deploy 時自動產生 CNAME 檔案

```
$ npm install hexo-generator-cname --save
```

```
$ cd source/
$ touch CNAME
$ vim CNAME # 輸入domain，EX：dexiang.tw
```


## 主題 ##

每一家的 Theme 都有長處，可依個人喜好，以下是以 github 星星數整理出來的排名。

> 1. NexT
>	
>	[https://github.com/iissnan/hexo-theme-next](https://github.com/iissnan/hexo-theme-next "star: 7303")

> 2. Yilia
> 
>  [https://github.com/litten/hexo-theme-yilia](https://github.com/litten/hexo-theme-yilia "star: 3136")

> 3. Tranquilpeak
> 
>  [https://github.com/LouisBarranqueiro/hexo-theme-tranquilpeak](https://github.com/LouisBarranqueiro/hexo-theme-tranquilpeak "940")

> 4. Yelee
> 
>  [https://github.com/MOxFIVE/hexo-theme-yelee](https://github.com/MOxFIVE/hexo-theme-yelee "848")

> 5. Jacman
> 
>  [https://github.com/wuchong/jacman](https://github.com/wuchong/jacman "743")

> 6. Maupassant
> 
>  [https://github.com/tufu9441/maupassant-hexo](https://github.com/tufu9441/maupassant-hexo "875")

> 7. Apollo
> 
>  [https://github.com/pinggod/hexo-theme-apollo](https://github.com/pinggod/hexo-theme-apollo "814")

> 8. Icarus
> 
>  [https://github.com/ppoffice/hexo-theme-icarus](https://github.com/ppoffice/hexo-theme-icarus "789")

> 9. Material
> 
>  [https://github.com/viosey/hexo-theme-material](https://github.com/viosey/hexo-theme-material "1236")

> 10. Fexo
>  
>  [https://github.com/forsigner/fexo](https://github.com/forsigner/fexo "646")


我選用的是 `Yilia Theme`




## 常見問題 ##

1. 修改配置時需注意 `YAML` 語法，參數冒號後 (:) 一定要留一個空格
2. 所有問題請轉成 UTF-8 格式