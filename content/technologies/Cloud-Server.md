---

title: 雲端主機
categories: 
  - tech
tags: 
date: 2016-12-10 00:33:06

---

之前有一大段時間都把服務放在 AWS 的 EC2 上，但最近在整理環境的時候開始思考，以我的需求有需要把服務放在 EC2 上嗎？ 就開始研究相關的服務，查了一些文章及同事的推薦，就想說把這些訊息分享出來。

## 虛擬主機

若是有玩過虛擬機的人，例如 VMware、VirtualBox 這些東西，其實原理是一樣的。虛擬主機就像大通舖一樣，一群人要一起共用設施，床位也可能因為旁人的影響而限縮，但優點就是便宜。

## VPS

VPS 是 Virtual Private Server 的縮寫，就是在一台機器上以軟體的方式模擬成多台機器，讓這些機器能分享CPU、記憶體、硬碟…等硬體資源，並各自運作不同的程式，不互相干擾。VPS 就像套房一樣，有獨立的衛浴及設施，相對的價格比較高。

目前 VPS 的技術比較常見的兩種，分別為 Xen 跟 OpenVZ，兩者使用的虛擬技術不太一樣，OpenVZ 的每一台虛擬機的資源由 OpenVZ 動態控制著，共用著所有的 kernel，實體上來說，每一部虛擬機器並不是真的擁有自己的資源 ( CPU、記憶體...)；而 Xen 則是以模擬硬體的方式，讓每部虛擬機器擁有自己的各種硬體環境，所以，每部虛擬機器是完全獨立的，一旦分到多少的資源，就是多少，不像 OpenVZ 那樣可以動態的調整，因此，採用 XEN 的電腦所能夠分割出來的虛擬機器數量，因為被固定住資源，所以，可能會比較 OpenVZ 來的少。

<!-- more -->

## 主機代管 / 實體主機

其實 VPS 的需求對我來說已經很夠用了，但是若是需要考慮到安全和擴充性可以再往上考慮主機代管或實體主機的方案，這兩個方案可以由自己的需要來擴充設備，不同於 VPS 來說，是真正獨立的資源。若 VPS 是租房，那麼這方案就是買房了，可以完全由自己決定要甚麼樣的建築及結構。

## EC2

VPS 的一種，採用 Xen 技術，與一般的 VPS 不同的是它的彈性很大，有不同的 region 可供選擇，且依照小時來計價，更有彈性。

另外，在 2016/11/30 Amazon 也開始有平價 VPS 供選擇：[Amazon Lightsail](https://amazonlightsail.com/ "Amazon Lightsail")，一個月最低 5 美元，第一個月免費。

<!--

參考連結：
什麼是VPS? 使用VPS有什麼好處嘛?
https://coder.tw/?p=4526

架站更上一層樓，我推薦的五個虛擬專屬主機（VPS）服務
https://free.com.tw/sign-up-vps-hosting/

【美國主機】共享主機、VPS、專屬主機的差別
http://gordon168.net/shared-hosting-and-vps-and-delicated-hosting.html

雲端服務與虛擬主機之比較(一)
https://coolman911.wordpress.com/2010/04/02/%E9%9B%B2%E7%AB%AF%E6%9C%8D%E5%8B%99%E8%88%87%E8%99%9B%E6%93%AC%E4%B8%BB%E6%A9%9F%E4%B9%8B%E6%AF%94%E8%BC%83%E4%B8%80/

阿正老師教你免費玩Amazon EC2雲端主機(下篇)：主機實戰篇
https://pcrookie.com/?p=824

什麼是雲端服務？阿正老師教你免費玩Amazon EC2雲端主機！(上篇)
https://pcrookie.com/?p=823

主機方案選擇分析與比較
https://host.com.tw/%E4%B8%BB%E6%A9%9F%E6%96%B9%E6%A1%88%E9%81%B8%E6%93%87%E5%88%86%E6%9E%90%E8%88%87%E6%AF%94%E8%BC%83

AWS launches Amazon Lightsail
http://venturebeat.com/2016/11/30/aws-vps/
-->

