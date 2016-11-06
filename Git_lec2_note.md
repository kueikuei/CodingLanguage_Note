>github是有名的rails專案

####commit講解
一個 commit 在 Git 中就是一個節點，這些 commit的節點就是未來你可以回朔及追蹤的參考，你可以想像就像是電玩遊戲時的存檔，每一個 commit 是一次存檔，讓我們未來在需要的時候都可以回到這些存檔時的狀態。

##U r the sum of all ur training!!

####[檔案在 git 底下的四種狀態]
![File Status LifeCycle](https://s3.amazonaws.com/media-p.slid.es/uploads/406442/images/3199193/687474703a2f2f6769742d73636d2e636f6d2f666967757265732f3138333333666967303230312d746e2e706e67.png "File Status LifeCycle")

1.untracked:未追蹤的，代表尚未被加入 Git 儲存庫的檔案狀態  
2.staged:等待被 commit 的，代表下次執行git commit會將這些檔案全部送入儲存庫。新檔案透過git add後的狀態。  
3.modified:已修改的，代表檔案已經被編輯過，或是檔案內容與上一個版本內容是不一致的狀態。通常是已經做了git add後會呈現的狀態。commit完後回到unfodify狀態。  
staging_area暫存區：只有放在裡頭的檔案才能進行commit，一定要用git add才會放入暫存區。

流程的整理：
修改檔案 => 加入 stage (git add) => 提交( git commit )=> 繼續修改其他檔案

####[復原版本]
*--soft 代表銷毀 commit 但是保留 commit 內容*
*HEAD^ 代表上一個 commit (版本)*
#####git reset --soft HEAD^









