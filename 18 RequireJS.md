# RequireJS
-   是一个javascript模块加载器,使用RequireJS加载模块化脚本将提高带啊的加载速度和质量
-   作用
    *   实现js文件的异步加载,避免网页失去响应
    *   管理模块之间的依赖性,便于代码得编写和维护
-   使用
```
    <script src="require.js" data-main="实际要用的js路径"></script>
    //这里的data-main是固定写法,作用是告诉RequireJS,让它帮我们自动引入我们要用的js文件(主模块)
```
-   RequireJS提供的全局函数 ==> require()
```
    require(['模块1','模块2','模块3'],function(){
        //主模块的代码下载这个函数里面
    })
    //第一个参数: 当前主要所依赖的模块,['模块1','模块2','模块3']就是这个主模块所依赖的3个模块
    //当require函数执行的时候,它就会帮我们异步加载这三个模块对应的js文件
    //第二个参数: 是个回调函数,主模块的代码就写在这里面,当着三个依赖的模块都被加载只有,这个函数才会执行
    //这个回调函数中的形参就对应依赖的三个模块所对应的对象
    
    //注意: 模块的地址是相对于html的
    
```
-   lodash
    *   是一个插件,可以在Require中使用
    *   从数组中随机取一个值
    *   _sample(arr);

-   RequireJS的方法
    -   注意事项
        *   require函数中的路径是相对于引入RequireJS的html所在路径
        *   define函数中的路径是相对当前文件的所在路径
        *   别名: 配置时不要写后缀
        *   别名: 路径是相对当前文件的路径
    -   下载
        *   cnpm i requirejs --save-dev
    -   在html中的引用
        *   直接引用require.js文件
```
    <script src="./node_modules/requirejs/require.js" data-main="./js/main.js"></script>
```
    -   基本的引用过程
        *   引用插件
```
    //代码从这里开始执行
    //配置别名
    require.config({
        //路径默认是根据当前文件的相对路径
        //通过baseUrl可以修改默认的路径
        baseUrl:'./node_modules',   //这里的./是相对于html的
        paths:{
            //配置jquery,其名字不可以改,其他插件名字可以改
            //最后的后缀名不要
            //jquery:'../node_modules/jquery/dist/jquery',
            jquery:'jquery/dist/jquery',    //配置了baseURL后此处不用./
            //名字可以自定义
            lodash: 'lodash/lodash'         //配置了baseURL后此处不用./
        }
    })
    require(['jquery', 'lodash'], function ($, _) {
      // 这里就可以使用$和_，他们分别是jquery和lodash提供的对象
      // 这里的代码只有在jquery,和lodash都加载完成之后才会执行
      console.log(_)
    })
```
        *   引入自定义的js文件
```
//main.js的代码
    var obj = {a: 18}
    require([
      '../node_modules/jquery/dist/jquery.js',
      '../node_modules/lodash/lodash.js',
      './js/calc.js'], function ($, _, obj) {
      // 这个回调函数是，当它所依赖的这几个模块全都加载完成之后执行！
      // console.log($)
      var arr = ['小明', '小红', '小月']
      console.log(_.sample(arr))
      console.log(_)
      console.log(obj)
      console.log(obj.add(1, 1))
      console.log('%c' + obj.add(1, 1), 'color:red')
    })
//clac.js里的代码
    // 这个模块完成加减法计算
    // 除了主模块之外，其他的模块中需要使用define函数(也是RequireJS提供)
    // 写法和require函数相似
    // 假设我们这个calc.js模块不依赖于其他模块，代码如下：
    
    // 注意: 这里加载依赖模块时的路径中的 . 是相对于当前文件所在路径
    define(['./scroll.js', '../node_modules/jquery/dist/jquery.js'], function (obj, $) {
        // console.log($)
        // 把这个模块的代码写在这个函数里，当这个模块被加载时，这个函数就会执行
        // window.alert('我执行了!')
        console.log('我执行了')
        console.log(obj)
        function add (x, y) {
            return x + y
        }
        function sub (x, y) {
            return x - y
        }
        // 这里，如果想让别的模块使用到这里的局部的两个方法，需要return 出去
        // 注意: return  的值必须是对象
        // 别的模块在引入它时，这个对象，会被自动传到回调函数中
        // require(['calc.js'], function (obj))
        return {
            add: add,
            sub: sub
        }
    })
//scroll.js里面的文件
    // 这个模块完成轮播图功能
    // 定义模块
    // 除了主模块，其他模块都需要使用define函数
    define(function () {
      function slideShow () {
        console.log('轮播图功能完成了')
      }
      return {
        slideShow: slideShow
      }
    })
```

### define
    *   当前js不依赖其他模块时用define
    *   除了主模块,其他模块都需要使用define
    *   define(function(){ window.alert(123) })
    *   require与define的使用区别
        +   require在入口的文件中使用
        +   define在后面文件中都可使用
        +   使用的方法都一样

### 引用bootstrap的时候注意项
-   boorstrap是依赖于jQuery的,所以引用bootstrap的时候得先引入jquery
-   但是不能直接引用,需要告诉require, bootstrap是依赖jquery
```
     require.config({
        //配置别名
        baseUrl:'./node_modules',
        paths:{
            jquery:'jquery/dist/jquery',   
            bootstrap: 'bootstrap/dist/bootstrap' 
        },
        
        //配置shim,用于不支持require.js规范的插件
        //专门用来配置非规范化(rquirejs规范)的模块
        shim:{
            //这里写的bootstrap是需要和paths里面的名字保持一致
            bootstrap:{
                //用来表示依赖于....
                deps:['jquery'] //用数组的原因是可能不仅仅依赖于一个包
                //这里写的jquery是需要和paths里面的名字保持一致
            }
        }
    })
    //引用
    require(['bootstrap'],function(){
        
    })
```
-   配置shim
    -   告诉RequireJS我们引入的包依赖于谁
    -   如果引入了一个非模块化的模块,
    -   deps => 告诉requirejs,当前对象依赖于xx
    -   exports => 告诉requirejs, 当前文件中的xx对象传递到requirejs中
-   underscore.js
    -   和lodash一样的功能
    -   
    -   
   aaaa