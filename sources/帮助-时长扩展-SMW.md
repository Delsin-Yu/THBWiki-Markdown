# 帮助:时长扩展/SMW

<!-- source html: D:\Repos\THBWiki-Markdown-Builder\THBWikiMarkdown\Temp\other\f\fb\ns12%3A%E6%97%B6%E9%95%BF%E6%89%A9%E5%B1%95%2FSMW.html -->

扩展帮助文档

  
以下是**时长扩展**SMW部分的说明文档。
  

## 目录

- [1 安装](#安装)
  - [1.1 SMW_SQLStore3.php](#SMW_SQLStore3.php)
  - [1.2 SMW_DataItem.php](#SMW_DataItem.php)
  - [1.3 SMW_Language.php](#SMW_Language.php)
  - [1.4 SMW_LanguageEn](#SMW_LanguageEn)
  - [1.5 SMW_LanguageZh](#SMW_LanguageZh)


- [2 时长类型](#时长类型)
  - [2.1 定义](#定义)
  - [2.2 搜索](#搜索)
  - [2.3 预设格式](#预设格式)
  - [2.4 自订格式语法](#自订格式语法)
  - [2.5 例子](#例子)
  - [2.6 数学运算](#数学运算)


- [3 链接类型](#链接类型)
  - [3.1 定义](#定义_2)
  - [3.2 搜索](#搜索_2)
  - [3.3 预设格式](#预设格式_2)




## 安装
  
需要修改的**SMW**文件有：
  

- `\extensions\SemanticMediaWiki\includes\storage\SQLStore`目录下的`SMW_SQLStore3.php`
- `\extensions\SemanticMediaWiki\includes\dataitems`目录下的`SMW_DataItem.php`
- `\extensions\SemanticMediaWiki\languages`目录下的`SMW_Language.php`和`SMW_LanguageEn`、`SMW_LanguageZh.php`或其他语言的`SMW_LanguageXX.php`


### SMW_SQLStore3.php
  
`protected static $di_type_tables = array( ... )`里，加上：
  

```
SMWDataItem::TYPE_LINK => 'smw_di_uri', ```

  
`public function getDataItemHandlerForDIType( $diType ) { ... }`里的`switch ( $diType ) { ... }`里，加上：
  

```
case SMWDataItem::TYPE_LINK: $this->diHandlers[$diType] = new SMWDIHandlerLink( $this ); break; ```


### SMW_DataItem.php
  
`abstract class SMWDataItem { ... }`里，加上：
  

```
const TYPE_LINK = 21; ```


### SMW_Language.php
  
`static protected $enDatatypeAliases = array( ... )`里，加上：
  

```
'Duration' => '_dur', 'Link' => '_lin', ```


### SMW_LanguageEn
  
`protected $m_DatatypeLabels = array( ... )`里，加上：
  

```
'_dur' => 'Duration', // name of the duration type '_lin' => 'Link', // name of the link type ```


### SMW_LanguageZh
  
`protected $m_DatatypeLabels = array( ... )`里，加上：
  

```
'_dur' => '时长', // 'Duration', // name of the duration type '_lin' => '链接', // 'Link', // name of the Link type ```


## 时长类型
  
用于储存时长值。
  

### 定义

1. 在属性页面加上`[[Has type::Duration]]`。
2. 在词条页面加上`[[时长属性名::时长字串]]`。


### 搜索

```
{{#ask:[[持续长度::>04:12--00:03]][[持续长度::<04:12++00:03]] |?名称 |?持续长度 |limit=10|searchlabel=|sort=持续长度|order=desc|mainlabel=-}}```


### 预设格式
  
默认格式为MEDIAWIKI。
  

```
{{#ask:[[总时长::+]]|?名称 |?总时长#MEDIAWIKI=维基格式 |?总时长#SHORT=短格式 |?总时长#LONG=长格式 |?总时长#ISO=ISO标准 |?总时长#CUE=CUE格式 |limit=20|searchlabel=|sort=总时长|order=desc|mainlabel=-}}```


### 自订格式语法

```
{{#ask:[[总时长::+]]|?名称 |?总时长#$O=$O // 以小时为单位的时长 |?总时长#$I=$I // 以分钟为单位的时长 |?总时长#$E=$E // 以秒为单位的时长 |?总时长#$i=$i // 以分钟为单位的时长（向下取整） |?总时长#$e=$e // 以秒为单位的时长（向下取整） |?总时长#$H=$H // 时长的小时部分（前导零） |?总时长#$M=$M // 时长的分钟部分（前导零） |?总时长#$S=$S // 时长的秒部分（前导零） |?总时长#$D =$D // 时长的小数部分，唯存在时才显示小数点，可能会返回空值所以在某些格式中不能单独使用 |?总时长#$h=$h // 时长的小时部分 |?总时长#$m=$m // 时长的分钟部分 |?总时长#$s=$s // 时长的秒部分 |?总时长#$d=$d // 时长的小数部分，取整并后导零至四位 |limit=20|searchlabel=|sort=总时长|order=desc|mainlabel=-}}```


### 例子

```
{{#ask:[[专辑总时长::+]]|?专辑名称 |?专辑总时长#$h小时 $m分钟 $s秒=$h小时 $m分钟 $s秒 |?专辑总时长#$i分$s$D秒=$i分$s$D秒 |?专辑总时长#$O小时=$O小时 |limit=20|searchlabel=|sort=专辑总时长|order=desc|mainlabel=-}}```


<table><tbody><tr><th class="专辑名称"><a title="属性:专辑名称">专辑名称</a></th><th class="$h小时-$m分钟-$s秒"><a title="属性:专辑总时长">$h小时 $m分钟 $s秒</a></th><th class="$i分$s$D秒"><a title="属性:专辑总时长">$i分$s$D秒</a></th><th class="$O小时"><a title="属性:专辑总时长">$O小时</a></th></tr><tr data-row-number="1" class="row-odd"><td class="专辑名称 smwtype_txt">东方二次同人(Fan Games)专辑8bit洛克人风格Remix</td><td class="$h小时-$m分钟-$s秒 smwtype_dur" data-sort-value="46519">12小时 55分钟 19秒</td><td class="$i分$s$D秒 smwtype_dur" data-sort-value="46519">775分19秒</td><td class="$O小时 smwtype_dur" data-sort-value="46519">12.921944444444小时</td></tr><tr data-row-number="2" class="row-even"><td class="专辑名称 smwtype_txt">東方幻奏響Revival弐 ～魔法少女vs魔王勇者～</td><td class="$h小时-$m分钟-$s秒 smwtype_dur" data-sort-value="39882">11小时 4分钟 42秒</td><td class="$i分$s$D秒 smwtype_dur" data-sort-value="39882">664分42秒</td><td class="$O小时 smwtype_dur" data-sort-value="39882">11.078333333333小时</td></tr><tr data-row-number="3" class="row-odd"><td class="专辑名称 smwtype_txt">東方幻奏響UROBOROS業 ～eNDoFtHEuLTIMATEoVERdRIVE～</td><td class="$h小时-$m分钟-$s秒 smwtype_dur" data-sort-value="39292">10小时 54分钟 52秒</td><td class="$i分$s$D秒 smwtype_dur" data-sort-value="39292">654分52秒</td><td class="$O小时 smwtype_dur" data-sort-value="39292">10.914444444444小时</td></tr><tr data-row-number="4" class="row-even"><td class="专辑名称 smwtype_txt">大弾奏結界 総集篇纂組曲 ～The Suite～</td><td class="$h小时-$m分钟-$s秒 smwtype_dur" data-sort-value="38533">10小时 42分钟 13秒</td><td class="$i分$s$D秒 smwtype_dur" data-sort-value="38533">642分13秒</td><td class="$O小时 smwtype_dur" data-sort-value="38533">10.703611111111小时</td></tr><tr data-row-number="5" class="row-odd"><td class="专辑名称 smwtype_txt">Re Comp with We Love The Toho RMXes!</td><td class="$h小时-$m分钟-$s秒 smwtype_dur" data-sort-value="37274">10小时 21分钟 14秒</td><td class="$i分$s$D秒 smwtype_dur" data-sort-value="37274">621分14秒</td><td class="$O小时 smwtype_dur" data-sort-value="37274">10.353888888889小时</td></tr><tr data-row-number="6" class="row-even"><td class="专辑名称 smwtype_txt">東方幻奏響UROBOROS弐 ～fAIRYtAILoVERdRIVE～</td><td class="$h小时-$m分钟-$s秒 smwtype_dur" data-sort-value="37103">10小时 18分钟 23秒</td><td class="$i分$s$D秒 smwtype_dur" data-sort-value="37103">618分23秒</td><td class="$O小时 smwtype_dur" data-sort-value="37103">10.306388888889小时</td></tr><tr data-row-number="7" class="row-odd"><td class="专辑名称 smwtype_txt">Beyond Boundaries</td><td class="$h小时-$m分钟-$s秒 smwtype_dur" data-sort-value="36630">10小时 10分钟 30秒</td><td class="$i分$s$D秒 smwtype_dur" data-sort-value="36630">610分30秒</td><td class="$O小时 smwtype_dur" data-sort-value="36630">10.175小时</td></tr><tr data-row-number="8" class="row-even"><td class="专辑名称 smwtype_txt">We Love the Toho Rmxes!～Iemitsu.Productions Toho RMX Series Complete Box～</td><td class="$h小时-$m分钟-$s秒 smwtype_dur" data-sort-value="36437">10小时 7分钟 17秒</td><td class="$i分$s$D秒 smwtype_dur" data-sort-value="36437">607分17秒</td><td class="$O小时 smwtype_dur" data-sort-value="36437">10.121388888889小时</td></tr><tr data-row-number="9" class="row-odd"><td class="专辑名称 smwtype_txt">いえろ～ぜぶら　ふぃな～れBOX</td><td class="$h小时-$m分钟-$s秒 smwtype_dur" data-sort-value="35517">9小时 51分钟 57秒</td><td class="$i分$s$D秒 smwtype_dur" data-sort-value="35517">591分57秒</td><td class="$O小时 smwtype_dur" data-sort-value="35517">9.8658333333333小时</td></tr><tr data-row-number="10" class="row-even"><td class="专辑名称 smwtype_txt">Look Back</td><td class="$h小时-$m分钟-$s秒 smwtype_dur" data-sort-value="30458">8小时 27分钟 38秒</td><td class="$i分$s$D秒 smwtype_dur" data-sort-value="30458">507分38秒</td><td class="$O小时 smwtype_dur" data-sort-value="30458">8.4605555555556小时</td></tr><tr data-row-number="11" class="row-odd"><td class="专辑名称 smwtype_txt">MEGA ZUN</td><td class="$h小时-$m分钟-$s秒 smwtype_dur" data-sort-value="29574">8小时 12分钟 54秒</td><td class="$i分$s$D秒 smwtype_dur" data-sort-value="29574">492分54秒</td><td class="$O小时 smwtype_dur" data-sort-value="29574">8.215小时</td></tr><tr data-row-number="12" class="row-even"><td class="专辑名称 smwtype_txt">EastNewSound 10th Special Best</td><td class="$h小时-$m分钟-$s秒 smwtype_dur" data-sort-value="29380">8小时 9分钟 40秒</td><td class="$i分$s$D秒 smwtype_dur" data-sort-value="29380">489分40秒</td><td class="$O小时 smwtype_dur" data-sort-value="29380">8.1611111111111小时</td></tr><tr data-row-number="13" class="row-odd"><td class="专辑名称 smwtype_txt">東方幻奏響UROBOROS肆 ～dEATHtINYoVERdRIVE～</td><td class="$h小时-$m分钟-$s秒 smwtype_dur" data-sort-value="29041">8小时 4分钟 1秒</td><td class="$i分$s$D秒 smwtype_dur" data-sort-value="29041">484分1秒</td><td class="$O小时 smwtype_dur" data-sort-value="29041">8.0669444444444小时</td></tr><tr data-row-number="14" class="row-even"><td class="专辑名称 smwtype_txt">東方九十九折</td><td class="$h小时-$m分钟-$s秒 smwtype_dur" data-sort-value="27358">7小时 35分钟 58秒</td><td class="$i分$s$D秒 smwtype_dur" data-sort-value="27358">455分58秒</td><td class="$O小时 smwtype_dur" data-sort-value="27358">7.5994444444444小时</td></tr><tr data-row-number="15" class="row-odd"><td class="专辑名称 smwtype_txt">東方幻奏響UROBOROS参 ～とある魔法と幻想の無限螺旋～</td><td class="$h小时-$m分钟-$s秒 smwtype_dur" data-sort-value="26568">7小时 22分钟 48秒</td><td class="$i分$s$D秒 smwtype_dur" data-sort-value="26568">442分48秒</td><td class="$O小时 smwtype_dur" data-sort-value="26568">7.38小时</td></tr><tr data-row-number="16" class="row-even"><td class="专辑名称 smwtype_txt">東方空宴歌-COMPLETE-</td><td class="$h小时-$m分钟-$s秒 smwtype_dur" data-sort-value="24243">6小时 44分钟 3秒</td><td class="$i分$s$D秒 smwtype_dur" data-sort-value="24243">404分3秒</td><td class="$O小时 smwtype_dur" data-sort-value="24243">6.7341666666667小时</td></tr><tr data-row-number="17" class="row-odd"><td class="专辑名称 smwtype_txt">イノキー ザ ベスト3</td><td class="$h小时-$m分钟-$s秒 smwtype_dur" data-sort-value="24101">6小时 41分钟 41秒</td><td class="$i分$s$D秒 smwtype_dur" data-sort-value="24101">401分41秒</td><td class="$O小时 smwtype_dur" data-sort-value="24101">6.6947222222222小时</td></tr><tr data-row-number="18" class="row-even"><td class="专辑名称 smwtype_txt">東方魔法少女 アルティメット☆れいむ</td><td class="$h小时-$m分钟-$s秒 smwtype_dur" data-sort-value="22230">6小时 10分钟 30秒</td><td class="$i分$s$D秒 smwtype_dur" data-sort-value="22230">370分30秒</td><td class="$O小时 smwtype_dur" data-sort-value="22230">6.175小时</td></tr><tr data-row-number="19" class="row-odd"><td class="专辑名称 smwtype_txt">The Afterlogue</td><td class="$h小时-$m分钟-$s秒 smwtype_dur" data-sort-value="20254">5小时 37分钟 34秒</td><td class="$i分$s$D秒 smwtype_dur" data-sort-value="20254">337分34秒</td><td class="$O小时 smwtype_dur" data-sort-value="20254">5.6261111111111小时</td></tr><tr data-row-number="20" class="row-even"><td class="专辑名称 smwtype_txt">The FreeBird</td><td class="$h小时-$m分钟-$s秒 smwtype_dur" data-sort-value="19310">5小时 21分钟 50秒</td><td class="$i分$s$D秒 smwtype_dur" data-sort-value="19310">321分50秒</td><td class="$O小时 smwtype_dur" data-sort-value="19310">5.3638888888889小时</td></tr></tbody></table>


### 数学运算
  
此功能需要修改**SemanticResultFormats**的文件。
  

<table>
<tbody><tr><th>数学运算</th><th>总时长</th></tr>
<tr><td>加总(format=sum)</td><td>16</td></tr>
<tr><td>平均(format=average)</td><td>0</td></tr>
<tr><td>中值(format=median)</td><td>0</td></tr>
<tr><td>最大(format=max)</td><td>2</td></tr>
<tr><td>最小(format=min)</td><td>0</td></tr>
</tbody></table>


## 链接类型
  
用于储存URL链接和替代字串，接受`[https://thwiki.cc/ 首页]`（只能通过#set）和`https://thwiki.cc/ 首页`的格式。
  

### 定义

1. 在属性页面加上`[[Has type::Link]]`。
2. 在词条页面加上`[[链接属性名::链接字串]]`。
3. 可以使用`[[链接属性名::链接字串|#显示格式]]`的方法来改变属性在该页的显示方式。


### 搜索

```
{{#ask:[[社团页面::+]] |?名称 |?社团页面 |limit=10|searchlabel=|mainlabel=-}}```


```
{{#ask:[[其他页面::~* D-STAGE]] |?-Has subobject |?其他页面=通贩页面 |limit=10|searchlabel=|mainlabel=-}}```


### 预设格式
  
默认格式为link。
  

```
{{#ask:[[官网页面::+]][[分类:同人专辑]]|?专辑名称 |?官网页面#link=链接 |?官网页面#url=URL |?官网页面#alter=替代字串 |?官网页面#-=纯文字 |limit=5|searchlabel=|mainlabel=-}}```


<table><tbody><tr><th class="专辑名称"><a title="属性:专辑名称">专辑名称</a></th><th class="链接"><a title="属性:官网页面">链接</a></th><th class="URL"><a title="属性:官网页面">URL</a></th><th class="替代字串"><a title="属性:官网页面">替代字串</a></th><th class="纯文字"><a title="属性:官网页面">纯文字</a></th></tr><tr data-row-number="1" class="row-odd"><td class="专辑名称 smwtype_txt">_(:з」∠)_</td><td class="链接 smwtype_lin"><a rel="nofollow" class="external free" href="https://weibo.com/p/1005056353823018">https://weibo.com/p/1005056353823018</a> 官网<br><a rel="nofollow" class="external free" href="https://music.163.com/#/album?id=35154134">https://music.163.com/#/album?id=35154134</a> 官网</td><td class="URL smwtype_lin"><a rel="nofollow" class="external free" href="https://weibo.com/p/1005056353823018">https://weibo.com/p/1005056353823018</a><br><a rel="nofollow" class="external free" href="https://music.163.com/#/album?id=35154134">https://music.163.com/#/album?id=35154134</a></td><td class="替代字串 smwtype_lin">官网<br>官网</td><td class="纯文字 smwtype_lin"><a rel="nofollow" class="external text" href="https://weibo.com/p/1005056353823018">官网</a><br><a rel="nofollow" class="external text" href="https://music.163.com/#/album?id=35154134">官网</a></td></tr><tr data-row-number="2" class="row-even"><td class="专辑名称 smwtype_txt">"Activity" Case:01 -Graveyard Memory-</td><td class="链接 smwtype_lin"><a rel="nofollow" class="external free" href="http://gchm-music.com/cont/activity/">http://gchm-music.com/cont/activity/</a> 官网</td><td class="URL smwtype_lin"><a rel="nofollow" class="external free" href="http://gchm-music.com/cont/activity/">http://gchm-music.com/cont/activity/</a></td><td class="替代字串 smwtype_lin">官网</td><td class="纯文字 smwtype_lin"><a rel="nofollow" class="external text" href="http://gchm-music.com/cont/activity/">官网</a></td></tr><tr data-row-number="3" class="row-odd"><td class="专辑名称 smwtype_txt">"Activity" Case:02 -Nightmare Counselor-</td><td class="链接 smwtype_lin"><a rel="nofollow" class="external free" href="http://gchm-music.com/cont/activity2/">http://gchm-music.com/cont/activity2/</a> 官网</td><td class="URL smwtype_lin"><a rel="nofollow" class="external free" href="http://gchm-music.com/cont/activity2/">http://gchm-music.com/cont/activity2/</a></td><td class="替代字串 smwtype_lin">官网</td><td class="纯文字 smwtype_lin"><a rel="nofollow" class="external text" href="http://gchm-music.com/cont/activity2/">官网</a></td></tr><tr data-row-number="4" class="row-even"><td class="专辑名称 smwtype_txt">"Activity" Case:03 -Historical Vacation-</td><td class="链接 smwtype_lin"><a rel="nofollow" class="external free" href="http://gchm-music.com/cont/activity3/">http://gchm-music.com/cont/activity3/</a> 官网</td><td class="URL smwtype_lin"><a rel="nofollow" class="external free" href="http://gchm-music.com/cont/activity3/">http://gchm-music.com/cont/activity3/</a></td><td class="替代字串 smwtype_lin">官网</td><td class="纯文字 smwtype_lin"><a rel="nofollow" class="external text" href="http://gchm-music.com/cont/activity3/">官网</a></td></tr><tr data-row-number="5" class="row-odd"><td class="专辑名称 smwtype_txt">"Activity" Case:04 -Cosmic Horoscope-</td><td class="链接 smwtype_lin"><a rel="nofollow" class="external free" href="http://activity-case-04.tumblr.com/">http://activity-case-04.tumblr.com/</a> 官网</td><td class="URL smwtype_lin"><a rel="nofollow" class="external free" href="http://activity-case-04.tumblr.com/">http://activity-case-04.tumblr.com/</a></td><td class="替代字串 smwtype_lin">官网</td><td class="纯文字 smwtype_lin"><a rel="nofollow" class="external text" href="http://activity-case-04.tumblr.com/">官网</a></td></tr></tbody></table>


---

此文档由 [THBWiki-Markdown-Builder](https://github.com/Delsin-Yu/THBWiki-Markdown-Builder) 构建。

文档中的所有内容除特殊注明外，均在 [**知识共享(Creative Commons) 署名-非商业性使用-相同方式共享 3.0 协议**](https://creativecommons.org/licenses/by-sa/3.0/deed.zh-hans) 下提供，附加条款亦可能应用。

引用类型与其他类型作品版权归原作者所有，如有作者授权则遵照授权协议使用。

详细请查阅 [THBWiki：免责声明](https://thbwiki.cc/THBWiki:%E5%85%8D%E8%B4%A3%E5%A3%B0%E6%98%8E)。

