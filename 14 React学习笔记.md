# React基础
## 初识React
-   是MVC框中的V层
-   有两个半Api
    *   createElement(后面不常用)
    *   createClass
    *   render
-   是创建一个虚拟的Dom元素(virtual),实质上是一个js对象,用js对象存储dom上的信息,因此比真实的DOM小的多,因此可以节省性能
-   React在有优化上
    *   渲染时的性能优化
    *   创建的是虚拟DOM,因此不会依赖于某个端(不依靠浏览器),如果要在某个端上进行渲染,则调用不同的render方法
-   使用React
    *   需要安装两个库
    *   一个是react.js
    *   另一个是react-dom.js

## createElent方法
-   作用:创建虚拟DOM
-   参数
    *   第一个参数:表示虚拟DOM的名称(如:p,div,h1....还可以是一个组件的名称)
    *   第二个参数:表示虚拟DOM上的一些必要的属性(如:id,class,title等等)
    *   从第三个参数开始表示该虚拟DOM中所有子元素(定义文本节点我们可以直接书写,不用createElement)
    *   返回值是虚拟DOM
-   例题:创建一个h1
```
    var h1 = React.createElement(
        'h1',
        {
            title:'这是一个标题'
        },
        '我是一个普通的h1标签'
    )
```

## ReactDOM中的render方法
-   是将虚拟DOm渲染到页面中的方法
-   第一个参数是虚拟iDOM
-   第二个参数表示真实的DOM容器元素
-   第三个参数是一个毁掉函数
-   例:
``` 
    var div = document.querySelecter('div');
    ReactDom.render('h1',div)
```

## 创建组件createClass
-   如果一个虚拟DOM复用多次,我们将它封装在一个组件中
-   创建组件的方法是createClass
-   参数是一个对象,对象中的属性和方法是对组件说明
-   有一个属性叫render方法,是将组建中的虚拟DOM输出的,所以我们将虚拟DOM定义render方法中
-   组件名称第一个字母大写
-   Render
    *   返回值是虚拟DOM树

#  JSX语法
### 基本概念
-   JSX语法就是让我们用书写html中元素标签方式来定义一个虚拟dom,在html中怎么书写元素,在jsx中就怎么书写虚拟dom元素
-   例如
```
    var Uls = React.createClass({
            render:function(){
                return (
                    <ul>
                        <li>女装 / 男装 / 内衣</li>
                        <li>女装 / 男装 / 内衣</li>
                        <li>女装 / 男装 / 内衣</li>
                    </ul>  
                )
            }
        });
        // var ul = (<Uls></Uls>);
        var ul = (<Uls />); //严格意义上是上面的写法,但是中间没有内容,可以简写成单标签
        ReactDOM.render(ul,document.getElementById('dv'));
```
-   但是js不支持这个语法,所以需要编译的插件,或者工程化编译
    -   工程化工具: babel2插件
```
    //创建一个jsx
    fis.match('**.jsx',{    //定义配置捕获所有jsx文件
        parser: 'babel2',   //引入插件
        rExt:'.js'          //更改后缀名
    })
```
    
#    插值
-   在React中,插值的语法是 { } , 在大括号中我们可以书写任意的表达式
-   在jsx语法中书写注释,必须写在插值符号中,还是多行注释的格式

```
    //插值练习,显示上午/下午好
    var header = React.createClass({
        render:function(){
            var username = 'zs';
            var data = new Date();
            return (
                <div className="header">
                    <div className="inner">
                        {/* 注释必须写在这里面 */}
                        <span> { username } </span>
                        <span> {new Date().getHours()>12 ? '下午好' : '上午好'} </span>
                    </div>
                </div>
            )
        }
    })
```

#   组件属性
### Props 属性
-   getDefaultProps 添加默认属性的
    -   一定有返回值,返回值就是默认属性


#   定义样式
-   不能是字符串形式,一定要是对象的形式
-   例如:
```
    var Title = React.createClass({
        render:function(){
            //定义样式对象
            var styles = {
                color : 'red',
                fontSize: '12px',
                WebkitBoxShadow: '10px 10px #000'
            }
            //添加样式
            return (<h1 style={ styles }>女子暴打鳄鱼</h1>)
        }
    })
    //将组件渲染到页面
    ReactDOM.render(<Title />, document.getElementById('dv'));
```


#   状态组件 state
### 无状态组件
-   如果组件被创建并渲染到页面后不再更改,这类组件在创建之初为其添加一些属性即可完成样式行为的控制,则称为无状态组件

### 有状态组件
-   如果组件创建后会根据用户的不同交互产生不同的样式或行为,这一类称之为有状态组件,组件处于哪种状态是由用户决定的

### state
-   state通常是在产生交互的时候产生的,因此它的改变永远伴随着一个交互
-   每次state , props的改变都会执行一次render方法来重新渲染组件,组件是否更改是由虚拟DOMM有没有改变来决定
-   getInitialState设置的,设置方式同props一样通过return来设置的
-   在组件内部改变状态我们通过setState方法来改变
-   setState方法调用会触发render方法来渲染

#   事件
-   在react中定义一个事件跟js中为元素绑定事件是一模一样的,是通过on+事件名称定义的
-   事件都有回调函数,通常将事件定义在组件内部,通过this来添加事件回调函数
-   