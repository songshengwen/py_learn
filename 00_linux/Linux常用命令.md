## 0. 起步：

- 使用Linux命令的通用格式：
```
命令名 [选项] [参数]
```
> 命令名区分大小写字母; 选项和参数, 可以没有, 也可以有（可选）
---

## 1. ls 命令：

- 作用：显示某个文件夹的内容或文件的信息
```    
ls      显示当前文件夹的可见内容
ls -l   使用长格式显示内容/或者文件信息（类似于Windows的详细信息）
ls -h   配合 -l 选项以更任性化的方式来显示文件或文件夹的大小
ls -a   显示当前文件夹中全部文件或者目录，包括隐藏文件在内的内容，第一个字母是 . 是隐藏文件或者目录
ls 目录名或者文件名   显示某个文件夹的内容或文件的信息
```
---

## 2. pwd 命令：

- 作用：显示当前工作目录的路径名

> Linux文件系统中, 目录结构采用树形目录结构, 目录数的根用 `/` 表示; 路径分为绝对路径, 相对路径; 路径就是记录文件或文件夹的字符串, 绝对路径就是从根目录开始的路径
---

## 3. cd 命令：

- 作用：进入某个目录/或者叫切换工作目录
```
cd 目录名     （目录名可以使用绝对路径、或者相对路径）
cd -          在最近访问的两个目录间来回切换
cd 直接回车    回到用户的主目录（家目录）
```
---

## 4. mkdir 命令：

- 作用：创建工作目录
```
mkdir 文件夹名     创建文件夹
mkdir -p          逐级创建文件夹
实例：mkdir -p yy/zz/xx
     mkdir -p yy/xx zz/aa

在Linux文件系统中：
.    表示当前目录
..   表示父目录/上级目录

创建目录练习：当前目录下, b 文件存在，用一条命令在 b 文件夹下创建src, lib, docs, build 文件夹
答案：$ mkdir -p b/src b/lib b/docs b/build
```
> 在输入当前文件夹内的文件名或者文件夹名时，可以使用Tab来自动补全。
---

## 5. 看帮助：

- 命令名 --help
- man 命令名
```
使用 q 键退出
使用方向键翻页查看内容
使用鼠标滚轮也可查看内容
```
---

## 6. history 命令：

- 作用：查看所有操作
> 在终端窗口输入的命令，可以使用上、下键来查看，并可执行。
---

## 7. rmdir 命令：

- 作用：删除一个或多个文件夹（文件夹必须为空）
```
rmdir 文件夹名
rmdir -p 如果中间的文件夹也为空，则逐级删除中间的文件夹
实例：rmdir -p a/bb/ccc/dddd (有时选项和参数的位置可以互换)
```
> 注：逐级删除文件夹是必须保证中间文件夹为空
---

## 8. touch 命令：

- 作用：如果文件不存在，则创建这个文件; 如果文件存在，则用系统时间更新这个文件夹
```
格式：touch 文件或文件夹
实例：touch newfile
     touch oldfile
```
---

## 9. rm 命令：

- 作用：删除单个或或多个文件或文件夹
```
rm 【选项】文件/文件夹
实例：rm a b c d

常用选项：
    -r 递归删除文件夹内部的文件和文件夹
    -i 删除前给出提示（y代表yes，n代表no）
    -f 强制删除，不给出提示（此时-i选项无效），默认是yes删除

操作带有“特殊 字符"路径的方法
用两个双引号（“”）将路径括起来
实例： $ mkdir "a b"
      $ rmdri "a b"
```
---

## 10. 通配符

