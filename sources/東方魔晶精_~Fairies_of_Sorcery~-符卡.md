# 東方魔晶精_~Fairies_of_Sorcery~/符卡

<!-- source html: G:\repos\THBWiki-Markdown-Builder\THBWikiMarkdown\Temp\main\9\9f\ns0%3A%E6%9D%B1%E6%96%B9%E9%AD%94%E6%99%B6%E7%B2%BE_%7EFairies_of_Sorcery%7E%2F%E7%AC%A6%E5%8D%A1.html -->

Nono_443

  
每个敌方符卡都分类于此列表。
  
  
每一个条目包含相关截图、中日文（必要的话会包含英文）、在哪一关出现等。
  

: - [Stage 1 符卡](./東方魔晶精_~Fairies_of_Sorcery~-符卡-Stage_1.md)
- [Stage 2 符卡](./東方魔晶精_~Fairies_of_Sorcery~-符卡-Stage_2.md)
- [Stage 3 符卡](./東方魔晶精_~Fairies_of_Sorcery~-符卡-Stage_3.md)
- [Extra关卡 符卡](./東方魔晶精_~Fairies_of_Sorcery~-符卡-Extra.md)
- [Double Burst模式 符卡](./東方魔晶精_~Fairies_of_Sorcery~-符卡-Double_Burst.md)


  
备注：
 **Double Burst** 符卡为Spell Practice模式下特有，类似于永夜抄Last Word，需要一定条件解锁。
  
  
此模式的符卡练习存rep播放时会出错。
  


<table>

<tbody><tr>
<th>修复double burst模式rep出错的办法：
</th></tr>
<tr>
<td>在文件夹th_mss\script\th_mashousei\enemy\boss\lib中，找到lib_spellName.dnh，使用记事本打开
<p>查找并删除以下内容（注意只有一句代码和以下代码精确匹配）：
</p><p>if(IsReplay){chr--;}
</p><p>let Sp_R_Array = GetAreaCommonData("SpellResultArea", LastWard_R_Char[spellNum-1], [0, 0, 0, 0]);
</p><p>即可修复rep播放弹错。
</p>
</td></tr></tbody></table>






---

此文档由 [THBWiki-Markdown-Builder](https://github.com/Delsin-Yu/THBWiki-Markdown-Builder) 构建。

文档中的所有内容除特殊注明外，均在 [**知识共享(Creative Commons) 署名-非商业性使用-相同方式共享 3.0 协议**](https://creativecommons.org/licenses/by-sa/3.0/deed.zh-hans) 下提供，附加条款亦可能应用。

引用类型与其他类型作品版权归原作者所有，如有作者授权则遵照授权协议使用。

详细请查阅 [THBWiki：免责声明](https://thbwiki.cc/THBWiki:%E5%85%8D%E8%B4%A3%E5%A3%B0%E6%98%8E)。

