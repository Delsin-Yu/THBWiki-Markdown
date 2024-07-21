# 游戏攻略/STG常用工具/VsyncPatch

<!-- source html: G:\repos\THBWiki-Markdown-Builder\THBWikiMarkdown\Temp\main\3\3c\ns0%3A%E6%B8%B8%E6%88%8F%E6%94%BB%E7%95%A5%2FSTG%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7%2FVsyncPatch.html -->



## 目录

- [1 简介](#简介)
- [2 基本使用方法](#基本使用方法)

  - [2.1 配合thcrap使用](#配合thcrap使用)



- [3 配置文件介绍](#配置文件介绍)
- [4 实用性功能](#实用性功能)

  - [4.1 游戏窗口设置](#游戏窗口设置)
  - [4.2 replay快进](#replay快进)
  - [4.3 replay慢放](#replay慢放)
  - [4.4 游戏加速](#游戏加速)



- [5 修复性功能](#修复性功能)

  - [5.1 风神录弑神炮](#风神录弑神炮)



- [6 注释](#注释)




## 简介
  
VsyncPatch（直译：垂直同步补丁），一般简称为  **VPatch**  或  **VP** 。下文统一简称为VP。
  
  
功能强大的辅助软件，一般用于减少射击作游戏的逻辑延迟，但也具有很多其他实用功能。
  
  
支持红魔乡到绀珠传的所有射击作游戏（包括 **小数点射击作** 及 **黄昏酒场** ），以及东方弹幕风的0.12m版本（需先进行UPX展开）。
  
  
请尽量使用日文原版游戏，或类似于启动器的汉化版游戏（如喵玉汉化和thcrap），否则会出现难以预料的错误。
  
  
附带文档：
  

- [vpatch_instructions](./游戏攻略-STG常用工具-VsyncPatch-vpatch_instructions.md)
- [vpatch_readme](./游戏攻略-STG常用工具-VsyncPatch-vpatch_readme.md)【后面文档中的内容基于此文档（即文中「rev6版本的readme」）】（2008/04/01 rev1 至 2009/09/25 rev6）
- [vpatch_readme_test](./游戏攻略-STG常用工具-VsyncPatch-vpatch_readme_test.md)（2010/05/20 rev7 test3）
- [vpatch_readme_th128](./游戏攻略-STG常用工具-VsyncPatch-vpatch_readme_th128.md)（2010/09/06 rev th128-1）
- [vpatch_readme_th13](./游戏攻略-STG常用工具-VsyncPatch-vpatch_readme_th13.md)（2011/10/31 rev th13-1）
- [vpatch_readme_th15](./游戏攻略-STG常用工具-VsyncPatch-vpatch_readme_th15.md)（2015/11/28）

## 基本使用方法
  
将  **vpatch.exe** 、 **vpatch.ini** ，以及对应游戏的 **thxx.dll**  共 **3个文件** 放入游戏文件夹。
  
  
thxx.dll中的xx为游戏代号，详见下表：
  


<table>

<tbody><tr>
<th>游戏代号对照表
</th></tr>
<tr>
<td><table class="wikitable">
  <tbody><tr>
    <th>游戏代号</th>
    <th>游戏名</th>
    <th>dll文件名</th>
  </tr>
  <tr>
    <td>06</td>
    <td>红魔乡</td>
    <td>vpatch_th06.dll</td>
  </tr>
  <tr>
    <td>07</td>
    <td>妖妖梦</td>
    <td>vpatch_th07.dll</td>
  </tr>
  <tr>
    <td>08</td>
    <td>永夜抄</td>
    <td>vpatch_th08.dll</td>
  </tr>
  <tr>
    <td>09</td>
    <td>花映塚</td>
    <td>vpatch_th09.dll</td>
  </tr>
  <tr>
    <td>10</td>
    <td>风神录</td>
    <td>vpatch_th10.dll</td>
  </tr>
  <tr>
    <td>alcostg</td>
    <td>黄昏酒场</td>
    <td>vpatch_alcostg.dll</td>
  </tr>
  <tr>
    <td>11</td>
    <td>地灵殿</td>
    <td>vpatch_th11.dll</td>
  </tr>
  <tr>
    <td>12</td>
    <td>星莲船</td>
    <td>vpatch_th12.dll</td>
  </tr>
  <tr>
    <td>13</td>
    <td>神灵庙</td>
    <td>vpatch_th13.dll</td>
  </tr>
  <tr>
    <td>14</td>
    <td>辉针城<sup id="cite_ref-1" class="reference"><a href="#cite_note-1">1</a></sup></td>
    <td>vpatch_th14.dll</td>
  </tr>
  <tr>
    <td>15</td>
    <td>绀珠传</td>
    <td>vpatch_th15.dll</td>
  </tr>
  <tr>
    <td>095</td>
    <td>文花帖</td>
    <td>vpatch_th095.dll</td>
  </tr>
  <tr>
    <td>125</td>
    <td>文花帖DS</td>
    <td>vpatch_th125.dll</td>
  </tr>
  <tr>
    <td>128</td>
    <td>妖精大战争</td>
    <td>vpatch_th128.dll</td>
  </tr>
  <tr>
    <td>dnh</td>
    <td>弹幕风</td>
    <td>vpatch_th_dnh.dll</td>
  </tr>
</tbody></table>
</td></tr></tbody></table>


  
调整好vpatch.ini后，运行vpatch.exe即可。
  
  
VP对于游戏版本也有要求，一般要求为游戏的最新版本，详见下表：
  


<table>

<tbody><tr>
<th>游戏版本对照表
</th></tr>
<tr>
<td><table class="wikitable">
  <tbody><tr>
    <th>游戏名</th>
    <th>支持的版本</th>
  </tr>
  <tr>
    <td>红魔乡</td>
    <td>1.02h</td>
  </tr>
  <tr>
    <td>妖妖梦</td>
    <td>1.00b</td>
  </tr>
  <tr>
    <td>永夜抄</td>
    <td>1.00d</td>
  </tr>
  <tr>
    <td>花映塚</td>
    <td>1.50a</td>
  </tr>
  <tr>
    <td>风神录</td>
    <td>1.00a</td>
  </tr>
  <tr>
    <td>黄昏酒场</td>
    <td>1.00a (web配布版)</td>
  </tr>
  <tr>
    <td>地灵殿</td>
    <td>1.00a</td>
  </tr>
  <tr>
    <td>星莲船</td>
    <td>1.00b</td>
  </tr>
  <tr>
    <td>神灵庙</td>
    <td>1.00c</td>
  </tr>
  <tr>
    <td>辉针城</td>
    <td>1.00b<sup id="cite_ref-2" class="reference"><a href="#cite_note-2">2</a></sup></td>
  </tr>
  <tr>
    <td>绀珠传</td>
    <td>1.00b</td>
  </tr>
  <tr>
    <td>文花帖</td>
    <td>1.02a</td>
  </tr>
  <tr>
    <td>文花帖DS</td>
    <td>ver1.00a</td>
  </tr>
  <tr>
    <td>妖精大战争</td>
    <td>ver1.00a</td>
  </tr>
  <tr>
    <td>弹幕风</td>
    <td>v0.12m<sup id="cite_ref-3" class="reference"><a href="#cite_note-3">3</a></sup></td>
  </tr>
</tbody></table>
</td></tr></tbody></table>


### 配合thcrap使用
## 配置文件介绍
  
VP通过ini配置文件来管理配置。
  
  
ini文件是Initialization file的缩写，即为初始化文件，是Windows系统配置文件所采用的存储格式。
  
  
ini文件的格式如下：
  

```
[这是一个节]
配置项（键） = 值
```

  
一对键和值的组合称为参数，所有的参数以节为单位组织在一起。
  
  
在某个节的声明之后，直到一个新的节的声明为止，所有的参数都属于该节。节没有显式的结束标识符。
  
  
<big>本文中所有的参数前都会提示该参数归属的节，但 **一个节只需要声明一次，同属于这个节的参数只要加在后面即可。** </big>
  
  
正确示例：
  

```
[Section1]
Setting1 = 1
Setting2 = 1
[Section2]
Setting3 = 1
```

  
错误示例：
  

```
[Section1]
Setting1 = 1
[Section1]
Setting2 = 1
[Section2]
Setting3 = 1
```

## 实用性功能
### 游戏窗口设置
```
[Window]
enabled = 1    ;是否使以下配置项生效。0为禁用，0以外为启用
X = 0    ;画面顶点横坐标，单位像素
Y = 0    ;画面顶点纵坐标，单位像素
Width = 640    ;画面宽度，单位像素
Height = 480    ;画面高度，单位像素
TitleBar = 1    ;是否使用标题栏，0为不使用，0以外为使用
AlwaysOnTop = 0    ;是否使用窗口置顶，0为不使用，0以外为使用
```

  
注意事项：
  

- 请务必保持  **enabled**  这一配置项位于最上方（ **[Window]**  的下方），否则可能无法使位于该项上方的配置项生效。
- 画面顶点指的是游戏画面左上角的点（也就是不包括标题栏的意思）
- 如果不使用标题栏，你可以避免系统底部任务栏将游戏遮挡住的情况，但你将无法通过鼠标拖动来改变窗口位置，也就是固定死了。

### replay快进
  
VP为 **红妖永花** 四作添加了rep快进的功能。
  

```
[Option]
ReplaySkipFPS = 240    ;快进时的帧率，单位fps（帧每秒）
```

  
使用方法：长按Ctrl键（准确来说是跳过键）
  
  
注意事项：
  

- 默认值为240。如无需修改可以无视此条。
- 如果性能不够则可能达不到目标帧率
- 妖妖梦快进时可能导致最终分数有少许偏差。

### replay慢放
  
VP为所有作品添加了rep慢放功能。
  

```
[Option]
ReplaySlowFPS = 30    ;慢放时的帧率，单位fps（帧每秒）
```

  
使用方法：长按shift键（准确来说是低速键）
  
  
注意事项：默认值为30。如无需修改可以无视此条。
  

### 游戏加速
  
VP可以通过设置运行帧率来使游戏加速运行。
  

```
[Option]
GameFPS = 60    ;游戏运行帧率，单位fps（帧每秒）。数值大于等于60才会生效。
```

- 例如设置为90则相当于游戏整体加速至1.5倍。

## 修复性功能
### 风神录弑神炮
  
由于ZUN代码错误，风神录贯通机体3power右侧主炮在高速下的火力极高，VP可以使其变为正常火力。
  

```
[Option]
BugFixTh10Power3 = 0    ;0为不修复，1为修复。
```

- 默认值为0（不修复）
- 使用修复功能时保存的贯通机体replay在原版中无法正常播放。


[^cite_note-1]: 疑似第三方添加支持。





---

此文档由 [THBWiki-Markdown-Builder](https://github.com/Delsin-Yu/THBWiki-Markdown-Builder) 构建。

文档中的所有内容除特殊注明外，均在 [**知识共享(Creative Commons) 署名-非商业性使用-相同方式共享 3.0 协议**](https://creativecommons.org/licenses/by-sa/3.0/deed.zh-hans) 下提供，附加条款亦可能应用。

引用类型与其他类型作品版权归原作者所有，如有作者授权则遵照授权协议使用。

详细请查阅 [THBWiki：免责声明](https://thbwiki.cc/THBWiki:%E5%85%8D%E8%B4%A3%E5%A3%B0%E6%98%8E)。

