# npm
-   用来下载一些包的: jQuery , bootstrap ......都称之为包
-   npm install jquery //就会到npm这个工具所在的服务器自动下载jquery代码
-   注意点: 
    *   一般先 npm init 生成一个json文件

# gulp
-   下载: npm install -g gulp-cli
-   cnpm i gulp --save-dev 下载gulp
-   gulp -v 来验证是否安装好
-   国内的: cnpm
-   npm set config --registry=https://registry.npm.taobao.org
-   查看下载到哪个文件夹: npm get prefix

# gulp基本
-   前端自动化构建工具
-   gulp的四个方法
    *   gulp.task()     //要处理的任务
    *   gulp.src()      //匹配要处理的东西
    *   gulp.dest()     //指定位置存储我们处理好的结果
    *   gulp.watch()    //当需要执行任务里自动执行某个任务

# gulp的使用
-   小例题
```
    //相当于引入了gulp这个包,并且把gulp这个对象赋值给gulp变量
    var gulp = require('gulp') //引入node_modules中的gulp中的代码
    //创建一个任务
    gulp.task(
        //参数1 => 任务名
        'heimao',
        //参数2 => 回调函数
        function(){ //当我们去执行heimao这个任务的时候,回调函数就会被运行
            console.log(123)
        }
    )
    //调用的时候在命令提示符输入 gulp heimao
```
-   使用步骤
    *   要在项目文件夹中通过npm下载好gulp
    *   在文件夹中新建一个文件'GulpFile.js',这个文件名是固定的,不能改
```
    //基本代码如下
    var gulp = require('gulp'); //这个参数gulp就对应我们通过gulp下载的gulp这个包
    //创建任务
    gulp.task('heimao',function(){
        console.log(123);//当执行这个任务时,这个函数就会执行
    })
    //如何执行
    gulp haimao //在当前路径打开命令行,输入代码
```

# 用gulp压缩js
-   需要一个依赖包, 这就是gulp的插件: gulp-uglify
-   下载命令: npm install gulp-uglify
-   GulpFile.js代码
```
    //1.引包
    var gulp = require('gulp')
    var uglify = require('gulp-uglify')
    gulp.task('zero',function(){
    //a.找到要压缩的js
    //b.将其压缩
    //c.制定一个位置来保存压缩后的代码
    //gulp.src(['./app.js','./js/*.js'])//获取app.js和js目录下的所有js文件
    gulp.src(['./app.js'])
    .pipe(uglify())     //这里传递这个uglify()方法的返回值,内部会自动压缩
    .pipe(gulp.dest('./tmpjs'))    //指定压缩后的文件放到tmpjs目录中
})
```

# 用gulp压缩css
-   依赖包是 gulp-csso
-   步骤同上

# less转换为css
-   使用的包 gulp-less
-   步骤同上

# 压缩html
-   使用的包 gulp-htmlmin
-   pipe(htmlmin({collapseWhitespace:true})) //这一步特殊一点
-   其他步骤同上

# 自动执行gulp.watch()
-   代码
```
    gulp.task('default',function(){
        gulp.watch(['./路径名/**/*.*'],['html','script','less']);
        //或者分开写
        gulp.watch(['./路径名/js/*.js'],['html'])
    })
```
