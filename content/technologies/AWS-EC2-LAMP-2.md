---

title: AWS EC2 LAMP (2)
categories:
  - tech
tags:
  - AWS
  - EC2
  - LAMP
  - Apache
  - PHP
  - MySQL
date: 2016-10-18 00:00:06

---

上一篇介紹了如何建置 LAMP 環境，這篇要來介紹如何建立一個網頁服務的相關設定

## Domain name

想到網頁當然第一個想到的是網址也就是 Domain name
我用的是 godaddy，到上面去設定 A Record 就可以了

## Apache 設定

若是有需要在一台機器上設定多個網站，那麼就用 virtualhost 吧

### virtualhost

建立預存放目錄

```zsh
# XXX 表示專案名稱
$ mkdir /var/www/workspace/XXX
```

<!-- more -->

修改 Apache 設定

```zsh
$ vi /etc/httpd/conf/httpd.conf
```

```
# XXX 專案
<VirtualHost *:80>
    ServerAdmin administrator@mail.com
    ServerName XXX.domain.com
    ServerAlias domain.com

    DocumentRoot "/var/www/workspace/XXX"
    <Directory "/var/www/workspace/XXX">
            AllowOverride All
            Options FollowSymlinks MultiViews
            Require all granted
    </Directory>
</VirtualHost>
```

重啟 Apache

```zsh
$ service httpd restart
```

## phpMyAdmin
若是需要由網頁來 access MySQL，phpMyAdmin 不失為一個選擇
我自己是下載 phpMyAdmin-4.4.11-all-languages.tar.xz

解壓縮

```zsh
$ tar -Jxvf phpMyAdmin-4.4.11-all-languages.tar.xz
```

變更檔名

``` zsh
$ mv phpMyAdmin-4.4.11-all-languages phpMyAdmin
```

移動檔案

```zsh
$ cp -r phpMyAdmin /var/www
```

設定 phpMyAdmin

```zsh
$ cp config.sample.inc.php config.inc.php
$ vi config.inc.php
```

```PHP
$cfg['Servers'][$i]['auth_type'] = 'http';
```

修改 Apache 設定

```zsh
$ vi /etc/httpd/conf/httpd.conf
```

```
Alias /phpMyAdmin "/var/www/phpMyAdmin"
```

重啟 Apache

```zsh
$ service httpd restart
```