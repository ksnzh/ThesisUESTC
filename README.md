# 基于XeLaTeX的电子科技大学毕业论文模板

**ThesisUESTC**提供基于XeLaTeX写作的用于排版电子科技大学毕业论文的模板类，旨在帮助电子科技大学的毕业生高效地完成毕业论文的写作。模板提供各种方便的命令，自动化地排版论文的各个部分，使毕业论文轻易地满足学校的格式要求。为了支持更好的字体效果，模板基于XeLaTeX编写，只能使用XeLaTeX引擎编译，并且放弃对CTeX的依赖，使模板更加稳定。

模板由电子科技大学物理电子学院2014级硕士研究生王稳编写，由于在毕业论文写作中遇到各种问题，希望有一个理想的解决方案，所以决定写一个模板出来。祝愿此项目能继续发展，解决各位同学毕业论文写作中的困难。

## 使用方法
使用模板需要系统安装任意一种TeX环境，如TeXLive、MacTeX和MiKTeX（都自动带有XeLaTeX引擎，但是不推荐CTeX），安装有SimSun和SimHei字体（其实就是宋体和黑体）以及Times New Roman英文字体。字体方面也可以像在线编辑环境那样指定所使用的字体文件。模板采用LaTeX类的形式封装，导入模板只需要把thesis-uestc.cls文件放在文档所在目录，在文档开头使用`\documentclass{thesis-uestc}`命令将文档的类设置成thesis-uestc即可。模板类有bachelor、master和doctor三个选项，对应本科、硕士和博士的毕业论文。默认选项为master。文档内容的书写参考范例`main.tex`。

编译文档请使用XeLaTeX引擎。使用WinEdt、Texmaker或Texpad等编辑环境直接使用操作界面提供的编译按钮即可，不需要复杂的编译脚本，但是记得将编译引擎设置成XeLaTeX。命令编译如`xelatex main.tex`即可，文档内部有引用或参考文献的情况下需要编译两次。

使用在线编辑环境如Overleaf或ShareLaTeX的情况下需要上传字体文件到项目的根目录，修改模板最后的字体设置，直接指定所使用的字体文件。详细做法参考模板代码末尾的注释。

```latex

\setallmainfonts{Times New Roman}
\setCJKmainfont[BoldFont=SimHei]{SimSun}

%
% If you want to use this template in online editing system like Overleaf
% or ShareLaTeX, upload the font files to the root folder of your project,
% delete above two lines and uncomment the configurations below. Remember
% to keep the names of font files the same as specified in the code.
%
% \setCJKmainfont[BoldFont=simhei.ttf]{simsun.ttf} % SimSun and SimHei
% \setallmainfonts[
%     BoldFont=timesbd.ttf,     % Times New Roman Bold
%     ItalicFont=timesi.ttf,     % Times New Roman Italic
%     BoldItalicFont=timesbi.ttf,     % Times New Roman Bold Italic
% ]{times.ttf}     % Times New Roman Normal Font
%
```

模板目前还不支持bibtex参考文献，作者目前正积极解决这一问题。

## 论文写作指南

### 中英文摘要

中英文摘要的内容应包含在`chineseabstract`和`englishabstract`环境中，关键字使用`\chinesekeyword`和`\englishkeyword`命令添加，并包含在相应环境中。模板自动设置页眉和页脚，其中中文摘要标题中间空一格，页眉不空格。根据学校的格式说明，模板自动根据摘要结束所在的页数决定是否再空一页。

### 论文目录

论文目录由命令`\thesistableofcontents`添加，这个命令自动处理标题，页眉以及缩进等问题。根据学校的格式说明，模板自动根据目录结束所在的页数决定是否再空一页。

### 绪论

绪论固定是每篇论文第一个正式的章节，由于格式特殊（其实主要是页眉中间没有空格）所以由单独一个命令`\thesischapterexordium`开始。

### 论文主体

论文主体的写作参考一般的LaTeX教程，可以自由添加章节，章节内自由加入所需要的内容，分小节，插入公式、表格和图片。

### 致谢

致谢由命令`\thesisacknowledgement`开始，实际上是重新开始了一个无编号的章节。

### 参考文献

参考文献使用`thesisbibliography`环境，在其中使用`\bibitem`命令加入文献条目。引用分直接引用`\cite`命令和上标引用命令`\citing`两种。直接引用在正文中的标号显示为正常字体，上标引用显示为上标字体。暂时不支持bibtex方式的参考文献。

### 附录

附录由命令`\thesisappendix`开始，实际上是重新开始了一个无编号的章节。为了书写方便，附录中可以继续分小节，只不过附录中的小节不会在目录中显示。

### 攻读学位期间取得的成果

将文章条目放在`thesisachievement`环境下，方法与参考文献相同。

### 外文资料原文

本科毕业论文要求翻译一篇外文资料，资料原文应由命令`\thesistranslationoriginal`开始。为了书写方便可以继续分小节，只不过这部分中的小节不会在目录中显示。

### 外文资料译文

资料译文应由命令`\thesistranslationchinese`开始。为了书写方便可以继续分小节，只不过这部分中的小节不会在目录中显示。

### 插入图片和表格

插入图片使用`figure`环境，自动调整图片上下的间距。图片文件可以统一放在`./pic`目录下。插入表格使用`table`环境，自动调整表格上下的间距，还有默认的字体大小。具体插入图片和表格代码的写法参考书写范例`main.tex`。

### 定理环境

请使用模板类提供的定义（definition）、公理（axiom）、证明（proof）、定理（theorem）、推论（corollary）和引理（lemma）环境。

### 算法描述

算法描述使用`algorithm`环境，具体写法参考书写范例`main.tex`。模板类自动加载的`algorithm2e`宏包，详细的使用方法请参考[文档](http://mirrors.ustc.edu.cn/CTAN/macros/latex/contrib/algorithm2e/doc/algorithm2e.pdf)。

### 枚举环境和脚注

枚举使用标准的`enumerate`、`itemize`以及`description`环境。脚注用标准的`\footnote`命令插入。

### 主要符号表和缩略词表

由于学校没有给出清楚的格式说明，暂时不提供此功能。

## 技术交流

如果希望用QQ即时交流可加QQ群：成电LaTeX技术交流（71480604）。验证信息请说明身份，不要空置。由于作者不怎么访问清水河畔论坛，如有问题请在项目issue模块提出，或者邮件联系作者（wanygen@gmail.com）。类模板完全由作者手动编写，并非由代码工具生成，相对容易修改和阅读。在此欢迎高阶使用者改进模板代码，提出建议，分享更好的写法。