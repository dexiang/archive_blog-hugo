---

title: 刪除 .DS_Store 隱藏檔
categories: 
  - tech
tags:
  - MacOSX
  - git
date: 2017-06-17 16:50:20

---


最近新買了一台 NAS，在連線的時候常常會發現多了 .DS_Store 這個隱藏檔，平常在 Mac 上倒是無所謂，但是出現在 NAS 裡就覺得煩人了

## DS_Store ##

.DS_Store (Desktop Services Store) 是一種 Mac OS X 作業系統所創造的隱藏文件，目的在於存貯目錄的自定義屬性，例如文件們的圖標位置或者是背景色的選擇。

## 刪除 DS_Store ##

刪除當前目錄下的 `.DS_Store` 檔案（包含子目錄）：

```
$ find . -name ".DS_Store" -depth -exec rm {} \;
```

刪除系統上所有 .DS_Store 檔案：

```
$ sudo find / -name ".DS_Store" -depth -exec rm {} \;
```

## 自動產生 DS_Store ##

關閉系統自動產生 .DS_Store 的服務

```
$ defaults write com.apple.desktopservices DSDontWriteNetworkStores true
```

恢復自動產生 .DS_Store 的服務

```
$ defaults delete com.apple.desktopservices DSDontWriteNetworkStores
```

### Git & .DS_Store ###

另外在使用 git 時也會遇到 .DS_Store 追蹤，這裡也記錄一下解法

可使用 `git rm -f` 來移除掉特定的檔案

```
$ git rm -f *.DS_Store
```