# ZUN/游戏的修罗场6

<!-- source html: G:\repos\THBWiki-Markdown-Builder\THBWikiMarkdown\Temp\main\3\3e\ns0%3AZUN%2F%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA6.html -->

ZUN | 采访

- 本次访谈刊载于にじけん（Nijiken）的合同志游戏的修罗场6。
- 翻译：京都人形
- 协助：atrican（术语指导），霜月（代码录入）


<table><tbody><tr align="left" valign="top"><td style="min-width:200px;"><br>
<p><big><b>上海爱丽丝幻乐团 zun氏 访谈</b></big>
</p>
<div class="poem">
<p>采访对象：上海爱丽丝幻乐团 zun氏（以下略称zun）<br>
采访者：出水洸太郎（以下略称出水）<br>
本次向以东方Project而著名的zun氏，采访了关于东方使用的弹幕脚本以及对于游戏的看法等话题。<br>
<br>
</p>
<dl><dt>zun</dt>
<dd>总之，先要点喝的吧。没有喝的也聊不起劲……。<br></dd></dl>
<p>（于是，要了啤酒）
</p>
</div>
<div id="toc" class="toc" role="navigation" aria-labelledby="mw-toc-heading"><input type="checkbox" role="button" id="toctogglecheckbox" class="toctogglecheckbox" style="display:none"><div class="toctitle" lang="zh" dir="ltr"><h2 id="mw-toc-heading">目录</h2><span class="toctogglespan"><label class="toctogglelabel" for="toctogglecheckbox"></label></span></div>
<ul>
<li class="toclevel-1"><a href="#弹幕脚本"><span class="tocnumber">1</span> <span class="toctext">弹幕脚本</span></a></li>
<li class="toclevel-1"><a href="#何谓游戏的卖点"><span class="tocnumber">2</span> <span class="toctext">何谓游戏的卖点</span></a></li>
<li class="toclevel-1"><a href="#游戏的制作方法"><span class="tocnumber">3</span> <span class="toctext">游戏的制作方法</span></a></li>
<li class="toclevel-1"><a href="#懒洋洋酒桌闲聊"><span class="tocnumber">4</span> <span class="toctext">懒洋洋酒桌闲聊</span></a></li>
<li class="toclevel-1"><a href="#关于音乐"><span class="tocnumber">5</span> <span class="toctext">关于音乐</span></a></li>
<li class="toclevel-1"><a href="#开始制作同人游戏之前"><span class="tocnumber">6</span> <span class="toctext">开始制作同人游戏之前</span></a></li>
<li class="toclevel-1 tocsection-7"><a href="#注释"><span class="tocnumber">7</span> <span class="toctext">注释</span></a></li>
</ul>
</div>

<h3><span id=".E5.BC.B9.E5.B9.95.E8.84.9A.E6.9C.AC"></span><span class="mw-headline" id="弹幕脚本">弹幕脚本</span></h3>
<dl><dt>zun</dt>
<dd>那么从何说起呢。</dd></dl>
<dl><dt>出水</dt>
<dd>啊，在黄昏酒场<sup>1</sup>的时候后记里有句「弹幕脚本好可怕」的评论，我就想问问这方面的事情。</dd></dl>
<dl><dt>zun</dt>
<dd>正好，我也把那个文件带过来了。</dd></dl>
<dl><dt>出水</dt>
<dd>那么，就看看那个吧。我让我的笔记本电脑开机。</dd></dl>
<dl><dt>zun</dt>
<dd>这是神灵庙5面BOSS的脚本。</dd></dl>
<dl><dt>出水</dt>
<dd>笔记本里要是有完整的神灵庙游戏就好了……。但是，那就只能用键盘玩了。</dd></dl>
<dl><dt>zun</dt>
<dd>用键盘玩只能是更难。（笑）</dd></dl>
<dl><dt>出水</dt>
<dd>但是，键盘党也有很多啊。</dd></dl>
<dl><dt>zun</dt>
<dd>因为用键盘可以更精确地斜向移动。手柄的话不自觉地就斜了。</dd></dl>
<dl><dt>出水</dt>
<dd>98<sup>2</sup>的时候我是在键盘旁边放个摇杆，只有在低速移动的时候用键盘的SHIFT键。</dd></dl>
<dl><dt>zun</dt>
<dd>98的时候啊~，因为没有按键所以没法设置低速移动的按键<sup>3</sup>呢~。我就是一直用键盘玩的……。现在也一直是用键盘设置的。</dd></dl>
<dl><dt>出水</dt>
<dd>啊，PC准备完成了。</dd></dl>
<hr>
<div class="poem">
<p><sup>1</sup>吞兵卫会制作的STG。东方Project使用的引擎为其游戏母体。现在已经成为免费软件，可以下载。 <a rel="nofollow" class="external free" href="http://alcostg.amatukami.com/">http://alcostg.amatukami.com/</a><br>
<sup>2</sup>指PC-9801。被称为东方旧作的5个作品在此平台上公布。<br>
<sup>3</sup>使用游戏手柄的时候，由于硬件限制只能识别2个按键。那2个按键由于分配给了射击和Bomb，低速移动只能使用键盘。
</p>
</div>
<hr>
<dl><dt>zun</dt>
<dd>我尽可能地考虑如何才能写得少。我给予弹幕各种各样的参数来让它们运动。其特征应该是无论什么样的参数都可以加入对应不同难易度的值。不必使用if文来分配，很方便。</dd></dl>
<dl><dt>出水</dt>
<dd>这很有意思。</dd></dl>
<pre>func:Boss1_at(float rd2)
  @set_et(0, ETON_CIR, ET32H, BLUE32, &lt;span style="background-color:gray;"&gt;{{color:white|20：32：42：58}}&lt;/span&gt;, 1, 0, R_10, 3.1, 1.0)
  @exi_effon1(0)
  @exi_spup(0, EX_WAIT, 90, -3.0/120.0, NEG)
  @exi_delay(0, 60)
  @exi_spup(0, EX_WAIT, 120, 6.0/120.0, NEG)

  et_ofs(0, 0, -24)

  float r = RDEG
  float rd = 0
 
  Times(10){
    //
    et_r(0, r, R_20)
    r += rd
    rd += rd2
    et_on(0)
    wait(10)
  }
