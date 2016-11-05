#小知識
irb管ruby
rails consle管rail

#rails db 查詢技巧
＊搜尋某一筆
find.by
ex DBTable_find_by_name("Bob")

＊搜尋多筆
where

#Validation
"永遠不要相信前端傳來的東西"
SQL很難debug => How to deal with it?
將邏輯判斷寫在應用程式端(application)=>Model層面(好處：不用考慮資料庫總類、與資料庫直接做連結)
最好作法千端也後端也寫

#ruby in HTML
Controller
```ruby
def new
    # Order為order class，對應到Order Model，對應到資料表的
    # Order Table，產生出一個新的Order物件並存到order實例變數
    
    @order = Order.new
end
```

new.html.erb
<!-- 三行code如何變成這麼多東西？
Ruby轉換而成... -->
<h1>New Order</h1>
<!-- form為封包，將固定的html寫成此form封包
render 為呼叫此封包 -->
<%= render 'form', order: @order %>
<%= link_to 'Back', orders_path %>

#form.html.erb
噴錯為一個error array
<!-- f.label產生一個前端的label
f.text_field將輸入的東西綁定:name -->
```html5
<div class="field">
    <%= f.label :name %>
    <%= f.text_field :name %>
</div>
```

#Create Method
Post對應到Order#create
針對不同需求(前端或其他)傳遞不同類型資料(HTML or JSON)

###order_params
將前端資料層層過濾，只允許name、phone、description等資料能傳進資料庫

#用bind.pry去偵錯
Gemfile->gem:'pry'
打包成params 
params[:order]
=> <ActionController::Parameters 
{"name"=>"123123", "phone"=>"12", "description"=>"212"} permitted: false>

params.require(:order)
=> <ActionController::Parameters 
{"name"=>"123123", "phone"=>"12", "description"=>"212"} permitted: false>

 params.require(:order).permit(:name)
Unpermitted parameters: phone, description
=> <ActionController::Parameters {"name"=>"123123"} permitted: true>

層層過濾，最後存到新的@order物件

new為顯示空表
create為填好資料要把資料寫入資料庫時

# edit 與 update


#View Partial (局部樣板)
重複執行的程式碼打包起來
```ruby
before_action :set_order, only: [:show, :edit, :update, :destroy]
#<->before_action :set_order, except: [:index, :new, :create]

def set_order
      @order = Order.find(params[:id])
end
```

[作業]
留言板驗證做完
挑戰:show、index做出來


















