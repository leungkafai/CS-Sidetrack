
不定时更新，版本是vim8以上
先附gitee仓库地址，只要装好了vim8,把仓库的文件放到你的Linux主目录打开Vim就可以用，减少你从github下载插件的速度折磨（如果不可以请评论，我可以看看是什么问题）

[gitee地址](https://gitee.com/ricardo_gt/vim-copy.git)，git clone 就行。

下面附带说明

### 1.vim配置(内含已安装插件配置)

```powershell
"不与 Vi 兼容（采用 Vim 自己的操作命令）。
set nocompatible
"打开语法高亮
syntax on
set showcmd
set encoding=utf-8
"开启文件类型检查，并且载入与该类型对应的缩进规则。比如，如果编辑的是.py文件，Vim 就是会找 Python 的缩进规则~/.vim/indent/python.vim
filetype indent on  
"括号自动补全
inoremap ' ''<ESC>i
inoremap " ""<ESC>i
inoremap ( ()<ESC>i
inoremap [ []<ESC>i
inoremap { {<CR>}<ESC>O
"设置退格
set backspace=indent,eol,start

" set the runtime path to include Vundle and initialize
set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()
" alternatively, pass a path where Vundle should install plugins
"call vundle#begin('~/some/path/here')

" let Vundle manage Vundle, required
Plugin 'VundleVim/Vundle.vim'

"目录插件
Plugin 'preservim/nerdtree'
"状态栏插件
Plugin 'vim-airline/vim-airline'
"状态栏插件主题
Plugin 'vim-airline/vim-airline-themes'
"latex插件
Plugin 'lervag/vimtex'
"管理片段插件
Plugin 'SirVer/ultisnips'
"latex实时预览
Plugin 'xuhdev/vim-latex-live-preview'
"彩虹括号配置
Plugin 'rainbow_parentheses.vim'
"快速移动插件
Plugin 'easymotion/vim-easymotion'
"快速注释
Plugin 'preservim/nerdcommenter'
"大纲浏览
Plugin 'majutsushi/tagbar'
"语法检测
Plugin 'scrooloose/syntastic'
"前端插件
Plugin 'mattn/emmet-vim'
"PythonIDE
Plugin 'python-mode/python-mode'
" All of your Plugins must be added before the following line
call vundle#end()            " required
"

"打开文件类型，允许vim记载文件类型插件，允许vim为不同类型的文件定义不同的缩进格式
filetype plugin indent on    " required



"nerdtree配置
""自动打开
autocmd vimenter * NERDTree

"vimtex配置
let g:tex_flavor='latex'
let g:vimtex_view_method='zathura'
let g:vimtex_quickfix_mode=0
set conceallevel=1
let g:tex_conceal='abdmg'
let g:vimtex_compiler_latexmk = { 
        \ 'executable' : 'latexmk',
        \ 'options' : [ 
        \   '-xelatex',
        \   '-file-line-error',
        \   '-synctex=1',
        \   '-interaction=nonstopmode',
        \ ],
 	\}
"语法检测插件配置
set statusline+=%#warningmsg#
set statusline+=%{SyntasticStatuslineFlag()}
set statusline+=%*

let g:syntastic_always_populate_loc_list = 1
let g:syntastic_auto_loc_list = 1
let g:syntastic_check_on_open = 1
let g:syntastic_check_on_wq = 0
"管理片段插件配置
let g:UltiSnipsExpandTrigger = '<tab>'
let g:UltiSnipsJumpForwardTrigger = '<tab>'
let g:UltiSnipsJumpBackwardTrigger = '<s-tab>'

"latex实时预览配置
let g:livepreview_previewer = 'evince'
let g:livepreview_engine = 'xelatex'
""tex文件刷新保存时间
autocmd Filetype tex setl updatetime=3

"vim-airline主题配置
let g:airline_theme='deus'
"彩虹括号配置
let g:rbpt_colorpairs = [
    \ ['brown',       'RoyalBlue3'],
    \ ['Darkblue',    'SeaGreen3'],
    \ ['darkgray',    'DarkOrchid3'],
    \ ['darkgreen',   'firebrick3'],
    \ ['darkcyan',    'RoyalBlue3'],
    \ ['darkred',     'SeaGreen3'],
    \ ['darkmagenta', 'DarkOrchid3'],
    \ ['brown',       'firebrick3'],
    \ ['gray',        'RoyalBlue3'],
    \ ['black',       'SeaGreen3'],
    \ ['darkmagenta', 'DarkOrchid3'],
    \ ['Darkblue',    'firebrick3'],
    \ ['darkgreen',   'RoyalBlue3'],
    \ ['darkcyan',    'SeaGreen3'],
    \ ['darkred',     'DarkOrchid3'],
    \ ['red',         'firebrick3'],
    \ ]
au VimEnter * RainbowParenthesesToggle
au Syntax * RainbowParenthesesLoadRound
au Syntax * RainbowParenthesesLoadSquare
au Syntax * RainbowParenthesesLoadBraces
let g:rbpt_max = 16

"快速移动插件配置
map <Leader> <Plug>(easymotion-prefix)

"大纲浏览启动
nmap <F8> :TagbarToggle<CR>

```
### 2.插件介绍(不定时更新更多)
下面暂时只放效果图和github链接，只要使用上面发的gitee仓库的配置文件就有下面的效果（颜色可能不同）。有空我再详细翻译插件配置。

#### 2.1 Vundle

vundle是vim插件管理器，作用是在.vim文件夹下创建bundle文件夹，通过vundle安装的插件都会存放在里面
启动方法：将下面代码插入.vimrc的头部
	
```bash
	set nocompatible            
	filetype off                  
	set rtp+=~/.vim/bundle/Vundle.vim
	call vundle#begin()
	Plugin 'VundleVim/Vundle.vim'  
	call vundle#end()            "
	filetype plugin indent on    
```
安装其他插件方法是将要安装的插件名字放进 call vundle begin和call vundle end之间。如下图
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200302184429128.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1JpY2FyZG85OA==,size_16,color_FFFFFF,t_70)
仓库地址
[https://github.com/VundleVim/Vundle.vim
](https://github.com/VundleVim/Vundle.vim)

#### 2.2 Airline
下面是本插件功能配置
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200302183202232.gif)
1.仅打开一个选项卡时自动显示所有缓冲区。


