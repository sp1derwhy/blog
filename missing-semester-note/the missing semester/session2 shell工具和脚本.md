> 主要内容：关于操纵变量的语法，控制流以及函数

### 在shell中空格是需要注意的
```ad-example

foo=bar       // define foo with value bar

foo = bar     // shell会去寻找foo的执行目录，并且把 = 和 bar 作为foo的参数去执行，

echo "value is $foo"   -> value is bar

echo 'value is $foo'   -> value is $foo
```

### bash提供了很多特殊的变量用于表示参数
- $0   -> 脚本名
- $1到0 -> 表示脚本的第1到9个参数
- $@ -> 所有参数
- $# -> 参数个数
- $? -> 前一个命令的返回值

### bash支持函数，可以接受参数并基于参数操作
```
mcn(){
	mkdir -p "$1"
	cd "$1"
}
```

以上面的mcn函数来说，假设我们定义在了 mcn.sh 脚本中
```
source mcn.sh
mcn test
```
首先通过source将mcn脚本加载到shell中，然后就可以直接使用了

### 一个例子展示上述特性
```
#!/bin/bash

echo "Starting program at $(date)" # date会被替换成日期和时间

echo "Running program $0 with $# arguments with pid $$"

for file in "$@"; do
    grep foobar "$file" > /dev/null 2> /dev/null
    # 如果模式没有找到，则grep退出状态为 1
    # 我们将标准输出流和标准错误流重定向到Null，因为我们并不关心这些信息
    if [[ $? -ne 0 ]]; then
        echo "File $file does not have any foobar, adding one"
        echo "# foobar" >> "$file"
    fi
done
```

### 一些shell工具
- shellcheck 
- tldr   ->  简化man的说明，更便于阅读.并提供一些cheetsheet类似的例子
- find , ripgrep, ag, ack, fd  -> 查找工具，一般是文件名或者内容
- ctrl+R -> 查找历史命令，连续按是往前查找
- fzf -> 记得绑定一下快捷按键，如果是通过homebrew安装，运行下 opt/homebrew/opt/fzf/install以便于自动绑定快捷键
- tree -> show the contents of the current directory as a tree
- 和tree类似的还有 broot(推荐),比tree功能更方便
- fasd , autojump 快速跳转到常用目录