```
* 代表0个、1个或多个任意字符
？代表1个任意字符

实例： 
touch a ab ac abc aabb bc cd
a*  代表所有以a开头的文件
a*b 代表以a开头，以b结尾的文件
a？ 代表以a开头，后跟一个字符c

练习：
1、创建文件夹 cmd
2、在cmd文件夹内创建文件： a ab ac abc aabb bc cd
3、在cmd文件夹内创建文件夹： folder1 folder2
4、删除cmd文件夹内所有两个字符中的文件

答案：
$ mkdir cmd
$ cd cmd/
/cmd$ touch a ab ac abc aabb bc cd
/cmd$ mkdir folder1 folder2
/cmd$ rm ??
```

## 11. cp 命令（copy）：

- 作用：复制文件或文件夹
```
cp【选项】原文件或文件夹名1 目地文件或文件夹名2
选项：-a 复制子文件夹和相关文件
     -i 覆盖文件时提示
     -r 递归复制该目录下的所有子目录和文件，目标文件必须为一个目录名
实例：cp a.txt ~/  # 复制a.txt 到用户主目录下
```

## 12. mv 命令：

- 作用：用于搬移文件或文件更名
```
mv 原文件名 目标文件夹或文件名
```
---

## 13. clear 命令：

- 作用：清屏
```
Linux下的快捷键：ctrl + l
```
---

## 14. 文件的权限：

- 查看文件权限：ls -l
```
文件权限类型：
    r 读权限
    w 写权限
    x 执行权限
    - 无权限

Linux下的权限分组：
用户权限（user） 组权限（group） 其他权限（other）
    zyz           zyz           其他

最多权限： 
    rwx rwx rwx  ---> 777
    111 111 111

最少权限： 
    --- --- ---  ---> 000
    000 000 000
```
---

## 15. chmod 命令：

- 作用：用来修改文件的权限
```
格式：chmod 权限 文件名/文件夹名
权限：
    u 用户（属主）
    g 同组用户（属组）
    o 其他用户
    a 所有用户
    + 添加权限
    - 去除权限
    777 最高权限
    000 最低权限
想在终端执行命令的文件或文件夹，必须有可执行的权限

练习：操作文件权限
两个文件 a.txt b.txt 写入一些内容
让其他用户不能读取a.txt 文件
让组用户和其他用户不能读取b.txt
让用户自身对所有文件有执行权限

答案：
$ touch a.txt b.txt
$ vim a.txt
$ vim b.txt
$ chmod o-r a.txt
$ chmod go-r b.txt
$ chmod u+x a.txt b.txt
```
---

## 16. find命令：

- 作用：根据文件名查找指定的文件
```
find 路径 -name “文件名”
实例：$ find / -name “a.txt”
     $ find ~ -name “a.txt”

练习：
查找 /etc 目录下，有几个“passwd”文件，位置在哪儿？

答案：
find /etc -name "passwd"
```
---

## 17. grep 命令：

- 作用：根据文件内容查找相应的文件
```
grep “内容” [选项] 文件名或路径
常用选项：
    -n 显示行号
    -v 显示不包含指定内容的行
    -i 忽略大小写
    -R/-r 递归搜索文件夹内的文件
实例：$ grep "300" -r /home/tarena/*

练习：查找/etc 下哪儿个文件含有tedu这个字符串
答案：grep "tedu" -nr /etc
```
---

## 18. cat 命令：

- 作用：将文件内容作为标准输出显示，适合查看内容较小的文本文件
```
cat 文件1 文件2⋯⋯
常用选项：
    -b 对非空输出编号
    -n 对输出的所有行编号
实例：cat /etc/passwd
```
---

## 19. less/more 命令：

- 作用：显示文本文件内容（可以上下回滚）
```
less 文件名
基本操作：
    q：推出
    j：下翻
    k：上翻
    f/空格 下翻一页
    b：上翻一页
    /word 搜索word字符串
```
---

## 20. 压缩和解压缩命令：

1. gzip 命令：
- 作用：用zip压缩算法对文件进行压缩，生成压缩后的文件
```
gzip 文件名
注：压缩后的文件名后缀通常为 .gz
```

2. gunzip 命令：
- 作用：对.gz 文件进行解压缩
```
gunzip 文件名
实例：$ gunzip passwd.gz
```
---

