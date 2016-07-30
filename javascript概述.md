# javasctipt 是什么


> 程序语言


#  程序语言是什么



> 和计算机交流的语言


# 计算机是什么？能做什么？


> 用来做计算的


> 程序语言就是一条条的人类可读的指令告诉计算机怎么去做计算

 程序语言就像一份指令或者一份菜谱详细的描述了计算机应该怎么去计算

 一门程序语言必须具备一些能力才能和计算机交流明白

 #  必须能很清楚的告诉计算机 怎样去存储数据
 #  必须能很清楚的告诉计算机 怎样去做逻辑操作


 ##  javascript中的逻辑操作

   + - * / % && || ！===  ！==   <=   >=  <   >   (esLint)

   > if(){}
   > if(){}else{}
   > if(){}else if(){}else{}

   switch (val){
    case1:  ；
    *****
    break；
   }

   #  for(var i = 0; i<100; i++){

   }
   while(i<200){
   console.log(1);
       i++;
   }
   do{
      console.log(1);
      i++;
   }while()

   ##  数据存储

   var  _v = 1;               Number
   var  _v = 'aaa我';         String
   var  _v = [1,2,3];         Array
   var  _v = {a:1,b:2,c:3};   Object
   var  _v = functtion(){};   function
   var  _v = undefined;       undefined
   var  _v = null;            null
   var  _v = true;            Boolezn

   javascript中类似于'表'的形式来存储数据(对象)

##  函数对象

   var  fn=function(){
     alert(1);
     console.log(1);
     return 1;
   }


   定义函数的时候发生的什么？
   要把代表函数的那张表构建完全
   1.'调用'这个属性要赋值，函数体内部的字符串。
   2.要把当前可见范围内的所有变量由近到远的记录大链条中，形成一条作用域链


##  函数体里内容在哪里

   函数对象会用一个不可见的属性'调用'来存储函数体中的代码
   {'调用'：'console.log(1);return1'}
   函数这个对象相比其他对象的特殊之处在于它可以被调用
   函数名+()   可以调用函数
    调用函数的时候：函数对象会读取自己身上'调用'这个属性的值，取出来一些字符串，把这些字符串交给JS解析器去当作javascript代码去执行，
    与此同时还会取出函数的作用域链，用来辅助这段代码执行，

# 函数中 this是什么？

只有在函数中才有this这个东西
函数在作用的时候，根据调用的不同情况来决定this变成什么

# this不同的调用情况
//  正常的定义一个函数(不把函数作为某个对象的属性)
//  正常的调用一个函数(使用( )的方式调用函数)
  var fn=function(){
  console.log(this)
  }
//  正常调用一个函数
 fn();
//  this指向windows对象

 ``` javascript
     var obj={a:1,
     b:2,
     c:function(){
       console.log(this)
       }
    }
    obj.c();//this指向obj对象  指向它的宿主对象；  

    obj.c.call([1,3,3])//this指向里面的第一个参数([1,3,3])；
 ```
//如果需要把this换成任何我们想要的对象
//我们需要借助函数对象身上的call和apply方法

## 当我们写好一份程序之后，计算机在处理的过程中发生了什么？

对照代码，从上往下开始解析

# 用在展示信息的web页面中
# 用在web  app 中(网页中的word excel等)
# 数据存储
localStorage.setItem('d','xx')
//在浏览器中存储一些数据(只能是字符串)
localStorage.getItem('d')
//获取数据
localStorage.removeItem('d')
//删除数据
JSON.stringify()
//把对象转成字符串
// {a:1,b:2}   '{'a':1,'b':2} '
JSON.parse()
//把字符串转换为对象

2 input.checked=true||false
4 把数组排序，然后重绘  sore