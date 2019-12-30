---

title: AWS EC2 LAMP (1)
categories:
  - tech
tags:
  - AWS
  - EC2
  - LAMP
  - Apache
  - PHP
  - MySQL
date: 2016-10-17 00:33:06

---

使用 Linux 架設 web server，LAMP 是非常常用的選擇，LAMP 代表 Linux + Apache + MySQL + PHP，當然還有很多的組合，像是 LNMP (Linux + Nginx + MySQL + PHP) 等等的搭配，但這篇就先針對 LAMP 做介紹。

首先這篇採用 EC2 主機搭配作介紹，皆用 yum 安裝。

在安裝過程中因權限的關係，以下皆是以 root 的身分。

## 安裝 LAMP

### yum

查詢是否有安裝yum

```zsh
$ rpm -qa | grep yum
```

<!-- more -->

更新所有已安裝的套件 (-y 表示安裝更新時不跳確認提示)

```zsh
$ yum update -y
```

### Apache、PHP、MySQL

安裝 Apache、PHP、MySQL

```zsh
$ yum install -y httpd24 php56 mysql55-server php56-mysqlnd php56-mbstring
```

修改 php.ini

```zsh
$ vi /etc/php.ini
```

```INI
; PHP tag 簡寫 (應該是要保持關閉的....，但因為有些 legacy code，慚愧...)
short_open_tag = On
; 時區
date.timezone = Asia/Taipei
; 最大上傳檔案大小
upload_max_filesize = 50M
```

啟用服務

```zsh
$ service httpd start
$ service mysqld start
```

設定 mysql 管理者密碼

```zsh
# XXXX 表示密碼
# 設定密碼
$ mysqladmin -u root password 'XXXX'
# 修改密碼
$ mysqladmin -u root -p password 'XXXX'
```

設定開機時啟用

```zsh
$ chkconfig httpd on
$ chkconfig mysqld on
```