##[使用者認證]
網頁需要辨識使用者身份，查看該使用者是否有權限能做某些事或使用某些功能

##[session]
1.HTTP 溝通協定不會記住使用者狀態 (登入狀態，購物車內容 etc.)  
2.Server 與 Client 之間不是一直保持連線  
3.為了讓 browser 能跨 request 記住資訊，使用 session 來儲存資訊  
4.session 資訊是由 server 端產出  
5.為了使用者體驗，*session 資訊通常會放在 cookie 裡面*    
6.cookie 是 *browser 的暫存空間，只有 4k 的大小*

使用者輸入user id後，server會產生token暫存在客戶用戶端  
切換頁面時，user browser會自動將cookie的id再傳回server自動進行登陸

使用者認證功能  
rails內建功能
*has_secure_password validation: false* 
has_secure_password 會要求輸入兩次密碼故透過validation: false關掉

session沒有model但是session controller也可以當成物件
登入時創造一個新的session  
link_to是產生超連結  
gem'bcrypt':今天存在db的密碼是經過加密的密碼(安全性)  
devise go  
*付費有時是最省事的方法*  
||=：左邊變數當下是空值就將右邊結果存入左邊變數  
!放後面或前面：前面兩個!!代表把變數變成boolean(只要不是nil)

####[小提醒]
不要把太複雜的前端判斷式語法用ruby去寫  
其仍然要把ruby轉換為JS去進行操作。









