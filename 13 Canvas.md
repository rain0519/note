# 第一天

## 补充
-   单线程与多线程
-   单核与多核
-   单任务与多任务
-   数据简介
    *   数据在内存中只有数据
    *   ASCII码(7个二进制位表示) 0 - 127
    *   0-31位: 属于控制字符,不可见(如制表符)
    *   32位是空, 32以后的都是可见字符
    *   数字从48开始,0,1,2...其范围是48-57
    *   小写英文字母从97开始
    *   大写英文字母从65开始
-   unicode编码
    *   国际通用,现在使用的都是unicode编码
    *   前128个和ASCII编码一样
    *   但是有一个缺点,其所有字符都是由两个字节组成,在表示英文的时候很浪费
    *   所有引入了UTF系列
-   UTF-8
    *   UTF-8前128个都是一个字节,简体中文使用3个字符
    *   亚洲地区将中文,韩文,日文字符集常常称为CJK字符串

## Canvas基础
#### 什么是canvas
-   是HTML中的一个用于展示图片的标签
-   这个标签不能绘图, 是用来展示图片的, 利用这个标签来得到绘图上下文

#### 绘图上下文
-   就是绘图工具
-   由于绘图工具与画布有直接关系,因此不同的画布需要获得不同的绘图上下文
-   一个canvas对应一个工具,工具只能给这个canvas绘图

#### 如何使用canvas
-   语法: <canvas></canvas>
-   默认宽高: 300*150
-   宽高的意义: 是指canvas有对应的几个像素点
    *   宽300,则表示有300个像素
    *   高150,则表示有150个像素
    *   默认canvas是一个300 X 150的点阵屏幕
-   点阵图和矢量图
    *   点阵图是利用像素点一个一个的连接在一起形成图形
    *   矢量图是利用数学函数描述图形的轨迹,在图片放大的时候,轨迹会进行重新绘制
    *   使用canvas画出来的都是点阵图
-   设置canvas的宽高
    *   必须使用width和height,不能使用css的样式
    *   如果使用的css来设置,是将canvas进行拉伸处理
-   如何获得绘图工具
    *   canvas.getContext('2d');    ==>  绘图上下文
    *   获得2d图形的绘图api(绘图工具)
    *   canvas.getContext('webgl');
    *   绘制3d的图像(three.js)

## 计算机中的坐标系
#### 坐标轴
-   X轴水平向右,Y轴垂直向下
-   在绘制点的时候,需要注意的是计算坐标

#### 怎么绘制
-   在得到绘图上下文后,只需要使用工具即可
    *   落笔: context.moveTo(x,y);
    *   绘制直线: context.lineTO(x,y);
    *   在canvas中绘图与真实绘图一样,当你落笔后绘制到什么位置,就表示停到那个位置
    *   context.stroke() ==> 描线
    *   context.fill() ==> 填充

## Canvas的绘图原理
-   线宽设置奇数的时候会发虚

## Canvas的API
-   落笔: context.moveTo(x,y);
-   绘制直线: context.lineTO(x,y);
-   context.stroke() ==> 描线
-   context.fill() ==> 填充
-   context.lineWidth 设置线宽,不用带单位 默认线宽是1;
-   直线连接部分的处理方式
    *   属性:lineJoin
    *   取值: rounnd圆的, bevel平的, miter尖的(默认)
-   直线的闭合问题
    *   closePath 实现闭合路径,将本次绘制的起点和终点连接起来
    *   首推使用closePath,不推荐描线来闭合
-   绘制多样式的图形
    *   凡是在绘制过程中,用于描述绘制颜色,尺寸,样式是否为描边,是否为填充,都称为样式
    *   凡是要更改样式就需要调用一次context.beginPath方法
    *   注意:每次begin.Path的时候,前面的所有设置的样式都会被继承
-   单独改变描线的颜色和填充的颜色
    *   storkeStyle
    *   fillStyle
    *   取值与css的取值一样
-   绘制虚线
    *   设置lineDash即可
    *   调用 setLineDash 和 getLineDash 可以设置与获得当前虚线的样式
    *   虚线的样式使用 [ ] 来描述, 里面的数字表示实现部分与空白部分的长度
    *   一般表示等款虚线 [ 5 ] 
    *   设置 [ ] 可以把虚线设置成实线 

## 非零环绕原则
-   就是指图形在封闭曲线的情况下是否要填充的原则
-   在绘图的时候,复杂的图形填充需要引入非零环绕原则来判断一个区域是否需要填充
-   什么是非零环绕原则
    *   首先在不确定是否要填充的区域,随意的找一个点(找的时候尽量简单);
    *   由这个点向图形外面随意的作一条射线(尽可能简单);
    *   由这个点作为圆心,判断穿过这条射线的所有线以及其方向;
    *   将所有的顺时针方向计为+1, 将所有的逆时针记为-1;
    *   将所有的数字求和,如果结果为0,则不填充,结果非0,则填充;


