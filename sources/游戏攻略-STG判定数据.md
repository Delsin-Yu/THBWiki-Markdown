# 游戏攻略/STG判定数据

<!-- source html: G:\repos\THBWiki-Markdown-Builder\THBWikiMarkdown\Temp\main\1\1c\ns0%3A%E6%B8%B8%E6%88%8F%E6%94%BB%E7%95%A5%2FSTG%E5%88%A4%E5%AE%9A%E6%95%B0%E6%8D%AE.html -->



## 目录

- [1 方形判定](#方形判定)

  - [1.1 敌弹](#敌弹)
  - [1.2 自机](#自机)



- [2 圆形判定](#圆形判定)

  - [2.1 敌弹](#敌弹_2)
  - [2.2 自机](#自机_2)



- [3 弹型与判定示意](#弹型与判定示意)
- [4 判定对比实例](#判定对比实例)
- [5 其他](#其他)
- [6 外部链接](#外部链接)
- [7 注释](#注释)




## 方形判定
### 敌弹
  
适用于红魔乡、妖妖梦、永夜抄、风神录、地灵殿、星莲船。自机和子弹的判定区域都为正方形，判定大小数据为 **正方形的边长** 。  

判定公式为 **(自机中心点与子弹中心点的水平或竖直距离)&lt;自机判定范围÷2 +子弹判定范围÷2**   

意即，在水平或竖直的任意方向上，当 **两个正方形相交时，判定miss** 。
  

- 红魔乡至风神录的大玉适用于方形判定；地灵殿之后的大玉则全部适用于圆形判定。地灵殿的蔷薇弹和大玉判定完全相同（也是圆形）。  

- 从风神录到天空璋的所有常规激光判定均为点线距离。当判定点与激光的距离小于激光判定宽度/2+自机判定/2时即中弹。虽然部分激光头尾粗细不一，但判定上是完全一样的。  

- 从星莲船开始的曲线激光在判定上是由一段段直线激光拼接成的，判定原理和直线激光相同。  

- 正方形底边永远是水平的，不是说斜着飞的子弹判定就是斜着的正方形（擦汗）。

### 自机
  
红魔乡:全员2.5  

妖妖梦:灵梦：1.65；魔理沙：2.2；咲夜：2.2  

永夜抄:灵梦/紫：1.65；其他：2.0  

风神录到星莲船:灵梦：2.0；早苗：3.0；魔理沙：3.5   

  

## 圆形判定
### 敌弹
  
适用于神灵庙及之后的作品。自机和子弹的判定区域都为圆形，判定大小数据为 **圆的半径** （注意是半径）。  

判定公式为 **(自机中心点与子弹中心点的距离)²&lt;(自机判定范围)²+(子弹判定范围)²**   

意即，当 **两个圆心距离小于[正交](http://baike.baidu.com/view/1797672.htm)时，判定miss** 。
  

- 当碰到方形子弹时适用于方形公式，当碰到圆形子弹时适用于正交圆公式。
- 从地灵殿开始，所有的体术判定都适用于圆形判定。

### 自机
  
灵梦：璋以前2.0，璋以后3.0；非灵梦：3.0；绀珠传中，兔子bomb每一层护罩增加判定1.5。  

  

- 辉针城的变大符卡 (未找到链接)中，自机判定会放大10.8倍。
- 天空璋及之后，所有机体判定统一成了3.0。灵梦获得了史诗级削弱。
- 虹龙洞中，携带疾风业务员(文文)卡，则高速判定(无论是否按住射击)将变成1.0，其它情况仍然为3.0判定。(备注:此外在超高速移动瞬间会获得4帧无敌)

## 弹型与判定示意
  
子弹的 **自旋不影响子弹判定** ，仅仅是改变了贴图，中心点位置和判定区域没有任何变化。  

截图包含最瘦的自机和最胖的自机（嗯………）在高速和低速状态下（位置相同，只是显示不显示判定点而已）离每个子弹的极限距离（并未MISS）。单位均为 **像素(px)**   

截图中所有子弹和自机的判定中心均在同一水平线上。  

本表仅包含常规弹型（圆与方），不包含不规则形状子弹、激光和杂鱼模拟型子弹（动物弹[^cite_note-1]、电光弹等）。
红魔乡火弹判定为11.0，永夜抄妹红的火弹判定5.0，图咕咕咕中（红妖永的判定数据已经分析出来了，只是因为脚本复杂，不好做图）。
  


<table>

<tbody><tr>
<th>名称</th>
<th>判定大小<br>正方形边长<br>（风地星）</th>
<th>极限距离（风地星）</th>
<th>判定大小<br>圆的半径<br>（神灵庙之后）</th>
<th>极限距离（神灵庙之后）</th>
<th>备注
</th></tr>
<tr>
<td>点弹</td>
<td>4.0</td>
<td><a href="./文件-点弹1.jpg.md" class="image"><img alt="点弹1.jpg" src="https://upload.thwiki.cc/6/60/%E7%82%B9%E5%BC%B91.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>2.4</td>
<td><a href="./文件-点弹2.jpg.md" class="image"><img alt="点弹2.jpg" src="https://upload.thwiki.cc/3/30/%E7%82%B9%E5%BC%B92.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>
</td></tr>
<tr>
<td>菌弹</td>
<td>4.0</td>
<td><a href="./文件-葡萄弹1.jpg.md" class="image"><img alt="葡萄弹1.jpg" src="https://upload.thwiki.cc/6/66/%E8%91%A1%E8%90%84%E5%BC%B91.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>2.4</td>
<td><a href="./文件-葡萄弹2.jpg.md" class="image"><img alt="葡萄弹2.jpg" src="https://upload.thwiki.cc/4/4b/%E8%91%A1%E8%90%84%E5%BC%B92.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>
</td></tr>
<tr>
<td>粒弹</td>
<td>-</td>
<td>-</td>
<td>2.0</td>
<td><a href="./文件-粒弹2.jpg.md" class="image"><img alt="粒弹2.jpg" src="https://upload.thwiki.cc/e/ee/%E7%B2%92%E5%BC%B92.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>出现在文花帖DS-<a href="./胎儿之梦.md" title="胎儿之梦">胎儿之梦</a>,天邪鬼-<a href="./小人的地狱.md" title="小人的地狱">小人的地狱</a>中。
</td></tr>
<tr>
<td>小玉</td>
<td>6.0</td>
<td><a href="./文件-小玉1.jpg.md" class="image"><img alt="小玉1.jpg" src="https://upload.thwiki.cc/2/2d/%E5%B0%8F%E7%8E%891.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>4.0</td>
<td><a href="./文件-小玉2.jpg.md" class="image"><img alt="小玉2.jpg" src="https://upload.thwiki.cc/3/38/%E5%B0%8F%E7%8E%892.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>小玉的贴图直径为16.0。
</td></tr>
<tr>
<td>环玉</td>
<td>6.0</td>
<td><a href="./文件-环玉1.jpg.md" class="image"><img alt="环玉1.jpg" src="https://upload.thwiki.cc/4/4f/%E7%8E%AF%E7%8E%891.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>4.0</td>
<td><a href="./文件-环玉2.jpg.md" class="image"><img alt="环玉2.jpg" src="https://upload.thwiki.cc/8/8b/%E7%8E%AF%E7%8E%892.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>带环的，和小玉没区别。
</td></tr>
<tr>
<td>米弹</td>
<td>4.0</td>
<td><a href="./文件-米弹1.jpg.md" class="image"><img alt="米弹1.jpg" src="https://upload.thwiki.cc/7/7b/%E7%B1%B3%E5%BC%B91.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>2.4</td>
<td><a href="./文件-米弹2.jpg.md" class="image"><img alt="米弹2.jpg" src="https://upload.thwiki.cc/2/20/%E7%B1%B3%E5%BC%B92.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>
</td></tr>
<tr>
<td>链弹</td>
<td>4.0<br>5.0(红)</td>
<td><a href="./文件-链弹1.jpg.md" class="image"><img alt="链弹1.jpg" src="https://upload.thwiki.cc/1/19/%E9%93%BE%E5%BC%B91.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>2.4</td>
<td><a href="./文件-链弹2.jpg.md" class="image"><img alt="链弹2.jpg" src="https://upload.thwiki.cc/6/61/%E9%93%BE%E5%BC%B92.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>日文里叫做吸盘弹，也有叫苦无的。
</td></tr>
<tr>
<td>针弹</td>
<td>4.0</td>
<td><a href="./文件-针弹1.jpg.md" class="image"><img alt="针弹1.jpg" src="https://upload.thwiki.cc/1/16/%E9%92%88%E5%BC%B91.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>2.4</td>
<td><a href="./文件-针弹2.jpg.md" class="image"><img alt="针弹2.jpg" src="https://upload.thwiki.cc/3/3d/%E9%92%88%E5%BC%B92.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>有些符卡中会自旋导致看上去判定偏大。
</td></tr>
<tr>
<td>札弹</td>
<td>4.0</td>
<td><a href="./文件-札弹1.jpg.md" class="image"><img alt="札弹1.jpg" src="https://upload.thwiki.cc/a/ab/%E6%9C%AD%E5%BC%B91.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>2.8</td>
<td><a href="./文件-札弹2.jpg.md" class="image"><img alt="札弹2.jpg" src="https://upload.thwiki.cc/e/e1/%E6%9C%AD%E5%BC%B92.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>
</td></tr>
<tr>
<td>鳞弹</td>
<td>4.0</td>
<td><a href="./文件-鳞弹1.jpg.md" class="image"><img alt="鳞弹1.jpg" src="https://upload.thwiki.cc/4/4b/%E9%B3%9E%E5%BC%B91.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>2.4</td>
<td><a href="./文件-鳞弹2.jpg.md" class="image"><img alt="鳞弹2.jpg" src="https://upload.thwiki.cc/6/60/%E9%B3%9E%E5%BC%B92.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>判定中心偏翼端。
</td></tr>
<tr>
<td>铳弹</td>
<td>4.0</td>
<td><a href="./文件-铳弹1.jpg.md" class="image"><img alt="铳弹1.jpg" src="https://upload.thwiki.cc/6/6b/%E9%93%B3%E5%BC%B91.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>2.4</td>
<td><a href="./文件-铳弹2.jpg.md" class="image"><img alt="铳弹2.jpg" src="https://upload.thwiki.cc/8/85/%E9%93%B3%E5%BC%B92.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>
</td></tr>
<tr>
<td>杆菌弹</td>
<td>4.0</td>
<td><a href="./文件-杆菌弹1.jpg.md" class="image"><img alt="杆菌弹1.jpg" src="https://upload.thwiki.cc/7/7c/%E6%9D%86%E8%8F%8C%E5%BC%B91.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>2.4</td>
<td><a href="./文件-杆菌弹2.jpg.md" class="image"><img alt="杆菌弹2.jpg" src="https://upload.thwiki.cc/7/70/%E6%9D%86%E8%8F%8C%E5%BC%B92.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>
</td></tr>
<tr>
<td>星弹（小）</td>
<td>6.0<br>4.0(永)</td>
<td><a href="./文件-星弹（小）1.jpg.md" class="image"><img alt="星弹（小）1.jpg" src="https://upload.thwiki.cc/7/7c/%E6%98%9F%E5%BC%B9%EF%BC%88%E5%B0%8F%EF%BC%891.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>4.0</td>
<td><a href="./文件-星弹（小）2.jpg.md" class="image"><img alt="星弹（小）2.jpg" src="https://upload.thwiki.cc/c/ce/%E6%98%9F%E5%BC%B9%EF%BC%88%E5%B0%8F%EF%BC%892.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>会自旋导致看上去判定偏大。
</td></tr>
<tr>
<td>钱币</td>
<td>6.0</td>
<td><a href="./文件-钱币1.jpg.md" class="image"><img alt="钱币1.jpg" src="https://upload.thwiki.cc/2/2e/%E9%92%B1%E5%B8%811.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>4.0</td>
<td><a href="./文件-钱币2.jpg.md" class="image"><img alt="钱币2.jpg" src="https://upload.thwiki.cc/9/93/%E9%92%B1%E5%B8%812.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>
</td></tr>
<tr>
<td>中玉</td>
<td>10.0<br>16.0(红)</td>
<td><a href="./文件-中玉1.jpg.md" class="image"><img alt="中玉1.jpg" src="https://upload.thwiki.cc/a/a8/%E4%B8%AD%E7%8E%891.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>8.5</td>
<td><a href="./文件-中玉2.jpg.md" class="image"><img alt="中玉2.jpg" src="https://upload.thwiki.cc/f/f4/%E4%B8%AD%E7%8E%892.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>
</td></tr>
<tr>
<td>椭弹</td>
<td>8.0<br>5.0(永)</td>
<td><a href="./文件-椭弹1.jpg.md" class="image"><img alt="椭弹1.jpg" src="https://upload.thwiki.cc/a/af/%E6%A4%AD%E5%BC%B91.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>7.0</td>
<td><a href="./文件-椭弹2.jpg.md" class="image"><img alt="椭弹2.jpg" src="https://upload.thwiki.cc/8/80/%E6%A4%AD%E5%BC%B92.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>
</td></tr>
<tr>
<td>刀弹</td>
<td>8.0<br>9.0(红)</td>
<td><a href="./文件-刀弹1.jpg.md" class="image"><img alt="刀弹1.jpg" src="https://upload.thwiki.cc/d/df/%E5%88%80%E5%BC%B91.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>6.0</td>
<td><a href="./文件-刀弹2.jpg.md" class="image"><img alt="刀弹2.jpg" src="https://upload.thwiki.cc/d/de/%E5%88%80%E5%BC%B92.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>
</td></tr>
<tr>
<td>蝶弹</td>
<td>8.0<br>5.0(妖永)</td>
<td><a href="./文件-蝶弹1.jpg.md" class="image"><img alt="蝶弹1.jpg" src="https://upload.thwiki.cc/5/5f/%E8%9D%B6%E5%BC%B91.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>7.0</td>
<td><a href="./文件-蝶弹2.jpg.md" class="image"><img alt="蝶弹2.jpg" src="https://upload.thwiki.cc/8/8f/%E8%9D%B6%E5%BC%B92.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>
</td></tr>
<tr>
<td>星弹（大）</td>
<td>8.0</td>
<td><a href="./文件-星弹（大）1.jpg.md" class="image"><img alt="星弹（大）1.jpg" src="https://upload.thwiki.cc/1/11/%E6%98%9F%E5%BC%B9%EF%BC%88%E5%A4%A7%EF%BC%891.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>7.0</td>
<td><a href="./文件-星弹（大）2.jpg.md" class="image"><img alt="星弹（大）2.jpg" src="https://upload.thwiki.cc/6/6c/%E6%98%9F%E5%BC%B9%EF%BC%88%E5%A4%A7%EF%BC%892.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>会自旋导致看上去判定偏大。
</td></tr>
<tr>
<td>水光弹</td>
<td>6.0</td>
<td><a href="./文件-炎弹.jpg.md" class="image"><img alt="炎弹.jpg" src="https://upload.thwiki.cc/8/89/%E7%82%8E%E5%BC%B9.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>-</td>
<td>-</td>
<td>
</td></tr>
<tr>
<td>炎弹（红）</td>
<td>忍比</td>
<td>填坑</td>
<td>6.0</td>
<td><a href="./文件-炎弹红2.jpg.md" class="image"><img alt="炎弹红2.jpg" src="https://upload.thwiki.cc/1/1a/%E7%82%8E%E5%BC%B9%E7%BA%A22.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>火焰部分无判定。
</td></tr>
<tr>
<td>炎弹（紫）</td>
<td>忍比</td>
<td>填坑</td>
<td>6.0</td>
<td><a href="./文件-炎弹紫2.jpg.md" class="image"><img alt="炎弹紫2.jpg" src="https://upload.thwiki.cc/b/b3/%E7%82%8E%E5%BC%B9%E7%B4%AB2.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>
</td></tr>
<tr>
<td>炎弹（蓝）</td>
<td>忍比</td>
<td>填坑</td>
<td>4.0</td>
<td><a href="./文件-炎弹蓝2.jpg.md" class="image"><img alt="炎弹蓝2.jpg" src="https://upload.thwiki.cc/e/ea/%E7%82%8E%E5%BC%B9%E8%93%9D2.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>
</td></tr>
<tr>
<td>炎弹（黄）</td>
<td>忍比</td>
<td>填坑</td>
<td>4.0</td>
<td><a href="./文件-炎弹黄2.jpg.md" class="image"><img alt="炎弹黄2.jpg" src="https://upload.thwiki.cc/9/90/%E7%82%8E%E5%BC%B9%E9%BB%842.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>
</td></tr>
<tr>
<td>心弹</td>
<td>10.0</td>
<td><a href="./文件-心弹1.jpg.md" class="image"><img alt="心弹1.jpg" src="https://upload.thwiki.cc/9/9f/%E5%BF%83%E5%BC%B91.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>10.0</td>
<td><a href="./文件-心弹2.jpg.md" class="image"><img alt="心弹2.jpg" src="https://upload.thwiki.cc/b/bc/%E5%BF%83%E5%BC%B92.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>看起来不规则，其实是规则的。
</td></tr>
<tr>
<td>滴弹</td>
<td>4.0</td>
<td><a href="./文件-滴弹1.jpg.md" class="image"><img alt="滴弹1.jpg" src="https://upload.thwiki.cc/7/7e/%E6%BB%B4%E5%BC%B91.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>2.4</td>
<td><a href="./文件-滴弹2.jpg.md" class="image"><img alt="滴弹2.jpg" src="https://upload.thwiki.cc/a/ae/%E6%BB%B4%E5%BC%B92.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>
</td></tr>
<tr>
<td>箭弹</td>
<td>-</td>
<td>-</td>
<td>4.0</td>
<td><a href="./文件-箭弹2.jpg.md" class="image"><img alt="箭弹2.jpg" src="https://upload.thwiki.cc/5/53/%E7%AE%AD%E5%BC%B92.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>只有箭头有判定
</td></tr>
<tr>
<td>大玉</td>
<td>32.0(红)<br>24.0(妖永)<br>28.0（风）</td>
<td><a href="./文件-大玉1.jpg.md" class="image"><img alt="大玉1.jpg" src="https://upload.thwiki.cc/5/5a/%E5%A4%A7%E7%8E%891.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>14.0</td>
<td><a href="./文件-大玉2.jpg.md" class="image"><img alt="大玉2.jpg" src="https://upload.thwiki.cc/9/9a/%E5%A4%A7%E7%8E%892.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>地灵殿之后都是14.0圆形。
</td></tr>
<tr>
<td>蔷薇</td>
<td>-</td>
<td>-</td>
<td>14.0</td>
<td><a href="./文件-蔷薇1.jpg.md" class="image"><img alt="蔷薇1.jpg" src="https://upload.thwiki.cc/8/8a/%E8%94%B7%E8%96%871.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>只有地灵殿用过
</td></tr>
<tr>
<td>光玉</td>
<td>-</td>
<td>-</td>
<td>14.0(神)<br>12.0(其他)</td>
<td><a href="./文件-光玉2.jpg.md" class="image"><img alt="光玉2.jpg" src="https://upload.thwiki.cc/e/e5/%E5%85%89%E7%8E%892.jpg" decoding="async" loading="lazy" width="197" height="369" data-file-width="197" data-file-height="369"></a></td>
<td>
</td></tr>
<tr>
<td>音符</td>
<td>-</td>
<td>-</td>
<td>4.0</td>
<td><a href="./文件-音符2.jpg.md" class="image"><img alt="音符2.jpg" src="https://upload.thwiki.cc/6/62/%E9%9F%B3%E7%AC%A62.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>子弹中心在头部圆心偏下，尾部无判定。
</td></tr>
<tr>
<td>休止符</td>
<td>-</td>
<td>-</td>
<td>5.0</td>
<td><a href="./文件-休止符2.jpg.md" class="image"><img alt="休止符2.jpg" src="https://upload.thwiki.cc/7/7b/%E4%BC%91%E6%AD%A2%E7%AC%A62.jpg" decoding="async" loading="lazy" width="197" height="185" data-file-width="197" data-file-height="185"></a></td>
<td>
</td></tr>
<tr>
<td>阴阳玉（小）</td>
<td>-</td>
<td>-</td>
<td>10.0</td>
<td><a href="./文件-阴阳玉小2.jpg.md" class="image"><img alt="阴阳玉小2.jpg" src="https://upload.thwiki.cc/7/7b/%E9%98%B4%E9%98%B3%E7%8E%89%E5%B0%8F2.jpg" decoding="async" loading="lazy" width="197" height="110" data-file-width="197" data-file-height="110"></a></td>
<td>比中玉（8.5）大一圈
</td></tr>
<tr>
<td>阴阳玉（大）</td>
<td>-</td>
<td>-</td>
<td>28.0</td>
<td><a href="./文件-阴阳玉大2.jpg.md" class="image"><img alt="阴阳玉大2.jpg" src="https://upload.thwiki.cc/6/6d/%E9%98%B4%E9%98%B3%E7%8E%89%E5%A4%A72.jpg" decoding="async" loading="lazy" width="197" height="96" data-file-width="197" data-file-height="96"></a></td>
<td>判定为大玉（14.0）的两倍
</td></tr></tbody></table>


## 判定对比实例

  
设自机和子弹之间的极限距离为[math]\displaystyle{  d  }[/math]（为了方便，对于方形子弹这里仅考虑水平方向）。  

  

- 灵梦x小玉  


  
风地星：[math]\displaystyle{  d \lt  \tfrac{2.0}{2} + \tfrac{6.0}{2} = 4.0  }[/math]  

神辉绀：[math]\displaystyle{  d \lt  \sqrt{2.0^2 + 4.0^2} \approx 4.472136  }[/math]  

就小玉来说，判定变大了。  

  

- 魔理沙x小玉  


  
风地星：[math]\displaystyle{  d \lt  \tfrac{3.5}{2} + \tfrac{6.0}{2} = 4.75  }[/math]  

神辉绀：[math]\displaystyle{  d \lt  \sqrt{3.0^2 + 4.0^2} = 5.0  }[/math]  

同样变大很多，但是和灵梦的差距小了点 [math]\displaystyle{  (0.75 \to 0.53)  }[/math]。  

  

- 灵梦x椭弹  


  
风地星：[math]\displaystyle{  d \lt  \tfrac{2.0}{2} + \tfrac{8.0}{2} = 5.0  }[/math]  

神辉绀：[math]\displaystyle{  d \lt  \sqrt{2.0^2 + 7.0^2} \approx 7.28011  }[/math]  

  

- 灵梦x大玉  


  
风(只有风有方形大玉)：[math]\displaystyle{  d \lt  \tfrac{2.0}{2} + \tfrac{28.0}{2} = 15.0  }[/math]  

地星神辉绀：[math]\displaystyle{  d \lt  \sqrt{2.0^2 + 14.0^2} \approx 14.142135  }[/math]  

好像小了一点  

  

- 魔理沙x大玉  


  
风：[math]\displaystyle{  d \lt  \tfrac{3.5}{2} + \tfrac{28.0}{2} = 15.75  }[/math]  

地星：[math]\displaystyle{  d \lt  \sqrt{3.5^2 + 14.0^2} \approx 14.43087  }[/math]  

神辉绀：[math]\displaystyle{  d \lt  \sqrt{3.0^2 + 14.0^2} \approx 14.31782  }[/math]  

  

- 结论：将正方形算法改为正交圆算法之后，对于较大的子弹，梦机和其他机体的差异很小（大玉只差了[math]\displaystyle{  0.17  }[/math]像素）。  
而对于小子弹的差异很大（小玉差了[math]\displaystyle{  0.57  }[/math]像素）  
所以胖机体的真正杀手是小型子弹。  

- 小槌「你给我变大吧」 (未找到链接)  


  
灵梦x链弹：[math]\displaystyle{  d \lt  \sqrt{(2.0\times 10.8)^2 + 2.4^2} \approx 21.73292  }[/math]  

其他机体x链弹：[math]\displaystyle{  d \lt  \sqrt{(3.0\times 10.8)^2 + 2.4^2} \approx 32.48877  }[/math]  

差距有[math]\displaystyle{  1.5  }[/math]倍左右!
  


  
[](./文件-变大.jpg.md)
  

## 其他
- 风神录中，由于zun的失误，在有子弹变形的符卡中，仅仅变了子弹贴图而没有改变子弹判定，导致在神奈子的符卡筒粥「神之粥」 (未找到链接)（各难度均有）中，缩小的米弹实际上是椭弹判定。  
在天流「天水奇迹」 (未找到链接)中，也有同样的问题，鳞弹实际上是炎弹判定（死亡线大了一像素）。
- 神灵庙中，妖梦的“蓄力状态判定减小”特技，没有任何实际效果。
- 天邪鬼中，副道具阴阳玉“判定减小”特技，仅对激光型子弹有效，对其他的子弹无效。
- 有很多东西其实都是特殊的“假子弹”，比如老虎的粗号激光，勇仪的圈，布都的船等，判定都不是单纯的圆or方。

## 外部链接
  
[1](http://tieba.baidu.com/p/4710467563)
[2](http://tieba.baidu.com/p/4708163464)
  


[^cite_note-1]: 可参考[游戏攻略/东方神灵庙/其他](./游戏攻略-东方神灵庙-其他.md)





---

此文档由 [THBWiki-Markdown-Builder](https://github.com/Delsin-Yu/THBWiki-Markdown-Builder) 构建。

文档中的所有内容除特殊注明外，均在 [**知识共享(Creative Commons) 署名-非商业性使用-相同方式共享 3.0 协议**](https://creativecommons.org/licenses/by-sa/3.0/deed.zh-hans) 下提供，附加条款亦可能应用。

引用类型与其他类型作品版权归原作者所有，如有作者授权则遵照授权协议使用。

详细请查阅 [THBWiki：免责声明](https://thbwiki.cc/THBWiki:%E5%85%8D%E8%B4%A3%E5%A3%B0%E6%98%8E)。

