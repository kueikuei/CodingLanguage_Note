####主題  
>自建物件  



####自建物件  
>{}  
>new Object()  
>使用建構函數  
>ES6 建立物件

```javascript
//{}
//JS一定要有this才會正確指向類別成員
const nameCard = {
    name: 'Tony',
    age:20,
    printCard: function(){
        console.log(this.name);
        console.log(this.age);
    }
}
nameCard.name;
nameCard.printCard;

```

```javascript
//等同var nameCard = {};
const nameCard = new Object()//呼叫老祖宗

nameCard.name = 'Tony';
nameCard.age = 20;
nameCard.printCard = print;

function print(){
    console.log(this.name);
    console.log(this.age);
}

nameCard.name;
nameCard.printCard;

```

```javascript
//建構函數建立物件
//自首要大寫
//類別方法可以透過prototype去建立
function NameCard(name, phone, email){
    this.name = name;
    this.phone = phone;
    this.email = email;
    this.print = printCard;
}

function printCard(){
    console.log(this.name);
    console.log(this.age);
}

//prototype
NameCard.prototype.sayHi = function(){
    console.log('hi');
    console.log('this is prototype');
}

var myCard = new NameCard('CD','0987599848','dvd@yahoo.com.tw');
myCard.name;
myCard.print();


```

```javascript
//ES6建立物件
class Cat{
    constructor(name){
        this.name = name;  
    }
    speak(){
        console.log(this.name + '喵喵');
    }
}
c = new Cat('Mirza');
c.speak();
 
```

####obj 常用方法  
>hasOwnProperty:

####逐一印出array、obj的value
```javascript
//array
arr = ['Tom','Jason'];

arr.forEach(function(value){
  console.log(value);
});

```

```javascript
//obj
const nameCard = {
    name: 'Tony',
    age:20,
}

Object.keys(nameCard).forEach(function(value){
  console.log(value);
  console.log(nameCard[value]);
  //=======result:=======
  // name
  // Tony
  // age
  // 20
});

//or by this method
for(key in nameCard){
  if(nameCard.hasOwnProperty(key)){
    console.log(nameCard[key]);
  }
}

```

####類別靜態屬性方法  
>static關鍵字  
>不用new出來就可以直接使用類別裡的的方法

```javascript
class Point{
    constructor(x,y){
        this.x = x;  
        this.y = y;  
    }
    static sum(a,b){
        return a+b;
    };
}
console.log(Point.sum(2,5));

```

####JS物件導向觀念基礎  
>JS為prototype-based(原型基礎的物件導向)，不同於class-based  
>封裝(Encapsulation)  
>繼承(Inhertance)  
>多型(poly...)  

```javascript
//繼承(Inhertance)
class Animal{
    constructor(name){
        this.name = name;  
    }
    speak(){
        console.log(this.name + '喵喵');
    }
}

//狗狗繼承動物
class Dog extends Animal{
    speak(){
        console.log(this.name + '旺旺');
    }

    parentFunc(){
        super.speak();
    }
}

const dog = new Dog('momo');
dog.speak();
dog.parentFunc();
```

####this  
>隱性綁定(implicit binding)  
>>誰呼叫就指向誰
>顯性綁定  
>>為了解決隱性綁定implicit問題，顯性綁定可以指定this的值，利用call、bind、apply等方法  

```javascript
    var sayName = function(a,b,c){
        console.log('My name is '+ this.name +' '+a+' '+b+' '+c);
    };

    var Tom = {
        name:'Tom',
        age:20,
    };

    var language = ['Python','JS','Ruby'];

//call function
sayName.call(Tom,language[0],language[1],language[2]);
//be equal to apply
sayName.apply(Tom,language);
//be equal to bind, but it can reserve into var
var bind = sayName.bind(Tom,language[0],language[1],language[2]);
bind();
```
>new Binding (new Object)  
>全域 window Binding  

```javascript
//example1
var age = 12;
var sayAge = function(){
    console.log(this.age);
};
var me = {
    age:25
};
sayAge();//print to window this 12
sayAge.call(me);//print to this 25

//example2
var x = 10;
var Obj = {
    x:20,
    f:function(){
        console.log(this.x);
        var foo = function(){console.log(this.x);}
        foo();//call from window obj
    }
};
Obj.f();

//result by var - that
//that can be any var name
var Obj = {
    x:20,
    f:function(){
        console.log(this.x);
        var that = this;
        var foo = function(){console.log(that.x);}
        foo();
    }
};
```
>callback  