## 21. tar 命令：

- 作用：对文件够文件夹进行打包、解包的操作
```
tar[选项] 文件名 [被打包的文件或路径]
常用选项：
    -c  创建包 （打包的时候可以将tar包放在任意目录，不用-C选项）
        如：tar -czvf 任意路径excise.tar.gz /home/excise.txt
    -x   解包
    -f 文件名   操作文件的名称
    -v   显示操作的文件
    -z   用gzip、gunzip 对包进行压缩和解压缩的操作
    -C 路径   改变解压缩的路径（只对解包有效）
        如：tar -xzvf /home/excise.tar.gz -C /home/a
    注：-号可以省略不写

# 打包并压缩
$ tar -czvf a.tar.gz a

# 解压缩和解包
$gunzip a.tar.gz
$tar -xvf a.tar

# 以下两步一次完成
$tar -xzvf a.tar.gz

练习：试把excise.txt打包，移动到家目录下解包
答案： $ tar -czvf excise.tar.gz excise.txt
        $ tar -xzvf excise.tar.gz -C ~/
```
---

## 22. 输出重定向：

> 输出分为两种：1、标准输出 2、标准错误输入

```
标准输出重定向：
>   将一个命令的标准输出重定向到一个文件中
>>  将一个命令的标准输出追加到一个文件中
实例：
find /etc -name "passwd" > stdout.txt
find /usr -name "ls" >> stdout.txt

标准错误输出重定向：
    2>   将一个命令的标准错误输出重定向到一个文件中
    2>>  将一个命令的标准错误输出追加到一个文件中
实例：
    find /etx -name "passwd" 2> stderr.txt
    find /etc -name "ls" 2>> stderr.txt

重定向所有输出：
    &>
    &>>
作用：将所有标准输出和标准错误输出重定向到一个文件中
```
---

## 23. echo 命令：

- 作用：默认情况下输入到标准输出，可以使用重定向输出到
```
echo x
选项：-n   不尾随换行符
     -e   启用解释反斜杠的转义功能
     -E   禁用解释反斜杠的转义功能

实例：echo "Raspberry" > test.txt
# 覆盖文件原内容并重新输入内容，若文件不存在则创建文件
```
---

## 24. 管道操作, 运算符： |

- 管道的作用：将命令的“输出”，重定向为另一个命令的“输入”
```
命令1 参数选项 | 命令2 ⋯⋯
实例：cat /etc/passwd | grep "zyz"
```
---

## 25. 进程相关命令：

> 什么叫进程：是指正在执行的程序

1. ps 命令：

- 作用：查看进程
```
ps [选项]
选项：-aux 查看当前系统内所有的进程的详细信息
实例：ps
     ps -aux
```

2. kill 命令：
- 作用：杀死一个进程
```
kill 进程pid号
```
---

## 26. sudo 命令：

- 作用：1、切换root用户  2、用超级用户root权限来执行这些命令
```
sudo 命令 [选项] [参数]
常用选项：
    -i   切换到root用户
    $ sudo -i
```
---

## 27. exit 命令：

- 作用：退出用户登录
```
练习：
    1、在~/a/下创建pbase
    2、在~/a/pbase下创建三个文件夹：b c d
    3、在~/a/b/e.txt，仅让当前用户可以读写此文件
答案：
    $ cd a/
    $ mkdir pbase
    $ cd pbase/
    $ mkdir b c d
    $ touch e.txt
    $ chmod 600 e.txt

练习：编写一个shell脚本，要求实现：
    1、在/home/a/下创建文件夹：mydir
    2、在/etc下查找passwd文件，把屏幕所有输出重定向，到：mydir/result.txt
    3、将result.txt打包压缩为result.tar.gz
    4、再将result.tar.gz解压到/home/目录
答案： 
    $ cd a/
    $ mkdir mydir
    $ find /etc/passwd > mydir/result.txt
    $ cd mydir
    $ tar -czvf result.tar.gz result.txt
    $ tar -xzvf excise.tar.gz -C /home/
```
---

