# 第一天
1、页面中的顶级对象不是html，是document

2、xml

    a、xml是一个标签文件，标记语言（都是标签）
    b、xml文件中的代码都是小写的，尽可能的是成对的（有开始就有结尾）
    c、hxml就是写html的时候遵循xml的标准
    d、hxml侧重展示信息
    
3、html中所有的标签都可以叫元素，也可以叫对象

4、DOM的作用

    操作页面中的元素的
    
5、文档

    指的是html文件或者是xml文件
    
6、节点node

    页面中所有的内容都叫节点（标签，文本，属性）
    
7、元素element

    页面中所有的标签叫元素
    
8、根元素（根节点）

    最外面的html标签
    
9、API

    一套工具（或者方法）
    
10、DOM的级别

    a、初级阶段
    b、DOM1规定了节点的类型Node （现在用的）
    c、DOM2新增了一个方法，但是很多浏览器不支持
    d、DOM3大多浏览器都没有支持
    
11、document.getElementById("id名").事件=function (){}

12、document.getElementsByTagName("标签名")[第几个].事件=function (){}

13、innerText

    html中的成对的标签都可以使用它来改变文本内容
    
14、html中的属性如果只有一个，并且就是自己，此时在DOM的操作中，设置该属性的时候用true/false 

15、DOM：document object model 文档对象模型
    
# 第二天

1、return false

    给a标签的onclick的事件加上return false，可以让它不跳转，且地址可以不变
    
2、javascript:void[0];

    给a标签的地址栏写javascript:void[0];和javascript：；是一样的效果，阻止跳转
    
3、document.getElementsByName("名")[第几个].事件=function (){}

4、document.getElementsByClassName("类名")[第几个].事件=function (){}

5、获取焦点
    onfocus
    
6、失去焦点
    onblur
    
7、键盘按键事件
    onkeyup 
    onkeydown

# 第三天

1、innerHTML和innerText的区别

    a、在设置文本内容的时候，两者一样
    b、innerText无法创建标签，innerHTML可以创建标签
    c、如果设置标签中的文本内容，两者都可以
        如果获取一个标签中的文本内容，两者都可以
        如果是设置/获取标签中的标签和文本内容，用innerHTML
        
2、一个浏览器不支持这个属性，得到的结果是undefined
    这种判断能力叫做能力检测
    
3、setAttribute和getAttribute

    语法：对象.setAttribute（("自定义类名"，值)）
          对象.getAttribute（("自定义类名")）
          
4、lastElementchild   

5、节点
    a、nodetype节点类型
        1、标签
        2、属性
        3、文本
    
    b、nodeName节点的名字
        标签：标签的名字
        属性：属性的名字
        文本：text
    
    c、nodeValue节点的值  
        标签的nodevalue是null，
        文本的nodevalue是文本内容
    
# 第四天

1、移除元素的属性

    removeAttribute("属性名")；
    
2、创建元素的三种方式

    a、document.write("标签及内容");        //直接写到文档中
    b、对象.innerHTML="标签及内容";         //直接把内容写到某个标签中，可以是标签或者文本和属性
    c、document.createElement("标签名字");  //直接创建，需要配合appendchild使用
    
3、 appendchild 追加

    对象.appendchild(对象名);
    
4、insertBefore 在前面添加一个元素

    对象.insertBefore(节点，子节点);    //在子节点之间加入节点
    
5、appendchild 只添加一个元素

    if(!节点){
        则创建节点
    }












