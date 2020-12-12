+++
title = "Markdown"
date = 2020-12-12T14:02:46+08:00
tags = []
categories = []
isCJKLanguage = true
description = ""
weight = 10
+++



Emacs Markdown Mode 入门 (1)
markdown是一种非常适合文字工作者的轻量标记语言，相比富文本编辑工具，它能使写作者更加专注于内容的生产，而不是在繁琐的布局和格式上浪费时间。
现如今市面上有很多markdown写作工具，而作为有“编辑器之神”称号的emacs入坑者，当然希望能在emacs下更加高效的编写markdown文档。
本文是对emacs markdown 模式使用手册的翻译文章，希望能让更多的中文emacs爱好者学会markdown模式下的快捷键的基本使用方法。


用法
快捷键按照功能分组,每组具有不同的前缀.
例如,插入链接的命令在分组C-c C-a中,其中的C-a是HTML中标签< a >的助记符.
其他一些情况与HTML的联系并不直接.
例如,处理标签的命令以C-c C-t开始(titling的助记符).
下面介绍的每个分组中主要的命令.你可以使用C-c C-h获得所有快捷键的列表.
移动和转向命令倾向于使用成对的定界符,如 M-{和M-}以及C-c <和C-c >.
大纲导航相关的快捷键与org-mode一致.
最后运行Markdown和对打开文件进行维护命令分在以C-c C-c为前缀的组中.

超链接:C-c C-a
在这个分组中,C-c C-a l以格式[text] (url)插入一个行内的链接.
链接的文档由以下内容决定:1.如果具有活动的区域,以它为链接文本;
2.如果光标停留在一个单词内,以这个单词为链接文本.
在这两种情况下原始文本被链接替换并且光标移至插入URL的位置.否则,链接内容为空,光标移至插入文本的位置.

C-c C-a L以[text] [label]格式插入一个引用链接以及对应参考标签的定义.
链接文本以行内链接相似的方式确定,但是与插入空标记时不同,这种情况下链接文本会从minibuf中读取.
引用标签也都是从minibuf中读取的,可以依据当前已经定义的引用来补全.
为了创建一个隐含的引用链接,按下RET来接收默认值,一个空标签.
如果输入的引用标签没有定义,会出现对URL和标题的输入提示,
如果输入了一个URL,引用定义将使用markdown-reference-location插入,
如果输入了一个标题,新定义将被插入到当前引用定义的最后,并在转换成XHTML时填充标题的属性.


C-c C-a u插入一个纯url,以尖括号界定.如果有活动区域,活动区域的文本被视作url.
如果光标在一个url内,这个url被使用.否则插入一个尖括号并且光标在尖括号内以输入url.

C-c C-a f插入一个脚注,并在下方插入脚注的定义,并将光标移至脚注文本输入处.
需要注意的是,脚注是Markdown的一个扩展,并非所有处理器支持.

C-c C-a w的行为与行内链接插入命令相似,它以格式[[WikiLink]]插入一个wiki链接.
如果有活动区域,使用该区域作为链接文本,如果光标在单词内,使用该单词为链接文本.
否则,只是简单插入链接标记.需要注意的是,wiki链接是Markdown的一个扩展,并非所有处理器支持.

图片 C-c C-i
C-c C-i i以格式! [] ()插入一个行内图像标记,使用活动区域或光标所在单词作为提示文本, C-c C-i I的行为与之相似,插入的是引用风格的图片.

本地图片与图片链接相关,可以使用C-c C-i C-t在buffer中显示.这是一个切换命令,所以再按一次移除行内图片。

样式 C-c C-s
C-c C-s e插入能使区域或单词变成斜体的标记(< em >/emphasisi标签).
如果有活动区域或单词,将其变成斜体.如果光标在已经是斜体的文本上,则移除斜体标记.否则只是增加一个定界符,在其中输入斜体文本.
类似的使用C-c C-s s加粗(< strong >标签),使用C-c C-s c标记代码(< code >标签),使用C-c C-s k插入< kbd >标签（用来表示文本是从键盘上键入的）.