end
</pre>
<p>这是物部布都最初的弹幕的脚本。灰色的部分，是对应不同难易度的参数的部分。写下4个数值并用逗号隔开，就分别成为了EASY,NORMAL,HARD,LUNATIC的值。在这里，EASY中是20方向的同心圆弹，在LUNATIC中则会成为58方向的同心圆弹。以下左为EASY，右为LUNATIC的照片，同心圆弹的弹数发生了变化。
</p><p><a href="./文件-游戏的修罗场.jpg.md" class="image"><img alt="游戏的修罗场.jpg" src="https://upload.thwiki.cc/thumb/e/e5/%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA.jpg/600px-%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA.jpg" decoding="async" loading="lazy" width="600" height="345" srcset="https://upload.thwiki.cc/thumb/e/e5/%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA.jpg/900px-%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA.jpg 1.5x, https://upload.thwiki.cc/thumb/e/e5/%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA.jpg/1200px-%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA.jpg 2x" data-file-width="1677" data-file-height="964"></a>
</p>
<dl><dt>zun</dt>
<dd>有时也会在命令之前写难易度。这种情况下可以达到EASY和NORMAL是这样，HARD和LUNATIC是那样的效果。</dd></dl>
<pre># 第三阶段符卡
func:BossCard3()
  @CardStart()
 
  interrupt(0, 0, TIME_CARD2*60, "Boss4")　　　 　　　　　　　　　  # 死了的时候
