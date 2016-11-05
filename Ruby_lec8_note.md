[前言]
[我是這樣學會 Ruby on Rails：12 個星期打造 12 個網頁 APP]
看每個人知識背景狀況，不見得這就是好方式。
真正厲害的人：keep learning!!!keep practicing!!!刻意去練習。例如打造四個網站但是用的技術都不同、永遠都要挑戰自己沒做過的東西。

[gem 都被安裝到了哪裏？]
bundle show 'bootstrap'
 顯示是否有沒有裝成功
bundle show --paths
copy paths 貼到 find => 但小心別亂改



#[打造view partial]
#統一顯示的frame
create:_title.html.erb 
```html
<h1><%= title %></h1>
```
new.html.erb
```html.rails
#view partial 就像是一個 method，是可以允許呼叫者丟參數進來
<%= render 'title', title:'New Order' %>
```
index.html.erb
```html.rails
<%= render 'title', title:'訂單列表' %>
```

form_for跟一個物件綁定
所有的erb都是patial

#再看錄影複習
#[Url Helper] 
把url打包成變數或說metohd
url_helper 簡化了我們的程式碼，用 ruby 變數的方式指向原本複雜的 url
不止被使用在前端也可以用在後端

before:
/orders
after:
orders_path

說明路徑 http://localhost:3000/rails/info/routes

#link_to
link_to:幫我們產生 hyperlink (超連結) 的方法
吃兩個參數

orders_path：顯示許多Order
order_path：顯示單筆(show)
(new)

resource-post 
index posts_path
show  post_path
new   new_post_path
edit  edit_post_path

有URL Helper都是靜態頁面，有Get搜尋資料的

自己定義URL

#[BootStrap]
#應徵工作只會它一定被刷掉，但是如果是全端或許就ＯＫ

Rails 可以使用 gem 把 Bootstrap 裝進專案
靜態資源不會因為資料改變而改變：
app/assets/javascript/application.js
app/assets/stylesheets/application.css

CSS:SASS跟SCSS
SASS是寫rails的人寫的，SCSS是另一派寫的

#引用bootstrap
改application.css為application.scss
@import "bootstrap" 進入專案

在_form.html.erb實作：
```html 
<div class='well'></div>
<%= f.submit(class:'btn btn-primary') %>

```

#在複習
form_for(order) do |f|=>order? f?
route、controller



