C-c C-s b使用活动区域创建一个块引用,或者一个空的块引用,它总是对块进行操作,不管是否是活动状态.
它可以根据上下文的缩进自动计算合适的缩进,也可以使用区域缩进命令稍后调整.

C-c C-s p以类似的方式插入预格式化的代码块,C-c C-s C-p仅对区域有效.

标题 C-c C-t
所有标题命令都会使用活动区域作为标题来插入.
否则如果当前行非空,使用该行文本作为标题.
如果没有活动区域或者当前行是空行,最终设置文本命令会提示输入标题文本.

C-c C-t h根据前面的标题自动选择标题类型和级别来插入标题.
C-c C-t H的行为类似,但是优先使用下划线形式的标题.
如果自动推导的级别不是你想要的情况下,级别可以快速提升和下降,下文会介绍.此外在命令前加一个C-u可以提成一个级别,加两个可以下降一个级别.

为了插入特定级别和类型的标题,C-c C-t 1-6插入atx类型的标题,C-c C-t !或者C-c C-t @分别插入一级和二级setext类型的标题.

如果光标位于单词内,以上命令会覆盖当前的标记并更新标题的级别.可以通过C-c C-k移除标题,通过C-y将标题拽回buffer.

水平线 C-c -
C-c -插入一个水平线.默认情况下,使用markdown-hr-strings列表里面第一个字符串构成水平线.
带有C-u前缀时使用列表中最后一个字符.带有数字N前缀时,使用位置N上的字符(从1开始算起).(默认* -两种字符以及3种长度,共6种).

编译和维护命令 C-c C-c
编译 C-c C-c m命令会在当前buffer中运行markdown,并在另一个buffer中输出显示.
预览 C-c C-c p命令在当期buffer中运行markdown,将输出保存到临时文件,并在浏览器中预览.
导出C-c C-c e命令在当期buffer中运行markdown,将输出保存到basename.html文件,这里basename与md文件去掉后缀的名字相同.
导出并预览 C-c C-c v导出到文件并在浏览器中预览.打开 C-c C-c o直接使用markdown-open-command打开markdown源文件.
实时导出 C-c C-c l打开markdown-live-preview-mode模式以查看由markdown源文件导出的文件.
对所有的导出命令,输出文件默认覆盖没有提醒.markdown-live-preview-function可以配置成打开游览器而不是eww.
你可以通过配置markdown-split-window-direction强制将预览窗口显示在底部或右侧.

小结:
C-c C-c m: markdown-command > markdown-output buffer.
C-c C-c p: markdown-command > temporary file > browser.
C-c C-c e: markdown-command > basename.html.
C-c C-c v: markdown-command > basename.html > browser.
C-c C-c w: markdown-command > kill ring.
C-c C-c o: markdown-open-command.
C-c C-c l: markdown-live-preview-mode > eww buffer.

C-c C-c c会检查未定义的引用.如果存在,会打开一个小buffer将未定义的引用以及出现的行号列出来.
在Emacs 22以后的版本中,从这些列表中选择一个引用并按下RET将会在buffer的尾部插入一个空的引用定义.类似地,选择一个行号将跳转的相应的行.

C-c C-c n为buffer中任何不在有序的有序的列重新编号.

C-c C-c ]补全buffer中所有标题以及统一所有水平线.

跟踪链接 C-c C-o
当光标在一个行内或引用链接下时,按下C-c C-o在浏览器中打开URL.
当光标在一个wiki链接下时,在另一个buffer中显示URL内容(加C-u前缀显示在新窗口,无前缀显示在当前窗口).
使用M-p和M-n快速跳转到前一个或者下一个任何类型的链接(注意:需要配置markdown-open-command).

