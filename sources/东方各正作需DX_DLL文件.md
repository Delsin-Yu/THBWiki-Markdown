# 东方各正作需DX_DLL文件

<!-- source html: G:\repos\THBWiki-Markdown-Builder\THBWikiMarkdown\Temp\main\9\90\ns0%3A%E4%B8%9C%E6%96%B9%E5%90%84%E6%AD%A3%E4%BD%9C%E9%9C%80DX_DLL%E6%96%87%E4%BB%B6.html -->

待完成页面 | 资料

本页是整理东方Project  
 **相关资料** 的词条
<center>

<table>
<tbody><tr>
<td class="mbox-image"><div style="width: 52px;">
  <a href="./文件-ConstructionClock.png.md" class="image"><img alt="ConstructionClock.png" src="https://upload.thwiki.cc/thumb/f/f1/ConstructionClock.png/50px-ConstructionClock.png" decoding="async" loading="lazy" width="50" height="43" srcset="https://upload.thwiki.cc/thumb/f/f1/ConstructionClock.png/75px-ConstructionClock.png 1.5x, https://upload.thwiki.cc/thumb/f/f1/ConstructionClock.png/100px-ConstructionClock.png 2x" data-file-width="689" data-file-height="587"></a></div></td>
<td class="mbox-text" style=""><br>本页面词条尚未完工。<br><br></td>
</tr>
</tbody></table>


</center>
  
未安装Dx9c的情况下会遇到如图所示的错误提示而无法启动游戏。  

[](./文件-丢失DLL.jpg.md)
  

```
无法启动此程序，因为计算机中丢失 d3dx9_XX.dll。尝试重新安装该程序以解决此问题。
```

  
其中DLL名称中的数字可能因作品不同而不同，其解决方案均为安装Dx9c或复制正确位数的对应DLL到游戏目录下。  

  
  
本页面提供该问题解决方案。
  


## DirectX官方在线更新程序
  
该程序是微软官方提供的，用于在线更新补充本机DirectX组件的，运行过程需要连接互联网并下载对应文件。  

