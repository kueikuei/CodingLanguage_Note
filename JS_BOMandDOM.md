####主題  
>BOM(Browser Object Model)  
>DOM(Document Object Model)

####BOM  
>window物件不用宣告，可直接使用，代表目前瀏覽器視窗  
>所有全域變數、函式、物件都屬於window
>可操作包含：開啟/關閉視窗、改變視窗大小、計時器與取得網址、存取瀏覽器屬性
![Loading Fail](https://www.tutorialspoint.com/javascript/images/html-dom.jpg "DBOM")

```HTML5
<body>
    <p>輕功水上飄</p>
    <button onclick = "scrollWin()">點我</button>
</body>

```

```javascript
function scrollWin(){
    window.scrollTo(500,0);
}
```

####DOM  
>給HTML與XML文件使用的一組API  
>簡單說是將網頁物件化
>將HTML想像為一棵節點樹，如：  
![Loading Fail](http://www.webreference.com/programming/javascript/ppk1/figure8-1.gif "DOM")  

```javascript
//DOM API選擇器
document.getElementById(elementId)//by id
document.getElementsByTagName(tagename)//by element name
document.getElementsByName(name)//by name
document.getElementsByClassName(classname)//by classname

//CSS選擇器
document.querySelectorAll()
document.querySelector()
```
>有不止一個元素符合，則回傳NodeList集合，使用item()存取，透過forEach取值
>>Example:

```HTML5
<body>
    <div id = 'danger'></div>
</body>
```

```javascript
document.querySelector('#danger').innerHTML = 'Testing'
```

>取得父子結點  

```HTML5
<body>
    <div id = 'papa'>
        <div>Hi Bro</div>
        <div id = 'bro'>H</div>
    </div>
</body>
```

```javascript
var node = document.getElementById('papa');
//取得父節點body
var nodeParent = node.parentNode;
console.log(nodeParent.nodeName);
//取得兒子節點
var node = document.getElementById('papa');
var nodeBro = node.firstElementChild;
console.log(nodeBro.textContent);
```

>存取HTML屬性

```HTML5
<body>
    <div id = 'test' data-num = '1'>
        HTML
    </div>
</body>
```

```javascript
console.log(document.querySelector('#test').getAttribute('data-num'));
```

>更改CSS
>>屬性上與JS不同
>>>JS:backgrundColor/CSS:backgrund-color

```HTML5
<body>
    <button id = 'btn'>點我</button>
</body>
```

```javascript
document.getElementById('btn').style.backgroundColorColor='red';
```

>取出input值
>>前端表單驗證

```HTML5
<body>
    <input type = "text" id = "input">
    <button id = 'btn'>點我</button>
</body>
```

```javascript
console.log(document.getElementById('input').value);
```

>動態插入元素(element)

```HTML5
<body>
    <div id = 'test' data-num = '1'>
        HTML
    </div>
</body>
```

```javascript
const parent = document.getElementById('test');

var createBtn = document.createElement('button');
createBtn.textContent = '點我點我';

//動態插入button
parent.appendChild(createBtn);

//動態刪除
parent.removeChild(createBtn);
```