跳转 C-c C-l
使用C-c C-l从一个对象跳转到同级对应的下一个对象.可以在引用链接和定义之间,在脚注标记和脚注文件之间跳转.
如果多于一个链接使用相同的引用名称,会弹出一个包含各个链接按钮的新缓冲区,可点击的按钮跳转到单个链接.
也可以使用TAB或者S-TAB来在当前窗口中的按钮之间跳转.

升级和降级 C-c C–与C-c C-=
标题,水平线,列表项可以被升级或者降级,还包括加粗和斜体的文本.
对于标题,升级指的是标题的级别数字减小（h2->h1,实际级别效果是升级）,而降级则是标题的级别数字增大.
对于水平线,升级和降级指的是在markdown-hr-strings的水平线字符列表中向前或者向后移动.
对于加粗和倾斜文本,升级和降级指的是改变文本的下划线和星号标签.也可以在光标所在位置按M-LEFT来对元素进行升级操作.

要记牢这个命令,需要注意-号意味着标题级别数字减小（升级）,=号对应着标题的级别数字增大（降级）,与此类似,左右箭头符号风别暗指atx风格的标题的升级和降级.

自动补全 C-c C-]
补全标签一般来说是指,将setext风格标题的下划线补全到和标题文本相同的长度,或者atx风格标题的收尾的#号数量相同,且没有多余的空格.
总之,C-c C-]补全光标当期位置的不完整的标签.

编辑列表 M-RET, M-UP, M-DOWN, M-LEFT, M-RIGHT
新的列表项可以使用M-RET或者 C-c C-j插入.这个命令检测附近的项目来决定合适的标签以及缩进级别.
如果光标前后没有列表,那么开始一个新列表.在命令前加一个C-u前缀可以减小一个缩进级别,两个前缀可以增加一个缩进级别.

已经存在的列表项目可以使用M-UP或者M-DOWN上下移动,使用M-RIGHT或者M-LEFT减小或增大缩进长度

编辑子树 M-S-UP, M-S-DOWN, M-S-LEFT和M-S-RIGHT
atx风格的标题可以使用M-S-LEFT和 M-S-RIGHT来升级和降级整个标题子树,与列表项目的升级和降级绑定关系相同.
类似的子树可以使用M-S-UP和 M-S-DOWN上下移动.

注意下面的升级和降级的边界行为.任何8级标题不能降级并且任何1级标题升级后将失去标题标签.

转移区域 C-c < 和C-c >
区域中的文本可以作为一个组使用C-c >增加缩进到下一个缩进点,C-c <较少缩进到前一个点.这些键的绑定和python模式中的一样.

删除元素 C-c C-k
按下C-c C-k以删除当前光标位置的东西并且增加重要的没有标签的文本到kill ring.
可以被删除的东西包括:行内代码,标题,水平下,链接（链接文本加入到kill ring）,图像（提示文本加入到kill ring）,angle URI,邮件地址,加粗,倾斜,引用定义,脚注标签和文本（标签和文本都加入到kill ring）,列表项.

大纲导航 C-c C-n, C-c C-p, C-c C-f, C-c C-b和C-c C-u
在标题之间导航可以使用大纲模式.使用C-c C-n和 C-c C-p在可见的前后标题间移动.
类似的C-c C-f和 C-c C-b在同级标题间前后移动.最后C-c C-u可以向上移动到一个更低级别的可见标题上.

段落和块间的移动 M-{和M-}
这些键通常会绑定到forward-paragraph和backward-paragraph,但是这些内置的emacs函数仅仅基于简单正则表达式并且会在markdown模式下失效.
markdown模式下的块包括代码块,块引用,列表项目,标题,水平线或者以空格分割的纯文本段落.
因此,这些键实际绑定到markdown-forward-block和markdown-backward-block.可以使用M-h和 C-x n b（实测无该命令）来扩大或者缩小选定的区域.

