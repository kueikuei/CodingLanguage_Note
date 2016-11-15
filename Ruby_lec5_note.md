----------------lec5------------------

####作業講解
4.找出array中非字串
[].select(|x|x [].class != String)

6.arr = [1,2,3,3].uniq
=> [1,2,3] 但保留原始 arr
[1,2,3,4].uniq!
=> [1,2,3] 不保留原始 arr

*小知識*
```ruby
arr = [1,2,3,3].uniq! #arr = [1,2,3]
#!放後面會改變原本的值  
```

**ruby方法能加?或!**  
>清楚告訴使用者大概會回傳怎樣的值  
>?回傳boolean;!代表值會改變

####提醒，git上傳
縮排兩格，sublime=>space 2  
命名方式：蛇底式寫法  
變數命名：  
instace var => @  
class var => @@  
class是工廠

###MVC 架構
1. Model 封裝資料與商業邏輯，與資料庫裡的資料表對應
2. View 處理使用者介面，顯示及編輯表單，可內嵌Ruby語法
3. Controller 負責將資料送進送出Model，處理從外界 (也就是瀏覽器) 來的HTTP Request請求，與Model互動後輸出View (也就是HTML)

＃早期網頁都沒有JS，透過php夾雜在html裡頭去做邏輯判斷與資料庫連結  
＃rails的view特別之處在於能嵌入ruby程式碼  
＃桌機跟網路MVC差別，網頁不會自動跟新資料(http協定)  
＃後端(controller & model)  
＃controller決定要CRUD哪個動作，根據路由(Routing)規則決定派往哪一個Controller
 的 Action，類似於MEAN的app.js  

##Rails MVC 架構
![Loading Fail](https://ihower.tw/rails/images/basic-mvc-diagram.png "rails mvc")  
1. 瀏覽器發出HTTP request請求給Rails  
2. 路由(Routing)根據規則決定派往哪一個Controller 的 Action  
3. 負責處理的 Controller Action 操作 Model 資料
4. Model 存取資料庫或資料處理  
5. Controller Action 將得到的資料餵給View樣板  
6. 回傳最後的 HTML 成品給瀏覽器


Model File
和資料庫的資料表相對應的抽象類別，和其他資料表的關聯、行為、商業邏輯等
都是在這裡定義或處理

View File
HTML頁面，顯示為主

Controller File主要的功能：
1. 收集 request 的資訊，例如 使用者傳進來的參數
2. 操作 Model 來做資料的處理
3. 回傳 response 結果


###rails scaffold 訂便當系統

**scaffold鷹架指令：**
```terminal
$rails g scaffold order name:string phone:string description:text
```

**scaffold做了什麼？**  
>產生諸多CRUD新檔案
>>網頁運作，就是把CRUD URL與背後邏輯實做出來   
>routes.rb  
>>resource:orders  
>>>自動產生整個CRUD function  
>>>>觀念:
>>>>>post跟new綁在一起  
>>>>>edit跟update綁在一起     
![Loading Fail](http://www.weijieworld.com/wp-content/uploads/2015/02/screen-shot-2015-02-24-at-4-02-00-pm.png "rails CRUD")

**rails routes URL 定義**  
**route file**
```ruby
#route
get 'orders/index' => 'order#index'

#controller
def index
    @order=Order.all
end
```
＊routes.rb為專案最主要的檔案，http請求後給予相對應回應檔案，Rails 專案的路由
都是在這裡設定  
＊routes info:http://localhost:3000/rails/info/routes  
>也可在 terminal 裡輸入 rake routes 查詢

＊取資料get 產生資料post

**controller file**  
**controller功能**  
1. 收集 http request 的資訊，例如:使用者傳進來的參數  
2. 操作 Model 來做資料的處理  
3. 回傳 response 結果  

繼承ApplicationController
 
**modelfile**
**model功能**  
和資料庫的資料表相對應的抽象類別，和其他資料表的關聯、行為、商業邏輯等都是在這裡定義或處理

**Active Record**
>翻譯官:Ruby的ORM(對映射關聯式資料與物件資料)
>>SQL<->ruby
**把data table物件化，讓開發者不須使用SQL語法，直接用熟悉的Ruby語法操作資料**
>order table經過ActiveRecord後是一個class

| CRUD      |          功能           |
|-----------|:----------------------:|
| CREATE    |         新增資料         |
| READ      |         讀取資料         |
| UPDATE    |         編輯資料         |
| DELETE    |         刪除資料         |

CREATE  -  Order.create(name: "Bob", description: "hamburger")  
READ    -  Order.all 
UPDATE  - Order.find(1).update(description: "sandwich")  
DELETE  - Order.find(1).destroy

**rail console**
>類似irb，不過只屬於rails專案的環境
>**可在裡面測試 ActiveRecord**
>>$rails console
>>>Order.all
>>>Order.all.find()

*skinny constroller, fat model*
>商業邏輯該放哪？ruby習慣放在model，controller越小越好，處理CRUD就好

**html.erb file**
＊ruby的html為.erb，代表可以嵌入ruby語言的html
```ruby
#controller
def index
    @order=Order.all
end

#html.erb
<tbody>
    <% @orders.each do |order| %>
      <tr>
        <td><%= order.name %></td>
        <td><%= order.phone %></td>
        <td><%= link_to 'Show', order %></td>
        <td><%= link_to 'Edit', edit_order_path(order) %></td>
        <td><%= link_to 'Destroy', order, method: :delete, data: { confirm: 'Are you sure?' } %></td>
      </tr>
    <% end %>
</tbody>
```

$bundle install  
>確保相關package安裝，並且不用再裝舊或新pcakage版本  
>類似MEAN的npm install  
>gem.file 紀錄需要的package 類似node 的.json檔

###rails 專案建立步驟
1. $rails new "my_app_name"  
2. 安裝執行這個專案需要的gem: $ bundle install  
  
rails framwork也是由其他諸多framwork共同建立起來  
必須要depend on其他套件=>由GemFile記錄=>$bundle install  
>What is bundler?  
>>Gem依存性(dependencies)管理工具
會根據 Gemfile 的設定自動下載及安裝 Gem 套件
在團隊開發時，維持開發者之間套件版本的一致性

#####Rails 專案裡一些重要的設定檔
config/database.yml => ruby預設是sqlite資料庫，輕量化版本的資料庫，避免遇到麻煩的環境設定
>gem sqlite3:rails跟sqllite的接口

config/routes.rb => 查看支援哪些功能(function)
Gemfile => dependency  
>Gemfile.lock:不要隨便動它。
>>裝sqlite browser檢驗DB資料

class method => 整體   
instance method => 單一










