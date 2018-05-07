# 第一天

## 视口

---

    -   在移动端的网页布局并不是基于窗口，而是基于视口，一般宽度为980
    -   故需先设置移动端视口宽度为手机屏幕宽度
    -   设置视口
            <meta name = "viewport" content = "width=device-width,maximum-scale=1.0,mininum-scale=1.0,initial-scale=1.0,user-scalable=no"
        快捷生成： meta:vp + TAB

## 响应式

---

    -   定义：针对任意设备，网页内容都可以进行完美布局的一种显示机制
    -   步骤：
        -   设备检测
            -   使用C3的媒体查询技术来检测设备宽度
                @media screen ad (min-width:1200px){    //最小1200px宽度的
                    div{
                        background-color = "pink";
                    }
                }
            -   大屏  >= 1200px
                中评  992-1199
                pad   768-992
                手机  <= 768
        -   根据不同的宽度来改变网页布局

## Bootstrap

---

    -   container   带有版心的布局容器
    -   container-fluid     宽度100%的布局容器
    -   栅格系统
        -   .col-xs     手机屏幕
        -   .col-sm     平板
        -   .col-md     中等屏幕
        -   .col-lg     电脑屏幕
        -   .row        行
        -   .col-xs-1   列 (一行最多12列)
        -   col-md-push-3   向右偏移3列
        -   col-md-pull-3   向左偏移3列
        -   col-lg-offset-n     整体向右偏移n列
        -   栅格可以嵌套
    -   响应式栅格

## Bootstrap基本内容

---

    -   <h1>主标题<small>副标题</small></h1>
    -   文字对齐方式
            class="text=left"
            class="text=right"
            class="text=center"
    -   表格
            -   class="table"           使表格有横向线
            -   class="text=center"     文字居中
            -   class="table-striped"   隔行变色
            -   class="table-bordered"  表格边框
    -   表单
    -   按钮
    -   图片
    -   浮动
            pull-left       左浮动
            pull-right      右浮动
            clearfix        清除浮动
    -   显示/隐藏
            show / hide
    -   响应式工具
    
    
# 第二天

##  Touch事件

---

    -   touchstart      触屏开始
        -   e.targetTouchs:     记录目标元素的触屏数据      （推荐使用）
        -   e.changedTouchs:    记录最后一次改变的书
        -   e.touchs:           记录屏幕上所有的触屏数据
    -   touchmove       触屏移动     
    -   touchend        触屏结束
        -   触屏结束只有e.changedTouchs会记录数据
        
## jQuery获取元素宽度的方法

---

    -   width()             获取内容的宽度
    -   innerwidth()        获取内容+padding的宽度
    -   outerwidth()        获取内容+padding+border的宽度
    -   outerwidth(true)    获取内容+padding+border+margin的宽度
    
    
# 第三天

## 百分比布局

---

    -   rem
        -   根据设计稿写出静态页面，以px为单位
        -   将px换成rem
        -   根据屏幕宽度，动态设置rem的值

## less



# 第四天    

## 京东

---

    -   去除移动端点击高亮效果
        -   -webkit-tap-highlight-color: transparent;
    -   清除在移动端**表单**可能会出现阴影高亮3d的效果
        -   -webkit-appearance: none;
    -   transtionend    过渡结束事件
        -   webkitTransitionEnd     兼容写法
    -   animationend    动画结束事件
        -   webkitAnimationEnd  兼容写法


# 第五天

-   做京东的移动页面

# 第六天

## tap事件

---

    本质是touch事件封装的，用来在移动端代替click事件
    
```
<script>
        var startTime = 0;
        var flag = false;
        var box = document.querySelector(".box");
        box.addEventListener("touchstart",function () {
            startTime = Date.now();
        });
        box.addEventListener("touchmove",function () {
            flag = true;
        });
        box.addEventListener("touchend",function () {
            if(!flag && Date.now()-startTime < 200){
                alert("click");
            }
            flag = false;
        });
</script>
```


## tap插件封装

---

    -   函数名：定义在全局的变量或者函数，会造成全局污染
        解决：使用命名空间
            var touch = {           //创建
                tap:function (){
                    
                }
            };
            touch.tap() //调用

## e.target

---

    -   事件对象，可以找到出发事件的最小的事件源
    
## zepto.js

---

    -   相当于移动版的jQuery，没有兼容代码，体积更小
    -   每个api都是独立的，需要单独引入

## swiper

---

    -   










