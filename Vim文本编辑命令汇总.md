介绍Vim三种操作模式和文本编辑命令。Vim编辑模式插入字符，行尾、行首插入，删除一个字符和删除整行命令，Vim复制和粘贴命令，vim替换输入以及撤销和反撤销命令，Vim保存和另存为文件，显示vim当前编辑文件名。

我们使用编辑器的常用文件操作主要是：`插入`、`删除`、`复制`、`粘贴`、`替换`、`撤销`、`保存`、`另存为`。

在介绍Vim中的上述基本文件操作命令前，需要先介绍下vim的操作模式。因为*vim的各种文件操作命令需要在不同操作模式下使用*。

### 一、Vim三种操作模式
Vim编辑器一共有3种模式，分别为**命令模式**(默认)、**编辑模式**、**尾行模式**。这3种模式的转换关系如下图所示。

![vim三种模式](https://image.vimjc.com/images/691e0c29gy1fltkwtx0gfj20hp08eae0.jpg)
#### 1.1 命令模式(command mode)
命令模式是Vim的默认操作模式，当使用vim命令打开一个文件时，默认进入的就是命令模式。不管用户处于何种模式，只要按下**Esc**键就可使进入命令行模式

#### 1.2 编辑模式(input mode)
只有在vim编辑模式下，才能将键盘键入的内容输入到当前打开的文件中

在命令模式下输入插入命令i(insert)、附加命令a (append)、打开命令o（open）、修改命令c（change）、取代命令r或替换命令s都可以进入文本编辑模式

#### 1.3 尾行模式(last line mode)
尾行模式主要用于保存文件或退出Vim，同时也可以设置编辑环境和一些编译工作，如[列出行号](https://vimjc.com/vimrc-config.html)(set nu)、[寻找字符串](https://vimjc.com/vim-search.html)(/target)等

在命令模式下，用户按冒号键**(:)**即可进入末行模式下，此时Vi会在显示窗口的最后一行显示一个"**:**"作为末行模式的提示符，等待用户输入命令

#### 二、Vim文本编辑命令

约定：在没有特殊说明的情况下，以下Vim编辑命令部分提到的命令均是在**命令模式**下使用。

#### 2.1 插入
在**命令模式**下按以下按键可进入编辑模式，执行插入操作，具体包括：

1. 从光标当前所在位置的【**前**】一个字符处开始插入：`i`
2. 从光标当前所在位置的【**后**】一个字符处开始插入：`a`

3. 从光标当前所在行的【**行首**】处开始插入：`I`
4. 从光标当前所在行的【**行尾**】处开始插入：`A`

5. 从光标当前所在行的【**下一行**】处开始插入：`o`
6. 从光标当前所在行的【**上一行**】处开始插入：`O`

**tips**：`i` (insert)是在当前位置**插入**，`a` (append)表示是在后面**追加**

#### 2.2 删除

在**命令模式**下按以下按键可执行删除操作，具体包括：

1. 删除光标位置的【**一个**】字符：`x`
2. 删除当前光标所在【**行**】：`dd`

3. 删除从光标所在位置到当前【**行首**】的内容：`d0`
4. 删除从光标所在位置到当前【**行尾**】的内容：`d$`

5. 删除从光标所在位置到当前【**单词结束**】部分的内容并进入插入模式：`cw`、`cW`
6. 删除从光标所在位置到当前【**单词开始**】部分的内容并进入插入模式：`cb`、`cB`

7. 删除从光标所在位置到当前【**单词结束**】部分的内容但**不**进入插入模式：`dw`、`dW`
8. 删除从光标所在位置到当前【**单词开始**】部分的内容但**不**进入插入模式：`db`、`dB`

**tips**: 

(1) Vim的命令中，`0` 表示行首，`$` 表示行尾，更多内容可参考Vim教程网上的[Vim操作范围、文件范围介绍](https://vimjc.com/vim-ranges.html)
(2) w(word)、b(back)命令用于光标移动，具体可参考vim教程网上的博客：[vim光标移动命令汇总](https://vimjc.com/vim-cursor.html)
(3) `cW`、`cB`、`dW`、`dB` 命令操作的单词是以空白字符（空格、Tab）分隔的字符串


1. 删除当前【**句子**】从光标位置开始到【**句末**】的内容：`d)`
2. 删除当前【**句子**】从光标位置开始到【**句首**】的内容：`d(`
 
3. 删除当前【**段落**】从光标位置开始到【**段末**】的内容：`d}`
4. 删除当前【**段落**】从光标位置开始到【**段首**】的内容：`d{`
 
**tips**：Vim命令中用 `(` 和 `)` 表示句子，`{` 和 `}` 表示段落

#### 2.3 复制、粘贴

在**命令模式**下按以下按键可执行复制、粘贴操作，具体包括：

1. 复制从光标所在位置到当前【**单词结束**】部分的内容：`yw`
2. 复制光标所在【**行**】的所有字符 (包含换行符)：`yy`


1. 将最后一次删除或复制操作的文本内容粘贴到光标所在字符之【**后**】：`p`
2. 将最后一个删除或复制操作的文本内容粘贴到光标当前字符之【**前**】：`P`

**tips**：`yyp` 操作可以实现复制一整行内容到当前所在行的下一行

#### 2.4 替换

在**命令模式**下按以下按键后，再输入字符可**替换**原始文件中的内容

1. 替换光标当前所在字符**一次**：`r` 
2. 一直替换光标所在字符，直到按下[ESC]键为止：`R`

------------------------
删除、复制操作的操作单位可以加操作次数，操作对象的范围为：操作次数 * 操作单位

**例如**：`d3w`命令表示删除三个单词，`10dd`命令表示从光标所在行开始删除后面的十行，更多内容可以参考[Vim中的操作符和动作命令](https://vimjc.com/vim-operator-and-motion.html)。

#### 2.5 撤销、反撤销

在**命令模式**下可执行撤销操作
1. 撤销最近的一次操作：`u`

2. 恢复最近的一次操作(取消撤销)：`<Ctrl> + r`

**tips**：多次执行*u* 命令可以连续撤销最近的操作

#### 2.6 保存
在**尾行模式**下执行以下命令可保存当前编辑的文件内容

1. 保存当前编辑的文件：`:w`
2. 保存当前编辑的文件并退出vim：`:wq`
3. 强制将当前编辑的文件保存：`:w!`

**tips**：上述操作是在尾行模式下执行的，所以命令都是以`:`开头

#### 2.7 另存为

在**尾行模式**下执行命令 `:w a.txt` 可将vim当前打开的文件另存为新文件a.txt.

**tips**：`w(write)` 表示将文件存档，`:` 表示尾行模式命令。

#### 2.8 显示当前文件名
命令 `<Ctrl> + g` 可显示当前编辑文件名及行数，可以在不退出 Vim 的情况下了解当前编辑文件的信息，更多内容，可参考[30个Vim常用命令和使用技巧](https://vimjc.com/vim-tips.htmls)。

----------------------------
Vim入门级文件编辑命令汇总就先介绍到这里了，更多Vim文件编辑命令和Vim相关操作可阅读vim教程网上的其他博客。