## 28. shutdown 命令
    
- 作用：关闭、重启计算机
```
shutdown [选项] [时间]
选项：-r now 马上重启
     now 立即关机
     时间 如：20:15
     +10 十分钟后关机
     -c 取消关机
     reboot 重启
```
---

## 29. ifconfig 命令（ip addr）

- 作用：查看/配置计算机当前的网卡配置信息
```
常用：ifconfig | grep inet
```
---

## 30. ping 命令

- 作用：检测到目标ip地址的连接是否正常
---

## 31. ssh 客户端的简单使用

- 作用：连接到远程服务器
```
格式：ssh [-p port] user@remote
选项：port 是ssh server 监听的端口，如果不指定，就为默认值：22
        user 是在远程机器上的用户名，如果不指定的话默认为当前用户
        remote 是远程机器的地址，可以是IP/域名，或者是别名
```

> 注：是用exit 退出当前用户的登录, 如果在windows 系统中，可以安装PuTTY 或者XShell 客户端软件即可
---

## 32. last 命令：

- 作用：显示最后一次ssh 连接的用户
---

## 33. scp 命令：

> scp 命令和ssh 命令很像，默认端口22，如果更改了端口号，需要用-P 大写指定端口号

- 作用：远程复制文件
```
把本地文件复制到远程  scp [-P port] 原文件路径 user@remote:目标文件路径

把远程文件复制到本地  scp [-P port] user@remote:目标文件路径 原文件路径

配合 -r 复制文件夹
```
---

## 34. ssh 免密登陆

> 有关ssh 配置信息都保存在用户目录下的 .ssh 目录下

```
配置步骤：
    1、执行 ssh-keygen 即可生成ssh 钥匙，一路回车即可
    2、上传公钥到服务器，执行 ssh-copy-id [-p port] user@remote，可以让远程服务器记住公钥
```
---

## 35. ssh 配置别名

- 作用：用ssh 别名来代替ssh [-p port] user@remote 一长串内容，登陆远程机器
```
步骤：
    1、打开～/.ssh/config 文件，没有则创建一个
    2、在～/.ssh/config 里面追加如下内容：
    Host 别名
        HostName 远程计算机的ip地址
        User 远程用户名
        port 端口号
保存后，即可用 ssh 别名的方式，实现登陆远程，scp 同样也可以使用
```
---

## 36. group 命令

- 作用：创建、删除组，需要通过sudo 执行
```
groupadd 组名    添加组
groupdel 组名    删除组
cat /etc/group  删除组信息
chgrp -R 组名 文件/目录名    修改文件/目录的所属组
```
---

## 37. 创建用户/设置密码/删除用户，需要通过sudo 执行

```
useradd -m -g 组 新建用户名   添加新的用户名
        -m 自动建立用户的家目录
        -g 指定用户所在的组，否则会建立一个和同名的组

passwd 用户名    
设置用户密码，如果是普通用户，可以用passwd 命令修改自己的账户密码

userdel -r 用户名    
删除用户名，-r 选项会自动删除用户家目录

cat /etc/passwd | grep 用户名    
确认用户信息，新建用户后，用户信息会保存在 /etc/passwd 文件中
```
---

## 38. id 命令

- 作用：查看用户信息
```
id [用户]
```
---

## 39. who 命令：

- 作用：显示登录系统的所有用户信息
---

## 40. whoami 命令：

- 作用：显示当前系统的登陆用户
---

## 41. which 命令：

- 作用：显示命令所在位置
---

## 42. cal 命令：

- 作用：查看当前日期命令
```
cal -y 年份 ：某一年的日历
```
---

## 43. date 命令：

- 作用：查看当前时间
---

## 44. df 命令：

- 作用：硬盘使用情况
