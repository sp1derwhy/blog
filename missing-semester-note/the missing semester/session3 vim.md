[一份基本的vim设置](https://missing-semester-cn.github.io/2020/files/vimrc)
> 使用方式：放在根目录，改名成 .vimrc
> 或者 `mv vimrc ~/.vimrc`

一些vim插件
*   [ctrlp.vim](https://github.com/ctrlpvim/ctrlp.vim): 模糊文件查找
*   [ack.vim](https://github.com/mileszs/ack.vim): 代码搜索
*   [nerdtree](https://github.com/scrooloose/nerdtree): 文件浏览器
*   [vim-easymotion](https://github.com/easymotion/vim-easymotion): 魔术操作
> 使用方式： 从vim8.0开始，不需要使用插件管理器， 创建 `~/.vim/pack/vendor/start/`文件夹，插件放在该目录下即可

## Vim

*   **正常模式**(一般在其他模式下esc返回)：在文件中四处移动光标进行修改
*   **插入模式**(i)：插入文本
*   **替换模式**(R)：替换文本
*   **可视化模式**（一般 v，行 V，块 ctrl+v）：选中文本块
*   **命令模式**(:)：用于执行命令

## 命令行
*   `:q` 退出（关闭窗口）
*   `:w` 保存（写）
*   `:wq` 保存然后退出
*   `:e {文件名}` 打开要编辑的文件
*   `:ls` 显示打开的缓存
*   `:help {标题}` 打开帮助文档
    *   `:help :w` 打开 `:w` 命令的帮助文档
    *   `:help w` 打开 `w` 移动的帮助文档

## 移动
多数时候你会在正常模式下，使用移动命令在缓存中导航。在 Vim 里面移动也被称为 “名词”， 因为它们指向文字块。

*   基本移动: `hjkl` （左， 下， 上， 右）
*   词： `w` （下一个词）， `b` （词首）， `e` （词尾）
*   行： `0` （行初）， `^` （第一个非空格字符）， `$` （行尾）
*   屏幕： `H` （屏幕首行）， `M` （屏幕中间）， `L` （屏幕底部）
*   翻页： `Ctrl-u` （上翻）， `Ctrl-d` （下翻）
*   文件： `gg` （文件头）， `G` （文件尾）
*   行数： `:{行数}<CR>` 或者 `{行数}G` ({行数} 为行数)
*   杂项： `%` （找到配对，比如括号或者 /* */ 之类的注释对）
*   查找： `f{字符}`， `t{字符}`， `F{字符}`， `T{字符}`
    *   查找 / 到 向前 / 向后 在本行的 {字符}
*   搜索: `/{正则表达式}`, `n` / `N` 用于导航匹配
* 数字组合：可以通过4j 向下移动4行,d4w删除四个单词等

### 可视化模式

*   可视化：`v`
*   可视化行： `V`
*   可视化块：`Ctrl+v`

可以用移动命令来选中。

## 编辑

所有你需要用鼠标做的事， 你现在都可以用键盘：采用编辑命令和移动命令的组合来完成。 这就是 Vim 的界面开始看起来像一个程序语言的时候。Vim 的编辑命令也被称为 “动词”， 因为动词可以施动于名词。

> 基本上嗯两遍单词表示对行进行操作，比如dd删除一行，yy复制一行
*   `i` 进入插入模式
    *   但是对于操纵 / 编辑文本，不单想用退格键完成
*   `O` / `o` 在之上 / 之下插入行
*   `d{移动命令}` 删除 {移动命令}
    *   例如，`dw` 删除词, `d$` 删除到行尾, `d0` 删除到行头。
*   `c{移动命令}` 改变 {移动命令} 
    *   例如，`cw` 改变词
    *   比如 `d{移动命令}` 再 `i`
*   `x` 删除字符（等同于 `dl`）
*   `s` 替换字符（等同于 `xi`）
*   可视化模式 + 操作
    *   选中文字, `d` 删除 或者 `c` 改变
*   `u` 撤销, `<C-r>` 重做
*   `y` 复制 / “yank” （其他一些命令比如 `d` 也会复制）
*   `p` 粘贴
*   更多值得学习的: 比如 `~` 改变字符的大小写

## 计数

你可以用一个计数来结合 “名词” 和“动词”，这会执行指定操作若干次。

*   `3w` 向前移动三个词
*   `5j` 向下移动 5 行
*   `7dw` 删除 7 个词

## 修饰语

你可以用修饰语改变 “名词” 的意义。修饰语有 `i`，表示 “内部” 或者“在内“，和 `a`， 表示” 周围 “。

*   `ci(` 改变当前括号内的内容
*   `ci[` 改变当前方括号内的内容
*   `da'` 删除一个单引号字符串， 包括周围的单引号


## 搜索和替换

`:s` （替换）命令（[文档](http://vim.wikia.com/wiki/Search_and_replace)）。

*   `%s/foo/bar/g`
    *   在整个文件中将 foo 全局替换成 bar
*   `%s/\[.*\](\(.*\))/\1/g`
    *   将有命名的 Markdown 链接替换成简单 URLs

## 多窗口

*   用 `:sp` / `:vsp` 来分割窗口
*   同一个缓存可以在多个窗口中显示。

## 宏

*   `q{字符}` 来开始在寄存器`{字符}`中录制宏
*   `q`停止录制
*   `@{字符}` 重放宏
*   宏的执行遇错误会停止
*   `{计数}@{字符}`执行一个宏 {计数} 次
*   宏可以递归
    *   首先用`q{字符}q`清除宏
    *   录制该宏，用 `@{字符}` 来递归调用该宏 （在录制完成之前不会有任何操作）
*   例子：将 xml 转成 json ([file](https://missing-semester-cn.github.io/2020/files/example-data.xml))
    *   一个有 “name” / “email” 键对象的数组
    *   用一个 Python 程序？
    *   用 sed / 正则表达式
        *   `g/people/d`
        *   `%s/<person>/{/g`
        *   `%s/<name>\(.*\)<\/name>/"name": "\1",/g`
        *   …
    *   Vim 命令 / 宏
        *   `Gdd`, `ggdd` 删除第一行和最后一行
        *   格式化最后一个元素的宏 （寄存器 `e`）
            *   跳转到有 `<name>` 的行
            *   `qe^r"f>s": "<ESC>f<C"<ESC>q`
        *   格式化一个的宏
            *   跳转到有 `<person>` 的行
            *   `qpS{<ESC>j@eA,<ESC>j@ejS},<ESC>q`
        *   格式化一个标签然后转到另外一个的宏
            *   跳转到有 `<person>` 的行
            *   `qq@pjq`
        *   执行宏到文件尾
            *   `999@q`
        *   手动移除最后的 `,` 然后加上 `[` 和 `]` 分隔符

*   `vimtutor` 是一个 Vim 安装时自带的教程
*   [Vim Adventures](https://vim-adventures.com/) 是一个学习使用 Vim 的游戏
*   [Vim Tips Wiki](http://vim.wikia.com/wiki/Vim_Tips_Wiki)
*   [Vim Advent Calendar](https://vimways.org/2019/) 有很多 Vim 小技巧
*   [Vim Golf](http://www.vimgolf.com/) 是用 Vim 的用户界面作为程序语言的 [code golf](https://en.wikipedia.org/wiki/Code_golf)
*   [Vi/Vim Stack Exchange](https://vi.stackexchange.com/)
*   [Vim Screencasts](http://vimcasts.org/)
*   [Practical Vim](https://pragprog.com/titles/dnvim2/)（书籍）