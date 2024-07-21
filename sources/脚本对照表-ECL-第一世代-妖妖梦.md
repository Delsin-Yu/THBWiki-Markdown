# 脚本对照表/ECL/第一世代/妖妖梦

<!-- source html: G:\repos\THBWiki-Markdown-Builder\THBWikiMarkdown\Temp\main\a\a0\ns0%3A%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8%2FECL%2F%E7%AC%AC%E4%B8%80%E4%B8%96%E4%BB%A3%2F%E5%A6%96%E5%A6%96%E6%A2%A6.html -->

脚本对照表

### 概述
  
本对照表是ZUN的妖妖梦的对照表
  
  
红色代表功能未知，需要测试和研究
  
  
蓝色代表虽然并未完全解读，但是大体功能已经知道，且此函数用途十分有限
  

### 弹幕系
  
64(int style, int color, int way, int layer, float minspeed, float maxspeed, float angle, float angle_dif, int flags)
  

```
   立即发射普通自机狙弹幕，style为子弹类型，color为颜色，way和layer的定义与后续世代的脚本一致，minspeed和maxspeed分别为最小速度和最大速度，angle为发射角度（实际角度为angle+发弹点与自机的夹角），angle_dif为每way之间角度差，flags为子弹flag
```

  
65(int style, int color, int way, int layer, float minspeed, float maxspeed, float angle, float angle_dif, int flags)
  

```
   立即发射普通弹幕，style为子弹类型，color为颜色，way和layer的定义同64，minspeed和maxspeed分别为最小速度和最大速度，angle为发射角度（默认角度为0），angle_dif为每way之间角度差，flags为子弹flag
```

  
66(int style, int color, int way, int layer, float minspeed, float maxspeed, float angle, float angle_dif, int flags)
  

```
   立即发射自机狙开花弹幕，style为子弹类型，color为颜色，way和layer的定义同64，minspeed和maxspeed分别为最小速度和最大速度，angle为发射角度（实际角度为angle+发弹点与自机的夹角），angle_dif为每层之间角度差，flags为子弹flag
```

  
67(int style, int color, int way, int layer, float minspeed, float maxspeed, float angle, float angle_dif, int flags)
  

```
   立即发射开花弹幕，style为子弹类型，color为颜色，way和layer的定义同64，minspeed和maxspeed分别为最小速度和最大速度，angle为发射角度（默认角度为0），angle_dif为每层之间角度差，flags为子弹flag
```

  
68(int style, int color, int way, int layer, float minspeed, float maxspeed, float angle, float angle_dif, int flags)
  

```
   暂时未知
```

  
69(int style, int color, int way, int layer, float minspeed, float maxspeed, float angle, float angle_dif, int flags)
  

```
   暂时未知
```

  
70(int style, int color, int way, int layer, float minspeed, float maxspeed, float angle, float angle_dif, int flags)
  

```
   立即发射分层随机弹幕，style为子弹类型，color为颜色，way的定义表示每层随机弹数量，layer的定义同64，minspeed和maxspeed分别为最小速度和最大速度，所有子弹的角度在(angle-angle_dif)与(angle+angle_dif)之间的范围内随机，但速度不变，flags为子弹flag
```

  
71(int style, int color, int way, int layer, float minspeed, float maxspeed, float angle, float angle_dif, int flags)
  

```
   立即发射速度随机弹幕，style为子弹类型，color为颜色，way和layer的定义与后续世代的脚本一致，速度在maxspeed与(maxspeed+minspeed)之间的范围内随机，angle为发射角度（实际角度为angle+发弹点与自机的夹角），angle_dif为每way之间角度差，flags为子弹flag
```

  
72(int style, int color, int way, int layer, float minspeed, float maxspeed, float angle, float angle_dif, int flags)
  

```
   立即发射完全随机弹幕，style为子弹类型，color为颜色，向(angle-angle_dif)与(angle+angle_dif)之间的范围内，以maxspeed与(maxspeed+minspeed)之间的范围内随机的速度，发射(way * layer)个子弹，way和layer均失去原本意义，flags为子弹flag
```


<table>
<caption>子弹类型列表
</caption>
<tbody><tr>
<th>子弹编号</th>
<th>子弹类型（弹幕）</th>
<th>子弹类型（激光）
</th></tr>
<tr>
<td>0</td>
<td>点弹</td>
<td>高光激光段
</td></tr>
<tr>
<td>1</td>
<td>环玉</td>
<td>高光米弹
</td></tr>
<tr>
<td>2</td>
<td>米弹</td>
<td>激光段
</td></tr>
<tr>
<td>3</td>
<td>小玉</td>
<td>米弹
</td></tr>
<tr>
<td>4</td>
<td>链弹</td>
<td>高光鳞弹
</td></tr>
<tr>
<td>5</td>
<td>针弹
</td></tr>
<tr>
<td>6</td>
<td>鳞弹
</td></tr>
<tr>
<td>7</td>
<td>中玉
</td></tr>
<tr>
<td>8</td>
<td>蝶弹
</td></tr>
<tr>
<td>9</td>
<td>旧刀弹
</td></tr>
<tr>
<td>10</td>
<td>大玉
</td></tr></tbody></table>






---

此文档由 [THBWiki-Markdown-Builder](https://github.com/Delsin-Yu/THBWiki-Markdown-Builder) 构建。

文档中的所有内容除特殊注明外，均在 [**知识共享(Creative Commons) 署名-非商业性使用-相同方式共享 3.0 协议**](https://creativecommons.org/licenses/by-sa/3.0/deed.zh-hans) 下提供，附加条款亦可能应用。

引用类型与其他类型作品版权归原作者所有，如有作者授权则遵照授权协议使用。

详细请查阅 [THBWiki：免责声明](https://thbwiki.cc/THBWiki:%E5%85%8D%E8%B4%A3%E5%A3%B0%E6%98%8E)。

