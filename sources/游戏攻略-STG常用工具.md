# 游戏攻略/STG常用工具

<!-- source html: G:\repos\THBWiki-Markdown-Builder\THBWikiMarkdown\Temp\main\1\18\ns0%3A%E6%B8%B8%E6%88%8F%E6%94%BB%E7%95%A5%2FSTG%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7.html -->

游戏攻略

  
本页面整理了一些辅助练习的工具与游戏补丁，附带可能的外链下载地址，供参考使用。
  
  
注意，这些工具和补丁均非官方出品，且通常不作 **任何** 保证。使用前请备份重要文件（例如玩家数据文件 `
score.dat`
 等）。
  
  
大部分工具并没有实时更新至支持最新作品，也需要注意。
  


## 目录

- [1 常用工具](#常用工具)

  - [1.1 旧五作（TH01-TH05）模拟器](#旧五作（TH01-TH05）模拟器)



- [2 练习器与修改器](#练习器与修改器)
- [3 信息查看工具](#信息查看工具)
- [4 游戏补丁](#游戏补丁)
- [5 改版游戏](#改版游戏)
- [6 联机对战工具](#联机对战工具)
- [7 游戏文件相关工具](#游戏文件相关工具)

  - [7.1 游戏文件解包工具](#游戏文件解包工具)



- [8 相关链接](#相关链接)
- [9 注释](#注释)





## 常用工具
  
一些较常用到但又难以归类的工具，包括全开档、通用汉化工具 thcrap、键位修改工具 THKMC 和运行旧作所需的 PC-98 模拟器。
  
  
其他的常用工具有[通用练习器 thprac](#练习器与修改器)、[VsyncPatch 补丁和 d3d8to9](#游戏补丁)，都已分类至各自类别之下。
  
  
其中，thcrap 和 thprac 都可用作正作游戏启动器，和本页尚未囊括的 [Touhou Launcher](https://a-digital-project.github.io/launcher) 类似。
  

全开档（提取码：7q45）
: 更新至TH17，包括开启EX关，以及各单关练习模式的存档。替换掉对应作品的 `
score.dat`
 即可生效。
: 使用地灵殿某全开档可能会导致机签后带 "Ai" 标识，解决办法详见下方 th11aifix。
: 此外，ZUN在程序中内置了开启全部关卡的方式（后门），详见[全开档秘籍](./全开档秘籍.md)。
thcrap - 东方社群驱动的自动补丁器
: [Github](https://github.com/thpatch/thcrap/releases)，全名为Touhou Community Reliant Automatic Patcher。注意与 [thprac](#练习器与修改器) 区分开。
: 主要用途是通过 DLL 注入和 [Touhou Patch Center](https://www.thpatch.net/wiki/Touhou_Patch_Center:Main_page/zh) 的在线本地化资源，将东方原作本地化为各种语言，并自动更新。  
 理论上也可以做到修改素材、魔改游戏等功能。具体参见其[关于页面](https://www.thpatch.net/wiki/Touhou_Patch_Center:About/zh-hans)。
: 优点是无需直接修改游戏文件，可以规避其他汉化方法会造成的问题，且具有整合游戏、联网更新、支持Steam版等优势，还兼容VP等补丁。  
 缺点可能是每次启动时都要检查更新（可关闭）。
: 简易使用指南：  
 启动thcrap_configure.exe，点击Next即会进入补丁列表界面，可以选择相应补丁，之后选择对应的原作游戏（可以选择文件夹并扫描）并安装。
: 关于更详细的说明文档以及thcrap的其他拓展功能，可参考以下说明、[本文](https://www.zybuluo.com/yanstime/note/1537159)以及其中的教程书。


<table>

<tbody><tr>
<th>此处以<b>安装汉化补丁</b>为例来说明thcrap的基本用法。
</th></tr>
<tr>
<td>将下载好的thcrap解压缩到合适的目录下（因为补丁文件会保存在thcrap里，不建议随便往哪一丢）并启动configure.exe。<br>点击Next后，会出现一串补丁列表，找到<b>lang_zh-hans</b>（简体中文的语言补丁），在输入框中输入对应的<b>补丁序号数字</b>并点击next。<br>之后，会出现次级补丁列表，如果不需要其他的补丁（或者完全看不懂英文）继续点next确认即可。<br>选择对应游戏所在的文件夹并确认（比如多个游戏放在同一个文件夹下，选择最上级的文件夹即可）。<br>程序会列出扫描到的所有原作游戏的启动器，依次输入对应的序号来确认“需要应用汉化补丁的游戏程序”。<br>程序会询问（Create shotcuts?）是否在thcrap文件夹内建立指向对应作品的快捷方式，确认即可。<br>最后，程序会生成各汉化游戏的启动器（以及本地化后的设置程序custom.exe）。
</td></tr></tbody></table>


THKMC - 东方STG专用键盘映射修改工具（提取码：wjmf）
: 作者：Wz520 (未找到链接)，[原帖地址](https://tieba.baidu.com/p/5849197015)，[喵玉发布帖](http://bbs.nyasama.com/forum.php?mod=viewthread&amp;tid=78904&amp;extra=page=1)，[GitHub](https://github.com/wz520/thkmc)。
: 一个为东方STG量身定制的键盘映射修改工具。通过直接修改东方STG游戏主程序文件中与键盘映射相关的代码，实现自定义游戏键位。
: 更新至 1.40，支持 TH6~TH17（花映冢除外）的官作 STG 以及黄昏酒场。


### 旧五作（TH01-TH05）模拟器
  
在其他硬件上运行 TH01-TH05 所必须的 PC-98 模拟器。
  
  
目前市面上存在以如下四种为主的多种各有优劣的方案，请根据需要进行选择。
  

RetroArch 方案
: 配置指南：[2024年，您还在使用Anex86玩东方旧作吗？](https://www.bilibili.com/opus/894274300553461760)，[第三方整合包](https://pan.baidu.com/s/1-eMIi4JIjyiTb8akg9r1Tw?pwd=9961)（仅 Windows，提取码：`
9961`
）
: RetroArch 是一款开源、跨平台且易用的多合一模拟器，其 PC-98 模拟支持基于 Neko Project II Kai（[日文主页](https://domisan.sakura.ne.jp/article/np2kai/np2kai.html)，[GitHub](https://github.com/AZO234/NP2kai)，[RetroArch 对其的介绍](https://docs.libretro.com/library/neko_project_ii_kai/)），可以实现相当准确的模拟，性能也过关。这使得 RetroArch 方案成为了当下最易用且均衡的旧作模拟方案，同时也是 Android 和 上的最佳模拟方案。
: 如果第三方整合包的版本过时，可按照配置指南，自行下载最新版本的 RetroArch 进行配置。
: 如果动手能力强，可以考虑直接使用 Neko Project II Kai 或其前代版本（前代版本例如 [Neko Project II](https://yui.ne.jp/np2/) 已经能实现相当好的模拟）。
DOSBox-X 方案
: 英文配置指南：[PC-98 emulation in DOSBox-X](https://dosbox-x.com/wiki/Guide:PC‐98-emulation-in-DOSBox‐X)
: DOSBox-X 是基于 [DOSBox](https://www.dosbox.com/) 的开源跨平台 DOS 系统模拟器。
: 由于 PC-98 通常使用修改自 MS-DOS 的操作系统，DOSBox 也就加入了 PC-98 支持，DOSBox-X 进一步改善了其支持，并且编写了配置指南。
: DOSBox-X 的 PC-98 模拟最为准确，但性能往往也最差。好在如今的电脑硬件基本能够弥补这一缺陷。
T98-Next 方案
: [Zophar 提供的英文版原程序下载](https://www.zophar.net/pc98/t98-next.html)，[第三方整合包](https://pan.baidu.com/share/link?shareid=1130699989&amp;uk=182521)
: 只支持 Windows。是此前最为常用的 PC-98 模拟器之一，操作上按键与 Windows 作品相同（Z、X、Shift）。
: 画面音频都有小问题但也都算过关，性能方面可能会有一些延迟，各方面较为均衡。
Anex86 方案
: [Zophar 提供的原程序下载](https://www.zophar.net/pc98/anex86.html)，支持英文，互联网上可找到汉化；[互联网档案馆上的第三方整合包](https://archive.org/details/anex86)；[touhou-memories 网站上的配置指南](https://touhou-memories.com/post/190684950124/configure-anex86)
: 只支持 Windows。模拟东方旧作时，至今仍旧是性能最好的 PC98 模拟器，但其模拟并不准确，画面和音频都存在问题。
: 如果条件允许，建议选用上面的其他方案。

  
更多链接：
  

- Shrinemaiden 论坛上 T98-Next 和 Anex86 方案的指南（英文）：[Configuring and Running PC-98 Emulators for Touhou](https://www.shrinemaiden.org/forum/index.php?topic=6549)
- [Zophar 的 PC-98 模拟器列表](https://www.zophar.net/pc98.html)  
 [Zophar's Domain](https://www.zophar.net) 是一个历史可追溯至 1996 年的老网站，比东方Project的历史都要早，上面英文指南中的下载链接即指向了这个网站。  
 这个网站上还收录了许多其他模拟器，其中这些 PC-98 模拟器或许也值得一试。


## 练习器与修改器
thprac - 东方通用内置型练习器
: 更新至v2.2.1.7， **目前功能最强大的练习器** ，也可当做全作游戏启动器使用。
: 支持所有Windows平台的官作STG（包括黄昏酒场），会自动识别并应用[VsyncPatch](#游戏补丁)，兼容部分汉化版游戏。[^cite_note-1]
: 支持多种启动方式，包括使用启动器功能启动游戏、在启动游戏后开练习器、将练习器放入游戏文件夹直接运行。如果出现异常，可尝试其他启动方式。  
 启动后，会修改游戏内的Practice模式，使其可以直接跳转至 **关卡中的某一段、某个boss甚至于某张符卡** ，  
 也可设置初始残机、火力等数据，最大限度模拟实战情况。的rep需要使用练习器播放。  
 此外，提供一些针对游戏本体错误（如虹龙洞大蜈蚣卡炸录像等）的修复（按F12呼出菜单）。  
 应用了修改的录像需要使用练习器播放，并尽量保证练习器版本大于等于录像保存时的版本。  
 其他说明可参见程序附带的说明文档。


<table>

<tbody><tr>
<th>历史
</th></tr>
<tr>
<td>2.0.8.3前由玩家<a rel="nofollow" class="external text" href="https://github.com/ack7139">Ack</a>制作，2.0.8.3后的版本由<a rel="nofollow" class="external text" href="https://github.com/32th-System">32th System</a><sup id="cite_ref-2" class="reference"><a href="#cite_note-2">2</a></sup>制作，<a rel="nofollow" class="external text" href="https://github.com/touhouworldcup/thprac">仓库地址</a>。<a rel="nofollow" class="external text" href="https://wws.lanzoux.com/b01hhxnbi">2.0.8.3版本下载，提取码20ri</a><sup id="cite_ref-3" class="reference"><a href="#cite_note-3">3</a></sup>
<p><b>注意：</b>原作者Ack已在其b站账号上宣布无限期地停止thprac的一切开发工作，相关代码已经开源。详情见<a rel="nofollow" class="external text" href="https://t.bilibili.com/645576384015499269?tab=2">原作者动态</a><span style="font-family: sans-serif; cursor: default; color:#555; font-size: 0.8em; bottom: 0.1em; font-weight: bold;" title="连接到已经失效网页">（已经失效）</span>
</p>
</td></tr></tbody></table>


thaid - 东方符卡练习器 - 东方全作通用练习辅助工具（Th18东方虹龙洞测试版下载）
: 作者：[Linsk](http://www.linsk.net/)（[Bilibili](https://space.bilibili.com/281053/)），[工具主页](http://www.linsk.net/tool/thaid/)
: 多功能练习器，支持无敌/锁残/锁B/自动雷等常见功能，且有做针对性设计，可以用于重复练习同一种子弹、研究子弹移动规律等。
: 详见工具主页或下载文件中的说明。
THSet - 车万修改器
: 作者：[swordarrow2](https://github.com/swordarrow2)
: 支持TH06-TH17，功能方面，支持锁残锁B等常见功能，和FPS修改等。
: 缺乏较新版本的二进制。如果需要，需要使用 Visual Studio 15 或以上版本自行编译。
thxx_init - 游戏初始值修改器（提取码：f7h0）
: 作者：Wz520 (未找到链接)，[发布来源](https://www.zybuluo.com/wz520/note/15842#thxxinit-游戏初始值修改器)，修改各作游戏内部数据的初始值，方便练习。
星莲船专用修改器(UFOassist)
: 除了一般的锁残、锁B、无敌功能外，还有显示激光轨迹、敌兵血量、飞碟变色以及停留时间，去掉封兽鵺的sc战的马赛克等各种星莲船特定功能。  
 使用这个软件打出来的replay会被其标记，以和正常replay区分。


## 信息查看工具
RPYVIEW - 东方回映录 - 东方STG录像信息查看器（提取码：83fq）
: 作者：Wz520 (未找到链接)，[原帖地址](https://tieba.baidu.com/p/6522266043)，[GitHub](https://github.com/wz520/thhyl)。
: Replay查看器，可以快速查看rep的分数、日期、玩家以及各关状态等细节数据。更新至1.87(th17)。
thwatch - 东方STG游戏数据监视器
: 作者：Wz520 (未找到链接)，[1.0版本原帖地址](https://tieba.baidu.com/p/3382041418)[2.0版本原帖地址](http://tieba.baidu.com/p/3685073224)（已经失效）[2.1/2.2 更新帖地址](https://tieba.baidu.com/p/3996362869)
: 在单独的命令行窗口中，以数值形式实时显示东方STG敌机的血量、最大血量、发动下一阶段弹幕所需HP、  
 当前血量占最大的百分比，以及自机坐标、敌弹数等信息（不同作品会显示不同的数据）。  
 最新版本为2.2，支持到TH15版本1.00b，详细请看原帖介绍。
thinput - Touhou Input Display - 实时按键状态显示工具
: 作者：[Drake](https://twitter.com/drakeirving)，[原更新帖](https://www.shrinemaiden.org/forum/index.php/topic,16024.0.html)，已更新至TH165（噩梦日记），支持 **所有作的原版和英化版，以及黄昏酒场** 。  
 [Touhou Wiki 上的 2.2.0 版本](https://mega.nz/file/5okiXDqJ#xbjCQcUhAh7VH1LwNGjvsaIHMJ-l6RWOdP35jidvniA)已支持 TH17 鬼形兽，但需要连接网络下载。
: 可以实时查看rep某时刻的按键情况。加入额外代码后，可支持渔场汉化版红魔乡、文花帖DS，请参见[这里（旧代码）](http://tieba.baidu.com/p/3599559143)。
: 若要适配风神录（th10）之后的独立EXE汉化版（形如thxx **c** .exe、thxx **chs** .exe的启动程序），可直接打开文件夹下thinput.ini，  
 将AddressList中对应游戏的一行复制，并将程序名重命名为对应程序名，保存即可。
Input Overlay - OBS 按键可视化工具
: [GitHub](https://github.com/univrsal/input-overlay)，[文档](https://github.com/univrsal/input-overlay/wiki)，[安装指南](https://github.com/univrsal/input-overlay/wiki/Installation)（英文）
: 适用于 OBS Studio 的按键可视化工具，可以为任意版本正作可视化按键，无需针对性更新支持，且能够自定义。
: 安装使用配置略为麻烦，如果还没有的话，请先学习安装和使用 OBS Studio，再了解 OBS 插件的安装，最后参考上面的安装指南和文档。
Bongo Cat 系列按键可视化工具
: 一方面可以视作更加多功能的 Input Overlay，支持 Live2D、显示鼠标操作等。  
 另一方面，它不是 OBS 插件，而是可以直接运行的软件，使用更为简便，只是一些游戏全屏时可能偶有问题。  
 但主要只是在外观方面有优势，有莉莉白版本，缺点是显示的按键不便查看。

: 
<table>
<tbody><tr>
<th>视频
</th>
<th>下载
</th></tr>
<tr>
<td><a rel="nofollow" class="external text" href="https://www.bilibili.com/video/av86818090">主播必备超萌替身工具Bongo Cat Mver ，8分钟入门</a>
</td>
<td><a rel="nofollow" class="external text" href="https://www.bilibili.com/read/readlist/rl191271">最新版本下载</a>
</td></tr>
<tr>
<td><a rel="nofollow" class="external text" href="https://www.bilibili.com/video/av201290260">【东方】莉莉白live 2d演示</a>
</td>
<td><a rel="nofollow" class="external text" href="https://pan.baidu.com/s/1MZ2krwXUzIK1ru0O-mDsnw?pwd=0bqq">下载</a>（提取码：0bqq）
</td></tr>
<tr>
<td><a rel="nofollow" class="external text" href="https://www.bilibili.com/video/av698445332">Bongo Cat 莉莉白按键显示桌宠-stg键位拓展版</a>
</td>
<td><a rel="nofollow" class="external text" href="https://pan.baidu.com/s/1hrhzWimrAR9Y9oziO7CGqA?pwd=Lily">下载</a>（提取码：Lily）
</td></tr>
<tr>
<td><a rel="nofollow" class="external text" href="https://www.bilibili.com/video/av201290260">非想天则直播桌宠Bongo Cat莉莉白版</a>
</td>
<td><a rel="nofollow" class="external text" href="https://pan.baidu.com/s/1STqS0LHcvrPKNqernvr3mA?pwd=291l">下载</a>（提取码：291l）
</td></tr></tbody></table>



: 另有一个国外开源的 OBS 插件版，但其功能相比之下比较简陋，也没有莉莉白版本：[Bongobs Cat Plugin](https://obsproject.com/forum/resources/bongobs-cat-plugin.992/)


## 游戏补丁
  
用于改变游戏设定或是修复游戏内bug的附加文件，可能需要放入原游戏文件夹中并替换掉原游戏文件，尽量先备份游戏程序及数据（`
score.dat`
 等）再使用。
  

VsyncPatch（VP）
: 作者：[swmpLV/75E（adonis）](https://twitter.com/kaei_adonis)，更新至th15，支持黄昏酒场。
: 多功能补丁，可以减少按键延迟，还有一些其他功能：
- 修复妖妖梦分数超过一百万、星莲船分数超过231
时的显示 bug；
- 为红妖永花四作的rep增加快进功能，为所有作品的rep增加慢放功能（Ctrl快进，Shift键慢放。妖妖梦快进时可能导致最终分数有少许偏差）；
- 将游戏速度调至60FPS以上（但不能降低）；
- 修改窗口大小等功能（可在vpatch.ini中设置，window选项中，enabled设置为1，然后W/H即为窗口的宽/高。）。

: 使用：将vpatch.exe、vpatch.ini，以及对应游戏的dll文件（如妖妖梦就是th07.dll）三个文件放入游戏文件夹，修改好vpatch.ini后，运行vpatch.exe即可。
:  **更多功能及具体配置方法可参照：[VsyncPatch](./游戏攻略-STG常用工具-VsyncPatch.md)** 
DirectX 8 转 DirectX 9 兼容性补丁
: TH06 红魔乡到 TH09 花映塚使用 DirectX 8 开发，在 Win10 上运行时会出现兼容性问题。  
 虽然不是专门的东方游戏补丁，但这种补丁一样能够修复 Win10 红魔乡千帧、萃梦想闪退等问题。
d3d8to9
: 作者：[crosire](https://github.com/crosire)，现代化且开源的 DirectX 8 转 DirectX 9 转接 DLL。
: 除了修复兼容性问题，还能够支持独占全屏、进一步降低输入延迟、改善与 OBS、ReShade 等外部软件的兼容性。
ENBSeries DX8 to DX9 Convertor
: 以前的“千帧红魔乡补丁”，修复红魔乡在 Windows 10 等版本较新的操作系统下出现的帧率问题。
: 长期未更新，已被 d3d8to9 代替，相比之下，有萃梦想图像模糊等问题。
: 下载后将补丁文件解压缩到红魔乡所在目录后，运行 custom.exe 配置游戏强制运行在 60FPS 即可。


thxxcnrpyfix
: 作者：Wz520 (未找到链接)，[原帖地址](https://tieba.baidu.com/p/2544479479)
: 让妖妖梦、永夜抄、花映塚日文版支持中文版录像的补丁。
th09saverpyfix - 东方花映塚保存录像出错修正补丁
: 作者：Wz520 (未找到链接)，[原帖地址](https://tieba.baidu.com/p/2496104991)
: 花映塚保存游戏录像时有一定几率会出错（尤其是 STORY MODE），此内存补丁试图降低该问题的发生几率。
支持 1.50a 日文版或渔场汉化版。
th11aifix - 东方地灵殿全开档机签修复补丁
: 作者：Wz520 (未找到链接)，[原帖地址](https://tieba.baidu.com/p/3200788584)
: 修复由于某流传很广的全开档导致的、所保存的每一个 REP 的机签后，都会莫名其妙地多出2个字母 "Ai" 的问题。
: [红魔乡单关练习保存录像补丁](https://pan.baidu.com/s/1pJqDCnh)（ **现已整合至 [thaid](#练习器与修改器) 中** ）
: 作者：[Linsk](http://www.linsk.net/)（[Bilibili](https://space.bilibili.com/281053/)）
: 众所周知，红魔乡的单关练习模式（Practice）无法保存 replay。这个补丁可以允许保存 practice replay 。  
 应用补丁后，当 practice 模式结束时，会像非 practice 模式一样记录成绩，并询问是否保存 replay。（补丁文件内置使用说明）  
 保存的单关 replay 可以在原版中正常播放。
禁用手柄检测补丁
: 作者：[疯受鶸](https://www.bilibili.com/read/cv25351189/)，TH17 之前的游戏程序会循环检测手柄，导致资源占用与卡顿，这个补丁可以禁用检测功能，以解决此逻辑引发的性能问题。  
 鬼形兽以后，ZUN 修复了这个问题，所以不再需要。  
 补丁解压缩直接丢进游戏文件夹即可，另建议在 custom.exe 里面把输入模式调成 fast。  
 这个补丁会导致bandicam没法注入游戏（obs可以）。如果需要用bandicam的话，可以换用vjoy[^cite_note-4]这样的工具创建一个虚拟手柄，来解决类似的卡顿问题。


## 改版游戏
  
可以体验基于原作但又略有区别的游戏，同样可能需要放入原游戏文件夹中并替换掉原游戏文件，尽量先备份游戏程序及数据（score.dat等）再使用。
  

Boss Rush
: [红魔乡](http://pan.baidu.com/s/1i5AUAah) [妖妖梦](http://pan.baidu.com/share/link?uk=4097052736&amp;shareid=10165070) [风神录](http://pan.baidu.com/s/1pLhCg11) [地灵殿](https://pan.baidu.com/s/1dF1wxCd)[^cite_note-5] [星莲船](http://pan.baidu.com/share/link?shareid=227343&amp;uk=3139616513) [大战争](http://pan.baidu.com/share/link?uk=4097052736&amp;shareid=1052751160) [绀珠传](http://pan.baidu.com/s/1bn8rEyV) [TH10-16(含12.8)，提取码：8bzq](https://pan.baidu.com/s/1FHG2D0QUU4uWmryXB9-xfw)。
: 跳过道中，直接进行boss战的游戏补丁（有些也跳过道中boss）。
妖妖梦95RANK补丁
: 将rank值锁定在95的妖妖梦补丁。
地灵殿DeathLable模式补丁
: 模仿怒首领蜂大往生，全程0残，初始满P，故事模式有12P的补给，EX有4P的补给，只保留关底boss的游戏模式。
overdrive难度解锁补丁（神灵庙、辉针城）
: 神灵庙的符卡练习中出现了overdrive难度，但故事模式和EX模式中没有出现，该难度解锁补丁可以实现在该难度下进行游戏。
: 辉针城的正常游戏中没有出现od难度，但主程序中也保留了该难度，故也可以解锁。
东方辉针城显示效果修改器
: 设置游戏内各物体是否显示的工具，可用于关闭游戏背景等。
东方倒着玩补丁
: [原帖地址](http://tieba.baidu.com/p/3431933591)，更适合鬼人正邪体质的补丁。修改过的游戏主程序，从 GAME START 进入后，会从6面开始，然后5,4,3,2,1,ENDING。  
 支持风神录 1.00a、地灵殿 1.00a、星莲船 1.00b、神灵庙 1.00c、辉针城 1.00b、绀珠传 1.00a。
绀珠传EX关完美模式补丁（提取码p6v5）
: 将 `
thhyl\改版EXE\th15_ex_pmode.exe`
 放到游戏目录下运行即可。本版本的EXTRA关卡只有完美模式。[对于中文版的支持参照原帖地址](http://tieba.baidu.com/p/4466644006)
永夜抄8关版（提取码hcdx）、9关版（提取码v2vs）
: 8关版是需要打两种四面和六面的版本，9关版在此基础之上还增加了EX面。将exe文件解压至游戏目录下运行即可。

  
Priw8 魔改作品：
  

东方辉绀传（提取码mw8b）
: LoDDK，顾名思义为辉针城与绀珠传的结合（仅boss），包含正篇与extra。由Priw8制作。
DDDDDDDDDDDD（提取码ukl3）
: 由Priw8制作的要素过多的辉针城魔改。
东方天空璋，但是妖精大战争（提取码ckdq）
: 由Priw8制作的天空璋魔改，将大战争的弹幕冰冻系统加入，取代季节解放系统。


## 联机对战工具
  
格斗作与花映塚/兽王园的联机对战工具。
  

非想天则联机工具 swarm
: 作者：[evshiron](https://github.com/evshiron)，适用于外网的双人联机对战工具，支持观战。
非想天则联机工具 Shitama
: 作者：[Remi IO](https://github.com/u-u-z)，适用于外网的双人联机对战工具，支持观战。已经很久未更新，但代码开源，可以自行构建部署使用。
通用联机工具 ThLink
: 作者：桜風の狐，适用于外网的双人联机对战工具，支持非想天则和凭依华多人观战。花映塚连机需配合 adonis2 使用。
花映塚连机工具 adonis2
: 适用于外网的双人联机对战工具。（内网可以用映射。）
: 


<table>

<tbody><tr>
<th>使用说明
</th></tr>
<tr>
<td><div class="poem">
<p>汉化版本的adonis的readme是这样的，大概对应意会一下吧<br>
1 将全部文件复制到HYZ1.50版本游戏目录下<br>
2 打开adonis_config.ini<br>
3 修改name 让人容易辨识(比如“UUF TJ”)<br>
4 保存关闭<br>
5 可能需要从共享下载全人物档<br>
6 运行一次custom汉化版 保证1p 2p均为键盘全部<br>
7 adonis.exe/adonis_cn.exe<br>
主机建用s(外网) 客机c 观看w<br>
8 建主:<br>
&#160;s <br>
&#160;输入端口(推荐 10800 )<br>
&#160;等待插入<br>
&#160;插入后选择delay 回车为自动选择（推荐）<br>
&#160;选择自己的机器 1p/2p/随机  回车为1p<br>
9 客机<br>
&#160;c<br>
&#160;输入对方ip<br>
&#160;输入端口<br>
&#160;等待主机进一步<br>
10 观看<br>
&#160;&#160;w<br>
&#160;&#160;和客机相同<br>
11 比赛开始后即可游戏 胜负分出后选择重战 换角色 存rep退出(可以选择后不存 反正就是退出)<br>
<br>
关键点是要改ini里的玩家名，使用全开档避免自机不全，按键设置正确（且固定成默认按键），<br>
然后会用命令行（汉化版做了图形化界面，但不太好用，还是命令行稳定）<br>
连接成功后，两边电脑都可以同步控制游戏画面。进入对战模式后，分别控制P1和P2。<br>
网络质量一般时，可能会在网络联机时卡顿。<br>
实际上想联机打花的话，加个花映塚对战群是比较方便的
</p>
</div>
</td></tr></tbody></table>


ZeroTier
: 免费且稳定的虚拟局域网组网工具，支持多个网络，多台主机。配置简单，只需初次配置。


## 游戏文件相关工具
Touhou Vorbis Compressor - BGM压缩工具（提取码：tb8m）
: 更新至TH15正式版。将原作游戏的wav格式音源压缩为ogg格式，从而极大减少游戏文件夹的总体积。  
 使用方法见压缩包内howto.txt文件  
 当然不是指手机/掌机等等可用的版本。  
 [压缩好的全作游戏分流](https://cloud.lilywhite.cc/s/4ZUW?path=/东方Project/官方游戏/OGG版 (节约硬盘空间))
THResHack
: STG正作魔改辅助工具，在不解包的情况下便捷地替换thxx.dat文件，且可在游戏运行时替换。  
 使用方法：将dinput8.dll放入游戏目录，新建名为data的文件夹，将需要替换的文件放入data内即可。  
 目前支持到th19体验版（v1.00a）。[下载链接](https://pan.baidu.com/s/1XH89sKNP2TjASa_PP9LT-A?pwd=2215)，编译日期为20230526。


### 游戏文件解包工具
Touhou Toolkit（thtk），一个用于解包东方正作游戏的工具集
: 用来解包东方正作（主要是弹幕作）游戏的工具集，喵玉殿上面有详细[教程](https://bbs.nyasama.com/forum.php?mod=viewthread&amp;tid=1834509)，具体可以阅读Readme。  
 最新release 12版本支持至th17鬼形兽，部分兼容虹龙洞，最新master版本支持至th19兽王园。  
 [release 12](https://bbs.nyasama.com/forum.php?mod=attachment&amp;aid=MTU3Mjg1fDJjZjI1NTUyfDE1ODQ0MzgyNjl8MjI5ODAyfDE4MzQ1MDk=) [最新master版本](https://nightly.link/thpatch/thtk/workflows/build/master/thtk-win32-x64.zip)
Touhou Project Data Unpack For Touhou Toolkit 提取码：f2m0
: 基于Touhou Tooklkit的UI版东方正作解包工具  
 注意：目前是测试版本，且开发时间只有20小时，难免会有一些作者没有察觉到的bug，如发现了bug可以通过邮箱向作者反馈，作者会尽快修复。  
 也可以通过邮箱向作者提出意见，作者会合理进行更改。
THxxBGM
: 东方正作音乐播放和解包工具，支持弹幕作、萃绯则、黄昏酒场。
bgm提取器
: 在已知BgmForAll信息的情况下，可以提取出或直接播放游戏的bgm。
ThbgmExtractor
: 也可以提取和播放游戏BGM，所需的相应txt曲目文件资源在主页下的列表中列出。
THBGM-UNPacker
: 配合thtk使用可提取出BGM并生成相应的BgmForAll.ini文件。
THMusicBox
: 配合thtk使用的安卓版游戏BGM播放器。


## 相关链接
Game Tools and Modifications - Touhou Wiki
: 英文 Touhou Wiki 上的游戏工具和修改页面，介绍了 dgVoodoo2、ThMouse、TouhouKeymap 等本页面暂未覆盖到的实用工具和大量解包工具。
Priw8的工具站
: 国外魔改大神Priw8的个人网站。
: 其中包含若干魔改，如DDDDDDDDDDD，LoDDK（东方辉绀传），下载资源需要科学上网；  
 包含对正作脚本系统的解析与网页版[sht文件编辑器](https://priw8.github.io/sht-webedit/)（可以在有限的范围内修改自机性能数据）；  
 以及一些外链。
Wz520 东方project 相关工具
: Wz520 (未找到链接)（百度贴吧 ID：[天使的枷锁](https://tieba.baidu.com/home/main?id=f861cceccab9b5c4bccfcbf83d00)）是THKMC、东方回映录等大量工具与补丁的作者，这是他自己的工具集合页面。


[^cite_note-1]: 
完美兼容 **类似于启动器的汉化版** （如喵玉汉化版辉针城与thcrap）；  

但对 **修改游戏dat文件的汉化版** （例如市面上流行的“永夜抄汉化版+日文版”中，存在`
th08.dat`
和`
th08c.dat`
）可能出现跳转失效的情况。





---

此文档由 [THBWiki-Markdown-Builder](https://github.com/Delsin-Yu/THBWiki-Markdown-Builder) 构建。

文档中的所有内容除特殊注明外，均在 [**知识共享(Creative Commons) 署名-非商业性使用-相同方式共享 3.0 协议**](https://creativecommons.org/licenses/by-sa/3.0/deed.zh-hans) 下提供，附加条款亦可能应用。

引用类型与其他类型作品版权归原作者所有，如有作者授权则遵照授权协议使用。

详细请查阅 [THBWiki：免责声明](https://thbwiki.cc/THBWiki:%E5%85%8D%E8%B4%A3%E5%A3%B0%E6%98%8E)。

