---
layout: page
title:  "平台安裝"
date:   2022-04-06 17:39:04 +0800
lang: zh_TW
---

# RTE 平台基礎套件安裝 CentOS

## 版本：

|日期|版號|備註|
|:--:|:--:|:--:|
|2022-03-30|2022030001|初版|

## 作業目的：

    在安裝系統前，必須先安裝RTE及伺服器端所需的相關套件。

## 環境需求：

|項目|內容|備註|
|:--:|:--:|:--:|
|帳號|請使用本機帳號，且該帳號具有Administrator權限||
|作業系統|CentOS 7 以上||
|資料庫版本|MS SQL 2012 以上||
|安裝套件|autodeploy.zip|下載帳號密碼請聯繫服務窗口|

## 安裝步驟：

### 基本套件安裝

1.下載安裝套件 <br>

    wget ftp://{帳號}:{密碼}@agri.ruru.tw/openjdk.zip
    wget ftp://{帳號}:{密碼}@agri.ruru.tw/tomcat-ruru.zip
    wget ftp://{帳號}:{密碼}@agri.ruru.tw/ArcareEng.war

2.解壓縮檔案於該路徑 <br>

    unzip openjdk.zip -d /opt
    unzip tomcat-ruru.zip -d /opt
    cp ArcareEng.war /opt/tomcat/webapps

3.設定環境變數 <br>

    echo "JAVA_HOME=/opt/jdk-8u201-ojdkbuild-linux-x64" >> /etc/profile
    echo "PATH=$JAVA_HOME/bin:$JAVA_HOME/jre/bin:$PATH" >> /etc/profile
    echo "/opt/tomcat/bin/startup.sh" >> /etc/rc.d/rc.local

4.指定遠端管理用IP白名單、由於管理來源基於安全必須限制，預設是本機電腦為開放遠端管理，所以需要設定來源白名單<br>

    echo "遠端管理電腦IP" >> /opt/tomcat/conf/source_list.txt
    chmod 755 /opt/tomcat/conf/source_list.txt