节的移动 C-M-a, C-M-e和C-M-h
一般emacs命令可以用来在defuns间移动.在markdown模式下defuns是一个节.
一般C-M-a将移动到当前节的开始或者上一节,C-M-e将会移到当前节的结束或者下一节,C-M-h将选取整个节的区域.

注意事项
注意,上面命令的行为结果取决于短标记模式是否开启（在短标记模式下实现了标准的选择-高亮行为）.
如果短标记模式开启且区域是活动状态,命令将应用在选择区域的文本上.
对于那些不使用短标记模式的用户,emacs 22可以使用C-SPC C-SPC临时开启.当没有开启时,许多命令的行为只对当期所在的单词或行生效.

适当情况下,命令针对非短标记模式下的区域的行为与标准模式下有相同的快捷键绑定关系,但是通常字母是大写的.
举例来说,markdown-insert-blockquote被绑定到C-c C-s b并对短标记模式下的区域有效,
另一情况下,markdown-blockquote-region被绑定到C-c C-s B并且总是对区域生效.

注意,特定区域的函数在大多数情况下都非常有用,尽管并非显而易见.
举例来说,从kill ring中拉取文本会将标记放在文本的最前面,并将光标移动到最后面.因此,非活动区域包含了拉取的文本.
所以C-c C-s C-b后的C-y会拉取文本并转换为块引用.

markdown模式试图灵活处理缩进.当你重复按下TAB,光标会在多个可能的缩进级别间循环变化,这些位置与在行尾或TAB键后按下RET时你脑中想要的结果相符.
举例来说,你可能想要一个新的列表项,继续一个有缩进的列表项,缩进为重叠的前级块等等.当退格键在没有空白部分的行的开始位置按下时,反缩进也是相同的处理.

markdown模式支持outline-minor-mode和org-mode-style下atx或者#号风格标题的循环可见.
有两种循环可见：按下S-TAB在目录视图,大纲视图和全文档视图间全局切换；
按下TAB时,当前位置的标题会循环在子树不同可见级别间循环：全部折叠,子标题内容可见,全部可见.
注意混合使用#号标题和下划线标题会产生无法预期的结果.


github风格markdown(GFM)
github风格markdown模式也叫gfm模式.github实现的markdown与标准的markdown略有不同,
它支持诸如单词中使用下划线,自动链接URL,删除线文本以及使用可选语言关键字标记的代码块等不同行为.

上述GFM才有的特征常应用于github仓库中的README.md文件,wiki页面,和其他markdown格式的文件.
github也支持一些额外的特征以帮助在网页上书写markdown，例如在github中书写issues,pull requests,messages等。
这些特征还包括任务列表(复选框),对应于硬换行的新行,自动链接到issues和commits的引用,wiki链接等等.
尽管任务列表作为GFM的一部分并不合适,它使事情变得更复杂,但是自从2014年它们在网站的软件仓库的所有的markdown文档中被提供.
下面来介绍gfm模式与markdown模式下相关的扩展内容.

URL自动链接
markdown模式和gfm模式都支持高亮显示没有尖括号标记的URL字符串.

单词中的多下划线
必须使能gfm模式下的支持单词中间的下划线功能开关,在这种模式下,例如a_test_variable这样的变量名将不会被解释为斜体.

围住的代码块
用反引号标记的代码块可以加入可选的编程语言关键字并且在markdown模式和gfm模式下高亮显示.
使用C-c C-s P可以插入这样的代码块.如果有活动区域,区域中的文本将会移动到代码块中,同时你将被要求输入语言的名字,但可以直接输入回车跳过输入.

删除线
删除文本仅在gfm模式下被支持,可是使用C-c C-s d插入.向其他命令绑定关系的助记词一样,d与HTML中的标签< del >对应.

任务列表
GFM的任务列表在markdown-make-gfm-checkboxes-buttons被设置为非空值时(默认设为t)以emacs复选框按钮形式在markdown模式和gfm模式下提供.
鼠标点击,在按钮上按下RET或者光标位于复选框的某处时使用C-c C-x C-x可以激活复选框.

