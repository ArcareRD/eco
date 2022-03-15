---
layout: page
title:  "雲端虛擬機架構建議"
date:   2022-03-15 09:22:00 +0800
lang: zh_TW
---

## 版本

|最後更新日期|備註|
|:--:|:--:|
|2022-03-15|初版|

## RTE - 運行平台 (Run Time Environment)雲端虛擬機設定建議

|項目|AP伺服器|DB伺服器(或AP + DB)|備註|
|:-:|:-|:-|:-:|
|CPU|2 core以上|4 core以上||
|記憶體|至少8G以上|至少16G以上||
|OS硬碟|優化/進階SSD IPOS至少500以上(100MBs) 剩餘容量50G以上|優化/進階SSD IPOS至少500以上(100MBs) 剩餘容量50G以上||
|DB DATA硬碟||優化/進階SSD IPOS至少1100以上(125MBs)||
|伺服器作業系統|Microsoft Windows Server 2012 以上版本|Microsoft Windows Server 2012 以上版本||
|資料庫||Microsoft SQL Server 2012 以上版本|建議採用含MSSQL影像檔建立|
|Excel|Microsoft Excel 2007~2016||安裝IRIS系統才需要|

## 效能提升方式建議

|AP伺服器|DB伺服器(或AP + DB)|備註|
|:-|:-|:-:|
|以CPU 1code + 記憶體4g配對升級|以CPU 2code + 記憶體8g、DATA磁碟IPOS 1000配對升級|配對升級提供最佳資劉流暢度|