# 第一天

## 服务器
    能够提供某种服务的机器称为服务器
## 客户端
    具备向服务器索取服务能力的终端
## 前端开发
    以浏览器为宿主环境，结合HTML，CSS，javascript等技术而进行的开发。
## ip地址
    查看本机ip的方法：在命令窗口输入ipconfig　ifconfig
## DNS
    记录ip和域名的对应关系的
## 域名
    就是ip包的外壳，在命令窗口ping一下ip地址后可以出现对应域名
## 访问网址的过程
    -   当在浏览器地址栏输入域名后，浏览器会先查找本机host文件中ip域名的对应关系，如果找到ip直接请求服务器
    -   如果没有找到，再去查找DNS服务器，返回了ip再请求服务器
    -   如果还没找到，则报错DNS错误
## 端口
    每个程序都有自己的端口
## php基础

---

    -   php是一种创建动态交互站点的强有力的服务器端脚本语言
    -   php代码放置位置
        <?php
            echo 'helloword';   //必须有分号
        ?>
        写在代码块外面的会被php执行程序直接忽略，最后会返回给浏览
    -   echo作用
        -   可以把服务器的数据输出到浏览器
        -   只能输出简单数据类型
    -   复杂数据类型的输出
        -   print_r();
        -   var_dump();
    -   变量
        -   以$开头，字母/数字/下划线组成，不能以数字开头
        -   区分大小写
    -   数据类型
        -   字符型
            -   如果双引号中包裹的是变量名，此时会输出该变量的值；
            -   单引号则把该变量当字符串输出；
        -   整型
            -   就是整数
        -   浮点型
            -   是小数
        -   布尔型
            -   true输出的是1
            -   false输出的是空字符串
        -   数组
            -   $arr = arry(1,2,3,4,5);
                print_r($arr);
                var_dump($arr);
            -   根据索引获取单个元素
                    echo $arr[2];
            -   获取数组长度
                    echo count($arr);
            -   关联数组
                $info = array(
                        "name" => "zs",
                        "age" => 18,
                        "sex"=> "men"
                    );
                -   输出关联数组
                    var_dump($info);
                -   输出数组中的某个值
                    echo $info['age'];
        -   对象
            -   
        -   NULL
    -   字符串拼接
        $str1.$str2.'你好'.$age.'岁'
    -   设置编码格式utf-8
        header('content-Type:text/html；charset=utf-8')    //没写完
    -   函数
        -   定义函数
            function say($name){
                echo 'hello'.$name;
            }
            say('world');
    -   foreach遍历关联数组
        $info = array(
            "name"=>"zs",
            "age"=>18
        );
        foreach ($info as $key => $value){
            echo $key.'--'.$value.'-----';
        }
        
## 表单提交数据

---

    -   action: 把表单指定提交给哪个后台处理程序
    -   method：指定表单数据的提交方式get/post
    -   name属性是必不可少的，后台通过name属性来获取前端传的数据
    -   $_GET 可以用于获取get方式传递的数据
    -   $_POST  可以用于获取post方式传递的数据
        例：    
            $name=$_POST['name'];//获取用户名
            $pwd=$_POST['pwd'];//获取密码
            if($name == 'admin' && $pwd == '666666'){
                echo '登陆成功';
            }else{
                echo '登陆失败';
            }
    -   get和psot的区别
        -   get请求会在url地址后面拼接数据，数据量只有4kb，速度快，不安全
        -   post相对安全点，对数据量没有限制，可以上传图片
    -   $_FILES 用于获取传递的文件
    -   move_uploaded_file(filename,destination)
        -   第一个参数是要转移的文件
        -   第二个参数是转移的路径
    

# 第二天

## php的动态渲染

## http协议

---

    -   常见协议
            http协议，https协议     ==》    超文本传输协议
            ftp协议                 ==》    文本传输协议
            smtp协议                ==》    简单邮件传输协议
    -   http协议主要由请求request 和 响应respose 构成
    -   请求方式
        -   get
        -   post
        -   put
        -   delete
    -   请求报文
        -   请求行
        -   请求头
        -   请求主体
    -   响应报文
        -   状态行
        -   响应头
        -   响应主体

## Ajax编程

