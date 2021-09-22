---
layout: post
title:  "歡迎光臨如如智慧軟體機器人世界"
date:   2021-09-22 11:00:00 +0800
categories: jekyll update
---

# ruRU 智慧軟體機器人
它是一個創新的企業軟體機器人 PaaS 服務，提供企業軟體的開發設計以及維護的平台服務

軟體正在驅動整個世界，企業的運行需要大量的系統軟體， "ruRU"智慧軟體機器人的服務能提供企業快速、品質穩定、可長期維運的系統，並且協助企業有限的 IT 資源做最優化的配置，"ruRU"智慧軟體機器人將是所有企業邁向成功的標準配備。


# ruRU軟體機器人平台技術簡介
- [ruRU軟體機器人平台架構](#Introduction-1)
- [ruRU軟體機器人平台各功能模組說明](#Introduction-2)
- [ruRU軟體機器人平台之技術規格](#Introduction-3)
- [ruRU軟體機器人平台之硬體規格](#Introduction-4)


	
## ruRU軟體機器人平台架構 {#Introduction-1}
![](/img/Introduction-1.png)

## ruRU軟體機器人平台各功能模組關聯圖 {#Introduction-2}
![](/img/Introduction-2.png)

----
## ruRU軟體機器人平台各功能模組之功能說明
### 1. IDE (Integrated Design Environment 設計台)
- 提供Web base的GUI圖形化操作介面，讓系統分析師或領域專家，針對Web/APP資料庫應用系統之需求，不用撰寫程式，直接透過拖拉及設定的方式，進行版面、表單欄位/按鍵規格、及資料庫結構之設計
- 針對設計出來的表單或系統，提供打樣、檢錯功能
- 針對設計出來的表單或系統，提供測試及預覽運行操作畫面之功能
- 可產生Word形式的系統需求規格文件或系統設計規格文件
- 將通過檢錯打樣之系統進行發行以產生安裝包(Install Pack)
- 提供多個企業的多個應用系統在同一IDE設計台同時進行設計之管理功能，包含
- 規格設計：依據軟體系統需求，透過IDE設計介面，以結構化方式定義軟體規格
- 站台管理：提供站台管理員(Site Manager)新增/維護在此IDE設計台上的各個企業管理員帳號
- 企業管理：提供各企業管理員新增/維護企業內的各帳號
- 授權管理：針對企業內的各IDE帳號進行權限管理
- 身分驗證：針對登入IDE設計台的帳號/密碼進行驗證

### 2. FMS (Factory Management System 管理中心)
- 專案管理：負責IDE中各專案資訊之管理
- 發行管理：負責將IDE發行需求分派給適當的AMS軟體工廠去執行

### 3. AMS (Assembly Management System 軟體工廠)
- 負責將FMS轉來的發行需求，運用軟體工廠的各軟體機器人轉譯為應用系統

### 4. RTE (Run Time Environment 運行台)
- 3-Tier三層式Web資料庫應用系統架構
- 提供運行台[執行引擎]讓軟體機器人所產出的應用系統在其上運行
- 提供各應用系統運行時的一些[共同服務]，包含程式設定、API設定、排程服務、郵件發送、推播通知等
- 提供應用系統運行時的應用系統管理功能，包含
	- 系統資訊：組織資訊、應用系統執行時所需相關資訊等
	- 系統管理：API管理、圖示管理、檔案管理、推播通知管理等
	- 授權管理：標準帳號授權模式、整合式單一簽入模式、及支援應用系統物件授權管理等
	- 異常管理：當應用系統運行異常時會提供錯誤訊息及錯誤代碼、即快速封裝與回報機制、以供系統管理者做為障礙排除之參考
- 提供多個企業的多個應用系統在同一運行台運行之管理功能，包含
	- 站台管理：提供站台管理員(Site Manager)新增/維護在此運行台上的各個企業管理員帳號
	- 企業管理：提供各企業管理員新增/維護企業內的各帳號
	- 身分驗證：針對登入運行台的帳號/密碼進行驗證，並支援與AD Server整合執行單一帳號登入Single Sign On (SSO)
	- 維運管理：線上使用者的服務與管理、推播通知服務與管理、系統排程服務管理、稽核管理、系統安裝與更新等

### 5. MAE (Mobile Application Environment 行動裝置運行台)
- 提供運行台[執行引擎]讓軟體機器人所產出的應用系統在其上運行
- 提供各應用系統運行時的一些[共同服務]，包含伺服器指定、程式設定、推播通知等
- 與 RTE的站台管理採同架構

---- 

## ruRU軟體機器人平台之技術規格 {#Introduction-3}
### 1. IDE設計台 
- 技術架構：Microsoft .Net Framework
- 資料庫：MS SQL

### 2. FMS管理中心
- 技術架構：Java
- 資料庫：MS SQL

### 3. AMS軟體工廠
- 技術架構：Java
- 資料庫：MS SQL

### 4. RTE運行台
- 技術架構：Java
- 資料庫：MS SQL
 
### 5. MAE APP
- 技術架構：Flutter

---- 

## ruRU軟體機器人平台之硬體規格 {#Introduction-4}
* #### [檔案下載](/INSTALLS/運行環境系統需求表V3.01.pdf){:target='_blank'}
 
### A. 伺服器軟硬體需求
1. CPU(中央處理器)：Intel 4核心處理器，2.4GHZ或以上。若使用AWS或其它雲端主機，至少2個CPU。
2. RAM(隨機存取記憶體)：8GB、建議16G或更多
3. HDD(硬式磁碟機)：容量1TB或以上。若使用AWS或其它雲端主機，作業系統及應用程式(AP)需100GB，資料庫(DB，或RDS)部份則視需求而定。如果雲端資料庫有備份需求，則需求大小為DB硬碟空間*備份保留天數，例如DB為10GB，需保留7天備份，則備份空間需求為70GB。
4. OS(作業系統)：以下擇一
- Microsoft Windows Server 2012
- Microsoft Windows Server 2016
- Microsoft Windows Server 2019
5. DB(資料庫)：以下擇一
- Microsoft SQL Server 2012
- Microsoft SQL Server 2012 express
- Microsoft SQL Server 2014
- Microsoft SQL Server 2014 express
- Microsoft SQL Server 2016
- Microsoft SQL Server 2016 express
- Microsoft SQL Server 2017
- Microsoft SQL Server 2017 express
- Microsoft SQL Server 2019
- Microsoft SQL Server 2019 express
6. Excel
- Microsoft Excel 2007~2016

### B. 終端機軟硬體需求
1. CPU(中央處理器)：依各作業系統建議之CPU
2. RAM(隨機存取記憶體)：依各作業系統建議之RAM容量
3. OS(作業系統)：以下擇一
- Microsoft Windows 8
- Microsoft Windows 8.1
- Microsoft Windows 10
- Android 
- iOS 
4. Web browser(瀏覽器)：Chrome、Firefox、Internet Explore(僅支援11版)、Safari
5. Excel Microsoft Excel 2007~2016


