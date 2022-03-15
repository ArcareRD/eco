---
layout: page
title:  "安裝說明"
date:   2022-03-15 09:22:00 +0800
lang: zh_TW
---

## 版本

|最後更新日期|備註|
|:--:|:--:|
|2021-09-22|改版|
|2022-03-15|改版|

## RTE - 運行平台 (Run Time Environment)

### 設備建議

|品名|內容|備註|
|:-:|:-|:-:|
|CPU|Intel 4 core以上||
|記憶體|至少8G以上、建議16G||
|硬碟|SSD / HD IO速度至少500MBs以上 剩餘容量50G以上||
|伺服器作業系統|Microsoft Windows Server 2012 以上版本||
|用戶端作業系統|Microsoft Windows 8 以上版本||
|資料庫|Microsoft SQL Server 2012 以上版本||
|Excel|Microsoft Excel 2007~2016|安裝IRIS系統才需要|

## 程式安裝路徑建議

* 1. 作業系統單獨使用磁碟、保持至少25 ~ 50G空間
* 2. RTE可以安裝於系統磁碟(如需要較佳效能、則建議獨立磁碟)
* 3. RTE相關暫存路徑可與RTE主程式安裝路徑相同(如需要較佳效能、則建議獨立磁碟)
* 4. 資料庫資料檔使用獨立磁碟存放
* 5. 資料庫交易檔可與資料庫資料檔放於同一磁碟(如需要較佳效能、建議獨立磁碟)
* 6. 如需較佳效能建議AP伺服器與DB伺服器分開建立

### 雲端架構建議

* [雲端架構建議](CLOUD.html)

### 文件下載
* #### [下載[運行環境系統需求表]文件](運行環境系統需求表V3.02.pdf){:target='_blank'}

### 安裝流程
* #### [平台基礎套件安裝](RTE/PACKAGE/README.html)
* #### [專案安裝](RTE/PROJECT/README.html)

## MAE - 行動運行台 (Mobile Application Environment)

### 設備建議

|系統類別|系統版本|備註|
|:-:|:-:|:-:|
|IOS|IOS 11 以上||
|Android|Android 7.1 以上||

### 安裝路徑

| IOS | Android |
|:-:|:-:|
| [![alt APP Store](img/mae-logo-ios-30.png)](https://apps.apple.com/us/app/id1489699152) | [![alt APP Store](img/mae-logo-android-30.png)](https://play.google.com/store/apps/details?id=com.arcare.ruru.smarr)  |