---

    -   asynchronous
        javascript
        and
        xml
    -   作用：在页面不刷新的情况下请求服务器，局部更新页面数据
    
    
# 第三天

## XMLHttpRequest详解

### API介绍

---

    -   xhr = new XMLHttpRequest(); //新建xml对象
    -   xhr.open()
    -   xhr.setRequestHeader(); //get方法可以省略这一步
    -   xhr.send();
    -   xhr.onreadystargechange //服务器返回数据完成后的事件

### XML

---

    -   可拓展的标记语言
    -   与HTML的共同点和不同点
        -   共同点
            -   都要使用标签来标记语言
            -   都具有自我描述性
            -   语法类似
        -   不同点
            -   XML标签可拓展 自定义
            -   功能不同，HTML用于展示数据，XML用于存储和传递数据
    -   语法规则
        -   必须有一个根标签
        -   标签不可交叉嵌套
        -   区分大小写
        -   不经饿有空格，数字开头
        -   注释和HTML一样
        -   引号是双引号
        
### JSON

---

    -   JavaScript Object Notation
    -   另一种轻量级的文本数据交换格式，独立于语言 ==> 本质上是一种特殊格式的字符串
    -   js对象转成json字符串
        var obj = {};   //js对象
        var str = JSON.stringify(obj);  //转成json
    -   字符串转成js对象
        str1 = '';  //字符串 
        str1 = JSON.parse(str1);    //转成js对象
    -   php中将数据转成json字符串
        $info = json_encode($info);
        echo $str;
    -   php中将json字符串转成对象
        $str = json_decode($str);
        echo $str -> name;
    

# 第四天

## jQuery中其他的几种ajax方法(不常用)

#### $.GET()     //用法同$.ajax()
    只能发送get请求

#### $.post()     //用法同$.ajax()
    只能发送post请求

#### $.getJSON()    //用法同$.ajax()
    从服务器获取json数据，会自动调用JSON。parse()方法

#### $.getScript()   //动态引入js文件
    例：
```
    $('button').click(function(){
        $.getScript('test.js',function(){
            say();
        })
    })
```
#### $.load()    //可以将另一个页面的内容加载到当前的页面中
    例：
```
    $('button').click(function(){
        $.('.box').load('test.html',function(){
            alert('ok');
        })
    })
```

## 表单序列化   //jQuery方法，可以直接将表单内容转化为请求报文的请求行的内容格式

---

    var formData = $('#form').serialize();
    console.log(formData);  
    //输出结果：name=zs&pass=123&repass=123;

## 案例

---

    -   注册页面（重点）
    -   

## 模板引擎

---

    -   作用：快速动态生成结构及内容，代替了字符串的拼接
    -   ArtTemplate ==> 在各个流行模板引擎中，其速度最快
        
    -   ArtTemplate语法
        <%  %>  中间写语法格式
        <%= %>  输出表达式的值
        
1   定义模板
       
```
     <script type="text/template" id = "tmp">
        <h1> <%= title %> </h1>
        <ul>
            <% for(var i=0; i<list.length; i++){ %>
                <li> <%= list[i] %> </li>
            <% } %>
        </ul>
     </script>
```
2   引入模板引擎插件
    
```
    <script src="template-bative.js"></script>
```
3   引用
```
    //参数1是模板ID，参数2必须是对象
    var html = template('tmp',data);
    console.log(html);
```

## 瀑布流插件

---

    -   console.log($.fn);  可以查看jQuery里面所有封装的函数
    -   封装jQuery插件本质上就是向$.fn中添加方法
    -   $.extend(对象1，对象2);     //生成一个新对象
        //可以将两个对象扩展成一个对象，相同属性=》后面覆盖前面，不同属性=》都保存
    -   瀑布流插件的封装（难点）



# 第五天

## button按钮

---

    -   <input type='submit' value='注册'/> //点击后表单会刷新
    -   <input type='button' value='注册'/> //点击后表单不会刷新
    -   <button>按钮</button>   //点击后表单会刷新

## jQuery中attr（）与prop（）方法的区别

---

    -   对于HTML元素本身就带有的固有属性，在处理时，使用prop方法。
    -   对于HTML元素我们自己自定义的DOM属性，在处理时，使用attr方法。

