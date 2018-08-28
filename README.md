# javacript笔记[基础]
## 初探JavaScipt魅力
### getElementById
1. 第一个js兼容性问题
 1. 在FF下直接使用ID存在问题
 2. document.getElementByID在任何浏览器下均可使用
  ```HTML
<input type="checkbox" onmouseover="document.getElementById('div1').style.display='block';" onmouseout="document.getElementById('div1').style.display='none';">
 <div id="div1">请勿在公共电脑上点击此项！！</div>
```

2. 网页换肤
  1. 土豆网"开灯"、"关灯"效果
  2. 任何标签都可以加ID,包括link
  3. 任何标签的任何属性，也都可以修改
  4. HTML里面怎么写，JS里面就怎么写
------------


### if判断
1. 点击按钮显示/隐藏Div（弹出菜单）
 1. 特效实现过程及原理分析
 2. if的基本形式
  ```html
<div id="div1">showhide</div>
    <button onclick="showHide()">按钮</button>
    <script>
        function showHide(){
            var oDiv = document.getElementById('div1');
            if(oDiv.style.display=='block'){
                oDiv.style.display='none';
            }else{
                oDiv.style.display='block';
            }
        }
    </script>
```
2. 扩展
 1. 为a链接添加JS
 2. className的使用
    class是关键字
  ```html
<a href="javascript:;">链接</a>
```

------------
### 函数传参
1. 改变背景颜色
 1. 函数传参，参数就是占位符---函数定不下来的东西
  ```html
 <button onclick="setColor('red')">变红</button>
    <button onclick="setColor('blue')">变蓝</button>
    <button onclick="setColor('green','2000px')">变大绿</button>
    <div id="div1"></div>
    <script>
        function setColor(color,num){
           var oDiv = document.getElementById('div1');
           oDiv.style.background = color;
           oDiv.style.width = num;
        }
    </script>
```
2. 改变Div的任意样式
 1. 操纵属性的第二种方式
  1. 什么时候用：要修改的属性不固定
  2. 字符串和变量---区别和关系
     '常量'、变量
  2. 将属性名作为参数传递
  ```html
<input type="text" id="text1">
    <button onclick="setText()">改变文字</button>
    <script>
        function setText(){
            var oTxt = document.getElementById('text1');
        // 第一种操作属性的方法
        oTxt.value = 'dsdasdasd';
        // 第二种操作属性的方法
        oTxt['value'] = 'sadasdasdas'
        }
```
3. style与className
 1. 元素style属性=xxx是修改行间样式
     style加样式和取样式都是来自行间
 2. 之后在修改className不会有效果

------------


### 提取行间事件
1. 提取事件
 1. 为元素添加事件
 2. 事件和其他属性一样，可以用JS添加
 3. window.onload的意义
   页面加载完成后执行
 4. 行为、样式、结构三者分离
2. 获取一组元素
 1. getElementsByTagName----s充满了灵性
 2. 数组的使用
 3. 里面的

------------

### 循环
1. 用while引入循环的概念
 1. while循环语法
 2. 自增的意义
 3. 循环的构成：初始化、条件、语句、自增
 ```html
while(i=0;i<n;i++)
{
	循环语句
}
```
2. for循环
 1. 用for替代while循环
 2. 用for循环为一组元素添加事件
 3. 什么时候用循环----一组元素
 4. 例子 --全选/反选
 ```html
 <button onclick="setText()">全选</button>
    <button onclick="setText1()">全不选</button>
    <button onclick="setText2()">反选</button>
    <input type="checkbox" >
    <input type="checkbox" >
    <input type="checkbox" >
    <input type="checkbox">
    <script>
        function setText(){
            var inP = document.getElementsByTagName('input');
            for(i=0;i<inP.length;i++){
                inP[i].checked = true;
            }
        }  
        function setText1(){
            for(i=0;i<inP.length;i++){
            if(inP[i].checked == true){
                inP[i].checked = false;
            }
        }
        }
        function setText2(){
            for(i=0;i<inP.length;i++){
            if(inP[i].checked == true){
                inP[i].checked = false;
            }else if(inP[i].checked == false){
                inP[i].checked = true;
            }
        }
        }
    </script>
```

------------

### 选项卡
1. 按钮的实现
 1. 添加事件
 2. this的使用
2. 内容的实现（div）
 1. 先隐藏所有的Div，再显示“当前” div
 2. 索引值的使用
 3. 什么时候使用索引值-—————需要知道“第几个”的时候
 4. html 添加index  ——————会被FF过滤
 5. js添加index
 ```html
<div id="div">
            <button>教育</button>
            <button >人文</button>
            <button >社会</button>
            <div>111</div>
            <div>222</div>
            <div>333</div>
    </div>
    <script>
        var oDiv = document.getElementById('div');
        var abtn = oDiv.getElementsByTagName('button');
        var aDiv = oDiv.getElementsByTagName('div');
        for(i=0;i<abtn.length;i++)
        {    
            abtn[i].index = i;
            abtn[i].onclick=function()
            {
                for(i=0;i<abtn.length;i++)
                {
                    abtn[i].className = '';
                    aDiv[i].style.display = 'none';
                }
            this.className='active';
            aDiv[this.index].style.display = 'block';
            // 当前this的序号 对应div的数组
            }
        }  
```


