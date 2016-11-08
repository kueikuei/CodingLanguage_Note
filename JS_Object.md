####JS 三種內建物件  
1.內建原生物件共11種  
>object 老祖宗
>>string、array、boolean、date、global、math、number、regexp、error

2.宿主物件(host objects):由宿主提供物件(如：瀏覽器)，像是BOM(browser object model)  

3.使用者自訂物件 

========================
####[原生物件介紹]  
####string  
*與array的差別在於string用了method後不會改變原始變數*

```javascript
//兩種建立方式
const str1 = 'JS'; 
const str2 = new String('HIJS');

//////////相關方法////////////
//字串長度和大小寫
length //屬性可以取得字串長度 
toLowerCase() //方法可以將英文大寫轉小寫  
toUpperCase() //方法可以將英文小寫轉大寫
//取得字串指定字元
charAt(index)//取得 index 位置的字元   
charCodeAt(index)//取得 index 位置的 Unicode  
//字串搜尋
indexOf(string,index)//傳回第一次搜尋到字串的index，未 找到傳回-1，傳入字串為欲搜尋字串，index 為開始位置
lastIndexOf(string)//同上一方法，不過是從尾部反向搜尋  
match(string)//同第一種方式，但傳回找到字串，無則傳null  
search(string)//與 indexOf 功能類似，但可用正則式  
//子字串的處理
replace(string1,string2)//將找到的 string1 子字串取代為 string2
split(string)//使用參數 string 作為分割，並回傳分割後 Array 物件
substr(index,length)//從 index 開始取出length個字元   
substring(index1,index2)//取 index1 到 index2(不含)子字串   
concat(string)//將 string 新增到 string 物件字串之後
```

####array  
*能動態新增元素* 

```javascript
//三種使用方法  
//宣告有三個元素的陣列   
constnameA = new Array(3);   
nameA[0] = 'KD';   
nameA[1] = 'XD';   
nameA[2] = 'XDD';
//也可以在建立物件時建立元素值   
const num = new Array(100,22,34);  
//最簡單好記，使用[]  
const nameB = [];   
nameB[0] = 'KD';   
nameB[1] = 'XD';   
nameB[2] = 'XDD';  
//Array 物件內建屬性和方法
//與string方法相似
length//取得陣列長度   
join()//將陣列元素用 "逗號," 串成一個字串   
reverse()//將陣列元素反轉   
sort()//將陣列元素依照   
unicode //進行排序   
concat(array)//將參數中的陣列合併到目前陣列  
//建立二維陣列  
const users = new Array(2);
for(var i=0;i<2;i++){ 
    users[i] = new Array(2);
}//output:[[undefined, undefined], [undefined, undefined]]
 

```

####date  
*取得電腦日期和時間*
```javascript
//重要觀念！！！從1970開始算
const d = newDate(); //milliseconds since 1970/01/01   
const now = Date.now();  //1970/1/1到現在的毫秒數
const date = d.getDate();   //日期
constyear = d.getFullYear(); //年
```

####math 
*不需要 new 運算子自己就會 建立，故可以直接使用屬性和方法* 

```javascript
console.log(Math.PI);   
console.log(Math.E);  
console.log(Math.LN2);  
//Math物件的亂數最大和最小值
max(value1,value2)//傳回兩個參數中的最大值   
min(value1,value2)//傳回兩個參數中的最小值
//重要方法、random   
random()//傳回亂數值(0-1，不含1)   
round(value)//將參數四捨五入後傳回  
//Math物件的數學方法
abs()//傳回絕對值   
log()//傳會自然對數   
sqrt()//傳回平方根   
pow()//傳回次方   
exp()//自然對數
 
```
####error  
*Error 物件會儲存執行時發生錯誤的資 訊，發生錯誤時會自動建立*

```javascript
//基本錯誤處理架構
try{
    //此區塊內為需要例外處理的程式碼
} catch(e){
    //如果try區塊發生錯誤會執行此一區塊，並傳入e參數(Error物件)，可
} finally{
    //這是選擇性區域，是不管錯誤是否發生都會執行的區塊
}

```

####regexp  
*使用正規表示法的物件，用以比對其它字串是法符合範本字串*  

```javascript
exec(string)//檢查參數string字串是否符合正規運算是子字串，符合回傳字串陣列
test(string)//檢查參數string字串是否符合正規運算是子字串，符合回傳true不符合回傳false

//\S+至少有一非空白字元   
const matches=/(hello\S+)/.exec('Thisisahelloworld!');  
console.log(matches[1]);//helloworld!
conststr="helloworld!";   
constresult=/^hello/.test(str);   
console.log(result);//true

```

###總結
在這個章節中我們學會了:  
1. 物件基礎概念  
2. JavaScript 常用內建物件





