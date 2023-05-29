# 一些方便工具

## mac上常用homebrew进行包管理
- [homebrew](https://brew.sh/)

## 一份已经打包好的zsh配置(含fzf，fzftab等)
- [zsh4huamn](https://github.com/romkatv/zsh4humans)

### 常用的tool 
- obsidian 笔记软件
- obsidian插件
	- admonition
	- enhancing mindmap
	- mind map
	- media extended
	- media extended biliibili plugin
	- outliner
- 简阅 simpread 方便阅读的插件（chrome）
- wireshark

### brew安装的工具包
- broot 类似于tree更智能化
- zsh-autosuggestions
- zsh-fast-syntax-highlighting
- fzf
- fzf-tab 需要加 autoload complint && complint 在其zshrc中source之前
- graphviz 通过go自带的pprof，可以绘出火焰图方便性能分析
- htop
- powerlevel10k (not recommend)
- tmux
- stow 管理dotfiles  
	- 创建dotfiles目录
	- 创建对应应用的配置文件目录，比如 dotfiles/tmux
	- 将配置文件放在对应目录里， dotfiles/tmux/.tmux.conf
	- 在dotfiles目录下运行 stow tmux 就可以将tmux配置文件软链接上
- tldr 简约的man手册
- shellcheck 检查shell脚本
- golangci-lint go的lint工具
- navi (类似于cheatsheet)

### vim 插件
> 创建 ~/.vim/pack/vendor/start/ 目录，直接在该目录下git clone对应库就能用(vim 8.0版本后)
- surround.vim

### tmux 复制粘贴的技巧
1. ctrl+a +【            // 这边改过的配置替换ctrl为command
2. 然后鼠标拖动选中内容 
3. ctrl+a + 】 会将内容复制到当前命令行,以及剪切板 