,EN:cardE(CARD_ST5_3E, TIME_CARD2*60, SCORE_CARD1, "炎符「废佛之炎风」"）
,HL:cardE(CARD_ST5_3E, TIME_CARD2*60, SCORE_CAED1, "炎符「火烧樱井寺」"）

（以下割爱）
</pre>
<p>根据EASY,NORMAL和HARD,LUNATIC符卡名会发生变化的部分。由于没有if文，很整洁。
</p>
<dl><dt>zun</dt>
<dd>创作这种语言是很快乐的事情。</dd></dl>
<dl><dt>出水</dt>
<dd>我听说过去您都把BOSS这部分硬编码<sup>4</sup>，现在都是这种感觉了啊。</dd></dl>
<dl><dt>zun</dt>
<dd>你说的那个过去也是指98的时候了。那个时候还可以一次性使用，但是后来逐渐一次性不了了，于是使用脚本就更加轻松起来了。</dd></dl>
<dl><dt>出水</dt>
<dd>脚本的话不用重启程序就能测试，很方便呢。</dd></dl>
<dl><dt>zun</dt>
<dd>我会进行硬编码的只有游戏的系统这部分。那个部分不会再在别的地方用到。既不全是脚本，也不全是硬编码，保持二者之间的平衡是很好的。</dd></dl>
<dl><dt>出水</dt>
<dd>打倒敌人的时候该怎么办呢。</dd></dl>
<dl><dt>zun</dt>
<dd>啊，那个的话会在开头写上这种函数<sup>5</sup>。到达指定的时间，或者被打倒，就会跳到这个函数上去，这种感觉。</dd></dl>
<dl><dt>出水</dt>
<dd>原来如此，大致开始明白了。其他还有什么呢。</dd></dl>
<dl><dt>zun</dt>
<dd>频繁使用的是随机数。随机数会编入变量之中<br>用大写字母写着RI或者RF的就是随机数。因为RI是整数，所以不太经常用吧……。RF的话就是0~1的浮点数，RF2的话是-1~1的浮点数。一个一个都呼出函数是很麻烦的。</dd></dl>
<dl><dt>出水</dt>
<dd>确实，因为频繁使用随机数所以不做成函数，这点很有意思。只要有0~1和-1~1就大致上足够了。</dd></dl>
<hr>
<div class="poem">
<p><sup>4</sup>指将数据直接写入程序之中。这次作为脚本的反义词使用。<br>
<sup>5</sup>指interrupt函数。请注意下一页的源代码的开头部分。
</p>
</div>
<hr>
<pre># 第二阶段符卡
func:BossCard2()
  @CardStart()
  
  interrupt(0, 0, TIME_CARD2*60, "Boss3")      # 死了的时候
  cardE(CARD_ST5_2E, TIME_CARD2*60, SCORE_CARD1, "投皿「物部氏的八十平瓮」")
  pos_i(60, IT_2X_I, 0.0, 96.0)

+60 &#160;: nop
+60 &#160;: nop
  clip(0.0, 128.0, 96.0, 64.0)

  float x,y,r &lt;== PI/15: PI/15: PI/19: PI/23
  int max &lt;== 19: 32: 40: 48

  I0 &lt;== 9: 19: 24: 33
  while(1){
    @EffChargeCyan()
    anim_at(0)
    wait(60)
    BossCard2_at(r)
    wait(40)
    anim_at2(0, 2)
    r *= -1
    rot_r(120, IT_SIN_DI, 1.0)
    wait(140)

    if(I0 &lt; max){
      IO += 2
    }
  }
end

func:BossCard2_at(float rd)
  @set_et(0, ETON_FAN, ET32A, BLUE32, 1, 1, 0, R_10, 0.3, 1.0)
  @exi_effon1(0)
  @exi_spdown(0)
  @exi_ref(0, EX_WAIT, 1, NEG)
  @exi_on_br(0, ETON_RANDOM, ET16E, BLUE_L, 10, 1, -PI, PI, 0.5, 2.0, 6)

  @ex_effon1(0, 6)
  @exi_not_out(0, 180)
  @exi_spup2(0, EX_WAIT, 120, 0.1, NEG)
  et_ofs(0, 0, -16)

  float r &lt;== AIM + rd*5: AIM - rd*5: AIM – rd*5: AIM - rd*5, sp = 1.0, sp2

  Times(I0){
    et_sp(0, sp, 0)
    sp += 0.2
    sp2 = 1.3 + RF2*0.2
    @ex_spup(0, 9, EX_WAIT, 120, sp2/120, R_D+RF2*R_20)
    et_r(0, r, R_20)
    r += rd
    et_on(0)
    wait(1)
  }
end
</pre>
<p>将盘子扔出去，盘子打到画面边缘时反弹弹就会倾泻而下的符卡投皿「物部氏的八十平瓮」。IO的值代表扔的盘子的数量，每次增加2枚。正如访谈中所说，每次使用RF2这个变量时都会在-1~1的范围内返回一个随机浮点数值。
</p>
<dl><dt>zun</dt>
<dd>能让我关照到如此细微的地方便是脚本的好处。而且因为做得很简洁，所以很快。虽然没什么通用性。呼出这个的又是别的敌人。有一个看不见的无敌的敌人，它来呼出这个。</dd></dl>
<dl><dt>出水</dt>
<dd>那也就是说还有管理杂鱼战的敌人这种感觉吗。有一个无敌的敌人……。</dd></dl>
<dl><dt>zun</dt>
<dd>对对，一启动就会有一个叫“main”的敌人。很有C语言的感觉吧。</dd></dl>
<dl><dt>出水</dt>
<dd>是啊。中BOSS之类的是怎么处理的？</dd></dl>
<dl><dt>zun</dt>
<dd>有一个一直等到中BOSS死掉为止的命令。如果是BOSS，应当有一个等到对话结束为止的函数。</dd></dl>
<dl><dt>出水</dt>
<dd>看着这些就想把对话场景也加入脚本之中，但是没有呢。</dd></dl>
<dl><dt>zun</dt>
<dd>对话有单独的一个脚本。有像表情转换这样的指令，如果文字是以全角开始的就会被当成是对话内容，这种感觉。</dd></dl>
<dl><dt>出水</dt>
<dd>原来如此，还准备了一个专门用于对话的脚本啊。感觉那样做起来更简单，很棒呢。</dd></dl>
<dl><dt>zun</dt>
<dd>这些东西我也是在每次制作过程中加以改善的。这也是很愉快的事情。通过改进，亲自使用成长了的脚本也是令人高兴的。<br>由于没什么通用性，所以没法将其公开让大家使用。感觉公开了之后会出现各种缺了点什么的东西。而且不论用这个制作什么，也只会是东方。</dd></dl>
<dl><dt>出水</dt>
<dd>确实，东方有种“是那种感觉”的要素在里面。</dd></dl>
<dl><dt>zun</dt>
<dd>“是那种感觉”的感觉也可能是脚本导致的呢。</dd></dl>
<dl><dt>zun</dt>
<dd>啊，请再来一杯啤酒。</dd></dl>
<h3><span id=".E4.BD.95.E8.B0.93.E6.B8.B8.E6.88.8F.E7.9A.84.E5.8D.96.E7.82.B9"></span><span class="mw-headline" id="何谓游戏的卖点">何谓游戏的卖点</span></h3>
<dl><dt>zun</dt>
<dd>98的时候我可是拼了命的啊~。我想那是在游戏的制作方法方面，拼命地寻找现在什么样的游戏是好游戏的状态。想制作个卖点。那个时候没这种概念，总之技术本身就直接成了卖点。弄出在98中最多的子弹吧，之类的。我努力地研究了那方面。因为我是上了大学才首次接触编程。既没有互联网，想要找书也找不到什么书<sup>6</sup>。</dd></dl>
<dl><dt>出水</dt>
<dd>那时候确实没什么好书呢~。</dd></dl>
<hr>
<p><sup>6</sup>98的很多功能、原理都是非公开的，大多数都需要亲自摸索。因此也没什么好书。
</p>
<hr>
<dl><dt>zun</dt>
<dd>全都是反复试验。于是，逐渐搞明白了。我最初是从C语言开始的。但是，完全搞不懂。最先接触的是TurboC<sup>7</sup>这点可能不太好。</dd></dl>
<dl><dt>出水</dt>
<dd>咦，咦，咦，请等一下。TurboC不是不错吗。</dd></dl>
<dl><dt>zun</dt>
<dd>因为啊，用TurboC制作，即便是什么也没有写的程序不也会出来一个很大的可执行文件吗。于是，我非常在意那一点……。所以，我学习了汇编<sup>8</sup>，感觉这个更好理解。</dd></dl>
<dl><dt>出水</dt>
<dd>啊，去那边了啊。</dd></dl>
<dl><dt>zun</dt>
<dd>最初是用C语言写的，后来开始使用汇编，到了第5作的时候基本上都成了汇编。</dd></dl>
<dl><dt>出水</dt>
<dd>啊~是这样啊。</dd></dl>
<dl><dt>zun</dt>
<dd>这是非常有意思的。写子弹的时候只用了两种颜色，却使用了自修改代码<sup>9</sup>。</dd></dl>
<dl><dt>出水</dt>
<dd>使用自修改代码了吗。那可真厉害。</dd></dl>
<dl><dt>zun</dt>
<dd>使用自修改代码会出现各种问题。现在做不到了~。<br>作为当时提高了这种技术的结果，它就成为卖点了。现在就不会这样子了。3D的话会有漂亮的渲染技术在里面，但大家都已经司空见惯了……。</dd></dl>
<dl><dt>出水</dt>
<dd>是啊~。最近的游戏画面都非常漂亮，但不会再像以前那样惊讶了。</dd></dl>
<dl><dt>zun</dt>
<dd>在幕后却有着惊人的技术。过去自阴影<sup>10</sup>之类的是难以想象的，现在却都普普通通地在做。</dd></dl>
<dl><dt>出水</dt>
<dd>自阴影，变得简单了呢~。只需要在引擎的选项里面点几下。</dd></dl>
<dl><dt>zun</dt>
<dd>但是，这也是因为有着前人的智慧。PS2上出三国无双的时候，没有一个人能效仿他们在游戏中出现如此多的多边形模型。所以这就成了卖点。</dd></dl>
<dl><dt>出水</dt>
<dd>那个真是厉害啊。</dd></dl>
<hr>
<div class="poem">
<p><sup>7</sup>Borland制作的C语言编译器。在当时由于能够高速编译、生成高速运行的程序，该编译器广受好评。<br>
<sup>8</sup>和C语言相比更接近于机器的语言。虽然写出来的程序很难阅读，但可以写出比C语言效率更高的程序。<br>
<sup>9</sup>让程序修改自己的代码的技巧。详细后述。<br>
<sup>10</sup>阴影（shadow）可以投射在多边形模型自身上的功能。和通常的阴影比起来相当麻烦。
</p>
</div>
<hr>
<dl><dt>zun</dt>
<dd>再古老一点，最终幻想出在SFC上的时候，画面是其他公司难以想象地精美。明明色彩数很少，却有渐变色的窗口。那个太厉害了。那个本来是难以实现的，是利用水平消隐<sup>11</sup>硬做出来的。</dd></dl>
<dl><dt>出水</dt>
<dd>啊~，那是那么做出来的啊。</dd></dl>
<dl><dt>zun</dt>
<dd>但是放到现在这都是理所应当的了。现在说到窗口就是渐变色的。技术是卖点，虽然现在很难实现了，但是卖点本身却更好做了。如今，游戏都是乱七八糟的状态，程序和图像分开了。我不认为这是件好事。游戏就是游戏。最终负责人可能会分成几个人，但制作的时候可不能分开。这么做就能成为卖点了。只要制作有一体感的游戏就可以了。<br>如果不这样做的话游戏业界就那个了，所以我对今后有些不安。<br>E3<sup>12</sup>也不怎么成为话题。</dd></dl>
<dl><dt>出水</dt>
<dd>确实欠缺一种热情呢。也有家用机游戏都转向社交游戏了的原因。</dd></dl>
<dl><dt>zun</dt>
<dd>但是，我也不能说我讨厌社交游戏呢。卖不出去可不行，卖得出去就说明玩家都期待这种游戏，但我是不想制作的。<br>我觉得游戏是文化。虽然过去人们都说和小说比起来漫画根本算不上文化，但我认为现在漫画也是文化了。游戏也一样，我想社交游戏也是这样，但是它不妙的地方是和钱联系在一起。和柏青哥没什么区别。<br>社交游戏出现在游戏业界会让人觉得“原来那也是游戏啊”。如果人们开始限制社交游戏，对整个游戏业界来说也是有害的吧，我比较讨厌这一点。<br>游戏没能成为文化是没有公共机关设立奖项。现存的奖项都是某个企业私自设立的，关系到企业自身的宣传，作为奖项来说没什么意义。</dd></dl>
<dl><dt>出水</dt>
<dd>确实按照现在这样子游戏业界很有可能会灭亡呢。</dd></dl>
<dl><dt>zun</dt>
<dd>同人游戏都转而成了社交游戏，或者同人游戏被人们弃而不顾，被人们说成是普通的过时游戏，我不愿去想象这种事。</dd></dl>
<dl><dt>出水</dt>
<dd>虽然由于iPhone，人们更容易制作小规模的游戏了。</dd></dl>
<dl><dt>zun</dt>
<dd>用户也不会买啊。</dd></dl>
<hr>
<div class="poem">
<p><sup>11</sup>水平消隐间隔。详细后述。<br>
<sup>12</sup>Electronic Entertainment Expo的通称。在美国举办的世界最大的游戏展。
</p>
</div>
<hr>
<dl><dt>出水</dt>
<dd>和先花的85日元比起来后来花的3000日元<sup>13</sup>更好花呢。</dd></dl>
<dl><dt>zun</dt>
<dd>我也讨厌这种模式。会写免费的人都是些令人讨厌的人，再没有比免费更贵的东西了。故意写免费就说明这是收费的吧，我是这么想。并不是因为收钱，而是因为想要骗人才让我讨厌，总感觉那些人都心术不正。</dd></dl>
<p>我觉得把开发时的开销全都强加于玩家身上都可以。
</p>
<dl><dt>出水</dt>
<dd>从现状来看那是很难的。</dd></dl>
<dl><dt>zun</dt>
<dd>没错没错，所以我总说，还是同人游戏好。又便宜。也不用花额外的钱。大家要是都这么想就好了。</dd></dl>
<dl><dt>zun</dt>
<dd>啊，请再来一杯啤酒。</dd></dl>
<h3><span id=".E6.B8.B8.E6.88.8F.E7.9A.84.E5.88.B6.E4.BD.9C.E6.96.B9.E6.B3.95"></span><span class="mw-headline" id="游戏的制作方法">游戏的制作方法</span></h3>
<dl><dt>zun</dt>
<dd>对我来说，无论是制作程序还是绘画还是音乐，都没有一个一个做的感觉。我想制作的是游戏。因为制作游戏需要，所以我会编程也会画画，还会创作音乐。我还会写剧本。这些都是必要的。那么，要是有人问什么是制作游戏，我会说“不就是企划吗”。</dd></dl>
<dl><dt>出水</dt>
<dd>企划！</dd></dl>
<dl><dt>zun</dt>
<dd>虽然我说得可能有点抽象，游戏就是大家觉得好玩的东西。那不就是企划吗。大家都需要成为制作人。</dd></dl>
<dl><dt>出水</dt>
<dd>需要综合地看游戏。</dd></dl>
<dl><dt>zun</dt>
<dd>但是大概制作同人游戏的人都是以自我为中心的。感觉都会想，我的游戏是才是最好的。</dd></dl>
<dl><dt>出水</dt>
<dd>怎么说呢，我觉得某种程度上那个要素是必需的……。</dd></dl>
<dl><dt>zun</dt>
<dd>尤其是在年轻的时候，去想自己要制作些什么，为了制作那个需要些什么。技术渐渐地就会掌握。然后，你只需尽力而为。反正无论花多长时间也未必能制作出一个令自己满意的东西，那样的话还不如能出多少是多少，这是我的想法。</dd></dl>
<dl><dt>出水</dt>
<dd>原来如此。</dd></dl>
<dl><dt>zun</dt>
<dd>过去有很多未完成的大作呢。不知出了多少个体验版。</dd></dl>
<dl><dt>出水</dt>
<dd>呜哇~，对一部分人来说那可是很不好听的话啊。（笑）</dd></dl>
<hr>
<p><sup>13</sup>课金的最小单位。什么，没那么多？是吗？
</p>
<hr>
<dl><dt>zun</dt>
<dd>从制作者本人的角度来看，一定是因为自己不满意才说是体验版的吧。但是，如果截止日期已经到了，直接当成是成品就好了。对我来说，这是成长的阶梯。<br>所以，我对于已经完成的东西没什么执着。 不能总是看着过去制作的东西，说哪个哪个制作得好。</dd></dl>
<dl><dt>出水</dt>
<dd>人们都说制作了很多东西的人基本上都不会对过去的作品感兴趣。</dd></dl>
<dl><dt>zun</dt>
<dd>想要享受过去的故事，就应该和朋友聚在一起时说“好怀念啊~”。这和“过去更好”这样的吹嘘不同。不如说“那时真辛苦啊~，真快乐啊~”更有趣。要想能做到这样的事情，年轻的时候就一定要多做点事情。如果总是说“自己还不行~”，就连享受回忆也做不到了。</dd></dl>
<dl><dt>出水</dt>
<dd>是啊，万事贵在挑战。</dd></dl>
<dl><dt>zun</dt>
<dd>学习探讨会最近也很流行，要我说的话，很多人都以在那里发表游戏为目的了。我觉得制作游戏才应该是主要的。当然，在那种地方发表作品也很令人愉快，但不能让它成为目的。</dd></dl>
<dl><dt>出水</dt>
<dd>呃……那个对于一部分人来说也是不太好听的话……。呃~，啊~，杯子有点空了呢~。</dd></dl>
<dl><dt>zun</dt>
<dd>是啊~，接下来喝点什么呢~。</dd></dl>
<h3><span id=".E6.87.92.E6.B4.8B.E6.B4.8B.E9.85.92.E6.A1.8C.E9.97.B2.E8.81.8A"></span><span class="mw-headline" id="懒洋洋酒桌闲聊">懒洋洋酒桌闲聊</span></h3>
<dl><dt>zun</dt>
<dd>（看着菜单）我喜欢贝类。我喜欢把扇贝晒成干或者烤着吃。</dd></dl>
<dl><dt>出水</dt>
<dd>我虽然不能喝酒，但因为我喜欢吃下酒菜，所以我总吃扇贝干。毕竟我是在岛屿上长大的。</dd></dl>
<dl><dt>zun</dt>
<dd>海真好啊~，虽然我是山里长大的，但山野菜也不怎么好吃啊~。</dd></dl>
<dl><dt>出水</dt>
<dd>我倒是听说零余子很好吃。</dd></dl>
<dl><dt>zun</dt>
<dd>零余子没什么特别的。好吃的应该是楤木芽，做成天妇罗很好吃。那个油比较多，还有点苦味……。<br>不过，还有比那个更好吃的山野菜……山尖子！看起来像蜂斗菜，吃起来像土当归。特别爽口，非常好吃。爽口的蜂斗菜。</dd></dl>
<dl><dt>出水</dt>
<dd>山野菜……虽然不知道算不算山野菜，但我喜欢芹菜。</dd></dl>
<dl><dt>zun</dt>
<dd>芹菜很好啊。我喜欢芹菜。芹菜的叶子很有芹菜的感觉，特别好吃。</dd></dl>
<dl><dt>出水</dt>
<dd>说到叶子，芹菜叶的佃煮很好吃。虽然因为是家庭料理所以在店里很少见。</dd></dl>
<dl><dt>zun</dt>
<dd>佃煮！好想吃吃看啊~，芹菜和酒特别相配。</dd></dl>
<dl><dt>出水</dt>
<dd>是吗~，虽然芹菜个性很强，但也下酒吗？</dd></dl>
<dl><dt>zun</dt>
<dd>去酒馆基本上都能看到腌芹菜~。很配啤酒。虽然烧酒和清酒也可以。威士忌估计就不行了~。威士忌的香气太浓郁了。所以很不适合具有香气的食物……是啊~，如果是甜的或者是熏制的东西就很好。葡萄干非常配威士忌。</dd></dl>
<dl><dt>出水</dt>
<dd>确实，这是在酒吧常见的料理。其他的话……还有奶酪之类的……。</dd></dl>
<dl><dt>zun</dt>
<dd>奶酪的话和威士忌比起来……更适合红酒吧~。奶酪有股霉味。而红酒也有股霉味。但是，这种霉味很棒。同种类型的放在一起就会很不错。<br>啤酒绝对不能配甜的东西，不就是因为啤酒不甜吗。所以，一旦吃了甜东西之后啤酒的苦涩就会被突出，所以不太好。酒精有种可以将味道放大的性质。所以，同种类型的就很配了。<br>清酒是甜酒，所以和甜的东西很配。因为清酒是香气较淡的酒，所以和什么东西都配。它是万能的。一边吃米饭一边喝清酒也是可以的。我平时就这么干。一边吃咸的一边喝清酒也不错。<br>等等 这完全是酒的话题了吧~。说这些东西真的好么。（笑）</dd></dl>
<dl><dt>出水</dt>
<dd>怎么不好了。（笑）</dd></dl>
<h3><span id=".E5.85.B3.E4.BA.8E.E9.9F.B3.E4.B9.90"></span><span class="mw-headline" id="关于音乐">关于音乐</span></h3>
<dl><dt>出水</dt>
<dd>说起来，有时候光听音乐就能知道“这是ZUN先生的曲子！”……。</dd></dl>
<dl><dt>zun</dt>
<dd>我也是。（笑）而且，有时候那还不是我的曲子。有时听着CD，也会觉得“这不是我的曲子吗？”等等。</dd></dl>
<dl><dt>出水</dt>
<dd>会被加上野生的zun的标签的那种感觉。</dd></dl>
<dl><dt>zun</dt>
<dd>不过，这不是我自满，而是说明了我创作的东西就是如此固定。</dd></dl>
<dl><dt>出水</dt>
<dd>那是故意的吗？</dd></dl>
<dl><dt>zun</dt>
<dd>我没那么精明。<br>不过，如果有个人说自己会画各种画，我想我不会拜托他画什么东西。我拜托只是因为我中意那个人的画。音乐也是一样的。要说什么音乐都会创作的全能的人具不具有魅力……。不，我最近反而感觉那样更好。（笑）<br>即便如此，我觉得我也是在进化的。</dd></dl>
<dl><dt>出水</dt>
<dd>觉得自己喜欢的曲子就是自己创作的曲子。</dd></dl>
<dl><dt>zun</dt>
<dd>去想“自己还需要做好多事情”，就是自己的心情跌入低谷的时候。摆脱它的方法，就是想着「不必会做很多事情，自己只能做这个」去做事吧。</dd></dl>
<dl><dt>出水</dt>
<dd>我也觉得我是吊死在编程这一棵树上了……。</dd></dl>
<dl><dt>zun</dt>
<dd>音乐和编程兼容性很好的。</dd></dl>
<dl><dt>出水</dt>
<dd>是吗！</dd></dl>
<dl><dt>zun</dt>
<dd>演奏是别的能力了，但是作曲和编程没什么区别。不如说因为都是数字，比编程还轻松。MML<sup>14</sup>不也是代码吗。一边想象成品一边制作这一点和编程没什么区别。</dd></dl>
<dl><dt>出水</dt>
<dd>说到MML，FM音源<sup>15</sup>的音色很难<sup>16</sup>呢。</dd></dl>
<dl><dt>zun</dt>
<dd>音色很容易会养成习惯。只使用自己喜欢的音色。于是就会有使用这个音色的是谁谁谁这种说法。最终每个人使用的音色都会在某种程度上固定下来。有高音的对游戏来说很容易炒热气氛。因为不是真实的音色，既能让人轻松地听出旋律，又有冲击力的音比较好用。<br>不过，这也是FM音源时代的事了。现在已经不会从音色作曲了。偶尔也想出一些FM音源的曲子。但是，没有发表的地方。</dd></dl>
<dl><dt>出水</dt>
<dd>希望您能出CD呢。</dd></dl>
<dl><dt>zun</dt>
<dd>填满一张CD太麻烦了。而且，我也不想写MML，都是用Recomposer<sup id="cite_ref-1" class="reference"><a href="#cite_note-1">1</a></sup>制作的。</dd></dl>
<dl><dt>出水</dt>
<dd>那不就是MIDI了吗！</dd></dl>
<dl><dt>zun</dt>
<dd>MIDI更轻松啊。虽然现在愈发轻松了。现在就是暧昧地弹一弹，适当地作作曲的感觉。</dd></dl>
<dl><dt>zun</dt>
<dd>嗯~，差不多来点清酒吧。</dd></dl>
<h3><span id=".E5.BC.80.E5.A7.8B.E5.88.B6.E4.BD.9C.E5.90.8C.E4.BA.BA.E6.B8.B8.E6.88.8F.E4.B9.8B.E5.89.8D"></span><span class="mw-headline" id="开始制作同人游戏之前">开始制作同人游戏之前</span></h3>
<dl><dt>zun</dt>
<dd>偶尔有年轻人会来找我。说想制作同人游戏。</dd></dl>
<dl><dt>出水</dt>
<dd>啊，确实有呢~。</dd></dl>
<dl><dt>zun</dt>
<dd>于是我想问的就是，为什么想制作的不是游戏而是同人游戏。是因为他们觉得普通的游戏和同人游戏之间有什么差距吗。</dd></dl>
<hr>
<div class="poem">
<p><sup>14</sup>Music Macro Language的缩写。用文本文件来记述音乐的语言。<br>
<sup>15</sup>过去的游戏曲中很常见的，会发出电子音一般声音的音源装置。98的游戏大概都是用这个发出声音的。<br>
<sup>16</sup>制作FM音源的音色是一个凭经验和感觉调整数十个数字的工作。
</p>
</div>
<hr>
<dl><dt>zun</dt>
<dd>果然同人游戏很有魅力吗、<br>现在同人游戏给人的感觉和我想的应该不太一样吧。对于年轻人来说现在的同人游戏可能更有魅力。为什么说有魅力，是因为看起来很好玩。<br>如果是商业，就会有制作的人出来说一些似乎很了不起的话，或者只说些类似“接下来的计划是这个”之类的话。而且，这种人还是不怎么参与制作的人。这种业界不会让人觉得会有趣的。</dd></dl>
<dl><dt>出水</dt>
<dd>啊，确实如此~。不怎么参与的人在抛头露面。（笑）</dd></dl>
<dl><dt>zun</dt>
<dd>如果是因为这个而觉得同人游戏很有魅力，那我就需要给他们一个答案。我觉得我需要全面地表现同人游戏很欢乐这一点。我觉得可以接二连三地表现我们是在像笨蛋一样努力制作的。如果不表达这么做很有趣，同人游戏的存在意义可能就会消失了。</dd></dl>
<dl><dt>出水</dt>
<dd>存在意义会消失这点很令人害怕呢。</dd></dl>
<dl><dt>zun</dt>
<dd>是，关于存在意义的话题，我头一次觉得同人软件要完蛋了是SIMPLE系列出来的时候。刚开始都是些围棋或者将棋之类的还好，到后来什么奇怪的东西都有了。而且只需1500日元。我没法把价格设置得比那个更高了，所以直到现在（东方）也是1000日元。</dd></dl>
<dl><dt>出水</dt>
<dd>说起SIMPLE系列，地球防卫军<sup>17</sup>之类的很好玩呢。</dd></dl>
<dl><dt>zun</dt>
<dd>是啊，地球防卫军说是能大家一起兴高采烈地玩，但是不行啊。同人游戏这一边需要有危机感。比如说自己的定位该怎么办之类的。</dd></dl>
<dl><dt>出水</dt>
<dd>如果到了同人该干的事情都被商业拿去干了的时代，那可就辛酸了。</dd></dl>
<dl><dt>zun</dt>
<dd>虽然也可能有因为同人卖得好所以转向商业了这种趋势。</dd></dl>
<dl><dt>出水</dt>
<dd>确实同人卖得好的人基本上都去商业那边了。</dd></dl>
<dl><dt>zun</dt>
<dd>就我没弄商业。我最初开始同人单单是因为想制作游戏。随后我超越了同人这个框架走向了商业，但我觉得我所期望的游戏的制作方式不是这样的。因此，我回到了同人游戏。我是回归组的。</dd></dl>
<dl><dt>出水</dt>
<dd>回归组。（笑）</dd></dl>
<dl><dt>zun</dt>
<dd>所以，我对商业的看法可能和其他人不一样。同人软件要是像商业那样去制作是没有意义的，我需要向大家展示这一点。这就是现在的我。</dd></dl>
<p>　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　（终）
</p>
<hr>
<sup>17</sup>THE地球防卫军。以巨大的敌人成片出现为卖点的游戏。</td><td width="200px"><div class="thumb infobox noclear" style="width:200px; margin:0 3px 0 1em;">
<div class="thumbinner" style="float:right">
<div class="thumbimage" style="margin: 0; padding: 0;"><a href="./文件-ZUN（游戏的修罗场61）.jpg.md" class="image" title="游戏的修罗场61"><img alt="游戏的修罗场61" src="https://upload.thwiki.cc/thumb/8/81/ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA61%EF%BC%89.jpg/195px-ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA61%EF%BC%89.jpg" decoding="async" loading="lazy" width="195" height="246" srcset="https://upload.thwiki.cc/thumb/8/81/ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA61%EF%BC%89.jpg/293px-ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA61%EF%BC%89.jpg 1.5x, https://upload.thwiki.cc/thumb/8/81/ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA61%EF%BC%89.jpg/390px-ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA61%EF%BC%89.jpg 2x" data-file-width="2412" data-file-height="3040"></a></div><div class="thumbcaption" style="margin: 0 0 2px; padding: 0; line-height: 1.1em;">P001</div><div class="thumbimage" style="margin: 0; padding: 0;"><a href="./文件-ZUN（游戏的修罗场62）.jpg.md" class="image" title="游戏的修罗场62"><img alt="游戏的修罗场62" src="https://upload.thwiki.cc/thumb/0/09/ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA62%EF%BC%89.jpg/195px-ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA62%EF%BC%89.jpg" decoding="async" loading="lazy" width="195" height="232" srcset="https://upload.thwiki.cc/thumb/0/09/ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA62%EF%BC%89.jpg/293px-ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA62%EF%BC%89.jpg 1.5x, https://upload.thwiki.cc/thumb/0/09/ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA62%EF%BC%89.jpg/390px-ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA62%EF%BC%89.jpg 2x" data-file-width="2552" data-file-height="3040"></a></div><div class="thumbcaption" style="margin: 0 0 2px; padding: 0; line-height: 1.1em;">P002</div><div class="thumbimage" style="margin: 0; padding: 0;"><a href="./文件-ZUN（游戏的修罗场63）.jpg.md" class="image" title="游戏的修罗场63"><img alt="游戏的修罗场63" src="https://upload.thwiki.cc/thumb/3/36/ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA63%EF%BC%89.jpg/195px-ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA63%EF%BC%89.jpg" decoding="async" loading="lazy" width="195" height="233" srcset="https://upload.thwiki.cc/thumb/3/36/ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA63%EF%BC%89.jpg/293px-ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA63%EF%BC%89.jpg 1.5x, https://upload.thwiki.cc/thumb/3/36/ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA63%EF%BC%89.jpg/390px-ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA63%EF%BC%89.jpg 2x" data-file-width="2552" data-file-height="3048"></a></div><div class="thumbcaption" style="margin: 0 0 2px; padding: 0; line-height: 1.1em;">P003</div><div class="thumbimage" style="margin: 0; padding: 0;"><a href="./文件-ZUN（游戏的修罗场64）.jpg.md" class="image" title="游戏的修罗场64"><img alt="游戏的修罗场64" src="https://upload.thwiki.cc/thumb/3/34/ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA64%EF%BC%89.jpg/195px-ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA64%EF%BC%89.jpg" decoding="async" loading="lazy" width="195" height="233" srcset="https://upload.thwiki.cc/thumb/3/34/ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA64%EF%BC%89.jpg/293px-ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA64%EF%BC%89.jpg 1.5x, https://upload.thwiki.cc/thumb/3/34/ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA64%EF%BC%89.jpg/390px-ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA64%EF%BC%89.jpg 2x" data-file-width="2552" data-file-height="3044"></a></div><div class="thumbcaption" style="margin: 0 0 2px; padding: 0; line-height: 1.1em;">P004</div><div class="thumbimage" style="margin: 0; padding: 0;"><a href="./文件-ZUN（游戏的修罗场65）.jpg.md" class="image" title="游戏的修罗场65"><img alt="游戏的修罗场65" src="https://upload.thwiki.cc/thumb/b/b5/ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA65%EF%BC%89.jpg/195px-ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA65%EF%BC%89.jpg" decoding="async" loading="lazy" width="195" height="256" srcset="https://upload.thwiki.cc/thumb/b/b5/ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA65%EF%BC%89.jpg/293px-ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA65%EF%BC%89.jpg 1.5x, https://upload.thwiki.cc/thumb/b/b5/ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA65%EF%BC%89.jpg/390px-ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA65%EF%BC%89.jpg 2x" data-file-width="2316" data-file-height="3040"></a></div><div class="thumbcaption" style="margin: 0 0 2px; padding: 0; line-height: 1.1em;">P005</div><div class="thumbimage" style="margin: 0; padding: 0;"><a href="./文件-ZUN（游戏的修罗场66）.jpg.md" class="image" title="游戏的修罗场66"><img alt="游戏的修罗场66" src="https://upload.thwiki.cc/thumb/6/68/ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA66%EF%BC%89.jpg/195px-ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA66%EF%BC%89.jpg" decoding="async" loading="lazy" width="195" height="232" srcset="https://upload.thwiki.cc/thumb/6/68/ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA66%EF%BC%89.jpg/293px-ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA66%EF%BC%89.jpg 1.5x, https://upload.thwiki.cc/thumb/6/68/ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA66%EF%BC%89.jpg/390px-ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA66%EF%BC%89.jpg 2x" data-file-width="2552" data-file-height="3040"></a></div><div class="thumbcaption" style="margin: 0 0 2px; padding: 0; line-height: 1.1em;">P006</div><div class="thumbimage" style="margin: 0; padding: 0;"><a href="./文件-ZUN（游戏的修罗场67）.jpg.md" class="image" title="游戏的修罗场67"><img alt="游戏的修罗场67" src="https://upload.thwiki.cc/thumb/3/3c/ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA67%EF%BC%89.jpg/195px-ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA67%EF%BC%89.jpg" decoding="async" loading="lazy" width="195" height="247" srcset="https://upload.thwiki.cc/thumb/3/3c/ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA67%EF%BC%89.jpg/293px-ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA67%EF%BC%89.jpg 1.5x, https://upload.thwiki.cc/thumb/3/3c/ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA67%EF%BC%89.jpg/390px-ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA67%EF%BC%89.jpg 2x" data-file-width="2400" data-file-height="3044"></a></div><div class="thumbcaption" style="margin: 0 0 2px; padding: 0; line-height: 1.1em;">P007</div><div class="thumbimage" style="margin: 0; padding: 0;"><a href="./文件-ZUN（游戏的修罗场68）.jpg.md" class="image" title="游戏的修罗场68"><img alt="游戏的修罗场68" src="https://upload.thwiki.cc/thumb/0/00/ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA68%EF%BC%89.jpg/195px-ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA68%EF%BC%89.jpg" decoding="async" loading="lazy" width="195" height="232" srcset="https://upload.thwiki.cc/thumb/0/00/ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA68%EF%BC%89.jpg/293px-ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA68%EF%BC%89.jpg 1.5x, https://upload.thwiki.cc/thumb/0/00/ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA68%EF%BC%89.jpg/390px-ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA68%EF%BC%89.jpg 2x" data-file-width="2552" data-file-height="3040"></a></div><div class="thumbcaption" style="margin: 0 0 2px; padding: 0; line-height: 1.1em;">P008</div><div class="thumbimage" style="margin: 0; padding: 0;"><a href="./文件-ZUN（游戏的修罗场69）.jpg.md" class="image" title="游戏的修罗场69"><img alt="游戏的修罗场69" src="https://upload.thwiki.cc/thumb/9/95/ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA69%EF%BC%89.jpg/195px-ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA69%EF%BC%89.jpg" decoding="async" loading="lazy" width="195" height="251" srcset="https://upload.thwiki.cc/thumb/9/95/ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA69%EF%BC%89.jpg/293px-ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA69%EF%BC%89.jpg 1.5x, https://upload.thwiki.cc/thumb/9/95/ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA69%EF%BC%89.jpg/390px-ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA69%EF%BC%89.jpg 2x" data-file-width="2364" data-file-height="3044"></a></div><div class="thumbcaption" style="margin: 0 0 2px; padding: 0; line-height: 1.1em;">P009</div><div class="thumbimage" style="margin: 0; padding: 0;"><a href="./文件-ZUN（游戏的修罗场610）.jpg.md" class="image" title="游戏的修罗场610"><img alt="游戏的修罗场610" src="https://upload.thwiki.cc/thumb/9/9f/ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA610%EF%BC%89.jpg/195px-ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA610%EF%BC%89.jpg" decoding="async" loading="lazy" width="195" height="254" srcset="https://upload.thwiki.cc/thumb/9/9f/ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA610%EF%BC%89.jpg/293px-ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA610%EF%BC%89.jpg 1.5x, https://upload.thwiki.cc/thumb/9/9f/ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA610%EF%BC%89.jpg/390px-ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA610%EF%BC%89.jpg 2x" data-file-width="2340" data-file-height="3048"></a></div><div class="thumbcaption" style="margin: 0 0 2px; padding: 0; line-height: 1.1em;">P010</div><div class="thumbimage" style="margin: 0; padding: 0;"><a href="./文件-ZUN（游戏的修罗场611）.jpg.md" class="image" title="游戏的修罗场611"><img alt="游戏的修罗场611" src="https://upload.thwiki.cc/thumb/e/e7/ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA611%EF%BC%89.jpg/195px-ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA611%EF%BC%89.jpg" decoding="async" loading="lazy" width="195" height="246" srcset="https://upload.thwiki.cc/thumb/e/e7/ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA611%EF%BC%89.jpg/293px-ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA611%EF%BC%89.jpg 1.5x, https://upload.thwiki.cc/thumb/e/e7/ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA611%EF%BC%89.jpg/390px-ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA611%EF%BC%89.jpg 2x" data-file-width="2416" data-file-height="3044"></a></div><div class="thumbcaption" style="margin: 0 0 2px; padding: 0; line-height: 1.1em;">P011</div><div class="thumbimage" style="margin: 0; padding: 0;"><a href="./文件-ZUN（游戏的修罗场612）.jpg.md" class="image" title="游戏的修罗场612"><img alt="游戏的修罗场612" src="https://upload.thwiki.cc/thumb/2/24/ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA612%EF%BC%89.jpg/195px-ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA612%EF%BC%89.jpg" decoding="async" loading="lazy" width="195" height="259" srcset="https://upload.thwiki.cc/thumb/2/24/ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA612%EF%BC%89.jpg/293px-ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA612%EF%BC%89.jpg 1.5x, https://upload.thwiki.cc/thumb/2/24/ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA612%EF%BC%89.jpg/390px-ZUN%EF%BC%88%E6%B8%B8%E6%88%8F%E7%9A%84%E4%BF%AE%E7%BD%97%E5%9C%BA612%EF%BC%89.jpg 2x" data-file-width="2296" data-file-height="3048"></a></div><div class="thumbcaption" style="margin: 0 0 2px; padding: 0; line-height: 1.1em;">P012</div>
</div>
</div></td></tr></tbody></table>



[^cite_note-1]: PC98的音序器的一种





---

此文档由 [THBWiki-Markdown-Builder](https://github.com/Delsin-Yu/THBWiki-Markdown-Builder) 构建。

文档中的所有内容除特殊注明外，均在 [**知识共享(Creative Commons) 署名-非商业性使用-相同方式共享 3.0 协议**](https://creativecommons.org/licenses/by-sa/3.0/deed.zh-hans) 下提供，附加条款亦可能应用。

引用类型与其他类型作品版权归原作者所有，如有作者授权则遵照授权协议使用。

详细请查阅 [THBWiki：免责声明](https://thbwiki.cc/THBWiki:%E5%85%8D%E8%B4%A3%E5%A3%B0%E6%98%8E)。