------------


### JS实现简易日历
1. 程序实现思路
 1. 类似选项卡，只是下面有一个div
 2. innerHTML的使用
2. 数组的使用
 1. 定义：arr=[1,2,3]
 2. 使用：arr[0]
3. 字符串连接
 1. 作用：连接两个字符串
 2. 问题：连接中的优先级
 ```html
<div id="tab" class="calendar">
            <ul>
                <li class="active" style="margin-left:82px;"><h2>1</h2><p>JUN</p></li>
                <li><h2>2</h2><p>FER</p></li>
                <li><h2>3</h2><p>MAR</p></li>
                <li><h2>4</h2><p>APR</p></li>
                <li><h2>5</h2><p>MAY</p></li>
                <li><h2>6</h2><p>JUN</p></li>
                <li><h2>7</h2><p>JUL</p></li>
                <li><h2>8</h2><p>AUG</p></li>
                <li><h2>9</h2><p>SEP</p></li>
                <li><h2>10</h2><p>OCT</p></li>
                <li><h2>11</h2><p>NOV</p></li>
                <li><h2>12</h2><p>DEC</p></li>
            </ul>

            <div class="text">
                <h2>1月</h2>
                <p>欢迎你</p>
            </div>
        </div>
        <script>
            var arr=[
                '一年又开始了',
                '过年，开心！',
                '春天都了，动物们又到了繁殖的季节',
                '四月是一个努力的月份',
                '五一七天乐，您开心就好',
                '儿童节，我才幼儿园呢',
                '又是一年最热的时候',
                '热',
                '开学，惨！',
                '放假',
                '这是考试的月份',
                '一年有结束了',
            ];
            var ODiv = document.getElementById('tab');
            var aLi =ODiv.getElementsByTagName('li');
            var oTxt=ODiv.getElementsByTagName('div')[0];
            for(var i=0;i<aLi.length;i++){
                aLi[i].index=i;
                aLi[i].onclick=function(){
                    for(var i=0;i<aLi.length;i++){
                        aLi[i].className='';
                    }
                    this.className='active';
                    oTxt.innerHTML='<h2>'+(this.index+1)+'月</h2><p>'+arr[this.index]+'</p>';
                };
            }
        </script>
```

------------

## javascript基础
### javaScript组成
1. ECMAScript：解释器、翻译
2. DOM：Document Object Model--操作HTML的入口
3. BOM：Browser Object Model---浏览器操作
 1. 各组成部分的兼容性，兼容性问题由来
 ECMA兼容性>DOM>BOM(几乎不兼容)

------------

### 变量类型（1）
1. 类型：typeof运算符
 1. 用法、返回值
 2. 常见：number、string、boolean、undefined、object、function
 ```javascript
<script>
     var a = 12;
     var b ='asdasd';
     var c = true;
     var d = function(){}
     var e = document;
     var f = typeof[];
     console.log('12:'+typeof a+'\nasdasd:'+typeof b+'\nture:'+typeof c+'\nfunction(){}:'+typeof d+'\ndocument:'+typeof e+'\ntypeof:'+typeof f+'\nb:'+typeof b);
    </script>
```
2. 一个变量应该只存放一种类型的数据

------------

### 变量类型（2）
1. 数据类型转换
 1. 例子：计算两个文本框的和
 2. 显式类型转换（强制类型转换）
 3. 比如：parseInt()、parseFloat()
    从左到右扫描字符串，提取数字，遇到字母就跳出
  ```html
<input type="text" id="text1">
   <input type="text" id="text2">
   <input type="button" id="btn1" value="求和">
   <script>
       var tex1 = document.getElementById('text1');
       var tex2 = document.getElementById('text2');
       var btn1 = document.getElementById('btn1');
        btn1.onclick = function(){
            alert(typeof tex1.value)
            alert( typeof parseInt(tex1.value))
            alert(tex1.value+tex2.value);
            alert(parseInt(tex1.value)+parseInt(tex2.value));
            var n = parseInt(tex1.value);
            var m = parseInt(tex2.value);
            if(isNaN(n))
            {
                alert('第一个数字输入有误');
            }
            else if(isNaN(m)){
                alert('第二个数字输入有误');
            }else{
                alert(n+m);
            }

        }
   </script>
```
 4. NaN的意义和检测
   Not a Number 非数字（任何数+NaN=NaN）
