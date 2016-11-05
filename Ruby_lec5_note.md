----------------lec5------------------

#作業講解
4.找出array中非字串
[].select(|x|x [].class != String)


6.arr = [1,2,3,3].uniq
=> [1,2,3] 但保留原始 arr
[1,2,3,4].uniq!
=> [1,2,3] 不保留原始 arr

#MVC 架構
1. Model 封裝資料與商業邏輯，與資料庫裡的資料表對應
2. View 處理使用者介面，顯示及編輯表單，可內嵌Ruby語法
3. Controller 負責將資料送進送出Model，處理從外界 (也就是瀏覽器) 來的HTTP Request請求，與Model互動後輸出View (也就是HTML)

＃早期網頁都沒有JS，透過php夾雜在html裡頭去做邏輯判斷與資料庫連結
＃rails的view特別之處在於能嵌入ruby程式碼
＃桌機跟網路服務差別，網頁不會自動跟新資料(http協定)
＃後端(controller & model)
＃controller決定要CRUD哪個動作，根據路由(Routing)規則決定派往哪一個Controller
 的 Action，類似於MEAN的app.js

Model File
和資料庫的資料表相對應的抽象類別，和其他資料表的關聯、行為、商業邏輯等
都是在這裡定義或處理

View File
HTML頁面，顯示為主

Controller File主要的功能：
1. 收集 request 的資訊，例如 使用者傳進來的參數
2. 操作 Model 來做資料的處理
3. 回傳 response 結果


#rails scaffold 訂便當系統
＊db:migrate 自動產生資料表
＊http://localhost:3000/rails/info/routes=>routes所有介紹
＊routes.rb此專案最主要的檔案，http請求後給予相對應回應檔案，Rails 專案的路由
都是在這裡設定
＊取資料get 產生資料post
＊任何一個controller都是class
＊[model]
skinny constroller, fat model
商業邏輯該放哪？ruby習慣放在model，con越小越好，處理CRUD就好
＊ruby的html為.erb，代表可以嵌入ruby語言的html


$bundle install 
=> 確保相關package安裝，並且不用再裝舊或新pcakage版本
=> 類似MEAN的npm install
gem.file 紀錄需要的package 類似node 的.json檔

#rails 專案步驟
1. $rails new "my_app_name"
2. 安裝執行這個專案需要的 gem: $ bundle install

#拿到一個專案先看三個檔案(Rails 專案裡一些重要的設定檔)
config/database.yml => rube預設是sqlite資料庫，輕量化版本的資料庫，也避免遇到環境難建立的
config/routes.rb => 看有哪些功能(function)
Gemfile => dependency

#Active Record
把資料表物件化，讓開發者不須使用 SQL 語法，直接用熟悉的 Ruby 於法操作資料
它就是 SQL 語言與 Ruby 語言的翻譯官
CREATE  -  Order.create(name: "Bob", description: "hamburger")
READ      -  讀取資料
UPDATE - Order.find(1).update(description: "sandwich")
DELETE  - Order.find(1).destroy

#rail console
類似 irb，不過只屬於一個專案的環境
可在裡面測試 ActiveRecord
$rails console

//裝sqlite browser

class method => 整體 v.s instance method => 單一

#提醒，git上傳
縮排兩格，sublime=>space 2
命名方式：蛇底式寫法
變數命名：instace var => @ 、class var => @@
class是工廠

----------------lec6------------------
#[手動打造Action]
1. 產生＆編輯 migration 檔案
$rails generate migration add_users_table
$rails g migration create_order
2. 執行 rake db:migrate 改變資料庫
3. 建立和該 table 相對應的 model 檔
4. 寫出 Controller 檔案，宣告 action
5. 在 routes.rb 裡設定路由
6. 產生 view 所需要的 html.erb 檔案

在rails中資料表名稱永遠是複數
[migration]
透過ruby去寫SQL語法，並創造資料表
rake db:migrate 
schema_mygration:記錄資料表版本創造時間，再次run rake db:migrate時什麼事情都不會發生(已經被記錄了)
#可以把 migration 檔看成是 db schema 的版本控制
activeRecord專門處理rails與資料表溝通
schema.rb：所有migration檔案的加總

# 記得做install budle
資料表才會連結成功

post創造資料
new產生空表單，物件思考，後端產生空物件給前端填資料再傳到後端建立出來

#Rails delete table
rails g migration DropTablename

migration檔輸入：
  def up
    drop_table :tablename
  end

rake db:migrate

#檢查model檔案的方法
$ rails console
'datebase_name'.all


#rails檔案命名的嚴謹性
model命名方式一定要是單數，不能亂命名(物件觀念)
tableize可以幫忙檢查
ex "monkey".tableize

#controllcer
#view
1.建立新資料夾，名稱為 'datebase_name'
2.產生html.erb檔案，名稱為 'function_name'.html.erb

[腳本語言]
依序執行下來
不像JAVA或是C

db migrate ：

#[DB]
DB是網頁設計的基石
DB Schema為資料庫藍圖

#關聯
＃一對多
user <-> order(取得foreign_key:user.id)
has_many <-> belongs_to :user

＃多對多
1.has_many :through
By join table:記錄兩個table的多對多關係
EX:doctor <-> appointment(join table) <-> patient
has_many :appointments
has_many :patients, through: :appointments
<-> 
belongs_to :physician
belongs_to :patient
<-> 
has_many :appointments
has_many :physicians, through: :appointments

2.has_and_belongs_to_many
join table model file(migration file)取名為：databestTable1_databestTable2
model不需要另外有join table
缺點：缺乏彈性，不能在放其他欄位資料

rails 指令建立關係
Physician.first.patients << Patient.first ('<<':array push) 

#關聯驗證[相對單複數要注意]
我可以透過 user 搜尋到 orders
user.orders
也可以透過 order 搜尋到 user
order.user
*其他寫法
User.find(1).orders


#Active Record Query Interface
#all找尋全部資料
'databaseTable_name'all
# find 是透過資料的 id 搜尋
user = User.find(1) #尋找 users 資料表裡 id 為 1 的 record
資料表間關聯查詢
#'One_databaseTable_name'.find(primary id).'Other_databaseTable_name'
Example: User.find(4).orders
# where 是透過給訂的條件搜尋
result = User.where(name: "bob") # 會回傳一個有一或多筆 user 的陣列
# ActiveRecord 會有內建的搜尋方法，find_by_
bob = User.find_by_name("bob")
find_by_ 只會回傳符合條件的第一筆資料，請小心使用

#檢查資料庫資料
gem 'awesome_print'
$ bundle instal
$ rails c
ap 'datebase_name'.all

#[功課]
產生留言板migration file、model:association

#問
[debendo]
[scaffold 指令] => 鷹架之一
git commit -m "first commit" ， commit就是將某些檔案正式納入git監控，"first commit"
為對這些監控檔案進行的描述訊息
rails g scaffold order name:string phone:string description:text，
這份order需要哪些欄位加以定義schema






