介绍Vim配置文件.vimrc，配置Vim显示行号、支持utf8中文不乱码、突出显示Vim当前行，设置高亮显示括号匹配和tab缩进，解决Vim粘贴时多出缩进和空格问题。

### 一、Vim配置文件.vimrc
Vim编辑器相关的所有功能开关都可以通过**.vimrc**文件进行设置。

**.vimrc**配置文件分系统配置和用户配置两种。

系统vimrc配置文件存放在Vim的安装目录，默认路径为`/usr/share/vim/.vimrc`。可以使用命令`echo $VIM`来确定Vim的安装目录。

用户vimrc文件，存放在用户主目录下`~/.vimrc`。可以使用命令`echo $HOME`确定用户主目录。

*注意*：用户配置文件优先于系统配置文件，Vim启动时会优先读取当前用户根目录下的**.vimrc**文件。所以与个人用户相关的个性化配置一般都放在`~/.vimrc`中。


### 二、Vim基本配置

默认情况下，Vim编辑器里既不显示行号，也没有语法高亮度、智能缩进。为了方便使用，基本的Vim配置选项一般都会包括：

#### 2.1 支持中文不乱码

``` bash
'设置编码'
set fileencodings=utf-8,ucs-bom,gb18030,gbk,gb2312,cp936
set termencoding=utf-8
set encoding=utf-8
```
与Vim编码有关的变量包括：`encoding`、`fileencoding`、`termencoding`。
encoding选项用于缓存的文本、寄存器、Vim 脚本文件等；fileencoding选项是Vim写入文件时采用的编码类型；termencoding选项表示输出到终端时采用的编码类型。
#### 2.2 显示行号

``` bash
'显示行号'
set nu
set number
```
nu是number的缩写，所以上面两个配置命令是完全等效的。

#### 2.3 突出显示当前行

``` bash
set cursorline
set cul          'cursorline的缩写形式'
```

#### 2.4 突出显示当前列

``` bash
set cursorcolumn
set cuc          'cursorcolumn的缩写形式'
```

#### 2.5 启用鼠标

``` bash
set mouse=a
set selection=exclusive
set selectmode=mouse,key
```
Vim编辑器里默认是不启用鼠标的，也就是说不管你鼠标点击哪个位置，光标都不会移动。通过以上设置就可以启动鼠标，不过对于高级玩家来说，用Vim就是为了解放双方不用鼠标，所以这个设置可以根据个人爱好选择。

#### 2.6 显示括号匹配

``` bash
set showmatch
```

关于Vim的括号匹配，推荐阅读[Vim插件之多色彩括号匹配插件rainbow_parenthsis](https://vimjc.com/vim-rainbow-parentheses-plugin.html)。

#### 2.7 设置缩进

``` bash
'设置Tab长度为4空格'
set tabstop=4
'设置自动缩进长度为4空格'
set shiftwidth=4
'继承前一行的缩进方式，适用于多行注释'
set autoindent
```

关于Vim缩进的更多内容，可参考vim教程网上的文章[Vim自动缩进和tab键替换空格](https://vimjc.com/vim-indent.html)

#### 2.8 设置粘贴模式

``` bash
set paste
```
在Vim中通过[鼠标右键粘贴](https://vimjc.com/vim-paste.html)时会在行首多出许多缩进和空格，通过`set paste`可以在插入模式下粘贴内容时不会有任何格式变形、胡乱缩进等问题。

#### 2.9 显示空格和tab键
``` bash
set listchars=tab:>-,trail:-
```
Vim编辑器中默认不显示文件中的tab和空格符，通过上面的配置可以获得以下的显示效果，方便定位输入错误。
![vimrc显示空格和tab键](https://image.vimjc.com/images/691e0c29gy1flthpsci69j208j01hglg.jpg)

#### 2.10 显示状态栏和光标当前位置

``` bash
'总是显示状态栏'
set laststatus=2
'显示光标当前位置'
set ruler
```

#### 2.11 打开文件类型检测

``` bash
filetype plugin indent on
```

推荐阅读[Vim文件类型检测原理及应用](https://vimjc.com/vim-filetype.html)。

### 三、Vim配置变更立即生效

要让.vimrc变更内容生效，一般的做法是先保存 .vimrc 再重启vim，增加如下设置，可以实现保存 .vimrc 时自动重启加载
``` bash
'让vimrc配置变更立即生效'
autocmd BufWritePost $MYVIMRC source $MYVIMRC
```

----------------------------
Vim入门级基本配置就先介绍到这里了，更多Vim个性配置可参考vim教程网上的其他博客。

附上我的一张Vim配置示意图

![Vim配置](https://image.vimjc.com/images/691e0c29gy1fnptltfrnzj20hk0ddta2.jpg)
