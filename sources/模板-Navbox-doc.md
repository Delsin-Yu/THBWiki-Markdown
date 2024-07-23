# 模板:Navbox/doc

<!-- source html: G:\repos\THBWiki-Markdown-Builder\THBWikiMarkdown\Temp\other\5\59\ns10%3ANavbox%2Fdoc.html -->

包含定制样式的导航栏模板 | 模板文档

  
本模板允许通过提供一个或多个链接列表，从而相对快速地建立一个[导航模板](https://en.wikipedia.org/wiki/导航模板)。它配备了缺省样式，这些样式应能对付大多数导航模板。不建议改变缺省样式，尽管这是可以的。为了导航模板的标准化，也为了便于使用，强烈建议使用这个模板，或者它的「Navbox系列」姊妹模板中的某一个。
  


## 目录

- [1 用法](#用法)
- [2 参数列表](#参数列表)
- [3 参数描述](#参数描述)

  - [3.1 设置参数](#设置参数)
  - [3.2 单元格](#单元格)
  - [3.3 样式参数](#样式参数)

    - [3.3.1 缺省样式](#缺省样式)






- [4 表格的布局](#表格的布局)
- [5 示例](#示例)
- [6 与其他导航框模板的关系](#与其他导航框模板的关系)
- [7 技术细节](#技术细节)

  - [7.1 运作详情](#运作详情)



- [8 參見](#參見)





## 用法
  
请移除置空不用的参数。
  

```
{{Navbox
|name={{subst:PAGENAME}}
|title=
|image=
|above=

|group1=
|list1=

|group2=
|list2= 

……

|group20= 
|list20= 

|below= 
}}```


## 参数列表

<table><tbody><tr><td><table cellspacing="0" class="nowraplinks mw-collapsible uncollapsed" style="width:100%;;;"><tbody><tr><th style=";" colspan="3" class="navbox-title"><div class="navbar"><div class="noprint plainlinksneverexpand" style="background-color:transparent; padding:0; font-weight:normal; font-size:80%; white-space:nowrap;"><a class="mw-selflink selflink"><span style=";;border:none;" title="查看这个模板">查</span></a>&#160;<span style="font-size:80%;">•</span>&#160;<a href="/index.php?title=%E6%A8%A1%E6%9D%BF:Navbox/doc&amp;action=edit"><span style=";;border:none;" title="您可以编辑这个模板。请在储存变更之前先预览">编</span></a></div></div><span>{{{title}}}</span></th></tr><tr><td></td></tr><tr><td class="navbox-abovebelow" style=";" colspan="3">{{{above}}}</td></tr><tr><td></td></tr><tr><td class="navbox-group" style=";;">{{{group1}}}</td><td style=";;" class="navbox-list navbox-odd"><div>{{{list1}}}</div></td><td class="navbox-image" style="" rowspan="7">{{{image}}}</td></tr><tr><td></td></tr><tr><td class="navbox-group" style=";;">{{{group2}}}</td><td style=";;" class="navbox-list navbox-even"><div>{{{list2}}}</div></td></tr><tr><td></td></tr><tr><td colspan="2" style=";;" class="navbox-list navbox-odd"><div>{{{list3}}}<i>不带{{{group3}}}</i></div></td></tr><tr><td></td></tr><tr><td class="navbox-group" style=";;">{{{group4}}}</td><td style=";;" class="navbox-list navbox-even"><div>{{{list4}}}</div></td></tr><tr><td></td></tr><tr><td class="navbox-abovebelow" style=";" colspan="3">{{{below}}}<br>参见下方的其他替代导航格式：<a href="#表格布局"><i>表格布局</i></a></td></tr></tbody></table></td></tr></tbody></table>


  
Navbox使用小写的参数名称，如上面框中所示。如果省略其他参数，必需的 *name* 和 *title* 会创建一个单行方框。
  
  
请注意“group1”（等等）是可选的，命名为“above/below”的部分也是可选的。
  
  
基本的和最常见的参数如下所示（参见下方查看完整的列表）：
  

: `
name - `
模板的名称。
: `
title - `
标题栏的文字，像[[化学分支]]。
: `
state - autocollapse、uncollapsed、collapsed`
：方框的折叠状态，其中“autocollapse”会自动隐藏被堆叠的多个导航框。

: `
titlestyle - `
一个用于标题栏的CSS样式，像：`
background:gray;`

: `
groupstyle - `
一个用于分组单元格的CSS样式，像：`
background:#eee;`


: `
image - `
一个可选的置于右侧的图片（以完整的image标签的形式编码：[[File:XX.jpg|90px]]）。
: `
imageleft - `
一个可选的置于左侧的图片（编码方式与“image”参数相同）。

: `
above - `
在group/list区段之上显示的文字（可能是一栏综合的维基链接）。

: `
group<sub>n</sub> - `
左侧的文字，在list-n之前（如果group-n被省略，list-n从方框的左侧开始）。
: `
list<sub>n</sub> - `
列出维基链接的文字，通常以圆点符号模板分隔开来，像：[[A]]&lt;code&gt;{{·}}&lt;/code&gt; [[B]]
: `
below - `
在group/list区段之下显示的可选文字。

  
进一步的细节，以及复杂的约束，在下方[参数描述](#参数描述)章节作了解释。参见其他的一些替代导航格式：[表格布局](#表格布局)。
  


## 参数描述
  
下面是用于&#123;&#123;[Navbox](./模板-Navbox.md)&#125;&#125;的参数的一个完整清单。在大多数情况下，只要有参数`
name`
、`
title`
和`
list1`
就可以了，尽管[子导航框](#子导航框)甚至不需要设置那些参数。
  
  
&#123;&#123;[Navbox](./模板-Navbox.md)&#125;&#125;与它的姊妹模板&#123;&#123;Navbox with columns (未找到链接)&#125;&#125;、&#123;&#123;Navbox with collapsible groups (未找到链接)&#125;&#125;共用很多常用的参数名称，以提高一致性与易用性。带一个†
标记的参数适用于所有这三个主模板。
  


### 设置参数
: name†
: 模板的名称。为了在所有使用了所生成模板的页面上，“檢&#160;· 论&#160;· 编”链接都能正确地工作，就需要设置这个参数。你可以输入`
{{subst:PAGENAME}}`
作为这个参数的值，这也是个快捷的方法。此参数是必需的。
state† [autocollapse、uncollapsed、collapsed、plain、off]

- 缺省为`
autocollapse`
。如果在使用了其他可折叠表格的同一个页面上有两个或更多表格，那么该页面上的带`
autocollapse`
的导航框一开始就会折叠起来。否则，该导航框会被展开。要了解技术上的实现，请参见MediaWiki:Common.js (未找到链接)。
- 如果设置为`
collapsed`
，该导航框总会在开始时以折叠起来的状态展现。
- 如果设置为`
plain`
，该导航框总会在被展开时不带右侧的“隐藏”链接，并且标题会保持居中（通过使用补白来偏移<small>查 • 论 • 编 • 历</small>链接）。（英文模板已实现。）
- 如果设置为`
off`
，该导航框总会在被展开时不带右侧的“隐藏”链接，但是没有补白会被用来保持标题居中。这只是为了高级用法；“plain”选项应能满足大多数需要将“显示”/“隐藏”按钮隐藏起来的应用。（英文模板已实现。）
- 如果设置为除`
autocollapse`
、`
collapsed`
、`
plain`
或`
off`
之外的其他值（像“uncollapsed”），该导航框总会在开始时以展开的状态出现，但是带有“隐藏”按钮。

: 若要在独处（未被包含）时显示框体，而在一个条目中时自动隐藏内容，可以将“uncollapsed”置于标签之内：
- `
state = `
&lt;noinclude&gt;uncollapsed&lt;/noinclude&gt;
- 如此设置会强制框体在独处时（甚至是在跟有其他方框时）可见，显示“隐藏”按钮，而当被堆叠在一个条目中时自动折叠框体。

: 很多时候，对于一个导航框，编辑者会想要一个缺省的初始状态，并且在条目中它可以被覆写。要做到这一点，这里有个窍门：
: 在你的居间模板里，创建一个参数也命名为“state”作为一个传递，像这样：
- `
| state = {{{state&lt;includeonly&gt;|你想要的初始状态&lt;/includeonly&gt;}}}`

- The &lt;includeonly&gt;|会使得当查看模板页面本身时，模板会被展开。


: navbar†
: 缺省为`
Tnavbar`
。如果设置为`
plain`
，在标题栏左侧的<small>查 • 论 • 编 • 历</small>链接不会显示出来，而且补白会被自动应用以保持标题居中。设置为`
off`
可以移除<small>查 • 论 • 编 • 历</small>链接（英文模板已实现），但是不会应用补白（这只是为了高级用法；“plain”选项应能满足大多数不想要导航栏的应用。）强烈建议使用者不要隐藏导航栏，为的是使用户编辑该模板更加容易，并且可以贯穿各个页面都有一个标准的风格。



### 单元格
: title†
: 显示在表格顶端一行居中位置的文字。它通常是该模板的主题，也就是主体内容的一个简要描述。这应该是单独的一行，但是如果需要第二行，请使用`
{{-}}`
来保证正确的居中。本参数从技术上来说不是必需的，但是使用&#123;&#123;[Navbox](./模板-Navbox.md)&#125;&#125;而不带标题是相当没有意义的。


: groupn†
: （即 *group1* 、 *group2* 等等）如果被指定，文字会显示在位于 *list<sub>n</sub>* 左侧的抬头单元格中。如果被省略， *list<sub>n</sub>* 占用表格的全部宽度。


: listn†
: （即 *list1* 、 *list2* 等等）该模板的主体，通常为一栏链接。格式为内联；然而，如果整个列表被装入`
&lt;div&gt; &lt;/div&gt;`
之内，文字能够被输入到不同的行中。最少需要一个 *list* 参数；每个附加的 *list* 被显示在一个单独的表格行中。每个 *list<sub>n</sub>* 可能在其前面有一个相对应的 *group<sub>n</sub>* 参数，如果提供了的话（参见下方）。


: image†
: 一张图片，会显示在标题（title）之下、主体（group/list）之右侧的一个单元格中。为使图片能正确地显示，必须指定 *list1* 参数。 *image* 参数接受标准的维基代码来显示图片，即：
: `
image = [[File:Example.jpg|100px]]`




: imageleft†
: 一张图片，会显示在标题（title）之下、主体（list）之左侧的一个单元格中。为使图片能正确地显示，必须指定 *list1* 参数，而且不能指定分组（group）。 *imageleft* 参数接受标准的维基代码来显示图片，即：
: `
imageleft = [[File:Example.jpg|100px]]`




: above†
: 一个全宽度单元格，显示在标题栏与第一个group/list之间，也就是位于该模板的主体（group、list和image）之上。在一个不带图片的模板中， *above* 与不带 *group1* 参数的 *list1* 参数以同样的方式运作。


: below†
: 一个全宽度单元格，显示在该模板主体（group、list和image）的下方。在一个不带图片的模板中， *below* 与该模板最后面的不带 *group<sub>n</sub>* 参数的 *list<sub>n</sub>* 参数以同样的方式运作。



### 样式参数
  
一般不建议更改样式，以保持维基百科中模板和网页的一致性。然而，修改样式的选项还是有的。
  

: style†
: 指定应用到模板主体的CSS样式。 *bodystyle* 参数也有下面举例的同样效果，并能被用来代替这个 *style* 参数。此选项应谨慎使用，因为它可以导致视觉上的不一致。举例：


: : : `
style = background:# *nnnnnn* ;`

: `
style = width: *N*  [em/%/px or width:auto];`

: `
style = float:[ *left/right/none* ];`

: `
style = clear:[ *right/left/both/none* ];`




: titlestyle†
: 应用到 *title* 的CSS样式，最常见的有导航栏的背景颜色：


: : : `
titlestyle = background: *#nnnnnn* ;`

: `
titlestyle = background: *name* ;`




: groupstyle†
: 应用到 *groupN* 单元格的CSS样式。该选项覆写应用于整个表格的任何样式。举例：


: : : `
groupstyle = background:# *nnnnnn* ;`

: `
groupstyle = text-align:[ *left/center/right* ];`

: `
groupstyle = vertical-align:[ *top/middle/bottom* ];`




: liststyle†
: 应用到所有list的CSS样式。若指定了下面的 *oddstyle* 和 *evenstyle* 参数，则它们的优先级高于本参数。


: oddstyle
evenstyle
: 应用到奇数/偶数编号的列表。会推翻由 *liststyle* 定义的样式。缺省的表现是分别添加条纹状的颜色（白色和灰色）到奇数/偶数行，以提高可读性。除了在非常特别的情况下，这些设置不应更改。


: abovestyle†
belowstyle†
: CSS样式，应用到顶端单元格（通过 *above* 参数指定）和底端单元格（通过 *below* 参数指定）。典型地被用来设置背景颜色或文本对齐方式：


: : : `
abovestyle = background:# *nnnnnn* ;`

: `
abovestyle = text-align:[ *left/center/right* ];`





##### 缺省样式
  
这里列出的样式设置是使用导航框的编辑者最经常更改的那些设置。其他更加复杂的样式设置被排除在这个列表之外，以保持它简单。大多数样式是在MediaWiki:Common.css (未找到链接)中设置。
  

: `
bodystyle  = background:#fdfdfd; width:100%; vertical-align:middle;`

: `
titlestyle = background:#ccccff; padding-left:1em; padding-right:1em; text-align:center;`

: `
abovestyle = background:#ddddff; padding-left:1em; padding-right:1em; text-align:center;`

: `
belowstyle = background:#ddddff; padding-left:1em; padding-right:1em; text-align:center;`

: `
groupstyle = background:#ddddff; padding-left:1em; padding-right:1em; text-align:right;`

: `
liststyle  = background:transparent; text-align:left/center;`

: `
oddstyle   = background:transparent;`

: `
evenstyle  = background:#f7f7f7;`


  
由于 *liststyle* 和 *oddstyle* 是透明的，奇数列表有 *bodystyle* 的颜色，其缺省值是#fdfdfd（白色带有少许灰色）。一个list有`
text-align:left;`
设定，如果它有一个group的话；否则，它有`
text-align:center;`
设定。由于只有 *bodystyle* 有一个垂直对齐（vertical-align）属性，所 有其他样式继承其`
vertical-align:middle;`
设定。
  


## 表格的布局
  
由&#123;&#123;[Navbox](./模板-Navbox.md)&#125;&#125; **不带**  *image* 、 *above* 和 *below* 参数生成的表格（添加了灰色的列表背景色仅仅是为了演示）：
  


<table><tbody><tr><td><table cellspacing="0" class="nowraplinks mw-collapsible uncollapsed" style="width:100%;;;"><tbody><tr><th style=";" colspan="2" class="navbox-title"><div class="navbar"><div class="noprint plainlinksneverexpand" style="background-color:transparent; padding:0; font-weight:normal; font-size:80%; white-space:nowrap;"><a class="mw-selflink selflink"><span style=";;border:none;" title="查看这个模板">查</span></a>&#160;<span style="font-size:80%;">•</span>&#160;<a href="/index.php?title=%E6%A8%A1%E6%9D%BF:Navbox/doc&amp;action=edit"><span style=";;border:none;" title="您可以编辑这个模板。请在储存变更之前先预览">编</span></a></div></div><span>{{{title}}}</span></th></tr><tr><td></td></tr><tr><td class="navbox-group" style=";;">{{{group1}}}</td><td style="background:silver;;;" class="navbox-list navbox-odd"><div>{{{list1}}}</div></td></tr><tr><td></td></tr><tr><td class="navbox-group" style=";;">{{{group2}}}</td><td style="background:silver;;;" class="navbox-list navbox-even"><div>{{{list2}}}</div></td></tr><tr><td></td></tr><tr><td colspan="2" style="background:silver;;;" class="navbox-list navbox-odd"><div>{{{list3}}} <i>不带 {{{group3}}}</i></div></td></tr><tr><td></td></tr><tr><td class="navbox-group" style=";;">{{{group4}}}</td><td style="background:silver;;;" class="navbox-list navbox-even"><div>{{{list4}}}</div></td></tr></tbody></table></td></tr></tbody></table>


  
  

由&#123;&#123;[Navbox](./模板-Navbox.md)&#125;&#125; **带有**  *image* 、 *above* 和 *below* 参数生成的表格（添加了灰色的列表背景色仅仅是为了演示）：
  


<table><tbody><tr><td><table cellspacing="0" class="nowraplinks mw-collapsible uncollapsed" style="width:100%;;;"><tbody><tr><th style=";" colspan="3" class="navbox-title"><div class="navbar"><div class="noprint plainlinksneverexpand" style="background-color:transparent; padding:0; font-weight:normal; font-size:80%; white-space:nowrap;"><a class="mw-selflink selflink"><span style=";;border:none;" title="查看这个模板">查</span></a>&#160;<span style="font-size:80%;">•</span>&#160;<a href="/index.php?title=%E6%A8%A1%E6%9D%BF:Navbox/doc&amp;action=edit"><span style=";;border:none;" title="您可以编辑这个模板。请在储存变更之前先预览">编</span></a></div></div><span>{{{title}}}</span></th></tr><tr><td></td></tr><tr><td class="navbox-abovebelow" style=";" colspan="3">{{{above}}}</td></tr><tr><td></td></tr><tr><td class="navbox-group" style=";;">{{{group1}}}</td><td style="background:silver;;;" class="navbox-list navbox-odd"><div>{{{list1}}}</div></td><td class="navbox-image" style="" rowspan="7">{{{image}}}</td></tr><tr><td></td></tr><tr><td class="navbox-group" style=";;">{{{group2}}}</td><td style="background:silver;;;" class="navbox-list navbox-even"><div>{{{list2}}}</div></td></tr><tr><td></td></tr><tr><td colspan="2" style="background:silver;;;" class="navbox-list navbox-odd"><div>{{{list3}}} <i>不带 {{{group3}}}</i></div></td></tr><tr><td></td></tr><tr><td class="navbox-group" style=";;">{{{group4}}}</td><td style="background:silver;;;" class="navbox-list navbox-even"><div>{{{list4}}}</div></td></tr><tr><td></td></tr><tr><td class="navbox-abovebelow" style=";" colspan="3">{{{below}}}</td></tr></tbody></table></td></tr></tbody></table>


  
  

由&#123;&#123;[Navbox](./模板-Navbox.md)&#125;&#125; **带有**  *image* 、 *imageleft* 、 *lists* ，且 **不带**  *groups* 、 *above* 、 *below* 生成的表格（添加了灰色的列表背景色仅仅是为了演示）：
  


<table><tbody><tr><td><table cellspacing="0" class="nowraplinks mw-collapsible uncollapsed" style="width:100%;;;"><tbody><tr><th style=";" colspan="4" class="navbox-title"><div class="navbar"><div class="noprint plainlinksneverexpand" style="background-color:transparent; padding:0; font-weight:normal; font-size:80%; white-space:nowrap;"><a class="mw-selflink selflink"><span style=";;border:none;" title="查看这个模板">查</span></a>&#160;<span style="font-size:80%;">•</span>&#160;<a href="/index.php?title=%E6%A8%A1%E6%9D%BF:Navbox/doc&amp;action=edit"><span style=";;border:none;" title="您可以编辑这个模板。请在储存变更之前先预览">编</span></a></div></div><span>{{{title}}}</span></th></tr><tr><td></td></tr><tr><td class="navbox-imageleft" style="" rowspan="7">{{{imageleft}}}</td><td colspan="2" style="background:silver;;;" class="navbox-list navbox-odd"><div>{{{list1}}}</div></td><td class="navbox-image" style="" rowspan="7">{{{image}}}</td></tr><tr><td></td></tr><tr><td colspan="2" style="background:silver;;;" class="navbox-list navbox-even"><div>{{{list2}}}</div></td></tr><tr><td></td></tr><tr><td colspan="2" style="background:silver;;;" class="navbox-list navbox-odd"><div>{{{list3}}}</div></td></tr><tr><td></td></tr><tr><td colspan="2" style="background:silver;;;" class="navbox-list navbox-even"><div>{{{list4}}}</div></td></tr></tbody></table></td></tr></tbody></table>



## 示例

## 与其他导航框模板的关系
  
此导航框模板被特别设计使得能与另外两个姊妹模板协同工作：&#123;&#123;Navbox with columns (未找到链接)&#125;&#125;和&#123;&#123;Navbox with collapsible groups (未找到链接)&#125;&#125;。所有这三个模板共用常用的参数，以提高一致性与易用性（此类参数在上面的完整参数列表中用一个†
作了标记）。最重要的是，所有这三个模板能互相被用作另一个的子框。
  


## 技术细节
- 此模板为其大部分外观使用CSS类，因此它完全可以更换皮肤。
- 欲了解更多技术细节请参见其MediaWiki:common.css (未找到链接)中的CSS类以及MediaWiki:common.js (未找到链接)中用来隐藏框体的可折叠表格。


### 运作详情
- 列表单元格宽度初始被设置为100%。因此，如果你想手动设置分组单元格的宽度，你就需要同时指定liststyle使之有width:auto。如果你想设置分组宽度并使用图片，这取决于你已弄明白在groupstyle、liststyle、imagestyle和imageleftstyle参数中的CSS，以使所有部件都工作正常。以下两行是设置分组宽度的示例：

: : `
groupstyle = width:10em;`

: `
liststyle = width:auto;`



- 相邻的导航框在它们之间仅有一个1px的边框（除了在IE6中，因其不支持必需的CSS）。如果你设置了`
style/bodystyle`
的顶端外边距（top margin）或底顶端外边距（bottom margin），那么此特性就不运作了。
- 外层导航框表格的缺省的左外边距（margin-left）和右外边距（margin-right）被设置为“auto;”。如果你想使用导航框作为一个浮动对象（float），你需要手动设置左外边距和右外边距的值，因为自动外边距（auto margins)会阻止浮动（float）选项。例如，添加下列代码来使用导航框作为一个浮动对象：

: : `
style = width:22em;float:right;margin-left:1em;margin-right:0em;`




## 參見
- 中文维基百科：[Template:Navbox](https://en.wikipedia.org/wiki/zh:Template:Navbox)





---

此文档由 [THBWiki-Markdown-Builder](https://github.com/Delsin-Yu/THBWiki-Markdown-Builder) 构建。

文档中的所有内容除特殊注明外，均在 [**知识共享(Creative Commons) 署名-非商业性使用-相同方式共享 3.0 协议**](https://creativecommons.org/licenses/by-sa/3.0/deed.zh-hans) 下提供，附加条款亦可能应用。

引用类型与其他类型作品版权归原作者所有，如有作者授权则遵照授权协议使用。

详细请查阅 [THBWiki：免责声明](https://thbwiki.cc/THBWiki:%E5%85%8D%E8%B4%A3%E5%A3%B0%E6%98%8E)。

