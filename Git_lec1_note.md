###[前言]
經常在寫程式時遇到需要恢復原本程式狀態      
軟體發⾏，需要分成維護版跟開發版



[版本控制]
可以隨時復原修改，回到之前的版本  
多⼈協作時，不會把別⼈的東⻄蓋掉  
保留修改歷史記錄，以供查詢
軟體發⾏時，可以⽅便管理不同版本



###[What is git?]
一個開放源碼的版本管理系統(VCS)
發明⼈ Linus Torvalds (Linux creator)
*厲害的工程師都時也是軟體發明者*
git無論在local或remote都能進行版本控制

###[What is github?]
一個基於 git 開發出來的服務  
讓你能透過 git 在遠端備份程式碼
一般的使用免費但必須公開程式碼
廣受大量開源專案的喜愛
是程式設計師的寶庫 (可以在裡面查詢各式各樣的程式與實作的程式碼)

###[git安裝]
win:git cm windows
####$ git config --list 確認有無安裝成功

###[Repository (儲存庫)]
建立儲存庫的方式有很多種，最簡單的方式就是在切換到放置程式碼的路徑下，輸入：
####$ git init
要針對一個project進行控管就到其母資料夾

####cmd指令縮寫說明
mkdir: make directory
cd: change directory
pwd: print working directory

####git指令說明
git init:控管此路徑下檔案
ls -a:呼叫出所有路徑下檔案(包含隱藏檔案)









