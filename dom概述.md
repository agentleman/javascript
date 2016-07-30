# SOM是什么

Document  Object  Modal(文档对象模型)


我们在页面中看到的div,span,p,h1等等元素或文字，
在javascript眼中都是一个对象

# 辅助界面动画应用  还有  web应用
#从一个web应用的开发说起
 第一步 从一个web中选取元素出来，
 当我们的代码在浏览器中去运行时
 浏览器已经帮我们创建了很多对象，
 对象中有很多方法供我们使用
 这些东西都在一个叫做windows的全局变量里


 window对象中的属性，可以省略window. 去调用


 选取元素，我们从window.document开始

 ## 选取元素的方式

 * document.querySelector()
 * document.getElementById()
 * 
 * 
 *
 *

 这些方法的返回结果是什么？
 前俩个的返回结果是一个代表了页面中某个元素的对象，叫做DOM对象

 后四个返回结果是一个类数组对象，我们叫他dom集合
 var  obj={
 0:DOM对象，
 1：DOM对象，
 ·······
 }


 ## DOM对象中常用的属性和方法


 ### Object

 * toString()
 * valueOf()                                ///mdn + 关键字  搜索window对象

 ### EventTarget

 * addElementListener
 * 
 *
 ###  Node

我们能从每个DOM对象身上取到自己的相邻或父或子节点
 
 * ChildNodes        DOM集合(NodeList)
 * cloneNode         DOM对象默认是false 只取出这个元素不含有子元素；若是cloneNode(true)
                     会取出这个对象以及他的子元素
 * parentElement
 * parentNode
 * previousSibling
 * firstChild
 * lastChild
 * nextSibling

 描述节点(几乎所有的DOM对象都是一个节点，用着三个属性来描述一个节点)
 * nodeName
 * nodeType
 * nodeValue

 DOM对象提供了一些操作节点的方法
 采用  父DOM对象.xxx(dom对象)这种方法(可以链式调用)
 * contains()      判断一个节点包不包含另外一个节点
 * appendChild()   box.appendChild(el).style.color='red' (可以使用)
 * hasChildNodes() 返回布尔类型 // el.children.length
 * insertBefore()  返回你插入的那个对象
 * removeChile()   返回被移除的对象
 * replaceChild()

 取出节点的文本内容(会过滤掉标签)
 * textContent

 ###   Element
 元素和节点的区别
  带标签的既是元素又是节点，不带标签的比如div内部的文字注释等，它们只是节点，不是文字

从一个DOM对象开始获取子，父，兄弟元素
  * children  
  对元素属性的操作(HTML元素的属性就是头标签里的那些k=''中的k)               
  * classList     add  remove   toggle 
  * className
  * id
  * firstElementChild
  * getAttribute()
  * hasAttribute()     ****** 判断元素头标签中有没有某个元素  布尔值***************
  * setAttribute()            没有返回值，只是一个操作
  * removeAttribute()         没有返回值，只是一个操作

    获取视窗坐标或其他和位置相关的信息
  * getBoundingClientRect()   获取该元素的视窗坐标{top:1,bottom:1,width:1,height:1}
  * scrollLeft                可读写
  * scrollTop                 可读写
  * clientWidth               一般用来结合document.documentElement.clientWidth  
  * clientHeught  

快速从DOM中获取元素的方法
  * document.body
  * document.head
  * document.title
  * document.documentElement    代表了整个html标签的一个对象
  * getElementByClassName()
 从某个DOM对象开始，可以缩小范围去找元素
  * getElementByTagName()
  * querySelector()
  * querySelectorAll()
 
  * previousElementSibling
  * lastElementChild
  * nextElementSibling

  * outerHTML   
  * innerHTML              可读写 能设置某个某个DOM对象内部的html结构 
    Waring:   不要用这种方式追加元素el.innerHTML += '<div></div>' 
  * innerText             剥离标签，直接获取文本  
   
  * tagName
  ### HTMLelement
   * innerHTML
   * innerText
   实时获取元素信息   不带“px”只能得到数字
   * offsetHeight
   * offsetWidth   
   * offsetLeft
   * offsetTop
   * offsetParent     具有定位属性(非static)的祖先元素  DOM对象


    操作元素的行内样式
   * style            可读写的  实时获取元素行内样式的值 不会去计算css文件中样式的值
   ## HTML xxx Element

   * value
   * checked
   * focus()
   * src


## 添加事件的俩种方式及其区别

```javascript
  //使用onxxx
  var el=document.getElementById('box');
  el.style.color='red';
  el.onclick=(function(e){
      return  function(){
  }
  })();
  el.addEventListener('click',function(e){

  },false);
  false  冒泡执行
我们给DOM对象的哦那onclick属性赋值，值 为一个函数
和普通的对象赋值不一样
JS会告诉浏览器，密切关注这个元素，如果有人点击它，帮我把这个函数运行一下
运行函数的时候给我传一个参数，参数为一个对想；
对象中药详细记录这次点击的一些信息  这个对象呗称为事件对象
```
  事件  事件对象   添加事件的方式  不同方式之间的区别
  事件流  事件默认行为  阻止事件流  事件委托(委派)


 添加事件的俩种方式及其区别：
1. 一些H5事件并没有onxxx这个版本
2. onxxx  再赋值一次，会覆盖上次赋值的那个函数，addEventListener没有这个问题，他可以给一个
      事件添加多个函数，按照添加顺序逐个调用函数.

###  自定义事件
```
var  threeclick= new  Event('threeclick');
var  var  box=document.querySelector('.box');
   box.addEventListener('threeclick',function(){
   console.log(1);
   });
   box.addEventListener('click',function(){})
   box.dispatchEvent(threeclick);
```      

### 阻止事件冒泡和阻止事件默认行为
 yi.addEventListener('click',function(e){
 console.log(1);
 e.stopPropagation();//用这个来阻止事件冒泡
 });

 阻止事件默认
 要从事件的根源去阻止默认行为
 document.addEventListener('mousedown',function(e){ //阻止dom中的mousedown事件keyup 
 e.preventDefault();
 })

 回调函数
 当我们吧函数x作为参数传给函数y
 函数y内部有对函数x的调用
 我们把函数x叫回调函数

 var  arr=[1,2,3,4]
 arr.forEach(function(v){
 console.log(v)
 })


 var  arr = [];
 arr.forEach(function(v){
 console.log(v)
 })


 var  arr=[];
 forEach= arr.forEach;
 filter= arr.filter;
 var els=document.

 forEach.call(els,function(v){
 console.log(v)  v 就是DOM集合中的DOM对象
 })

 课程体系
 html - css-ECMAscript3-5  --Ajax  jQuery- phpcms   -css3+响应式布局 sass 动画 -html5 domAPI js
 -Angular.js+ionic
 -工作流程 用Hbuiler+前端技术制作手机App
 -微信二次开发   微信API