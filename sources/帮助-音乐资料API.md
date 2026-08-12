# 帮助:音乐资料API

<!-- source html: D:\Repos\THBWiki-Markdown-Builder\THBWikiMarkdown\Temp\other\9\97\ns12%3A%E9%9F%B3%E4%B9%90%E8%B5%84%E6%96%99API.html -->

帮助文档 | 扩展帮助文档

本页是THBWiki的[编辑帮助文档](./分类-帮助文档.md)  
**音乐资料API**是一个用来搜索专辑和曲目和获取资料的应用程序接口（API），支持 **使用专辑/曲目名称搜索** 和 **用搜索提供的SMWID或词条名获取资料** 。注意：**SMWID**不是一个永远固定不变的识别ID，Wiki系统有大更新或SMW有需要重新运算时，此ID会变更。
  
<center><big><big>**如果对编程苦手而直接想使用API进行专辑资料填写的话,可以直接跳转到基于此API的[Mp3tag插件](#实作范例)**</big></big></center>
## 目录

- [1 简介](#简介)
- [2 参数及用法](#参数及用法)
  - [2.1 通用](#通用)
    - [2.1.1 m / 查询模式](#m_/_查询模式)
    - [2.1.2 g / gzip压缩等级](#g_/_gzip压缩等级)
    - [2.1.3 d / 结果格式](#d_/_结果格式)


  - [2.2 搜索专辑](#搜索专辑)
    - [2.2.1 v / 搜索字串](#v_/_搜索字串)
    - [2.2.2 o / 是否返回社团名](#o_/_是否返回社团名)
    - [2.2.3 l / 限制结果数量](#l_/_限制结果数量)
    - [2.2.4 d / 结果格式](#d_/_结果格式_2)


  - [2.3 搜索曲目](#搜索曲目)
    - [2.3.1 v / 搜索字串](#v_/_搜索字串_2)
    - [2.3.2 o / 是否返回专辑名](#o_/_是否返回专辑名)
    - [2.3.3 d / 结果格式](#d_/_结果格式_3)


  - [2.4 获取专辑](#获取专辑)
    - [2.4.1 f / 专辑属性请求列表](#f_/_专辑属性请求列表)
    - [2.4.2 p / 曲目属性请求列表](#p_/_曲目属性请求列表)
    - [2.4.3 a / 专辑SMWID](#a_/_专辑SMWID)
    - [2.4.4 t / 专辑词条名](#t_/_专辑词条名)
    - [2.4.5 s / 多值内容分隔符](#s_/_多值内容分隔符)
    - [2.4.6 d / 结果格式](#d_/_结果格式_4)


  - [2.5 获取曲目](#获取曲目)
    - [2.5.1 i / 曲目SMWID列表](#i_/_曲目SMWID列表)
    - [2.5.2 d / 结果格式](#d_/_结果格式_5)




- [3 实作范例](#实作范例)


## 简介
  
此API的链接是[https://thwiki.cc/album.php](https://thwiki.cc/album.php)。
  
  
此API有四种查询模式：
  

- 搜索专辑：模糊搜索专辑名
- 搜索曲目：模糊搜索曲目名
- 获取专辑：用以上搜索提供的**SMWID**或词条名获取专辑资料和专辑含有的曲目资料列表
- 获取曲目：用以上搜索提供的**SMWID**列表获取曲目资料列表


## 参数及用法

### 通用

#### m / 查询模式
  
任何查询都必须含有此参数，用于判断查询模式，允许的值为：
  

- “0”或“sa”：表示搜索专辑
- “1”或“st”：表示搜索曲目
- “2”或“ga”：表示获取专辑
- “3”或“gt”：表示获取曲目

  
例子：
  
使用搜索专辑模式
: [https://thwiki.cc/album.php?m=sa](https://thwiki.cc/album.php?m=sa)
使用获取专辑模式
: [https://thwiki.cc/album.php?m=2](https://thwiki.cc/album.php?m=2)

#### g / gzip压缩等级
  
指定gzip压缩等级，0为不压缩，最大只接受2（因为2以上效果差别不大），默认为1。即使设定数字大于0，若用户端/浏览器不支持gzip，则不管怎样也不会压缩。长度在1024字节以内的内容也不会压缩。
例子：
  
搜索“pop Culture 5”，要求无压缩
: [https://thwiki.cc/album.php?m=sa&v=pop+Culture+5&g=0](https://thwiki.cc/album.php?m=sa&v=pop%20Culture%205&g=0)
搜索“mono”，要求返回社团名，要求等级2的压缩
: [https://thwiki.cc/album.php?m=sa&v=mono&o=1&g=2](https://thwiki.cc/album.php?m=sa&v=mono&o=1&g=2)

#### d / 结果格式
  
设定搜索返回的结果格式，默认为一般格式，允许的值为：
  

- “0”或“nm”：一般格式，以`[ [[ id, aSMWID ], [ 参数名1, a内容1 ], [ 参数名2, a内容2 ]], [[ id, bSMWID ], [ 参数名1, b内容1 ], [ 参数名2, b内容2 ]] ]`的结构返回json文件，搜索模式会省略参数名
- “1”或“nr”：一般（把**SMWID**放到最后）格式，以`[ [[ 参数名1, a内容1 ], [ 参数名2, a内容2 ], [ id, aSMWID ]], [[ 参数名1, b内容1 ], [ 参数名2, b内容2 ], [ id, bSMWID ]] ]`的结构返回json文件，搜索模式会省略参数名
- “2”或“kv”：键值格式，以`{ aSMWID: { 参数名1: a内容1, 参数名2: a内容2 }, bSMWID: { 参数名1: b内容1, 参数名2: b内容2 } }`的结构返回json文件，搜索模式会省略参数名
- “3”或“pa”：平行格式，以`{ id: [ aSMWID, bSMWID ], 参数名1: [ a内容1, a内容1 ], 参数名2: [ b内容2, b内容2 ] }`的结构返回json文件，搜索模式会省略参数名
- “4”或“pr”：平行（把**SMWID**放到最后）格式，以`{ 参数名1: [ a内容1, a内容1 ], 参数名2: [ b内容2, b内容2 ], id: [ aSMWID, bSMWID ] }`的结构返回json文件，搜索模式会省略参数名
- “5”或“tn”：一般文本格式，以`**\t**aSMWID**\t**a内容1**\t**a内容2**\n\t**bSMWID**\t**b内容1**\t**b内容2**\n**`的结构返回纯文字文本，多值的内容会强制被“|”串起来，搜索模式会省略参数名
- “6”或“tp”：平行文本格式，以`**\t**id**\t**aSMWID**\t**bSMWID**\n\t**参数名1**\t**a内容1**\t**b内容1**\n\t**参数名2**\t**a内容2**\t**b内容2**\n**`的结构返回纯文字文本，多值的内容会强制被“|”串起来，搜索模式会省略参数名


### 搜索专辑
搜索专辑模式
: [https://thwiki.cc/album.php?m=sa](https://thwiki.cc/album.php?m=sa)

#### v / 搜索字串
  
搜索专辑模式中必须含有此参数，不能为空，不能全是无效字元。输入的字串会被简化和切开，模糊匹配数据库内的专辑名。
  
  
例子：
  
搜索“pop Culture 5”
: [https://thwiki.cc/album.php?m=sa&v=pop+Culture+5](https://thwiki.cc/album.php?m=sa&v=pop%20Culture%205)
搜索“mono”
: [https://thwiki.cc/album.php?m=sa&v=mono](https://thwiki.cc/album.php?m=sa&v=mono)

#### o / 是否返回社团名
  
若含有此参数，搜索返回的专辑列表会包含专辑的制作社团名，多社团合作的专辑只会返回其中一个社团。
  
  
例子：
  
搜索“pop Culture 5”，要求返回社团名
: [https://thwiki.cc/album.php?m=sa&v=pop+Culture+5&o=1](https://thwiki.cc/album.php?m=sa&v=pop%20Culture%205&o=1)
搜索“mono”，要求返回社团名
: [https://thwiki.cc/album.php?m=sa&v=mono&o=1](https://thwiki.cc/album.php?m=sa&v=mono&o=1)

#### l / 限制结果数量
  
可以设定显示搜索返回的最大结果数量，默认为10，最多可以设为30。
  
  
例子：
  
搜索“pop Culture 5”，要求返回社团名，限制最大返回1个结果
: [https://thwiki.cc/album.php?m=sa&v=pop+Culture+5&o=1&l=1](https://thwiki.cc/album.php?m=sa&v=pop%20Culture%205&o=1&l=1)
搜索“mono”，要求返回社团名，限制最大返回30个结果
: [https://thwiki.cc/album.php?m=sa&v=mono&o=1&l=30](https://thwiki.cc/album.php?m=sa&v=mono&o=1&l=30)

#### d / 结果格式
  
具体参考[d / 结果格式](#d_/_结果格式)，搜索模式中tp平衡文本模式无效。
  
  
例子：
  
搜索“pop Culture 5”，要求返回社团名，以一般格式返回
: [https://thwiki.cc/album.php?m=sa&v=pop+Culture+5&o=1&d=0](https://thwiki.cc/album.php?m=sa&v=pop%20Culture%205&o=1&d=0)
结果
: 

```
[[131939,"POP|CULTURE 5","Alstroemeria Records"],[27733,"POP|CULTURE","Alstroemeria Records"],[70866,"POP|CULTURE 2","Alstroemeria Records"],[229524,"POP|CULTURE 3","Alstroemeria Records"],[234876,"POP|CULTURE 4","Alstroemeria Records"]]```

搜索“touhou”，要求返回社团名，限制最大返回5个结果，以键值格式返回
: [https://thwiki.cc/album.php?m=sa&v=touhou&l=5&d=kv](https://thwiki.cc/album.php?m=sa&v=touhou&l=5&d=kv)
结果
: 

```
{"9053": "TOUHOU I-S","17956": "Touhou Synthesis","35034": "TOUHOU meets HARDCORE 1","229905": "Touhou Project pops arranged instruments6","236022": "Touhou Project pops arranged instruments7"}```

搜索“touhou”，要求返回社团名，限制最大返回5个结果，以平行格式返回
: [https://thwiki.cc/album.php?m=sa&v=touhou&o=1&l=5&d=pa](https://thwiki.cc/album.php?m=sa&v=touhou&o=1&l=5&d=pa)
结果
: 

```
[[9053,35034,229905,236022,17956],["TOUHOU I-S","TOUHOU meets HARDCORE 1","Touhou Project pops arranged instruments6","Touhou Project pops arranged instruments7","Touhou Synthesis"],["趣味工房にんじんわいん","Rolling Contact","logical emotion","logical emotion","DDBY",]]```

搜索“mono”，要求返回社团名，以一般文本格式返回
: [https://thwiki.cc/album.php?m=sa&v=mono&o=1&d=tn](https://thwiki.cc/album.php?m=sa&v=mono&o=1&d=tn)
结果
: 

```
* 24253 MONOCHROME XL Project 43620 MONOMIND 2012 sampler MONOMIND 58524 monocolotion Foxtail-Grass Studio 36977 もののべ姫 SiesTail 20813 そこに在るもの 舞风 251169 ヒミツナグモノ TUMENECO 53556 唄いもの ししまいブラザーズ 36931 猫物語-ネコモノガタリ- Golden City Factory 156795 紅物語-アカモノガタリ- Golden City Factory 6317 紅魔と洋酒と宴会モノ。 AQUA STYLE * ```


### 搜索曲目
搜索曲目模式
: [https://thwiki.cc/album.php?m=st](https://thwiki.cc/album.php?m=st)
  
大致和[搜索专辑](#搜索专辑)差不多，这里只列出有差异的项。
  

#### v / 搜索字串
  
搜索曲目模式中必须含有此参数，不能为空，不能全是无效字元。输入的字串会被简化和切开，模糊匹配数据库内的曲目名。
例子：
  
搜索“sky drive”
: [https://thwiki.cc/album.php?m=st&v=sky%20drive](https://thwiki.cc/album.php?m=st&v=sky%20drive)
搜索“ドリーム”
: [https://thwiki.cc/album.php?m=st&v=%E3%83%89%E3%83%AA%E3%83%BC%E3%83%A0](https://thwiki.cc/album.php?m=st&v=ドリーム)

#### o / 是否返回专辑名
  
若含有此参数，搜索返回的曲目列表会包含曲目所在的专辑名。
  
  
例子：
  
搜索“sky drive”，要求返回专辑名
: [https://thwiki.cc/album.php?m=st&v=sky%20drive&o=1](https://thwiki.cc/album.php?m=st&v=sky%20drive&o=1)
搜索“ドリーム”，要求返回专辑名
: [https://thwiki.cc/album.php?m=st&v=%E3%83%89%E3%83%AA%E3%83%BC%E3%83%A0&o=1](https://thwiki.cc/album.php?m=st&v=ドリーム&o=1)

#### d / 结果格式
  
具体参考[d / 结果格式](#d_/_结果格式)，搜索模式中tp平衡文本模式无效。
  
  
例子：
  
搜索“sky drive”，要求返回专辑名，以一般格式返回
: [https://thwiki.cc/album.php?m=st&v=sky%20drive&o=1&d=0](https://thwiki.cc/album.php?m=st&v=sky%20drive&o=1&d=0)
结果
: 

```
[[75860,"SkyDrive!","Blooming Daydream the instrumental"],[75718,"SkyDrive!","Blooming Daydream"],[229776,"SkyDrive! (More POP)","Harmony of Twice"],[233482,"SkyDrive! (VALLEYSTONE Remix Extended)","Amateras Records Exclusive Disc Spring 2015"],[69210,"SkyDrive! [VALLEYSTONE Remix]","Reactionary Wave the Instrumental"],[75799,"SkyDrive! [VALLEYSTONE Remix]","Reactionary Wave -Amateras Records Remixes Vol.3-"],[231153,"Skydrive!","Amateras Records Best Vol.2"]]```


### 获取专辑
获取专辑模式
: [https://thwiki.cc/album.php?m=ga](https://thwiki.cc/album.php?m=ga)

#### f / 专辑属性请求列表
  
指定需要获取的专辑属性列表，属性名之间可以用空格、,或+分隔，不区分大小写，允许的属性为：
  

- alname：专辑名称
- event：发售展会名称
- eventpage：发售展会词条
- circle：制作方
- date：发售日期，格式为YYYY/MM/DD
- year：发售年份
- rate：年龄限制
- number：系列编号
- disc：专辑碟数
- track：专辑音轨数
- time：专辑总时长，以秒为单位的一个数字。
- property：专辑类型
- style：专辑风格
- only：专辑特定选材
- price：发售价格，格式为1234.567 JYP
- eventprice：会场售价，格式为1234.567 JYP
- shopprice：通贩售价，格式为1234.567 JYP
- note：备注
- official：官网页面
- cover：封面图片词条，只返回封面图片词条名，不包含命名空间。
- coverurl：封面图片链接，会生成最大800px×800px的封面图片缩图链接，可直接下载做成封面图。
- coverchar：封面角色

  
例子：
  
获取SMWID是131939的专辑（POP｜CULTURE 5）的alname、event、date和eventprice
: [https://thwiki.cc/album.php?m=ga&a=131939&f=alname+event+date+eventprice](https://thwiki.cc/album.php?m=ga&a=131939&f=alname%20event%20date%20eventprice)

#### p / 曲目属性请求列表
  
指定需要获取的曲目属性列表，属性名之间可以用空格、,或+分隔，不区分大小写，允许的属性为：
  

- name：曲目名称
- discno：曲目碟号
- trackno：曲目音轨号
- circle：制作方
- type：曲目类型
- time：曲目时长，以秒为单位的一个数字。
- ogmusic：曲目原曲
- ogmusicno：曲目原曲数
- ogwork：曲目来源
- ogworkno：曲目来源数
- artist：曲目人员，结合演唱、配音、编曲和作曲的属性，优先返回演唱，没有演唱则返回配音，没有配音则返回编曲，没有编曲则返回作曲。
- arrange：编曲
- vocal：演唱
- compose：作曲
- dub：配音
- lyric：作词
- script：剧本
- perform：演奏
- lrc：歌词lrc文件地址（由cd.thwiki.cc根据wiki上对应的歌词页面内容生成，不一定有效）

  
例子：
  
获取SMWID是131939的专辑（POP｜CULTURE 5）的曲目的name、trackno、artist和ogmusic
: [https://thwiki.cc/album.php?m=ga&a=131939&p=name+trackno+artist+ogmusic](https://thwiki.cc/album.php?m=ga&a=131939&p=name%20trackno%20artist%20ogmusic)

#### a / 专辑SMWID
  
指定获取的专辑的**SMWID**，**SMWID**可以用搜索专辑模式获取。若你很确定专辑的词条名，又不想浪费时间用搜索专辑模式获取**SMWID**，那你可以用[参数t](#t_/_专辑词条名)。参数a和参数t同时存在时，会优先用参数a寻找专辑，找不到再用参数t。
  
  
例子：
  
获取SMWID是131939的专辑（POP｜CULTURE 5）的alname、track和time
: [https://thwiki.cc/album.php?m=ga&f=alname+track+time&a=131939](https://thwiki.cc/album.php?m=ga&f=alname%20track%20time&a=131939)

#### t / 专辑词条名
  
指定获取的专辑的词条名，会运行必须的重定向，以确保能获取符合条件的专辑，在你很确定专辑的词条名，又不想浪费时间用搜索专辑模式获取**SMWID**的时候就很有用。若你想对专辑名模糊搜索，使用比重定向更高级的匹配方式，或想获取一个列表的专辑，那你可以用[参数a](#a_/_专辑SMWID)。参数a和参数t同时存在时，会优先用参数a寻找专辑，找不到再用参数t。
  
  
例子：
  
获取词条名是POP｜CULTURE 5的专辑的alname、track和time
: [https://thwiki.cc/album.php?m=ga&f=alname+track+time&t=POP%EF%BD%9CCULTURE+5](https://thwiki.cc/album.php?m=ga&f=alname%20track%20time&t=POP｜CULTURE%205)

#### s / 多值内容分隔符
  
定义所有多值内容的分隔符，定义后（不管是不是空）会把所有内容数组（如`["幽霊客船の時空を越えた旅", "キャプテン・ムラサ"]`）用该分隔符串起来。
  
  
例子：
  
获取SMWID是131939的专辑（POP｜CULTURE 5）的曲目的name和ogmusic，并把属性用“/”串起来
: [https://thwiki.cc/album.php?m=ga&a=131939&p=name+ogmusic&s=/](https://thwiki.cc/album.php?m=ga&a=131939&p=name%20ogmusic&s=/)

#### d / 结果格式
  
具体参考[d / 结果格式](#d_/_结果格式)。
  
  
例子：
  
获取SMWID是131939的专辑（POP｜CULTURE 5）的alname、event，其曲目的name、trackno、artist和ogmusic，以一般格式返回
: [https://thwiki.cc/album.php?m=ga&a=131939&f=alname+event&p=name+trackno+artist+ogmusic&d=nm](https://thwiki.cc/album.php?m=ga&a=131939&f=alname%20event&p=name%20trackno%20artist%20ogmusic&d=nm)
结果
: 

```
[[[ "alname", [ "POP｜CULTURE 5" ] ],[ "event", [ "Comic Market 89" ] ]],[[[ "id", 131943 ],[ "name", [ "POP|CULTURE 5" ] ],[ "trackno", [ 1 ] ],[ "artist", [ "Masayoshi Minoshima" ] ],[ "ogmusic", "" ]],[[ "id", 131944 ],[ "name", [ "Internal Ability" ] ],[ "trackno", [ 2 ] ],[ "artist", [ "nomico" ] ],[ "ogmusic", [ "霊人の休日" ] ]],[[ "id", 131945 ],[ "name", [ "Determine" ] ],[ "trackno", [ 3 ] ],[ "artist", [ "坂上なち" ] ],[ "ogmusic", "" ]],[[ "id", 250663 ],[ "name", [ "That Full Moon Over The Haunted Ship" ] ],[ "trackno", [ 4 ] ],[ "artist", [ "綾倉盟" ] ],[ "ogmusic", [ "幽霊客船の時空を越えた旅", "キャプテン・ムラサ" ]]],[[ "id", 250664 ],[ "name", [ "Sepia" ] ],[ "trackno", [ 5 ] ],[ "artist", [ "mican*" ] ],[ "ogmusic", [ "the Last Judgement" ] ]],[[ "id", 250665 ],[ "name", [ "Lonely Rabbit" ] ],[ "trackno", [ 6 ] ],[ "artist", [ "綾倉盟" ] ],[ "ogmusic", [ "兎は舞い降りた" ] ]],[[ "id", 250666 ],[ "name", [ "Not in the World" ] ],[ "trackno", [ 7 ] ],[ "artist", [ "綾倉盟" ] ],[ "ogmusic", [ "遠野の森" ] ]],[[ "id", 250667 ],[ "name", [ "Stardust" ] ],[ "trackno", [ 8 ] ],[ "artist", [ "ayame" ] ],[ "ogmusic", [ "感情の摩天楼 ～ Cosmic Mind" ] ]],[[ "id", 250668 ],[ "name", [ "Lapse(ZYTOKINE REMIX)" ] ],[ "trackno", [ 9 ] ],[ "artist", [ "坂上なち" ] ],[ "ogmusic", [ "Complete Darkness" ] ]],[[ "id", 250669 ],[ "name", [ "Visions(ARM REMIX)" ] ],[ "trackno", [ 10 ] ],[ "artist", [ "ayame" ] ],[ "ogmusic", "" ]]]]```

  
例子：
  
获取SMWID是131939的专辑（POP｜CULTURE 5）的alname、date，其曲目的name、time、arrange和ogmusic，用“/”做分隔符，以平行格式返回
: [https://thwiki.cc/album.php?m=ga&a=131939&f=alname+date&p=name+time+arrange+ogmusic&s=/&d=pa](https://thwiki.cc/album.php?m=ga&a=131939&f=alname%20date&p=name%20time%20arrange%20ogmusic&s=/&d=pa)
结果
: 

```
[{"alname": "POP｜CULTURE 5","date": "2015-12-30"},{"id": [131943,131944,131945,250663,250664,250665,250666,250667,250668,250669],"name": ["POP|CULTURE 5","Internal Ability","Determine","That Full Moon Over The Haunted Ship","Sepia","Lonely Rabbit","Not in the World","Stardust","Lapse(ZYTOKINE REMIX)","Visions(ARM REMIX)"],"time": ["84","271","297","283","286","313","284","295","305","315"],"arrange": ["","Masayoshi Minoshima","","かめりあ","Syrufit","Tracy","Masayoshi Minoshima","Masayoshi Minoshima","Masayoshi Minoshima/隣人","ARM"],"ogmusic": ["","霊人の休日","","幽霊客船の時空を越えた旅/キャプテン・ムラサ","the Last Judgement","兎は舞い降りた","遠野の森","感情の摩天楼 ～ Cosmic Mind","Complete Darkness",""]}]```

  
例子：
  
获取SMWID是131939的专辑（POP｜CULTURE 5）的alname、date，其曲目的name、time、arrange和ogmusic，以一般文本格式返回
: [https://thwiki.cc/album.php?m=ga&a=131939&f=alname+date&p=name+time+arrange+ogmusic&d=tn](https://thwiki.cc/album.php?m=ga&a=131939&f=alname%20date&p=name%20time%20arrange%20ogmusic&d=tn)
结果
: 

```
* alname POP｜CULTURE 5 date 2015-12-30 * id name time arrange ogmusic 131943 POP|CULTURE 5 84 131944 Internal Ability 271 Masayoshi Minoshima 霊人の休日 131945 Determine 297 250663 That Full Moon Over The Haunted Ship 283 かめりあ 幽霊客船の時空を越えた旅|キャプテン・ムラサ 250664 Sepia 286 Syrufit the Last Judgement 250665 Lonely Rabbit 313 Tracy 兎は舞い降りた 250666 Not in the World 284 Masayoshi Minoshima 遠野の森 250667 Stardust 295 Masayoshi Minoshima 感情の摩天楼 ～ Cosmic Mind 250668 Lapse(ZYTOKINE REMIX) 305 Masayoshi Minoshima|隣人 Complete Darkness 250669 Visions(ARM REMIX) 315 ARM * ```

  
例子：
  
获取SMWID是131939的专辑（POP｜CULTURE 5）的alname、date，其曲目的name、time、arrange和ogmusic，用“/”做分隔符，以平行文本格式返回
: [https://thwiki.cc/album.php?m=ga&a=131939&f=alname+date&p=name+time+arrange+ogmusic&s=/&d=tp](https://thwiki.cc/album.php?m=ga&a=131939&f=alname%20date&p=name%20time%20arrange%20ogmusic&s=/&d=tp)
结果
: 

```
* alname POP｜CULTURE 5 date 2015-12-30 * id 131943 131944 131945 250663 250664 250665 250666 250667 250668 250669 name POP|CULTURE 5 Internal Ability Determine That Full Moon Over The Haunted Ship Sepia Lonely Rabbit Not in the World Stardust Lapse(ZYTOKINE REMIX) Visions(ARM REMIX) time 84 271 297 283 286 313 284 295 305 315 arrange Masayoshi Minoshima かめりあ Syrufit Tracy Masayoshi Minoshima Masayoshi Minoshima Masayoshi Minoshima/隣人 ARM ogmusic 霊人の休日 幽霊客船の時空を越えた旅/キャプテン・ムラサ the Last Judgement 兎は舞い降りた 遠野の森 感情の摩天楼 ～ Cosmic Mind Complete Darkness * ```


### 获取曲目
获取曲目模式
: [https://thwiki.cc/album.php?m=gt](https://thwiki.cc/album.php?m=gt)
  
大致和[获取专辑](#获取专辑)差不多，这里只列出有差异的项。参数“a”、“t”、“f”均无效。
  

#### i / 曲目SMWID列表
  
指定获取的曲目的**SMWID**，**SMWID**可以用搜索曲目模式获取，可以用非数字的符号分隔多个**SMWID**，以获取多个曲目。
  
  
例子：
  
获取SMWID是131943、131944和131945的曲目的name、time、arrange和ogmusic
: [https://thwiki.cc/album.php?m=gt&p=name+time+arrange+ogmusic&i=131943,131944+131945](https://thwiki.cc/album.php?m=gt&p=name%20time%20arrange%20ogmusic&i=131943,131944,131945)

#### d / 结果格式
  
具体参考[d / 结果格式](#d_/_结果格式)。
  

## 实作范例
  
此API最主要的用途就是填写音频文件的ID3标签，此处给出一个基于[Mp3tag](http://www.mp3tag.de/en/)的插件，安装后可以在Mp3tag中从THBWiki获取专辑资料，自动填上ID3标签。能获取的属性包括专辑名、发售年份、制作方、发售展会、官网页面、光碟数、音轨号、曲目名、表演者和原曲。
  
  
安装此插件只需几个简单的步骤：
  

1. 首先要安装Mp3tag，谷歌百度一下都有教程
2. 下载此文件：[THBWiki.src](https://upload.thwiki.cc/upload/THBWiki.src)
3. 把文件放到以下路径：

: 
- Windows XP上是`C:\Documents and Settings\*username*\Application Data\Mp3tag\data\sources`
- Windows 7以上是`C:\Users\*username*\AppData\Roaming\Mp3tag\data\sources`
- 或可以直接在路径栏输入`%appdata%\Mp3tag\data\sources`然后按回车



1. 重新打开Mp3tag
2. 加入你需要处理的专辑文件夹，选取该专辑的所有曲目
3. 在顶部菜单里找到 标签数据源 -> THBWiki 并按下去，输入专辑名（或者会自动输入了），按下一步
4. 有多个专辑都匹配的话会出现一个选单，需要手动选取正确的那个，再按下一步，会出现用于最终调整的表单，适当 排序/上移/下移 右边的曲目列表让左右两边均一一匹配（最简单是匹配音轨号或把左边的列表滚动到最后比对时长），按确定
5. 完成


- <img alt="多个专辑都匹配的选单" src="https://upload.thwiki.cc/thumb/d/d3/Mp3tag%E6%8F%92%E4%BB%B6%E6%88%AA%E5%9B%BE1.png/120px-Mp3tag%E6%8F%92%E4%BB%B6%E6%88%AA%E5%9B%BE1.png" decoding="async" loading="lazy" width="120" height="55" srcset="https://upload.thwiki.cc/thumb/d/d3/Mp3tag%E6%8F%92%E4%BB%B6%E6%88%AA%E5%9B%BE1.png/180px-Mp3tag%E6%8F%92%E4%BB%B6%E6%88%AA%E5%9B%BE1.png 1.5x, https://upload.thwiki.cc/thumb/d/d3/Mp3tag%E6%8F%92%E4%BB%B6%E6%88%AA%E5%9B%BE1.png/240px-Mp3tag%E6%8F%92%E4%BB%B6%E6%88%AA%E5%9B%BE1.png 2x" data-file-width="895" data-file-height="412"> 多个专辑都匹配的选单
- <img alt="最终调整的表单" src="https://upload.thwiki.cc/thumb/0/00/Mp3tag%E6%8F%92%E4%BB%B6%E6%88%AA%E5%9B%BE2.png/120px-Mp3tag%E6%8F%92%E4%BB%B6%E6%88%AA%E5%9B%BE2.png" decoding="async" loading="lazy" width="120" height="54" srcset="https://upload.thwiki.cc/thumb/0/00/Mp3tag%E6%8F%92%E4%BB%B6%E6%88%AA%E5%9B%BE2.png/180px-Mp3tag%E6%8F%92%E4%BB%B6%E6%88%AA%E5%9B%BE2.png 1.5x, https://upload.thwiki.cc/thumb/0/00/Mp3tag%E6%8F%92%E4%BB%B6%E6%88%AA%E5%9B%BE2.png/240px-Mp3tag%E6%8F%92%E4%BB%B6%E6%88%AA%E5%9B%BE2.png 2x" data-file-width="1360" data-file-height="613"> 最终调整的表单


---

此文档由 [THBWiki-Markdown-Builder](https://github.com/Delsin-Yu/THBWiki-Markdown-Builder) 构建。

文档中的所有内容除特殊注明外，均在 [**知识共享(Creative Commons) 署名-非商业性使用-相同方式共享 3.0 协议**](https://creativecommons.org/licenses/by-sa/3.0/deed.zh-hans) 下提供，附加条款亦可能应用。

引用类型与其他类型作品版权归原作者所有，如有作者授权则遵照授权协议使用。

详细请查阅 [THBWiki：免责声明](https://thbwiki.cc/THBWiki:%E5%85%8D%E8%B4%A3%E5%A3%B0%E6%98%8E)。

