1.原型：

    原型连接在更新时是不起作用的。对某个做出改变，不会触及该对象的原型。只有在检索值的时候才被用到。
2.数组：

     删除： delete、splice
     delete：会在数组中留下空洞。
     splice（数组中的序号，要删除的元素个数）： 删除一些元素并将它们替换为其他的元素。
3.枚举：

for in :遍历一个数组的所有属性，无法保证属性的顺序。

for：可以保证属性的顺序。

区别数组和对象：
当属性名是小而连续的整数时，使用数组，否则，使用对象。

方法：

```
var is_array = function (value){
    return Object.prototype.toString.apply(value) === '[object Array]';
};
```
### 4.方法：
##### 《1》Array
       
    array.concat(item...)产生一个新数组，它包含一份array的浅复制并把一个或多个参数item附加在其后。（不会改变array）部分，返回array的新的length。
    
    array.push(item...)把一个或者多个参数item附加到一个数组的尾部。如果item是一个数组，它会把参数数组作为单个元素整个添加到数组中，并返回这个array的新长度值。（会改变array）
 
    array.unshift(item...)把元素添加到数组中的开始
    array.slice(start,end) 对array中的一段作浅复制。从array[start]开始，到array[end]结束，不包括array[end].
    
    array.join(separator) 把一个array构造成一个字符串。用separator分隔符把它们连接在一起，默认分隔符时逗号。想要无间隔的连接，使用空字符串。
    
    array.pop()  移除array中的最后一个元素并且返回该元素。如果array时empty，返回undefined。
    
    array.shift() 移除array中的第一个元素并且返回该元素。如果array时empty，返回undefined。（shift比po慢得多）
    
    array.reverse() 反转元素顺序，返回array本身。
 
             var a=['a','b','c'];
             var b=a.reverse();
             //a b都是['c','b','a'];
    array.sort(comparefn) 对array中的内容进行排序，不能正确的给一组数字排序。
    
    array.splice(start,deleteCount,item...)从array中移除一个或多个元素，并用新的item代替它们，返回被移除的元素数组。
     
   
##### 《2》Function

    function.apply(thisArg,argArray) 调用function.
##### 《3》Number

       number.toExponential(fractionDigits)把number转换成一个指数形式的字符串。参数标识小数点后的数字位数，值必须在0~20
    number.toFixed(fractionDigits)把number转换成一个十进制数形式的字符串。参数标识小数点后的数字位数，值必须在0~20，默认为0
    number.toPrecision(precision)  把number转换成一个十进制数形式的字符串。参数标识数字的精度，值必须在0~21
    number.toString(radix)把number转换成一个字符串。参数控制基数，值必须在2~36，默认是以10为基数的，最常用的是整数，但是可以用任意的数字。
##### 《4》Object
    Object.hasOwnProperty(name)若object包含一个名为name的属性，那么此方法返回true.原型链中的同名属性是不被检查的，这个方法对name就是“hasOwnProperty”时不起作用，此时返回false.
     
##### 《5》RegExp
    
      regexp.exec(string) 使用正则最强大和最慢的方法。匹配成功，返回数组，否则，返回null。
    regexp.test(string) 使用正则最简单和最快的方法。匹配成功，返回true,否则返回false.
##### 《6》String
      string.charAt(pos) 返回在string中pos位置的字符。pos<0或者pos>string.lenth,返回空字符串。

    string.charCodeAt(pos) 返回在string中pos位置的字符码位。pos<0或者pos>string.lenth,返回NaN。
    
    string.concat(string...)把字符串连接起来构成一个新的字符串，很少被使用，用+更方便。
    
    string.indexOf（searchString，position） 从开头查找searchString。找到返回第一个匹配字符的位置，否则返回-1
    
    string.lastIndexOf（searchString，position） 从末尾查找searchString。找到返回第一个匹配字符的位置，否则返回-1
    
    string.search(regexp)和indexOf方法相似，只是他接受的参数是一个正则表达式。此方法忽略g标识。
    
    string.localeCompare(that) 比较两个字符串。如果string比字符串that小，结果为负数。如果相等，结果为0。
    
    string.match(regexp)让字符串和正则表达式进行匹配。
    
    string.replace(searchValue,replaceValue)进行查找和替换，并返回一个新的字符串。
    
    string.slice(start,end)
    
    string.substring(start,end)和slice方法一样，但是不能处理负数参数。
    
    String.split(separator,limit)把字符串分割成片段来创建一个字符串数组。
    
    string.toLocaleLowerCase() 使用本地化的规则把string中的所有字母转换为小写格式。
    string.toLocaleUpperCase()
    
    string.toLowerCase()
    string.toUpperCase()
    string.fromCharCode(char...)根据一串数字编码返回一个字符串。
   
### 5.避免使用全局变量：
   
   1》依赖尽可能少的全局变量，即只创建一个全局变量。
   2》零全局变量：创建一个书签。使用一个立即执行的函数调用将所有脚本放置其中。
   
```
  (function（win）{
      ‘use strict’
      var doc=win.document;
     //这里定义其他变量
      
  }(window));
```
### 6.事件处理：
  隔离应用逻辑、不要分发事件对象。
 
### 7.避免“空比较”：

    1》检测原始值：  (number/string/undefined/null/boolean)
    
      检测字符串、数字、布尔值、undefined，使用typeof运算符。
       typeof variable
==注意：typeof的独特之处：将其用于一个未声明的变量也不会报错。未定义的变量和值为undefined的变量通过typeof都将返回undefined
       检测null,使用===或者！==和null进行比较。
    
    2》检测引用值:  value instanceof constructor
    (Object/Array/Date/Error)
   ==注意:instanceof的一个有意思的特性是它不仅检测构造这个对象的构造器，还检测原型链。==
   
    检测函数最好的方法：typeof(IE8以及IE8-，使用typeof来检测DOM节点中的函数都返回‘object’而不是‘function’)
    
    检测数组：
    
