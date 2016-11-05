[單元1]
# pokemon fight example
random():0~1
ES6:可以透過$代表變數並插入字串如：
var name="Jason";
'hello!I am ${name}'
prompt():使用者輸入function之一，輸入為字串透過parseInt轉成整數

```javascript
swith(){
    case x:
        ...
        break
    case y:
        ...
        break

}
```

[單元2]
What is programming?
用什麼方式存取資料？資料結構
用什麼方法做？演算法

#靜態網站vs動態網站

#JS能幹嘛？
1.網頁應用程式開發（JS前端/NodeJS後端）
2.by cmd 去操作沒有UI介面的瀏覽器=>模擬測試用：PhantomJS
3.跑在WebView瀏覽器核心的應用(WebView Application)、手機(phonegap)、桌面應用程式開發(Electron)
4.用JS寫的原生應用程式
5.網路爬蟲、VR/AR、IOT、Robotics等應用

[單元2-3]
#HTML
<meta>
描述資料的資料
<meta charset=utf8 />
<meta name='Jason' descrition='hello world'>

#標籤

```html
<!-- 有順序性 -->
<ol>
    <li>打顆蛋</li>
    <li>伴入蔥花</li><
    li>放入少許鹽巴</li>
</ol>

<!-- 無順序性 -->
<ul>
    <li>李白</li>
    <li>杜甫</li>
    <li>白居易</li>
</ul>

<a href="連結網址" target="開啟方式">帶我走</a>
<!-- target 常見屬性值（_blank（開新視窗）） -->
<img src="圖存放位置" alt="破圖說明" title="滑鼠移至圖上說明" />
<!-- alt也用在google搜尋檢索 -->

```

#絕對位置
URL
#相對位置
父資料夾../father/fathrt.html
子資料夾./sample/son.html
同資料夾./father.html

#Get vs Post 表單運作
<form></form> 表單是撰寫動態網站和資料庫互動的重要一環，常用於客戶端（Client）蒐集資訊，透過提交表單可以讓資料傳送到給後端程式處理。

```html
<form action="index.php"method="post">
    <!‐‐action放置後端程式位置，method為傳送方式，GET會顯示提交內容於網址列，POST則不會‐‐><input type="text"name="query">搜尋
    <input type="submit"value="提交">
</form>
```

瀏覽的網頁傳遞參數給 Server 端主要有兩種方法：

google搜尋為Getd。表單參數與填寫內容可在 URL看到，較不安全，但 GET的執行速度比較快，可加入書簽(Bookmark) 中。 一般用於獲取/查詢資源資訊

POST 資料傳遞時，網址並不會更動。透過 HTTP message body夾帶，故參數與值不會顯示於 URL，常用於更新資源、登入。

[單元6-8]
#CSS
開發者工具(Mac: alt + command + i)
層疊樣式表（原文：Cascading Style Sheets，簡寫CSS）
#CSS屬性分為兩大類:
外觀:主要負責控制如：文字顏色、大小、背影顏色等外觀
版面:負責如何將元素放置在螢幕中適切的位置
#三種使用方式
1. 行內樣式 (Inline Styles):放body
2. 內嵌樣式 (Embeded Styles):放head 
3. 外部樣式表 (External Stylesheets):最推薦的

#CSS 規則包含了兩部分：1. 選擇器2. 宣告
```css
<!-- p為選擇器 -->
p{
    <!-- 內容都是在宣告 -->
    color:red;
    font‐family:Arial;//屬性(元素的面向)：值(想用在該元素上的設定值)
}
```

#常用選擇器種類（重要）
#Universal selector（通用選擇器）
使用 * 選取所有元素
#Type selectors（型態選擇器）
Ex. h1、p ，選取該元素
#Class selectors（Class選擇器）
使用 .class 名稱，選取該class元素
#ID selectors（ID選擇器）
使用 #ID 名稱，選取該ID元素

#等級為:
id>class>>type>universal

#偽類(Pseudo-classes)選擇器
#超連結
:link (超連結平常的樣式) 
:visited (超連結點閱後的樣式) 
:hover (滑鼠滑入的樣式) 
:active (滑鼠按下的樣式) 
#css後來優先？lvha通常會這樣擺設

#css階層
#定義外觀樣式時難免會有不同的樣式去定義到同一個元素的情況
#月經卻指到element分數越高
Specificity 比大小
使用者優先
!important 大魔王
後來會覆蓋之前
越接近元素越強