## 接口化开发

---

    -  其实是指一个接口对应一个功能，并且严格约束了请求参数和响应结果的格式
        这样前后端在开发过程中，可以减少不必要的讨论，从而并行开发，
        可以极大的提升开发效率，
        另外一个好处，当网站进行改版后，服务端接口只需要进行微调；
    -   接口文档
        可以让前端开发独立进行，不用等待后端返回数据


## 同源&跨域

### 同源

---

    -   是浏览器的一种安全策略，协议，域名，端口完全相同
        //简单来说就是同一个服务器内部的页面

### 跨域

---

    -   协议，域名，端口不完全相同，即服务器不同
    -   跨域会受到很多的限制
        -   不允许DOM操作(了解)
        -   不能进行ajax请求（重要）
            //如果同一个公司有子服务器，但是与主服务器交流据属于跨域，想要解决这个问题，就是解决跨域问题；
    -   跨域解决方案
        -   document.domain + ifeame    //主域名相同时可以操作，但是兼容不好
        -   window.name + iframe
        -   location.hush + iframe
        -   window.postMessages + iframe
        以上都是有兼容问题，了解即可
        
        **常用的是JSONP方法**
        获取天气案例
    -   JSONP原理   JSON with Padding   **重点**
        -   本质是利用<script src="" ></script>标签具有可跨域的特性，
            由服务器返回一个预先定义好的javascript函数的作用，
            并且将服务器数据以该函数参数的形式传递过来，
            此方法需要前后端配合完成；
        -   当dataType设置为jsonp之后，$.ajax内部没有使用XMLHttpRequest，
            而是使用了script标签的特性来请求服务器
        -   跨域不能进行ajax请求，但可以请求图片和js文件，原因是href及src具备跨域条件
        -   原理总结：
            -   当$.ajax方法的dataType设置为jsonp之后，$.ajax内部没有使用XMLHttpRequest；
            -   而是使用了script标签的特性来请求服务器；
            -   会将url地址赋值给script标签的src属性；
            -   且传输的数据拼接在url地址的后面；
            -   并且还会传递给后台一个已经定义好的方法名；
            -   后台接受到请求后，会获取到前端传递的方法名；
            -   然后把数据以方法参数的形式拼接起来；
            -   最后把拼接好的字符串返回给前端浏览器；
            -   前端接收到后台返回的字符串形式的方法调用，把字符串当作js解析；
            
## XMLHttpRequ 2.0

### 设置超时

---

    -   xhr.timeout = 2000  //单位ms
    -   xhr.ontimeout = function(){
            alert('请求超时，请重试');
        }

### FormData对象    //用于管理表单数据

---

    -   var formData = new FormData();  
    -   只能以post形式传递，且不用设置请求头，浏览器会自动设置一个合适的请求头
    -   xhr.send(formData);//请求主体
    -   除了可以发送表单数据，还可以手动再添加
        formData.append('data','2017-6-7');

### 上传进度

---

    -   xhr.upload.onprogress = function (e){ //监听上传的进度
            var value = e.loaded（当前进度） / e.total(总进度);
            document.querySelector('.in').style.width = value*100 + "%";
        }

# 第六天

## ajax兼容问题

---

    -   IE7以下不支持json对象
        -   解决方法：引入一个插件
    -   xhr对象
        -   解决方法：
```
    if(XMLHttpRequest){
        xhr = new XMLHttpRequest();
    }else{
        xhr = new ActiveXObject('Microsoft.XMLHTP');
    }
```

        
## 同步和异步的区别

---

    -   xhr.open('get','test.php',ture);//当第三个参数为true时为异步（默认为true）；
        前面的代码没执行，后面的也会执行，用户体验好
    -   为false的时候为异步，前面的代码没执行，后面的也不会执行，用户体验差，
        且没有xhr.onreadystate事件
        
## 服务端跨域

---

    -   在服务端设置header('Access-Control-Allow-Origin:*')；
        但是所有人都可以访问，安全性不行
    -   header('Access-Control-Allow-Origin://www.study.com')；
        只有www.study.com的主域名的可以访问
    -   图灵机器人都是设置了服务端跨域，可以不用jsonp

