折腾了很久终于从坑里爬了出来，记录一下，后人可免踩坑
vimtex是vim中使用latex的最好插件（个人认为）
vim-live-preview是实时预览插件
# 1.vimtex配置
### 1.1安装插件
使用vundle，不会的自行百度

```bash
Plugin'lervag/vimtex'
```

### 1.2vimtex配置

```bash
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
```
### 1.3latexmk配置
latexmk一般linux都会自带有，直接在命令行输入latexmk可检查是否安装好了。
在你的home主目录下创建一下文件 .latexmkrc  (前面是点不要漏了)
然后内容为

```bash
$pdf_mode=5;
```
1为默认pdflatex
5为xelatex

然后vimtex就完成了，vim打开tex文件，快捷键 \ll编译检查结果

# 2.vim-latex-live-preview配置
### 2.1安装插件

```bash
Plugin 'xuhdev/vim-latex-live-preview'
```
### 2.2插件配置

```bash
let g:livepreview_previewer = 'evince'
let g:livepreview_engine = 'xelatex'
autocmd Filetype tex setl updatetime=3
```
第一条是选择阅读器，虽然官方说了支持Okular，可是本人测试okular很卡，不排除个人电脑问题。
第三条是选择tex文件的刷新时间，也就是隔几秒刷新一次实时预览。

Github官方文档中还推荐了
`let g:livepreview_cursorhold_recompile = 0
`
不过我测试了加了这条就需要保存才能实时预览，所以个人建议不加。

## 大功告成
享受linux和vim的快（zhe）乐(mo)吧，虽然学习曲线很陡，但是学成之后真的很有（zhuang）用(bi)～


