# 游戏攻略/STG常用工具/VsyncPatch/vpatch_instructions

<!-- source html: G:\repos\THBWiki-Markdown-Builder\THBWikiMarkdown\Temp\main\6\62\ns0%3A%E6%B8%B8%E6%88%8F%E6%94%BB%E7%95%A5%2FSTG%E5%B8%B8%E7%94%A8%E5%B7%A5%E5%85%B7%2FVsyncPatch%2Fvpatch_instructions.html -->

使用了翻译表的页面

- 纯文本格式（Wiki系统将从本页面下方的翻译表中自动获取内容并拼接成纯文本格式的页面）

: [日文版](http://omake.thwiki.cc/translate.php?u=游戏攻略/STG常用工具/VsyncPatch/vpatch_instructions&amp;t=ja)
: [汉化版](http://omake.thwiki.cc/translate.php?u=游戏攻略/STG常用工具/VsyncPatch/vpatch_instructions&amp;t=zh)

  
  

  


<table><tbody><tr class="tt-content" id="=-1" data-pos="&#91;&quot;=&quot;,1&#93;"><td class="tt-ja" lang="ja"><div class="poem">VsyncPatch</div></td><td class="tt-zh" lang="zh"><div class="poem">VsyncPatch<br></div></td></tr><tr class="tt-content" id="=-2" data-pos="&#91;&quot;=&quot;,2&#93;"><td class="tt-ja" lang="ja"><div class="poem">With every newly installed patch, always make a backup copy of your score.dat files in case something weird ever happens. <br>This is just a general rule. While I don't think this progam has ever caused any data (scores, history, etc) to corrupt or reset, <br>It's always a good idea to keep a backup in case it does happen by other means.</div></td><td class="tt-zh" lang="zh"><div class="poem">每次新安装补丁，请务必备份 <b>score.dat</b> 文件<sup id="cite_ref-1" class="reference"><a href="#cite_note-1">1</a></sup>，以防发生什么玄学问题。<br>这只是（安装游戏补丁的）一般准则。虽然我认为本程序不会导致任何数据（分数、历史等）损坏或重置，<br>但还是建议保留备份，万一你存档真炸了呢。<br></div></td></tr><tr class="tt-content" id="=-3" data-pos="&#91;&quot;=&quot;,3&#93;"><td class="tt-ja" lang="ja"><div class="poem">Modify the [Window] parameters to suit your liking. You can run it windowed, and if so you can control the window width/height<br>as well as the position it appears on your screen and such. Pretty self-explanatory.</div></td><td class="tt-zh" lang="zh"><div class="poem">你可以按照自己的喜好修改 [Window] 下的参数。您可以用窗口模式运行游戏，并控制窗口的宽度/高度<br>以及它出现在屏幕上的位置等。（配置文件中的参数）见名知意。<br></div></td></tr><tr class="tt-content" id="=-4" data-pos="&#91;&quot;=&quot;,4&#93;"><td class="tt-ja" lang="ja"><div class="poem">There are patches for some games in both revision 4 and 7. Use the latest version of the patch for each game.</div></td><td class="tt-zh" lang="zh"><div class="poem">有些游戏同时被rev4和rev7支持，用最新的补丁即可。<br></div></td></tr><tr class="tt-content" id="=-5" data-pos="&#91;&quot;=&quot;,5&#93;"><td class="tt-ja" lang="ja"><div class="poem">Leave a copy of vpatch.exe, vpatch.ini and the corresponding dll file in your game folder.<br>Do not have more than one vpatch_th**.dll file in one folder, or else a conflict might occur and the game won't launch.</div></td><td class="tt-zh" lang="zh"><div class="poem">在你的游戏文件夹中保留一份 vpatch.exe、vpatch.ini 和相应的 dll 文件。<br>一个文件夹中的vpatch_th**.dll文件不要超过一个，否则可能会发生冲突，进而导致无法启动游戏。<br></div></td></tr><tr class="tt-content" id="=-6" data-pos="&#91;&quot;=&quot;,6&#93;"><td class="tt-ja" lang="ja"><div class="poem">Rename each individual exe file to th**.exe, where the stars are the game number, except for EoSD and Uwabami Breakers, <br>which must be named 東方紅魔郷.exe and alcostg.exe, respectively. Naturally this will be true by default, but if you want <br>to run the english-patched game then you must rename the executable from th07e to th07, and so on.<br>EoSD must also be launched using AppLocale / Locale Emulator, or by setting your system to a japanese locale.</div></td><td class="tt-zh" lang="zh"><div class="poem">将每个游戏主程序文件分别重命名为th**.exe，星号是游戏编号，除了红魔乡和黄昏酒场，<br>它们必须分别命名为 東方紅魔郷.exe 和 alcostg.exe。通常情况下它们本来就是这样，但如果你想<br>运行英文版游戏<sup id="cite_ref-2" class="reference"><a href="#cite_note-2">2</a></sup>，你需要将th07e重命名为（标准形式的）th07，其他的同理。<br>红魔乡必须使用AppLocale / Locale（这样的转区工具）启动，或者将你的系统语言（区域）改为日语<sup id="cite_ref-3" class="reference"><a href="#cite_note-3">3</a></sup>。<br></div></td></tr><tr class="tt-content" id="=-7" data-pos="&#91;&quot;=&quot;,7&#93;"><td class="tt-ja" lang="ja"><div class="poem">Start the game by launching vpatch.exe.</div></td><td class="tt-zh" lang="zh"><div class="poem">启动 vpatch.exe 开始游戏。<br></div></td></tr><tr class="tt-content" id="=-8" data-pos="&#91;&quot;=&quot;,8&#93;"><td class="tt-ja" lang="ja"><div class="poem">Author: swmpLV/75E</div></td><td class="tt-zh" lang="zh"><div class="poem">作者：swmpLV/75E<br></div></td></tr></tbody></table>



[^cite_note-1]: 译者注：此文件在th128之前位于游戏根目录，之后位于C:\Users\用户名\AppData\Roaming\ShanghaiAlice，用于存储玩家数据（如收率等）





---

此文档由 [THBWiki-Markdown-Builder](https://github.com/Delsin-Yu/THBWiki-Markdown-Builder) 构建。

文档中的所有内容除特殊注明外，均在 [**知识共享(Creative Commons) 署名-非商业性使用-相同方式共享 3.0 协议**](https://creativecommons.org/licenses/by-sa/3.0/deed.zh-hans) 下提供，附加条款亦可能应用。

引用类型与其他类型作品版权归原作者所有，如有作者授权则遵照授权协议使用。

详细请查阅 [THBWiki：免责声明](https://thbwiki.cc/THBWiki:%E5%85%8D%E8%B4%A3%E5%A3%B0%E6%98%8E)。

