# git
## 基本bash命令
-   cd => 用来切换到指定路径
-   mkdir ./xx => 创建一个xx的文件夹
-   ls => 列出当前路径下的所有文件
-   touch ./index.tml => 创建一个index.html文件
-   pwd => 输出当前路径
-   cat => 查看文件内容,会在命令窗口输出全部内容
-   less => 与cat类似,如果文件名太长,则只显示一部分
-   rm => 删除指定文件和文件名
    > 删除文件: rm 文件路径
    > 删除文件夹: rm -rf 文件夹路径

## linux常用操作命令
#### 常用指令
-   ls      显示当前路径下的所有文件
-       -l  列出文件详细信息
-       -a  列出当前文件下所有文件及目录,包括隐藏的
-   mkdir   创建目录
-       -p  创建目录,若无父目录则创建p(parent)
-   cd      切换目录
-   touch   创建空文件
-   echo    创建带有内容的文件
-   cat     查看文件内容
-   cp      拷贝
-   mv      移动或重命名
-   rm      删除文件
-       -r  递归删除,可删除子目录及文件
-       -f  强制删除
-   find    在文件中搜索某文件
-   wc      统计文本中行数,字数,字符串
-   grep    在文本中查找某个字符串
-   rmdir   删除空目录
-   pwd     显示当前目录
-   ln      创建链接文件
-   more/less分页显示文件内容

#### 系统管理命令
-   stat        显示指定文件的详细信息，比ls更详细
-   who         显示在线登陆用户
-   whoami      显示当前操作用户
-   hostname    显示主机名
-   uname       显示系统信息
-   top         动态显示当前耗费资源最多进程信息
-   ps          显示瞬间进程状态 ps -aux
-   du          查看目录大小 du -h /home带有单位显示目录信息
-   df          查看磁盘大小 df -h 带有单位显示磁盘信息
-   ifconfig    查看网络情况
-   ping        测试网络连通
-   netstat     显示网络状态信息
-   man         命令不会用了，找男人  如：man ls
-   clear       清屏
-   kill        杀死进程，可以先用ps 或 top命令查看进程的id，然后再用kill命令杀死进程。

#### 关机/重启机器
-   shutdown
-       -r       关机重启
-       -h       关机不重启
-       -a       取消关机  
-   now          立刻关机
-   halt         关机
-   reboot       重启

## git的基本使用
-   版本控制工具
-   配置用户名和邮箱
    >   git config --global user.name "用户名"
    >   git config --global user.emal "邮箱"
    >   一个电脑只需要配置一次
-   git init    =>  初始化
    >   一个项目执行一次就行
-   git add -A  =>  把代码放到暂存区
-   git commit -m "注释" => 把暂存区代码放到仓库中
-   git log     =>  查看记录
-   git log --oneline => 查看记录,在一行显示
-   按键ctrl+c  => 终止操作
-   git status  =>  查看工作区代码与仓库中最新的代码是否是一样的
-   git add 文件路径 =>把指定文件放入到暂存区

## 分支
#### 创建分支
-   git branch 分支名   =>  分支名应该是英文的,例如git branch tmp
-   git checkout 分支名 =>  切换分支   

#### 合并分支
-   git checkout master =>  确保已经切换到master分支
-   git merge 分支名    => 将分支合并到master分支上
-   git checkout 分支 操作的时候,会把指定分支最后一次提交的代码放到工作区,替换掉原来的代码

## 版本回退
-   可以把仓库里任意一次提交过的代码拿到暂存区来,相同文件会被覆盖
-   git reset --hard 版本的id
-   git reflog  => 查看记录,更全

## 分布式与集中式

## gitHub
-   git push 上传
-   master:master 把本地的服务器上传到服务器的master

## 翻墙软件
-   小飞机(shadowsocks)
-   蓝灯

## gitHub
-   用SSH方式上传时,需要生成一个公钥和私钥,然后把公钥放到远程,私钥在上传时使用
-   私钥加密的只能用公钥解密
-   公钥加密的只能用私钥解密
-   生成一对公钥和私钥 ssh-keygen -t rsa
-   上传文件时
    *   git push 远端仓库地址 本地仓库分支名:远端仓库分支名
-   取数据
    *   第一次取的时候 git clone 地址 文件夹名
    *   当远端仓库不为空时: git pulll 远端仓库地址 远端仓库分支名:本地仓库分支名

## 关于冲突


