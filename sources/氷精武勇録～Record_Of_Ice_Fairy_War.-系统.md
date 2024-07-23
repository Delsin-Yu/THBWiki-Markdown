# 氷精武勇録～Record_Of_Ice_Fairy_War./系统

<!-- source html: G:\repos\THBWiki-Markdown-Builder\THBWikiMarkdown\Temp\main\6\69\ns0%3A%E6%B0%B7%E7%B2%BE%E6%AD%A6%E5%8B%87%E9%8C%B2%EF%BD%9ERecord_Of_Ice_Fairy_War%2E%2F%E7%B3%BB%E7%BB%9F.html -->

TEAM:SOCIALLY_UNFIT


## 目录

- [1 默认键位](#默认键位)

  - [1.1 常规](#常规)
  - [1.2 录像播放](#录像播放)



- [2 系统说明](#系统说明)

  - [2.1 基本事项](#基本事项)
  - [2.2 与本家妖精大战争的差别](#与本家妖精大战争的差别)



- [3 其它外部系统](#其它外部系统)

  - [3.1 自定义BGM](#自定义BGM)
  - [3.2 Twitter关联](#Twitter关联)
  - [3.3 关于WAS（Windows音频会话）API](#关于WAS（Windows音频会话）API)
  - [3.4 Replay图像化](#Replay图像化)
  - [3.5 符卡练习](#符卡练习)



- [4 词条导航](#词条导航)





## 默认键位
  
键位在option/key config选项中可以随意更改。
  


### 常规
- 方向键：移动自机或选单。
- SHOT（Z）：射击/确定。按住为蓄力，松开时会基于当前的蓄力值发动技能。
- BOMB（X）：符卡（完美冻结）/取消。
- SLOW（左shift）：低速。蓄力时强制低速。
- RAPID（C）：连续射击，按住也不会发动蓄力。
- SKIP（S）：加速对话。
- SNAP（P）：截图
- PAUSE（ESC）：暂停。暂停界面按R可以快速重新开始。


### 录像播放
- Z：按住时会变速播放replay，按住鼠标右键也可以。
- X：调节变速播放幅度。
- S：跳转到进度条指定位置，使用←→方向键或鼠标左键可以调节进度条位置。shift+方向键可以更大幅度移动进度条。
- C：切换为逐帧播放模式，使用←→方向键或鼠标滚轮可以逐帧进退。
- P：截图
- Ctrl：切换进度条相对时间（单关/全关）。
- R：显示子弹与自机判定
- D：显示/隐藏replay信息。
- ESC：暂停。
- 鼠标左键：启用放大镜（可放大一部分屏幕）。


## 系统说明

### 基本事项
  
使用琪露诺自机时，与[妖精大战争的系统](./游戏攻略-妖精大战争-系统.md)几乎相同，使用冰冻来消除弹幕、提升火力与获得资源。
  
  
使用宾卡自机时，蓄力会变为在当前位置释放反射护盾，会将所有的常规子弹反射回去（自动索敌，火弹和激光无法反射）。bomb则会变为近距离的高伤爆破弹。  

由于获得干劲（残机）的数值与造成的伤害有关，与琪露诺冰冻的单次高伤相比，反射弹攻击杂鱼获得的干劲会少一些。
  


### 与本家[妖精大战争](./妖精大战争.md)的差别
- 火弹在没有冰壁时会高光，在有冰壁时会加上黑色边框。因此在使用冰冻时火弹会闪一下，容易导致视觉干扰。
- 使用完美冻结（bomb）时不会减速、但没有擦弹判定。（本家是强制低速、但可以擦弹）
- 常规火弹的判定比本家略大。


## 其它外部系统

### 自定义BGM
  
这个游戏支持自定义游戏里播放的BGM。
  
  
在UseBGM里放入你要用的BGM文件，然后打开BGM_DATA.txt按提示填写循环节，之后在游戏设置里把SOUNDTYPE切换成USE就能在游戏里听你自己设置的曲子了。
  


### Twitter关联
  
这个游戏搭载了Twitter分享功能，可以在你发了的时候选择用你的推特账号发一条推，如果你有特别的上网技巧而且有推特账号的话可以绑一下推特账号。
  
  
没有或者根本打不开推特的话可以在config.exe里把Twitter功能关掉让它不尝试连接，这样游戏里的分享功能就没用了，可以避免手因为滑点到了分享键因为网络原因卡死的尴尬。
  
  
由于马斯克的乱搞，于2023年，本游戏的X（原Twitter）Api已经失效。现在无论如何都没法使用了。
  


### 关于WAS（Windows音频会话）API
  
如果你发现游戏声音能从你插进来的耳机或者音箱播放，但是系统的其他声音只能从其它扬声器放出来（比如你的笔记本电脑自带的喇叭）
  
  
请打开config.exe，将WAS API改为“共享模式”即可
  
  
至于具体的事情就不要管那么多啦，说了你也不一定懂（
  


### Replay图像化
  
在Ver1.02a版本中支持将Replay输出为一张图片来分享。只需要在Replay界面选择Replay，按下C键并确定后，就会把当前Replay输出为一张图片。
  
  
图片可以在修改为规范的文件名后重新被程序读取，但如果图片被压缩/修改过导致画质被改变的话，图片的Replay功能就会失效（也就是废了）。
  


### 符卡练习

- <font color="Red"> **剧透提示:  *以下内容包含详细故事情节，请自行决定是否继续阅读* ** </font>

在完成了27~35号隐藏成就之后，就会解锁37号的「Congratulations」成就。
  
但这个界面还隐藏了一个线索：左上角有一串秘密符号，实际上代表了方向：上右下左下上。
  
  
将这个方向序列用方向键输入进去，就会在游戏目录收到来自制作者Tir的信息，这条信息同时包含了一条最终的线索：反转输入密码。
  
  
将反转后的密码（下左上右上下）输入一遍就能解锁这个游戏最深秘的功能——————符卡练习！！！
  
  
在解锁这个功能后，播放任意replay时都可以从中途改为手动操作，与replay跳转进度功能一起使用相当于提供了练习功能。但这么基础的功能要达成这么复杂的条件才能解锁，你妹啊！
  
  
※如果你不小心错过了Congratulations界面可以从37号成就回看
  

※此外，在replay中使用“从这里开始自己操作”功能后，所有的成绩与符卡记录都不会计入分数版，关闭游戏重开即可恢复正常。


## 词条导航
  
  

<table><tbody><tr><td><table cellspacing="0" class="nowraplinks mw-collapsible mw-collapsed" style="width:100%;;;"><tbody><tr><th style=";" colspan="3" class="navbox-title"><div class="navbar"><div class="noprint plainlinksneverexpand" style="background-color:transparent; padding:0; font-weight:normal; font-size:80%; white-space:nowrap;"><a href="./氷精武勇録～Record_Of_Ice_Fairy_War.-导航.md" title="氷精武勇録～Record Of Ice Fairy War./导航"><span style=";;border:none;" title="查看这个模板">查</span></a>&#160;<span style="font-size:80%;">•</span>&#160;<a href="/index.php?title=%E6%B0%B7%E7%B2%BE%E6%AD%A6%E5%8B%87%E9%8C%B2%EF%BD%9ERecord_Of_Ice_Fairy_War./%E5%AF%BC%E8%88%AA&amp;action=edit"><span style=";;border:none;" title="您可以编辑这个模板。请在储存变更之前先预览">编</span></a></div></div><span><a href="./氷精武勇録～Record_Of_Ice_Fairy_War..md" title="氷精武勇録～Record Of Ice Fairy War.">冰精武勇录</a></span></th></tr><tr><td></td></tr><tr><td class="navbox-group" style=";;">角色</td><td style=";;" class="navbox-list navbox-odd"><div></div><table cellspacing="0" class="nowraplinks navbox-subgroup" style="width:100%;;;;"><tbody><tr><td class="navbox-group" style=";;"><div>自机</div></td><td style=";;" class="navbox-list navbox-odd"><div><a href="./琪露诺（武勇录）.md" title="琪露诺（武勇录）">琪露诺</a> &#8226; <a href="./宾卡瓦兹.md" title="宾卡瓦兹">宾卡瓦兹</a></div></td></tr><tr><td></td></tr><tr><td class="navbox-group" style=";;"><div>BOSS</div></td><td style=";;" class="navbox-list navbox-even"><div><a href="./莉莉霍瓦特（武勇录）.md" title="莉莉霍瓦特（武勇录）">莉莉霍瓦特</a> &#8226; <a href="./爱塔妮缇拉尔瓦（武勇录）.md" title="爱塔妮缇拉尔瓦（武勇录）">爱塔妮缇拉尔瓦</a> &#8226; <a href="./桑尼米尔克（武勇录）.md" title="桑尼米尔克（武勇录）">桑尼米尔克</a> &#8226; <a href="./露娜切露德（武勇录）.md" title="露娜切露德（武勇录）">露娜切露德</a> &#8226; <a href="./斯塔萨菲雅（武勇录）.md" title="斯塔萨菲雅（武勇录）">斯塔萨菲雅</a> &#8226; <a href="./克劳恩皮丝（武勇录）.md" title="克劳恩皮丝（武勇录）">克劳恩皮丝</a> &#8226; <a href="./大妖精（武勇录）.md" title="大妖精（武勇录）">大妖精</a> &#8226; <a href="./宾卡瓦兹.md" title="宾卡瓦兹">宾卡瓦兹</a> &#8226; <a href="./雾雨魔理沙（武勇录）.md" title="雾雨魔理沙（武勇录）">雾雨魔理沙</a> &#8226; <a href="./博丽灵梦（武勇录）.md" title="博丽灵梦（武勇录）">博丽灵梦</a></div></td></tr><tr><td></td></tr><tr><td class="navbox-group" style=";;"><div>挑战BOSS</div></td><td style=";;" class="navbox-list navbox-odd"><div><a href="./玛莉雪佛德.md" title="玛莉雪佛德">玛莉雪佛德</a> &#8226; <a href="./法布丽蒂丝.md" title="法布丽蒂丝">法布丽蒂丝</a> &#8226; <a href="./伊芙妮娅.md" title="伊芙妮娅">伊芙妮娅</a> &#8226; <a href="./丝诺柯狄亚.md" title="丝诺柯狄亚">丝诺柯狄亚</a> &#8226; <a href="./艾尔芬敏特.md" title="艾尔芬敏特">艾尔芬敏特</a></div></td></tr></tbody></table><div></div></td><td class="navbox-image" style="" rowspan="9"><a href="./文件-氷精武勇録～Record_Of_Ice_Fairy_War.封面.png.md" class="image"><img alt="氷精武勇録～Record Of Ice Fairy War.封面.png" src="https://upload.thwiki.cc/thumb/9/9f/%E6%B0%B7%E7%B2%BE%E6%AD%A6%E5%8B%87%E9%8C%B2%EF%BD%9ERecord_Of_Ice_Fairy_War.%E5%B0%81%E9%9D%A2.png/160px-%E6%B0%B7%E7%B2%BE%E6%AD%A6%E5%8B%87%E9%8C%B2%EF%BD%9ERecord_Of_Ice_Fairy_War.%E5%B0%81%E9%9D%A2.png" decoding="async" loading="lazy" width="160" height="120" srcset="https://upload.thwiki.cc/thumb/9/9f/%E6%B0%B7%E7%B2%BE%E6%AD%A6%E5%8B%87%E9%8C%B2%EF%BD%9ERecord_Of_Ice_Fairy_War.%E5%B0%81%E9%9D%A2.png/240px-%E6%B0%B7%E7%B2%BE%E6%AD%A6%E5%8B%87%E9%8C%B2%EF%BD%9ERecord_Of_Ice_Fairy_War.%E5%B0%81%E9%9D%A2.png 1.5x, https://upload.thwiki.cc/thumb/9/9f/%E6%B0%B7%E7%B2%BE%E6%AD%A6%E5%8B%87%E9%8C%B2%EF%BD%9ERecord_Of_Ice_Fairy_War.%E5%B0%81%E9%9D%A2.png/320px-%E6%B0%B7%E7%B2%BE%E6%AD%A6%E5%8B%87%E9%8C%B2%EF%BD%9ERecord_Of_Ice_Fairy_War.%E5%B0%81%E9%9D%A2.png 2x" data-file-width="640" data-file-height="480"></a></td></tr><tr><td></td></tr><tr><td class="navbox-group" style=";;">剧情</td><td style=";;" class="navbox-list navbox-even"><div></div><table cellspacing="0" class="nowraplinks navbox-subgroup" style="width:100%;;;;"><tbody><tr><td class="navbox-group" style=";;"><div>剧情文本</div></td><td style=";;" class="navbox-list navbox-odd"><div><a href="./氷精武勇録～Record_Of_Ice_Fairy_War.-故事背景.md" title="氷精武勇録～Record Of Ice Fairy War./故事背景">Misson1故事背景</a> &#8226; <a href="./氷精武勇録～Record_Of_Ice_Fairy_War.-Misson2故事背景.md" title="氷精武勇録～Record Of Ice Fairy War./Misson2故事背景">Misson2故事背景</a> &#8226; <a href="./氷精武勇録～Record_Of_Ice_Fairy_War.-Misson1宾卡瓦兹线故事背景.md" title="氷精武勇録～Record Of Ice Fairy War./Misson1宾卡瓦兹线故事背景">Misson1宾卡瓦兹线故事背景</a> &#8226; <a href="./氷精武勇録～Record_Of_Ice_Fairy_War.-Misson3故事背景.md" title="氷精武勇録～Record Of Ice Fairy War./Misson3故事背景">Misson3故事背景</a></div></td></tr><tr><td></td></tr><tr><td class="navbox-group" style=";;"><div>游戏对话&amp;结局</div></td><td style=";;" class="navbox-list navbox-even"><div><a href="./氷精武勇録～Record_Of_Ice_Fairy_War.-琪露诺.md" title="氷精武勇録～Record Of Ice Fairy War./琪露诺">琪露诺</a> &#8226; <a href="./氷精武勇録～Record_Of_Ice_Fairy_War.-宾卡瓦兹.md" title="氷精武勇録～Record Of Ice Fairy War./宾卡瓦兹">宾卡瓦兹</a></div></td></tr><tr><td></td></tr><tr><td class="navbox-group" style=";;"><div>Ex游戏对话</div></td><td style=";;" class="navbox-list navbox-odd"><div><a href="./氷精武勇録～Record_Of_Ice_Fairy_War.-琪露诺_ExStory.md" title="氷精武勇録～Record Of Ice Fairy War./琪露诺 ExStory">琪露诺</a></div></td></tr></tbody></table><div></div></td></tr><tr><td></td></tr><tr><td class="navbox-group" style=";;">场景</td><td style=";;" class="navbox-list navbox-odd"><div><a href="./春之小径.md" title="春之小径">春之草原</a> &#8226; <a href="./博丽神社.md" title="博丽神社">博丽神社</a> &#8226; 幻想乡上空湍流 &#8226; <a href="./雾之湖.md" title="雾之湖">雾之湖</a></div></td></tr><tr><td></td></tr><tr><td class="navbox-group" style=";;"><a href="/%E6%B0%B7%E7%B2%BE%E6%AD%A6%E5%8B%87%E9%8C%B2%EF%BD%9ERecord_Of_Ice_Fairy_War.#其他资料" title="氷精武勇録～Record Of Ice Fairy War.">其他资料</a></td><td style=";;" class="navbox-list navbox-even"><div></div><table cellspacing="0" class="nowraplinks navbox-subgroup" style="width:100%;;;;"><tbody><tr><td class="navbox-group" style=";;"><div>音乐</div></td><td style=";;" class="navbox-list navbox-odd"><div><a href="./氷精武勇録～Record_Of_Ice_Fairy_War.-Music.md" title="氷精武勇録～Record Of Ice Fairy War./Music">Music Room</a></div></td></tr><tr><td></td></tr><tr><td class="navbox-group" style=";;"><div>其他</div></td><td style=";;" class="navbox-list navbox-even"><div><a class="mw-selflink selflink">机体特性与系统说明</a> &#8226; <a href="./氷精武勇録～Record_Of_Ice_Fairy_War.-成就.md" title="氷精武勇録～Record Of Ice Fairy War./成就">成就系统</a> &#8226; <a href="/index.php?title=%E6%B0%B7%E7%B2%BE%E6%AD%A6%E5%8B%87%E9%8C%B2%EF%BD%9ERecord_Of_Ice_Fairy_War./%E5%85%B6%E4%BB%96&amp;action=edit&amp;redlink=1" class="new" title="氷精武勇録～Record Of Ice Fairy War./其他（页面不存在）">其他相关资料</a> &#8226; <a href="./氷精武勇録～Record_Of_Ice_Fairy_War.-符卡.md" title="氷精武勇録～Record Of Ice Fairy War./符卡">符卡列表</a></div></td></tr></tbody></table><div></div></td></tr><tr><td></td></tr><tr><td class="navbox-group" style=";;"><a href="/%E6%B0%B7%E7%B2%BE%E6%AD%A6%E5%8B%87%E9%8C%B2%EF%BD%9ERecord_Of_Ice_Fairy_War.#附带文档" title="氷精武勇録～Record Of Ice Fairy War.">附带文档</a></td><td style=";;" class="navbox-list navbox-odd"><div><a href="./氷精武勇録～Record_Of_Ice_Fairy_War.-游戏内Manual.md" title="氷精武勇録～Record Of Ice Fairy War./游戏内Manual">Manual</a> &#8226; <a href="./氷精武勇録～Record_Of_Ice_Fairy_War.-Readme.md" title="氷精武勇録～Record Of Ice Fairy War./Readme">Readme</a> &#8226; <a href="./氷精武勇録～Record_Of_Ice_Fairy_War.-Omake.md" title="氷精武勇録～Record Of Ice Fairy War./Omake">Omake</a> &#8226; <a href="/index.php?title=%E6%B0%B7%E7%B2%BE%E6%AD%A6%E5%8B%87%E9%8C%B2%EF%BD%9ERecord_Of_Ice_Fairy_War./%E7%B3%BB%E7%BB%9F%E8%A1%A5%E8%B6%B3&amp;action=edit&amp;redlink=1" class="new" title="氷精武勇録～Record Of Ice Fairy War./系统补足（页面不存在）">系统补足</a></div></td></tr></tbody></table></td></tr></tbody></table>







---

此文档由 [THBWiki-Markdown-Builder](https://github.com/Delsin-Yu/THBWiki-Markdown-Builder) 构建。

文档中的所有内容除特殊注明外，均在 [**知识共享(Creative Commons) 署名-非商业性使用-相同方式共享 3.0 协议**](https://creativecommons.org/licenses/by-sa/3.0/deed.zh-hans) 下提供，附加条款亦可能应用。

引用类型与其他类型作品版权归原作者所有，如有作者授权则遵照授权协议使用。

详细请查阅 [THBWiki：免责声明](https://thbwiki.cc/THBWiki:%E5%85%8D%E8%B4%A3%E5%A3%B0%E6%98%8E)。

