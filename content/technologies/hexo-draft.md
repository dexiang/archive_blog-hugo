---

title: Hexo 草稿
categories: 
  - tech
tags:
  - hexo
  - draft
date: 2017-02-02 19:08:43

---


在寫部落格的時候常常會因為篇幅過大沒辦法一次編寫完成，或是同時編寫多篇文章，這時候就會希望不要把這些文章發佈出去。

### 建立草稿 ###

```
$ hexo new draft <title>
```

Hexo 建立草稿後會產生檔案在 `source/_drafts` 下，在這目錄之下的文件不會被發佈出去。

### 預覽草稿 ###

那若是我想要看看我編輯的文章要怎麼辦呢？Hexo 提供了下面的方法：

```
$ hexo server --draft
```

### 發佈草稿 ###

```
$ hexo publish <file>
```
※ file 不包含副檔名
