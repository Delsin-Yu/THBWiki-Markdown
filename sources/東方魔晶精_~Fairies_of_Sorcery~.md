# 東方魔晶精_~Fairies_of_Sorcery~

<!-- source html: G:\repos\THBWiki-Markdown-Builder\THBWikiMarkdown\Temp\main\d\dd\ns0%3A%E6%9D%B1%E6%96%B9%E9%AD%94%E6%99%B6%E7%B2%BE_%7EFairies_of_Sorcery%7E.html -->

2012年9月9日 由 Nono 443  发布的STG同人游戏，可在 Windows 系统上运行，游戏人数为 单人模式，分级为 一般向

本页是关于东方Project  
 **二次创作同人软件 (未找到链接)** 的词条
## 目录

- [1 软件信息](#软件信息)
- [2 游戏介绍](#游戏介绍)
- [3 内容页面](#内容页面)
- [4 评论](#评论)
- [5 视频](#视频)
- [6 下载](#下载)




## 软件信息

<table><tbody><tr><th colspan="3">基本信息</th></tr><tr><td class="cover-artwork-mobile" colspan="2">无封面</td>
</tr><tr><td class="label">名称</td><td colspan="2"> 東方魔晶精 ~Fairies of Sorcery~ </td></tr><tr><td class="label">译名</td><td colspan="2"> 东方魔晶精 ~Fairies of Sorcery~ </td></tr><tr><td class="label">制作方</td><td><a href="/index.php?title=Nono_443&amp;action=edit&amp;redlink=1" class="new" title="Nono 443（页面不存在）">Nono 443</a></td><td class="cover-artwork" rowspan="8" style="min-width:224px;">无封面</td>
</tr><tr><td class="label">首发日期</td><td>2012-09-09</td></tr><tr><td class="label">类型</td><td>游戏</td></tr><tr><td class="label">分级指定</td><td>一般向</td></tr><tr><td class="label">游戏人数</td><td>单人模式</td></tr><tr><td class="label">游戏类型</td><td>STG</td></tr><tr><td class="label">运行平台</td><td>Windows</td></tr><tr><td class="label">语言</td><td>日文</td></tr><tr><td class="label">售价</td><td>免费</td></tr>
<tr><td class="label">官网页面</td><td colspan="2"><a rel="nofollow" class="external free" href="https://twitter.com/nono_shijimi">https://twitter.com/nono_shijimi</a></td></tr></tbody></table>

東方魔晶精 ~Fairies of Sorcery~（同人游戏，Nono 443，2012） - 2012年9月9日 由 Nono 443  发布的STG同人游戏，可在 Windows 系统上运行，游戏人数为 单人模式，分级为 一般向
## 游戏介绍
[](./文件-東方魔晶精_~Fairies_of_Sorcery~菜单界面.jpg.md)  [](./文件-東方魔晶精_~Fairies_of_Sorcery~菜单界面.jpg.md)菜单界面
  
东方魔晶精是弹幕风平台下的一款东方同人stg。
  
  
虽然是新版本的弹幕风游戏，但是优化的不错不太吃配置，一般的机器也没有明显的掉帧，很值得尝试。
  
  
Story模式一共有5个难度，共3面，此外还有extra关卡以及符卡练习模式（但没有任何剧情和对话）。
  
  
最新版本为2013/10/13发布的v1.20a，已经是相当好的成品了。
  
  
值得一提的是，这款游戏是使用弹幕风ph3β6版本新增的“封包”功能做出的第一个完整的游戏脚本。
  

## 内容页面
- [游戏设定](./東方魔晶精_~Fairies_of_Sorcery~-游戏设定.md)
- [系统说明](./東方魔晶精_~Fairies_of_Sorcery~-系统.md)
- [符卡](./東方魔晶精_~Fairies_of_Sorcery~-符卡.md)
- [其他相关资料](./東方魔晶精_~Fairies_of_Sorcery~-其他.md)

## 评论
- 修复double burst模式rep出错的办法：

  
1、记事本打开th_mss\script\th_mashousei\enemy\boss\lib\lib_spellName.dnh  

2、找到
  


<table>

<tbody><tr>
<th>代码
</th></tr>
<tr>
<td><div class="mw-highlight mw-highlight-lang-c mw-content-ltr" dir="ltr"><pre><span></span><span class="k">if</span><span class="p">(</span><span class="n">IsReplay</span><span class="p">){</span><span class="n">chr</span><span class="o">--</span><span class="p">;}</span><span class="w"></span>
<span class="n">let</span><span class="w"> </span><span class="n">Sp_R_Array</span><span class="w"> </span><span class="o">=</span><span class="w"> </span><span class="n">GetAreaCommonData</span><span class="p">(</span><span class="s">&quot;SpellResultArea&quot;</span><span class="p">,</span><span class="w"> </span><span class="n">LastWard_R_Char</span><span class="p">[</span><span class="n">spellNum</span><span class="mi">-1</span><span class="p">],</span><span class="w"> </span><span class="p">[</span><span class="mi">0</span><span class="p">,</span><span class="w"> </span><span class="mi">0</span><span class="p">,</span><span class="w"> </span><span class="mi">0</span><span class="p">,</span><span class="w"> </span><span class="mi">0</span><span class="p">]);</span><span class="w"></span>
<span class="n">let</span><span class="w"> </span><span class="n">got</span><span class="w"> </span><span class="o">=</span><span class="w"> </span><span class="n">Sp_R_Array</span><span class="p">[</span><span class="mi">2</span><span class="p">];</span><span class="w"></span>
<span class="n">let</span><span class="w"> </span><span class="n">chr</span><span class="w"> </span><span class="o">=</span><span class="w"> </span><span class="n">Sp_R_Array</span><span class="p">[</span><span class="mi">3</span><span class="p">]</span><span class="o">+</span><span class="mi">1</span><span class="p">;</span><span class="w"></span>
<span class="n">ObjText_SetText</span><span class="p">(</span><span class="n">objHis</span><span class="p">,</span><span class="w"> </span><span class="s">&quot;History: &quot;</span><span class="w"> </span><span class="o">~</span><span class="w"> </span><span class="n">IntToString</span><span class="p">(</span><span class="n">got</span><span class="p">)</span><span class="w"> </span><span class="o">~</span><span class="w"> </span><span class="s">&quot;/&quot;</span><span class="w"> </span><span class="o">~</span><span class="n">IntToString</span><span class="p">(</span><span class="n">chr</span><span class="p">));</span><span class="w"></span>
</pre></div>
</td></tr></tbody></table>

  
  

  
  
3、替换为
  


<table>

<tbody><tr>
<th>代码
</th></tr>
<tr>
<td><div class="mw-highlight mw-highlight-lang-c mw-content-ltr" dir="ltr"><pre><span></span><span class="n">let</span><span class="w"> </span><span class="n">Sp_R_Array</span><span class="w"> </span><span class="o">=</span><span class="w"> </span><span class="n">GetAreaCommonData</span><span class="p">(</span><span class="s">&quot;SpellResultArea&quot;</span><span class="p">,</span><span class="w"> </span><span class="n">LastWard_R_Char</span><span class="p">[</span><span class="n">spellNum</span><span class="mi">-1</span><span class="p">],</span><span class="w"> </span><span class="p">[</span><span class="mi">0</span><span class="p">,</span><span class="w"> </span><span class="mi">0</span><span class="p">,</span><span class="w"> </span><span class="mi">0</span><span class="p">,</span><span class="w"> </span><span class="mi">0</span><span class="p">]);</span><span class="w"></span>
<span class="n">let</span><span class="w"> </span><span class="n">got</span><span class="w"> </span><span class="o">=</span><span class="w"> </span><span class="n">Sp_R_Array</span><span class="p">[</span><span class="mi">2</span><span class="p">];</span><span class="w"></span>
<span class="n">let</span><span class="w"> </span><span class="n">chr</span><span class="w"> </span><span class="o">=</span><span class="w"> </span><span class="n">Sp_R_Array</span><span class="p">[</span><span class="mi">3</span><span class="p">]</span><span class="o">+</span><span class="mi">1</span><span class="p">;</span><span class="w"></span>
<span class="k">if</span><span class="p">(</span><span class="n">IsReplay</span><span class="p">){</span><span class="n">chr</span><span class="o">--</span><span class="p">;}</span><span class="w"></span>
<span class="n">ObjText_SetText</span><span class="p">(</span><span class="n">objHis</span><span class="p">,</span><span class="w"> </span><span class="s">&quot;History: &quot;</span><span class="w"> </span><span class="o">~</span><span class="w"> </span><span class="n">IntToString</span><span class="p">(</span><span class="n">got</span><span class="p">)</span><span class="w"> </span><span class="o">~</span><span class="w"> </span><span class="s">&quot;/&quot;</span><span class="w"> </span><span class="o">~</span><span class="n">IntToString</span><span class="p">(</span><span class="n">chr</span><span class="p">));</span><span class="w"></span>
</pre></div>
</td></tr></tbody></table>

  
  

  
- 修复符卡练习rep不统计分数的办法：

  
1、记事本打开th_mss\script\th_mashousei\lib\lib_Stage.dnh  

2、找到
  


<table>

<tbody><tr>
<th>代码
</th></tr>
<tr>
<td><code>loop(120){yield;}</code>
</td></tr></tbody></table>

  
  

  
  
3、替换为
  


<table>

<tbody><tr>
<th>代码
</th></tr>
<tr>
<td><div class="mw-highlight mw-highlight-lang-c mw-content-ltr" dir="ltr"><pre><span></span><span class="n">loop</span><span class="p">(</span><span class="mi">60</span><span class="p">){</span><span class="n">yield</span><span class="p">;}</span><span class="w"></span>
<span class="n">SetCommonData</span><span class="p">(</span><span class="s">&quot;FinalScore&quot;</span><span class="p">,</span><span class="w"> </span><span class="nb">true</span><span class="p">);</span><span class="w"></span>
<span class="n">yield</span><span class="p">;</span><span class="w"></span>
<span class="n">AddScore</span><span class="p">(</span><span class="n">GetCommonData</span><span class="p">(</span><span class="s">&quot;Score&quot;</span><span class="p">,</span><span class="w"> </span><span class="mi">0</span><span class="p">));</span><span class="w"></span>
<span class="n">loop</span><span class="p">(</span><span class="mi">59</span><span class="p">){</span><span class="n">yield</span><span class="p">;}</span><span class="w"></span>
</pre></div>
</td></tr></tbody></table>


## 视频
  
请注意：  
 **所有的相关视频地址均为站外链接，本站并不保证其来源的合法性以及链接的有效性和安全性** 
  
  
[Easy打分+EX](https://www.bilibili.com/video/BV1Es411Z7ct)
[EX](http://v.youku.com/v_show/id_XNjcyNDc3OTg0.html)
[DoubleBurst](http://v.youku.com/v_show/id_XNjg4NzM5MDU2.html)
  

## 下载
  
[BulletForge](https://www.bulletforge.org/u/shijimi_nono/p/fairies-of-sorcery/)
[汉化版](http://pan.baidu.com/s/1nuRAeeP)
  





---

此文档由 [THBWiki-Markdown-Builder](https://github.com/Delsin-Yu/THBWiki-Markdown-Builder) 构建。

文档中的所有内容除特殊注明外，均在 [**知识共享(Creative Commons) 署名-非商业性使用-相同方式共享 3.0 协议**](https://creativecommons.org/licenses/by-sa/3.0/deed.zh-hans) 下提供，附加条款亦可能应用。

引用类型与其他类型作品版权归原作者所有，如有作者授权则遵照授权协议使用。

详细请查阅 [THBWiki：免责声明](https://thbwiki.cc/THBWiki:%E5%85%8D%E8%B4%A3%E5%A3%B0%E6%98%8E)。