# 第二天

## 绘制曲线
-   利用直线绘制曲线

## 常见的坐标图
#### 散点坐标图
-   每一个点的坐标是不规律的,需要根据数据进行描点

#### 等间距点线图
-    
#### 封装生成表格



# 第三天
## 绘制矩形(rectangle)
#### 在canvas中,矩形相关api有4个
-   context.strokeRect(x,y,width,height)    ==> 绘制一个描边矩形
-   context.fillRect(x,y,width,height)      ==> 绘制一个填充矩形
-   context.rect(x,y,width,height)  ==> 绘制一个矩形的描点,需要自己手动调用strke或者fill
-   context.clearRect(x,y,width,height)   =>  清除一个矩形区域,类似于橡皮擦

#### 如果在绘制描边矩形或填充矩形的时候需要控制其样式
-   直接使用strokeStyle或者fillstyle
-   要写在绘制矩形的前面
-   context.rect方法很少使用,其可以同时描边和填充

#### context.clearRect => 用的非常多
-   一般在擦除的时候可以设置一个矩形区域


## 清屏
-   利用clearRect (推荐使用)
    *   ctx.clearRect(0,0,cas.width,cas.heght);
-   cas.width = cas.width

## 绘制圆弧的方法 arc
-   一个非常重要的指标就是开角的大小
-   角度的规定
    *   将水平向右的方向作为0度方向
    *   将顺时针方向记为正角方向
-   另一个参数就是半径
-   在角度计算中,使用最多的单位是弧度
-   换算
    *   半径    radius
    *   角度    angle
    *   弧度    radian
-   arc的语法
    *   context.arc(x,y,r,start,end[方向]);
    *   ctx.arc(300,200,100,开始的弧度,结束的弧度);//简单的语法
    *   ctx.arc(300,200,100,开始的弧度,结束的弧度,true/false);//左后一个参数代表是否使用逆时针,true为使用,false为不使用,默认的是false;

## 计算圆上任意点的坐标
#### 公式
-   x = ox + r * Math.cos(角度)
-   y = oy + r * Math.sin(角度)

## 饼形图
#### 一些细节
-   起点在-90度的位置

## 文字
#### 设置属性
-   ctx.font = '50px 黑体'
-   strokeText( text, x, y)
-   fillText( text, x, y)
-   textAlign = left,right,center
-   textBaseline = top,middle,bottom



# 第四天
## 绘制图片
-   drawImage ==>语法  ctx.drawImage( img, x轴位置, y轴位置, 宽度, 高度 );
-   例:
```
    img = dpcument.createElement('img');
    img.src = url;
    img.onload = function () {
        ctx.drawImage( img, 100, 100, 100, 100 );
    };
```
-   如果需要等比缩放,需要计算比例 => 图片的原始高度/原始宽度 = 绘制的高度/绘制的宽度;
-   最常用的用法:
    *   ctx.drawImage(图片对象,图坐标x,图坐标y,图宽,图高,画布x,画布y,画布宽,画布高);
    *   作用是将图片指定区域绘制到画布指定区域

## 变换
#### 所谓的变换,全称是坐标系变换
-   指的是通过改变坐标系的位置,比例,与旋转角度来绘制特殊的图形
-   平移变换 ctx.translate()
    *   语法: ctx.translate(x,y);
    *   参数的意义: 表示坐标系水平方向与垂直方向的移动情况
-   旋转变换 ctx.rotate()
    *   语法: ctx.rotate(弧度);
-   伸缩变换 ctx.scale
    *   语法: ctx.scale(x,y);
    *   参数的意义: 表示水平方向与垂直方向坐标的伸缩比,类型是浮点数
    *   例如: ctx.scale(1,0.6);
-   矩阵变换 ctx.transform()
-   这几个方法的参数都是指的增量

## 变换后的擦除问题
-   擦除的范围是依照新坐标系来擦除的,原坐标的东西可能擦不到
-   需要重新计算坐标来擦除

## 环境
-   在绘制canvas的时候,凡是进行样式变换的设置,beginPath都会继承
-   如果调用ctx.save()方法的时候,可以将当前状态保存起来;
-   调用ctx.restore()方法以后,就表示回复到刚才save的时候的状态;
-   但是后面再beginPath,相当于从save之前进行继承,再save与restore之间的样式设置都不继承

## 优化
-   和DOM一样,频繁的canvas绘制会造成浏览器刷新,造成性能低下;
-   可以先将画布在内存中绘制出来,然后将画布将绘制到画布上;
-   用法和绘制图片一样

## 画布保存
-   ctx.ToDataURL(输出类型,输出图片质量);
-   输出类型 : 例如 image/png 或 image/jpeg
-   输出图片质量: 取值为0-1之间,1表示无损,必须使用image/jpeg或image/webp才起作用;

## Echarts