2. 隐式类型转换
 1. ==、===
 2. 减法
 ```javascript
<script>
       var a = 5;
       var b = '5';
       alert(a==b);      //true    先转换类型，然后比较
       alert(a===b);     // false   不转换类型，直接比较
       alert（a-b);     //0       减法自动隐式类型转换
   </script>
```

------------

### 变量作用域和闭包
1. 变量作用域（作用范围）
 2. 局部变量、全局变量
 ```javascript
<script>
      var a = 10;
      var c;
      function aa(){
          var b = 20;      //局部变量
          c = 30;    
      }
      function bb(){
          alert(a);     //全局变量
        //   alert(b);  
          alert(c);     // 全局变量
      }
      aa();
      bb();
   </script>
```
1. 什么是闭包
 1. 子函数可以使用父函数中的局部变量
 2. 之前一直在使用闭包
 3. 网上对于闭包的定义
 4. 初步理解


------------
### 命名规范（1）
1. 命名规范及必要性
 1. 可读性—————能看懂
 2. 规范性—————符合规则
2. 匈牙利命名法
 1. 类型前缀
 2. 首字母大写

------------

### 命名规范（2）
![](http://lovedeartop.oss-cn-shanghai.aliyuncs.com/xproject/%E5%91%BD%E5%90%8D%E8%A7%84%E8%8C%83.jpg)

### 运算符
1. 算术：+加、—减、\*乘、/除、%取模
 1. 实例：隔行变色、转换时间
 ```javascript
<script>
       function aa()
       {
         var aLi = document.getElementsByTagName('li');
         for( i=0;i<aLi.length;i++) 
         {
            if(i%2==0)
            {
                aLi[i].style.backgroundColor = '#ccc';
            }
           else
           {
            aLi[i].style.backgroundColor = '';
           }
        }
       }
      aa();
   </script>
```
 ```javascript
 <script>
        var s = 156;
        alert(parseInt(s/60)+'分钟'+s%60+'秒');
    </script>
```
2. 赋值：=、+=、—=、
3. 关系：<、>、<=、>=、==、===、!=、!==
4. 逻辑：&&与、||或、！否
 1. 实例：全选与反选
5. 运算符优先级：括号

------------

### 程序流程控制
1. 判断：if、switch、?:
 1. `a%2==0?alert('双数'):alert('单数');`
2. 循环：while、for
3. 跳出：break、continue
 ```javascript
<script>
       for(i=0;i<5;i++){
           if(i==2){
            //    break ;    整个循环中断了
               continue;     // 本次循环中断了
           }
           alert(i);
       }
    </script>
```
4. 什么是真、什么是假：
 1. 真：true、非零数字、非空字符串、非空对象
 2. 假：false、数字零、空字符串、空对象、undefined

------------

### Json
1. 什么是Json
2. Json和数组
3. Json和for in
```javascript
<script>
      var json = {a:2,b:5,c:7};
      var arr = [12,5,7];
      alert(json['a']);
      alert(arr[0]);
    //   alert(json.lengh);
      alert(arr.length);
      for(var i in arr){
          alert('第'+i+'个东西:'+arr[i]);
      }
      for(var i in json){
          alert('第'+i+'个东西:'+json[i]);
      }
    </script>
```

------------
## 深入javascript

### 函数返回值
1. 函数返回值
 1. 函数的执行结果
 2. 可以没有return
2. 一个函数应该只返回一种类型的值

------------

### 函数传参
1. 可变参（不定参）：arguments
 1. 参数的个数可变，参数数组
2. 例子1：求和
 1. 求所有参数的和
3. 例子2：CSS函数
 1. 判断arguments.length
 2. 给参数取名，增强可读性
4. 取非行间样式（不能用来设置）：
 1. obj.currentStyle[attr]
 2. getComputedStyle(obj,false)[attr]

------------

### 数组基础
1. 数组的使用
 1. 定义
 2. var arr=[15,5,9];
 3. var arr=new Array[12,52,3];
 4. 没有任何差别，[]的性能略高，因为代码短
2. 数组的属性
 1. length
 2. 既可以获得、又可以设置
 3. 例子：快速清空数组
3. 数组使用原则：数组中应该只存一种类型的变量

------------

### 添加、删除元素
1. 数组的方法
 1. 添加
 2. push（元素），从尾部添加
 3. unshift（元素），从头部添加
2. 删除
 1. pop(),从尾部弹出
 2. shift(),从头部弹出

------------
### 排序、转换
1. sort（[比较排序]),排序一个数组
 1. 排序一个字符串数组
 2. 排序一个数字数组
2. 转换类
 1. concat(数组2)
 2. 连接两个数组
3. join(分隔符)
 1. 用分隔符，组合数组元素，生成字符串
 2. 字符串split

------------

### 插入、删除
1. splice
 1. splice（开始，长度，元素...）
 2. 先删除，后插入
2. 删除
 1. splice（开始，长度）
3. 插入
 1. splice（开始，0，元素...)
4. 替换










