wiki链接
makrdown模式支持一般的wiki链接,但是在gfm模式像在github上一样对待这些链接:文件名中的空格将被连字符代替并且第一个字符大写.
例如[[wiki link]]将映射到文件名为Wiki-link具有当前文件相同后缀的文件上.如果当前目录不存在这样的文件,会使用子目录中第一个匹配的文件.

新行
markdown模式和gfm模式都不会针对新建一行的行为做些什么.
如果你总是使用gfm模式在github上写comment或者issue,新建一行非常重要并且和硬分行相当,那么你会为buffer中的行使能visual-line-mode.
你可以像这样使用gfm-mode-hook来达到目的:


;; Use visual-line-mode in gfm-mode
(defun my-gfm-mode-hook ()
  (visual-line-mode 1))
(add-hook 'gfm-mode-hook 'my-gfm-mode-hook)
Preview: GFM-specific preview can be powered by setting markdown-command to use Docter.
This may also be configured to work with Marked 2 for markdown-open-command.


emacs解决markdown插件的gfm-mode注释换行失效问题

只要换行就会出现问题

临时解法重新加载gfm-mode

mx gfm-mode





之前写文章渐渐习惯了markdown，但是在交付或者打印的时候还是要通过pdf，
所以就想能不能通过什么工具直接从markdown转到pdf，于是在网上搜索方法，找了几篇文章，感觉最终的结果还不错，就把应用的过程记在这里。
1 安装pandoc和Miktex
我的是Windows平台，所以直接在pandoc官方网站下载了安装包安装即可。
http://www.pandoc.org/installing.html
上面有Miktex链接，一起下载下来安装。
2 中文支持
2.1 中文编译不通过
添加编译选项 --latex-engine=xelatex

2.2 中文不能显示
添加编译选项 -M CJKmainfont:SimSun
再添加-M mainfont:"Times New Roman" -M monofont:Monaco个人觉得好看一点。

2.3 不能自动换行
修改tex模板，先导出模板pandoc -D latex > template.tex
然后在
$if(mathfont)$
    \setmathfont(Digits,Latin,Greek)[$for(mathfontoptions)\$$mathfontoptions\$$sep$,$endfor$]{$mathfont$}
$endif$之后添加
\XeTeXlinebreaklocale "zh"

3. 排版
3.1 修改边距
在导言栏添加
\usepackage[tmargin=0.5in,bmargin=1in,lmargin=0.75in,rmargin=1.25in]{geometry}


3  代码配色
通过
 ```{.c .numberLines} code```



4. emacs markdown mode
下载markdown-mode.el  http://jblevins.org/projects/markdown-mode/



.emacs中添加如下配置

(autoload 'markdown-mode "markdown-mode"
   "Major mode for editing Markdown files" t)
(add-to-list 'auto-mode-alist '("\\.markdown\\'" . markdown-mode))
(add-to-list 'auto-mode-alist '("\\.md\\'" . markdown-mode))

(autoload 'gfm-mode "gfm-mode"
   "Major mode for editing GitHub Flavored Markdown files" t)
(add-to-list 'auto-mode-alist '("README\\.md\\'" . gfm-mode))

5. 其他配置
可以通过查看template.tex文件中的if语句，然后在命令行里添加相应的参数。



参考文献：

http://www.cnblogs.com/baiyangcao/p/5574483.html

http://www.bagualu.net/wordpress/archives/5396#pandoc%E4%B8%AD%E7%9A%84%E4%B8%AD%E6%96%87%E6%8D%A2%E8%A1%8C%E9%97%AE%E9%A2%98

我的命令：

pandoc test.md -o test.pdf --template=template.tex --latex-engine=xelatex -M CJKmainfont:SimSun -M mainfont:"Times New Roman" -M monofont:Monaco