最新版下载： [https://www.microsoft.com/zh-CN/download/confirmation.aspx?id=35](https://www.microsoft.com/zh-CN/download/confirmation.aspx?id=35)  

下载后联网安装即可。
  


## DirectX9.0c完整离线包
  
DirectX9.0c完整离线安装包，可以解决所有新作的DLL缺失问题。如果需要携带到不能连接网络的环境中，或者网速过慢，不希望反复下载，可以使用该离线安装包  

最新版下载：[https://www.microsoft.com/zh-cn/download/details.aspx?id=8109](https://www.microsoft.com/zh-cn/download/details.aspx?id=8109)  

  

```
下载之后先解压缩，解压缩得到的单个可执行文件不是安装程序，需要再次解压缩。运行这个程序，让你选择路径，实际上是解压缩路径。
最终解压得到一百多个压缩包文件和一个可执行文件。
打开解压到的位置，并找到这个可执行文件，该文件才是安装程序，运行它，不需要选择安装路径，安装完毕。```

  
如果觉得完整包太大，下载不方便的话（大约100MB）。下面提供单独文件下载。
  


## 各作所需DLL单独文件下载
  
请注意：x86和x64两种分别对应32位系统和64位系统。如果搞错了也会无效提示错误。请注意。
下载之后把DLL文件放到游戏根目录即可。也可以放到Windows目录下的System32文件夹下。 
  

```
如果不知道自己是多少位的系统，Win7用户请右键 **计算机** ，选择属性，系统类型项目中会写明系统位数。
XP用户如果没有特殊情况均为32位系统，Win11不支持32位，均为64位系统。
```


<table>
<caption>各作常见所需DX DLL单独文件下载
</caption>
<tbody><tr>
<th>编号</th>
<th>游戏</th>
<th>所需文件</th>
<th>x86</th>
<th>x64
</th></tr>
<tr>
<td>th06</td>
<td>东方红魔乡</td>
<td rowspan="6">d3dx9_27.dll<sup id="cite_ref-1" class="reference"><a href="#cite_note-1">1</a></sup></td>
<td rowspan="6"><a rel="nofollow" class="external text" href="http://down.touhou8.com/dll/d3dx9_27/x86/d3dx9_27.dll">下载地址</a></td>
<td rowspan="6"><a rel="nofollow" class="external text" href="http://down.touhou8.com/dll/d3dx9_27/x64/d3dx9_27.dll">下载地址</a>
</td></tr>
<tr>
<td>th07</td>
<td>东方妖妖梦
</td></tr>
<tr>
<td>th07.5</td>
<td>东方萃梦想
</td></tr>
<tr>
<td>th08</td>
<td>东方永夜抄
</td></tr>
<tr>
<td>th09</td>
<td>东方花映塚
</td></tr>
<tr>
<td>th09.5</td>
<td>东方文花帖
</td></tr>
<tr>
<td>th10</td>
<td>东方风神录</td>
<td>d3dx9_31.dll<sup id="cite_ref-2" class="reference"><a href="#cite_note-2">2</a></sup></td>
<td><a rel="nofollow" class="external text" href="http://down.touhou8.com/dll/d3dx9_31/x86/d3dx9_31.dll">下载地址</a></td>
<td><a rel="nofollow" class="external text" href="http://down.touhou8.com/dll/d3dx9_31/x64/d3dx9_31.dll">下载地址</a>
</td></tr>
<tr>
<td>th10.5</td>
<td>东方绯想天</td>
<td rowspan="2">d3dx9_33.dll</td>
<td rowspan="2"><a rel="nofollow" class="external text" href="http://down.touhou8.com/dll/d3dx9_33/x86/d3dx9_33.dll">下载地址</a></td>
<td rowspan="2"><a rel="nofollow" class="external text" href="http://down.touhou8.com/dll/d3dx9_33/x64/d3dx9_33.dll">下载地址</a>
</td></tr>
<tr>
<td>th12.3</td>
<td>东方非想天则
</td></tr>
<tr>
<td>th11</td>
<td>东方地灵殿</td>
<td>d3dx9_37.dll</td>
<td><a rel="nofollow" class="external text" href="http://down.touhou8.com/dll/d3dx9_37/x86/d3dx9_37.dll">下载地址</a></td>
<td><a rel="nofollow" class="external text" href="http://down.touhou8.com/dll/d3dx9_37/x64/d3dx9_37.dll">下载地址</a>
</td></tr>
<tr>
<td>th12</td>
<td>东方星莲船</td>
<td>d3dx9_40.dll</td>
<td><a rel="nofollow" class="external text" href="http://down.touhou8.com/dll/d3dx9_40/x86/d3dx9_40.dll">下载地址</a></td>
<td><a rel="nofollow" class="external text" href="http://down.touhou8.com/dll/d3dx9_40/x64/d3dx9_40.dll">下载地址</a>
</td></tr>
<tr>
<td>th12.5</td>
<td>DoubleSpoiler</td>
<td rowspan="2">d3dx9_42.dll</td>
<td rowspan="2"><a rel="nofollow" class="external text" href="http://down.touhou8.com/dll/d3dx9_42/x86/d3dx9_42.dll">下载地址</a></td>
<td rowspan="2"><a rel="nofollow" class="external text" href="http://down.touhou8.com/dll/d3dx9_42/x64/d3dx9_42.dll">下载地址</a>
</td></tr>
<tr>
<td>th12.8</td>
<td>妖精大战争
</td></tr>
<tr>
<td>th13</td>
<td>东方神灵庙</td>
<td rowspan="6">d3dx9_43.dll</td>
<td rowspan="6"><a rel="nofollow" class="external text" href="http://down.touhou8.com/dll/d3dx9_43/x86/d3dx9_43.dll">下载地址</a></td>
<td rowspan="6"><a rel="nofollow" class="external text" href="http://down.touhou8.com/dll/d3dx9_43/x64/d3dx9_43.dll">下载地址</a>
</td></tr>
<tr>
<td>th13.5</td>
<td>东方心绮楼
</td></tr>
<tr>
<td>th14</td>
<td>东方辉针城
</td></tr>
<tr>
<td>th14.3</td>
<td>弹幕天邪鬼
</td></tr>
<tr>
<td>th14.5</td>
<td>东方深秘录
</td></tr>
<tr>
<td>th15</td>
<td>东方绀珠传
</td></tr>
<tr>
<td>th15.5</td>
<td>东方凭依华</td>
<td rowspan="1">d3dx11_43.dll</td>
<td rowspan="1"><a rel="nofollow" class="external text" href="https://download.zip.dll-files.com/8e0bb968ff41d80e5f2c747c04db79ae/d3dx11_43.zip?token=SGjOlI6Ntqqn4KqMAuwasQ&amp;expires=1663645887">下载地址</a></td>
<td rowspan="1">下载地址
</td></tr>
<tr>
<td>th16</td>
<td>东方天空璋</td>
<td rowspan="3">d3dx9_43.dll</td>
<td rowspan="3"><a rel="nofollow" class="external text" href="http://down.touhou8.com/dll/d3dx9_43/x86/d3dx9_43.dll">下载地址</a></td>
<td rowspan="3"><a rel="nofollow" class="external text" href="http://down.touhou8.com/dll/d3dx9_43/x64/d3dx9_43.dll">下载地址</a>
</td></tr>
<tr>
<td>th17</td>
<td>东方鬼形兽
</td></tr>
<tr>
<td>th18</td>
<td>东方虹龙洞
</td></tr></tbody></table>



[^cite_note-1]: 这几作可能很少有人会提示缺少Dll，因为这几个版本需要的是DirectX 8.0或老版D9，XP以上版本系统都集成了。不提供DirectX 8.0的下载地址。 






---

此文档由 [THBWiki-Markdown-Builder](https://github.com/Delsin-Yu/THBWiki-Markdown-Builder) 构建。

文档中的所有内容除特殊注明外，均在 [**知识共享(Creative Commons) 署名-非商业性使用-相同方式共享 3.0 协议**](https://creativecommons.org/licenses/by-sa/3.0/deed.zh-hans) 下提供，附加条款亦可能应用。

引用类型与其他类型作品版权归原作者所有，如有作者授权则遵照授权协议使用。

详细请查阅 [THBWiki：免责声明](https://thbwiki.cc/THBWiki:%E5%85%8D%E8%B4%A3%E5%A3%B0%E6%98%8E)。