5.修改資料夾權限 <br>

    chmod 755 /opt/tomcat/conf
    chmod 755 /opt/tomcat/bin/*

6.重啟伺服器 <br>

    shutdown -r now

### 管理用工作站套件安裝

#### 1. 安裝Chrome瀏覽器

- [下載安裝chrome瀏覽器](https://www.google.com/intl/zh-TW/chrome)

#### 2. Tomcat設定

2-1.開啟瀏覽器，登入TOMCAT網頁(http://{伺服器IP或網址}:8080/manager)，確認TOMCAT是否正常。<br>
![alt 完成安裝Tomcat](img/007-7.jpg)

2-2.基於安全因素考量，建議Undeploy [docs] / [examples] <br>
![alt 完成安裝Tomcat](img/007-8.jpg)

2-3.Undeploy [docs] / [examples] 完成後 <br>
![alt 完成安裝Tomcat](img/007-9.png)

### 安裝RTE

1.開啟Tomcat管理視窗 (預設帳號密碼請聯絡服務窗口)<br>
![alt 完成安裝Tomcat](img/012.png)

2.按下[選擇檔案] <br>
![alt 完成安裝Tomcat](img/013.png)

3.選擇安裝檔[ArcareEng.war] <br>
![alt 完成安裝Tomcat](img/014.png)

4.按下[Deploy] <br>
![alt 完成安裝Tomcat](img/015.png)

5.完成安裝 <br>
![alt 完成安裝Tomcat](img/016.png)

### RTE環境初始化作業準備

#### 共用資料夾設定

用途說明：引擎運作時，需要一個磁碟空間來存放暫存檔案，所以需要在伺服器上規劃一個資料夾讓引擎使用。<br>

1.注意必須讓直行Tomcat程式的帳號有該資料夾讀取及寫入的完整權限。<br>

2.在伺服器任一磁碟路徑上，建立一個Share資料夾，例如：[/opt/storage/ArcareEngShare]<br>

3.如果運行的環境要使用多台AP伺服器進行負載平衡(load balance)，請於AP伺服器建立檔案目錄，並透過nfs服務掛載網路共享資料夾至該目錄，提供[共用資料夾網路路徑]設定使用。<br>

#### 資料庫設定

##### 作業說明

初次安裝RTE後，須進行資料庫設定以指定資料庫位置 <br>

##### 操作介面介紹

開啟Site資料庫設定 { http://{伺服器IP或網址}:8080/ArcareEng/SiteDatabaseSet.jsp }，進入頁面後輸入各項設定，完成後點擊右上儲存 <br>
![alt 完成安裝Tomcat](img/031.png)

###### Site資料庫區塊

輸入Server連線的SQL資料庫相關資訊，裝SQL_EXPRESS版本需注意，SQLServer名稱後面需加 [\SQLEXPRESS]且要先開啟TCP/IP相關設定才能進行此步驟 <br>

* SQL 類型：預設[MSSQL]，指定單機型SQL伺服器
* SQL Server名稱：輸入SQL Server電腦名稱
* SQL Server連接埠：輸入SQL Server連線port號
* SQL Server登入名稱：輸入登入帳號
* SQL Server登入密碼：輸入登入密碼
* SQL Server資料庫：挑選儲存Site資料的DB，預設建立 [WellWareProject]
* 資料庫備份資料夾：輸入系統更新時的自動備份路徑，例：[/opt/storage/ArcareEngDBbak]
* Table備份資料庫名稱：挑選Site資料庫的備份DB，預設建立 [WellWareProject_UPG]
* Table保留份數：輸入Site資料庫備份的份數
* 稽核Log資料庫：挑選儲存使用者操作紀錄的資料庫，預設建議 [LOGDB]
    * 註.稽核LOG資料庫有設定時，DB容量會快速累積，請隨時注意 

###### 暫存資料庫區塊

輸入SQL連線服務程式的相關設定 <br>

* 暫存資料庫設定：不勾選自訂則引擎會使用上方SQL Server設定連線，如需自訂則打勾選項並依序填寫相關連線資料 <br>
* 暫存資料庫：挑選資料庫，建議新增資料庫單獨給此功能使用，名稱建議：[TransactionCache]，此資料庫專為過帳暫存使用，日常備份不須備份此資料庫。 <br>

###### 引擎設定

* 遠端連線IpPort：Server遠端連線時的IP與PORT <br>
* 共用資料夾網路路徑：共用資料夾的網路磁碟路徑(請參考前面[共用資料夾設定]第3點)，如果沒有多台AP server架構，可設定和共用資料夾實體路徑相同即可 <br>
* 共用資料夾實體路徑：共用資料夾的實體路徑，例如 [/opt/storage/ArcareEngShare]。注意該路徑會定期清除，有需要保留的檔案請勿存放於此<br>

###### 設定Timeout資訊

輸入引擎處理各項功能時，逾期的秒數設定 <br>

* 連線資料庫(秒)：RTE與資料庫連線的逾期時間
* 執行命令(秒)：RTE執行資料庫作業的逾期時間
* 交易擁有資料的衝突鎖定(毫秒)：整個資料交易鎖定最長時間
* 交易時間(秒)：交易內單一作業逾期時間
* 匯入物件(秒)：匯入作業逾期時間

###### 設定取最大單號資訊

* 失敗重取次數：取單據號碼失敗時，重新取單據號碼的次數
* 失敗重取的間隔時間(毫秒)：每次重新取單據號碼的間隔時間

### RTE環境初始化作業

建議管理用電腦解析度至少 1300 x 1024

#### 站台激活

1. 進入管理介面 - 輸入網址【 http://{伺服器IP或網址}:8080/ArcareEng/SiteLogin.jsp 】 <br>
![alt 完成安裝Tomcat](img/022.png)

2. 預設帳戶密碼 [Admin_ArcareSite / arcare] <br>
![alt 完成安裝Tomcat](img/023.png)

3. 登入後進入設定國別/語系 <br>
![alt 完成安裝Tomcat](img/024.png)

4. 設定國別/語系 <br>

    1. 按下[載入預設]
    2. 選擇預設語系 [必要]
    3. 修改國別/語系項目
    4. 完成按[下一步]

![alt 完成安裝Tomcat](img/025.png)

5. 設定站台管理員密碼 [Admin_ArcareSite] <br>

    1. 舊密碼：預設初始密碼
    2. 新密碼：英文大小寫加數字
    3. 確認新密碼：與新密碼必須一致
    4. 完成按[下一步]

![alt 完成安裝Tomcat](img/026.png)

6. 修改站台管理員資訊 [Admin_ArcareSite] <br>

![alt 完成安裝Tomcat](img/027.png)

7. 建立中間台資訊 <br>

   中間台資訊主要是當多台負載平衡運作時指定排程有哪一台負責，避免重複執行 <br>

    1. 新增鍵：新增中間台設定值
    2. 伺服器：請使用電名稱
    3. 連接埠：8080
    4. 設定完成按下儲存鍵
    5. 選擇執行排程作業的機台
    6. 完成按[下一步]

![alt 完成安裝Tomcat](img/028.png)

8. 選擇處理排程機台後確認，請按 [確定] <br>

![alt 完成安裝Tomcat](img/029.png)

9. 指定站台名稱後，請按 [啟動完成] 完成初始化作業 <br>

    a. 站台名稱建議以中英文名，請避免使用特殊字元<br>
    b. 完成後按下[啟動完成]按鍵，完成啟動作業

![alt 完成安裝Tomcat](img/030.png)