```
Function isArray(value){
    return Object.prototype.toString.call(value) === "[object Array]";
}
```

3》检测属性：in

```
var object={
    
    count:0,
    related:null
};
if('count' in object ){
    
    //执行代码
}
if（‘related’ in object）{
    //执行代码
}
```
如果只想检查实例对象的某个属性是否存在，使用hasOwnProperty()方法。

### 8.将配置数据从代码中分离出来
    将配置数据拿到外部，最好放在单独的文件中。
### 9.抛出自定义错误：
    1》  在js中抛出错误： 
```
 throw new Error('Something bad happened')
```
  如果没有通过try-catch语句捕获，抛出任何值都将引发一个错误。
   
    2》try-catch语句：能在浏览器处理抛出的错误之前来解析它。
    可以增加finally块。finally块中的代码不管是否有错误发生，最后都会被执行。
    3》错误类型：
       Error           所有错误的基本类型
       EvalError       通过eval()函数执行代码发生错误时抛出。
       ReferenceError  期望的对象不存在时抛出。
       SyntaxError     给Eval()函数传递的代码中有语法错误时抛出。
       TypeError       变量不是期望的类型时抛出
       URIError        给encodeURI()、encodeURIComponent()、decodeURI()或者decodeURIComponent()等函数传递格式非法的URI字符串时抛出。
       
### 10.不是你的对象不要动：
   
    1》原则：  不覆盖方法、不新增方法、不删除方法。
    2》好的途径：  
        1.基于对象的继承（原型继承）：Object.create()
           
           
```
  var person={
      name:'aa',
      sayName:function(){
          alert(this.name);
      }
  };
  
  var myPerson=Object.create(person,{
      name:{
          value:'cc'
      }
  });
  myPerson.sayName(); //aa
  myPerson.sayName=function(){
      alert('bb');
  };
  myPerson.sayName();//bb
  person.sayName();//aa
```
    2.基于类型的继承： 通过构造的函数实现，而非对象。
    （首先，原型继承；然后，构造器继承）
    
```
functionn MyError(message){
    this.message=message;
}
MyError.prototype = new Error();
var error = new MyError("somethign bad happened.");
console.log()
```

       3.门面模式：
         为已存在的对象创建一个新的接口。
 3》阻止修改：
 
    防止扩展：禁止为对象添加属性和方法，但已存在的属性和方法可以被修改或者删除。Object.preventExtension()和Object.isExtensible（）
    密封： 类似防止扩展，而且禁止为对象删除已存在的属性和方法。Object.seal（） Object.isSealed()
    冻结：类似密封，而且禁止为对象修改已存在的属性和方法。（所有字段均只读）Object.freeze() Object.isFrozen()
### 11.校验：
  查找文件：

```
<fileset dir="./src" includes="**/*.js">
<fileset dir="./src" includes="**/*.js" excludes="**/*-test.js">

```
### 12.可以执行字符串的函数：
     
       
```
      1》eval();
      2》Function构造函数
      3》setTimeout()
      4》setInterval()
    

```
### 13.UI层的松耦合：
   1.将JavaScript从CSS中分离：
     
```
  不好的写法：
    .box{
        width:expression(document.body.offsetWidth+'px');
    }
```
 (IE9不再支持CSS表达式)
 
 2.将css从js中分离：
    
    不好的写法：
```
  直接修改DOM元素的style属性。
        element.style.color="red";
        element.style.cssText="color:red;left:10px;top:10px;visibility:hidden";        
```
   好的写法：
    操作CSS的className。
    
```
  .reveal{
      color:red;
      left:10px;
      top:100px;
      visibility:visible;
  }
  原生方法：
  element.className+="reveal";
  jQuery:
    $(element).addClass("reveal");
   HTML5：
   element.classList.add("reveal");
```
(注意：有一种使用style属性的情形可以接受：给页面中的元素定位，可以使用style.top/style.left等来对元素做正确定位。)

3.将JS从HML中抽离：

```
不好的写法：
  <button onclick="doSomething()" id="action-btn">click</button>
  
好的写法:
  IE8及IE8-不支持addEventListener（）函数。
  function addListener(target,type,handler){
      if(target.addEventListener){
          target.addEventListener(tye,handler,false);
      }else if(target.attachEvent){
          target.attachEvent("on"+type,handler);
      }else{
          target["on"+type]=handler;
      }
      
  }
    function doSomething(){
      //代码
  }
  var btn=document.getElementById("action-btn");
  addListener(btn,"click",doSomething);
```

```
  不好的写法：
   <script> doSomething();</script>
   
   好的写法：
    将js代码放在外置文件中。
```
4.将HTML从js中抽离：

   
```
  不好的写法：
    var div=document.getElementById("my-div");
    div.innerHTML= "<h3>Error</h3><p>address</p>"
    好的写法：
    方法一：从服务器加载：
    function loadDialog(name,oncomplete){
        var xhr=new XMLHttpRequest();
        xhr.open("get","/js/dialog"+name,true);
        xhr.onreadystatechange = function(){
            if(xhr.readyState==4&xhr.status ==200){
                var div=document.getElementById("dlg-holder");
                div.innerHTML= xhr.responseText;
                oncompletee();
            }else{
                //处理错误
            }
        }；
        xhr.send(null);
    }
方法二：简单客户模板
方法三：复杂客户端模板

```



 
       
    
    

  
  
  
  


   
   
   



   
   
    