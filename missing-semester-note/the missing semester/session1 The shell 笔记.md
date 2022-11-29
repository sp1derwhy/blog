## shell的概念

## shell的使用

#### shell是如何知道程序怎么运行的？

[shell通过环境变量知道如何运行程序](https://www.bilibili.com/video/BV1Eo4y1d7KZ/?vd_source=316166227e3bf5fede075909cf48866a#t=598.793895)

如果没有通过指定路径去运行可执行程序，shell会去查找环境变量PATH中的路径，如果在path中有对应的可执行文件的路径，就会执行，比如视频中的linux环境下，date是内置的程序，具体路径可以通过where查询，并且可以在$PATH中找到对应的目录，所以可以在任何地方直接执行date命令

## 在shell中导航
- 路径
- cd
- pwd
> print working directory 打印当前工作目录
- ls
- mv，cp，mkdir
```ad-example
mv fileA.txt fileB.txt //改名 

mv fileA.txt aDirectory/fileb.txt //将当前目录的fileA移动到aDirectory目录并命名为fileb

cp a b // cp from to 
```
- 用户手册man

## 在程序间创建连接

[如何在shell中让不同的程序连接起来](https://www.bilibili.com/video/BV1Eo4y1d7KZ/?vd_source=316166227e3bf5fede075909cf48866a#t=1679.906679)

- 流stream
程序默认会有两个流，一个输入流(input 默认是键盘输入)，一个输出流(output 默认是终端，也就是显示在屏幕上)
- 重定向
	- > , < , >>
这些符号提供了重定向流的方式，其中>>表示追加的意思，举个例子来说
```ad-example
echo hello > file.txt    //将echo hello的输出重定向为 file.txt的输入

echo hello >> file.txt   //会将hello追加到file.txt后，

此时执行cat，会看到两行hello
cat hello.txt

hello

hello
```

- pipe 管道
> 取左侧程序的输出，作为右侧程序的输入,这个和重定向是有区别的，重定向右侧只能是文件，而pipe可以是需要输入的程序，重定向执行在一个进程内，而pipe是触发两个子进程执行两边的程序


[帮助理解管道和sudo的使用以及和重定向的区别使用](https://www.bilibili.com/video/BV1Eo4y1d7KZ/?vd_source=316166227e3bf5fede075909cf48866a#t=2308.851782)

## shell可以帮助我们做什么

something like 自动化任务，测试程序（比如说运行一个程序知道他出错为止）

## 课后练习