```bash
let g:airline#extensions#tabline#enabled = 1
```
2.主题更换
需要添加插件

```bash
Plugin ' vim-airline / vim-airline-themes '
```
更换主题方法是

```bash
let g:airline_theme='<theme>'
```
风格样式在以下链接
[https://github.com/vim-airline/vim-airline/wiki/Screenshots](https://github.com/vim-airline/vim-airline/wiki/Screenshots)


仓库地址：
[https://github.com/vim-airline/vim-airline
](https://github.com/vim-airline/vim-airline)
#### 2.3 Nerdtree
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200302184238505.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1JpY2FyZG85OA==,size_16,color_FFFFFF,t_70)
1.自动打开

```python
autocmd vimenter * NERDTree
```
2.Ctrl+n打开关闭，也可以自己修改

```python
map <C-n> :NERDTreeToggle<CR>
```

仓库地址
[https://github.com/preservim/nerdtree
](https://github.com/preservim/nerdtree)
#### 2.4 vim+latex插件
详情见我另一篇文章
[https://blog.csdn.net/Ricardo98/article/details/104603811
](https://blog.csdn.net/Ricardo98/article/details/104603811)

#### 2.5 syntastic
 Vim语法检查插件。它通过外部语法检查器运行文件，并向用户显示所有由此产生的错误。这可以按需完成，也可以在保存文件时自动完成。如果检测到语法错误，则会通知用户，因为他们不必编译代码或执行脚本来查找它们。

1.官方推荐配置

```python
set statusline+=%#warningmsg#
set statusline+=%{SyntasticStatuslineFlag()}
set statusline+=%*

let g:syntastic_always_populate_loc_list = 1
let g:syntastic_auto_loc_list = 1
let g:syntastic_check_on_open = 1
let g:syntastic_check_on_wq = 0
```

 
 仓库地址
 [https://gitee.com/Harveyxu/syntastic?_from=gitee_search](https://gitee.com/Harveyxu/syntastic?_from=gitee_search)

#### 2.6 tagbar
可以浏览当前文件的标签并获得其结构的概述。它通过创建一个侧边栏来做到这一点

仓库地址
[https://gitee.com/mamamiyear/tagbar?_from=gitee_search](https://gitee.com/mamamiyear/tagbar?_from=gitee_search)

#### 2.7 nerdcommenter
快速注释

仓库地址
[https://github.com/preservim/nerdcommenter.git](https://github.com/preservim/nerdcommenter.git)

#### 2.8 vim-easymotion
快速移动

仓库地址
[https://github.com/Lokaltog/vim-easymotion](https://github.com/Lokaltog/vim-easymotion)

#### 2.9 rainbow_parentheses
高亮括号

仓库地址
[https://github.com/kien/rainbow_parentheses.vim](https://github.com/kien/rainbow_parentheses.vim)

#### 2.10 python-mode
python ide,可通过利用包括pylint，rope，pydoc，pyflakes，pep8，autopep8，pep257和mccabe的库来帮助您快速创建python代码 ， 这些 功能包括静态分析，重构，折叠，完成，文档和更多。

仓库地址
[https://github.com/python-mode/python-mode](https://github.com/python-mode/python-mode)

#### 2.11  emmet-vim
前端必备插件

仓库地址
[https://github.com/mattn/emmet-vim](https://github.com/mattn/emmet-vim)

#### 2.12 ctrlp.vim
强大的文本搜索工具

仓库地址
[https://github.com/ctrlpvim/ctrlp.vim.git](https://github.com/ctrlpvim/ctrlp.vim.git)
### 3.不同语言配置
不同语言（文件类型）可以有不同的配置来适应
1.缩进风格可创建 c.vim文件放于 .vim/indent 文件夹中，没有可自行创建，其他语言只需要改python.vim,以此类推。
2.高亮风格可创建c.vim放于 .vim/syntax文件中，如上
3.不同键映射（快捷键）可创建c.vim放于 .vim/ftplugin 中，如上。
##### 3.1 C++
太长，见gitee仓库  .vim/syntax

ctags：[https://blog.csdn.net/locher_liu/article/details/82147078?depth_1-utm_source=distribute.pc_relevant_right.none-task-blog-BlogCommendFromBaidu-3&utm_source=distribute.pc_relevant_right.none-task-blog-BlogCommendFromBaidu-3](https://blog.csdn.net/locher_liu/article/details/82147078?depth_1-utm_source=distribute.pc_relevant_right.none-task-blog-BlogCommendFromBaidu-3&utm_source=distribute.pc_relevant_right.none-task-blog-BlogCommendFromBaidu-3)

cscope:[https://blog.csdn.net/dengxiayehu/article/details/6330200?depth_1-utm_source=distribute.pc_relevant.none-task-blog-OPENSEARCH-4&utm_source=distribute.pc_relevant.none-task-blog-OPENSEARCH-4](https://blog.csdn.net/dengxiayehu/article/details/6330200?depth_1-utm_source=distribute.pc_relevant.none-task-blog-OPENSEARCH-4&utm_source=distribute.pc_relevant.none-task-blog-OPENSEARCH-4)
