# 脚本对照表/ECL/第一世代

<!-- source html: G:\repos\THBWiki-Markdown-Builder\THBWikiMarkdown\Temp\main\0\03\ns0%3A%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8%2FECL%2F%E7%AC%AC%E4%B8%80%E4%B8%96%E4%BB%A3.html -->

脚本对照表


## 目录

- [1 概述](#概述)
- [2 通用](#通用)
- [3 弹幕系](#弹幕系)
- [4 单位系](#单位系)
- [5 特殊系](#特殊系)
- [6 特殊变量表](#特殊变量表)





### 概述
  
本对照表是Zun的第一代ecl脚本的对照表,适用于红妖永花,文花帖
  
  
[妖妖梦](./脚本对照表-ECL-第一世代-妖妖梦.md)妖妖梦单独的ecl脚本表
  
  
粉色代表妖妖梦新增
  
  
深紫色代表永夜抄新增
  
  
绿色代表花映塚新增
  
  
棕色代表文花帖新增
  
  
红色代表功能未知，需要测试和研究
  
  
蓝色代表虽然并未完全解读，但是大体功能已经知道，且此函数用途十分有限
  
  
灰色代表是前作特殊地点使用过之后完全被抛弃的
  

- 注：永夜抄中单关脚本和符卡练习脚本是分开的


### 通用
  
10(?)
  

```
   参数不明，最后一个float与循环次数相关
```

  
52(int a)
  

```
   调用ID为a的函数（子例程）
   如ins_52(9961)即为调用反编译后名为sub_9961的函数
   注意：子例程ID与函数名无关
```

  
53()
  

```
   返回调用函数
```


### 弹幕系
  
96(int style, int color, int way, int layer, float minspeed, float maxspeed, float angle, float angle_dif, int flags)
  

```
   立即发射自机狙开扇弹，style为子弹类型，color为颜色，way和layer的定义与后续世代的脚本一致，minspeed和maxspeed分别为最小速度和最大速度，angle为发射角度（实际角度为angle+发弹点与自机的夹角），angle_dif为每层角度差，flags为子弹flag
```


<table>
<caption>子弹类型列表
</caption>
<tbody><tr>
<th>子弹编号</th>
<th>子弹类型（红魔乡）</th>
<th>子弹类型（妖妖梦）</th>
<th>子弹类型（永夜抄）
</th></tr>
<tr>
<td>0</td>
<td>点弹</td>
<td>点弹</td>
<td>点弹
</td></tr>
<tr>
<td>1</td>
<td>环玉</td>
<td>环玉</td>
<td>环玉
</td></tr>
<tr>
<td>2</td>
<td>米弹</td>
<td>米弹</td>
<td>米弹
</td></tr>
<tr>
<td>3</td>
<td>小玉</td>
<td>小玉</td>
<td>小玉
</td></tr>
<tr>
<td>4</td>
<td>链弹</td>
<td>链弹</td>
<td>链弹
</td></tr>
<tr>
<td>5</td>
<td>针弹</td>
<td>针弹</td>
<td>针弹
</td></tr>
<tr>
<td>6</td>
<td>中玉</td>
<td>鳞弹</td>
<td>鳞弹
</td></tr>
<tr>
<td>7</td>
<td>旧火弹</td>
<td>中玉</td>
<td>中玉
</td></tr>
<tr>
<td>8</td>
<td>刀弹</td>
<td>蝶弹</td>
<td>蝶弹
</td></tr>
<tr>
<td>9</td>
<td>大玉</td>
<td>旧刀弹</td>
<td>旧刀弹
</td></tr>
<tr>
<td>10</td>
<td>无</td>
<td>大玉</td>
<td>大玉
</td></tr>
<tr>
<td>11</td>
<td>无</td>
<td>无</td>
<td>札弹
</td></tr>
<tr>
<td>12</td>
<td>无</td>
<td>无</td>
<td>顺时针旋转小星弹
</td></tr>
<tr>
<td>13</td>
<td>无</td>
<td>无</td>
<td>逆时针旋转小星弹
</td></tr>
<tr>
<td>14</td>
<td>无</td>
<td>无</td>
<td>顺时针旋转大星弹
</td></tr>
<tr>
<td>15</td>
<td>无</td>
<td>无</td>
<td>逆时针旋转大星弹
</td></tr>
<tr>
<td>16</td>
<td>无</td>
<td>无</td>
<td>铳弹
</td></tr>
<tr>
<td>17</td>
<td>无</td>
<td>无</td>
<td>杆菌弹
</td></tr>
<tr>
<td>18</td>
<td>无</td>
<td>无</td>
<td>椭弹
</td></tr>
<tr>
<td>19</td>
<td>无</td>
<td>无</td>
<td>火弹
</td></tr>
<tr>
<td>20</td>
<td>无</td>
<td>无</td>
<td>刀弹
</td></tr></tbody></table>


  
  

97(int style, int color, int way, int layer, float minspeed, float maxspeed, float angle, float angle_dif, int trans_flags)
  

```
   同96，但不是自机狙，角度变为angle
```

  
111(int index, int type, int channel, int a, int b, float x, float y)
  

```
   为弹幕设置变换，index为变换序号，type为变换类型，channel为通道，a、b、x、y为变换参数，其余未知
```


<table>
<caption>变换列表
</caption>
<tbody><tr>
<th>变换类型（十进制）</th>
<th>a</th>
<th>b</th>
<th>r</th>
<th>s</th>
<th>注释
</th></tr>
<tr>
<td>64</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>a帧后停顿，角度变为原角度+r，速度变为s，重复b次
</td></tr>
<tr>
<td>128</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>a帧后停顿，角度变为自机方向+r，速度变为s，重复b次
</td></tr>
<tr>
<td>256</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>a帧后停顿，角度变为r，速度变为s，重复b次
</td></tr>
<tr>
<td>8192</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>设置屏幕外持续时间为a帧
</td></tr>
<tr>
<td>16384</td>
<td>O</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>改变子弹样式和颜色，a为子弹样式，b为子弹颜色
</td></tr>
<tr>
<td>131072</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>暂停a帧
</td></tr></tbody></table>


  
空参数（标记为X的）一般填为-1（整数）或-1.0f（浮点数）
  


### 单位系
  
80(int a)
  

```
   设置当前单位flag
```

  
124(int a)
  

```
  播放ID为a的音效
```

  
155(int a)
  

```
   设置当前符卡是否为时符
```

  
173(int a)
  

```
   设置boss是否对bomb免疫
```


### 特殊系
  
176(int a)
  

```
   永夜抄中用于设置当前模式是否为Last Spell
```

  
179(int a)
  

```
   永夜抄中用于控制时间的显示，如“子时一刻”
   a为1时则显示
```


### 特殊变量表

<table>
<caption>特殊变量表（永夜抄）
</caption>
<tbody><tr>
<th>地址</th>
<th>注释
</th></tr>
<tr>
<td>10000</td>
<td>可供随意使用的全局整数变量
</td></tr>
<tr>
<td>10001</td>
<td>可供随意使用的全局整数变量
</td></tr>
<tr>
<td>10002</td>
<td>可供随意使用的全局整数变量
</td></tr>
<tr>
<td>10003</td>
<td>可供随意使用的全局整数变量
</td></tr>
<tr>
<td>10004</td>
<td>可供随意使用的全局整数变量
</td></tr>
<tr>
<td>10005</td>
<td>可供随意使用的全局整数变量
</td></tr>
<tr>
<td>10006</td>
<td>可供随意使用的全局整数变量
</td></tr>
<tr>
<td>10007</td>
<td>可供随意使用的全局整数变量
</td></tr>
<tr>
<td>10008</td>
<td>单位局部整数变量
</td></tr>
<tr>
<td>10009</td>
<td>单位局部整数变量
</td></tr>
<tr>
<td>10010</td>
<td>单位局部整数变量
</td></tr>
<tr>
<td>10011</td>
<td>单位局部整数变量
</td></tr>
<tr>
<td>10012</td>
<td>单位局部整数变量
</td></tr>
<tr>
<td>10013</td>
<td>单位局部整数变量
</td></tr>
<tr>
<td>10014</td>
<td>单位局部整数变量
</td></tr>
<tr>
<td>10015</td>
<td>单位局部整数变量
</td></tr>
<tr>
<td>10016.0f</td>
<td>可供随意使用的全局浮点变量
</td></tr>
<tr>
<td>10017.0f</td>
<td>可供随意使用的全局浮点变量
</td></tr>
<tr>
<td>10018.0f</td>
<td>可供随意使用的全局浮点变量
</td></tr>
<tr>
<td>10019.0f</td>
<td>可供随意使用的全局浮点变量
</td></tr>
<tr>
<td>10020.0f</td>
<td>可供随意使用的全局浮点变量
</td></tr>
<tr>
<td>10021.0f</td>
<td>可供随意使用的全局浮点变量
</td></tr>
<tr>
<td>10022.0f</td>
<td>可供随意使用的全局浮点变量
</td></tr>
<tr>
<td>10023.0f</td>
<td>可供随意使用的全局浮点变量
</td></tr>
<tr>
<td>10024.0f</td>
<td>单位局部浮点变量
</td></tr>
<tr>
<td>10025.0f</td>
<td>单位局部浮点变量
</td></tr>
<tr>
<td>10026.0f</td>
<td>单位局部浮点变量
</td></tr>
<tr>
<td>10027.0f</td>
<td>单位局部浮点变量
</td></tr>
<tr>
<td>10028.0f</td>
<td>单位局部浮点变量
</td></tr>
<tr>
<td>10029.0f</td>
<td>单位局部浮点变量
</td></tr>
<tr>
<td>10030.0f</td>
<td>单位局部浮点变量
</td></tr>
<tr>
<td>10031.0f</td>
<td>单位局部浮点变量
</td></tr>
<tr>
<td>10032</td>
<td>随机整数
</td></tr>
<tr>
<td>10033.0f</td>
<td>随机浮点数
</td></tr>
<tr>
<td>10034</td>
<td>随机整数，与10032区别不明
</td></tr>
<tr>
<td>10035.0f</td>
<td>随机浮点数，与10032区别不明
</td></tr>
<tr>
<td>10036</td>
<td>可供随意使用的全局整数变量
</td></tr>
<tr>
<td>10037</td>
<td>可供随意使用的全局整数变量
</td></tr>
<tr>
<td>10038</td>
<td>可供随意使用的全局整数变量
</td></tr>
<tr>
<td>10039</td>
<td>可供随意使用的全局整数变量
</td></tr>
<tr>
<td>10040</td>
<td>当前难度
</td></tr>
<tr>
<td>10041</td>
<td>当前rank
</td></tr>
<tr>
<td>10042.0f</td>
<td>单位当前x坐标
</td></tr>
<tr>
<td>10043.0f</td>
<td>单位当前y坐标
</td></tr>
<tr>
<td>10044.0f</td>
<td>单位当前z（？）坐标
</td></tr>
<tr>
<td>10045.0f</td>
<td>自机当前x坐标
</td></tr>
<tr>
<td>10046.0f</td>
<td>自机当前y坐标
</td></tr>
<tr>
<td>10047.0f</td>
<td>自机当前z（？）坐标
</td></tr>
<tr>
<td>10048.0f</td>
<td>当前单位与自机的夹角
</td></tr>
<tr>
<td>10049</td>
<td>当前单位的计时器（？）
</td></tr>
<tr>
<td>10050.0f</td>
<td>当前单位与玩家的距离
</td></tr>
<tr>
<td>10051</td>
<td>当前单位生命值
</td></tr>
<tr>
<td>10052</td>
<td>机体类型
</td></tr>
<tr>
<td>10053</td>
<td>用于不明用途的第1个参数
</td></tr>
<tr>
<td>10054</td>
<td>用于不明用途的第2个参数
</td></tr>
<tr>
<td>10055</td>
<td>用于不明用途的第3个参数
</td></tr>
<tr>
<td>10056</td>
<td>用于不明用途的第4个参数
</td></tr>
<tr>
<td>10057.0f</td>
<td>用于不明用途的第5个参数
</td></tr>
<tr>
<td>10058.0f</td>
<td>用于不明用途的第6个参数
</td></tr>
<tr>
<td>10059.0f</td>
<td>用于不明用途的第7个参数
</td></tr>
<tr>
<td>10060.0f</td>
<td>用于不明用途的第8个参数
</td></tr>
<tr>
<td>10061</td>
<td>????
</td></tr>
<tr>
<td>10062</td>
<td>????
</td></tr>
<tr>
<td>10063</td>
<td>????
</td></tr>
<tr>
<td>10064</td>
<td>????
</td></tr>
<tr>
<td>10065.0f</td>
<td>????
</td></tr>
<tr>
<td>10066.0f</td>
<td>????
</td></tr>
<tr>
<td>10067.0f</td>
<td>????
</td></tr>
<tr>
<td>10068.0f</td>
<td>????
</td></tr>
<tr>
<td>10069.0f</td>
<td>当前单位角度
</td></tr>
<tr>
<td>10070.0f</td>
<td>当前单位运动（？）角度
</td></tr>
<tr>
<td>10071.0f</td>
<td>当前单位速度
</td></tr>
<tr>
<td>10072.0f</td>
<td>当前单位加速度
</td></tr>
<tr>
<td>10073.0f</td>
<td>当前单位圆周运动半径
</td></tr>
<tr>
<td>10074.0f</td>
<td>当前单位原点x坐标
</td></tr>
<tr>
<td>10075.0f</td>
<td>当前单位原点y坐标
</td></tr>
<tr>
<td>10076.0f</td>
<td>当前单位原点z坐标
</td></tr>
<tr>
<td>10077.0f</td>
<td>当前单位圆周运动速度
</td></tr>
<tr>
<td>10078.0f</td>
<td>当前单位圆周运动角度（存疑）
</td></tr>
<tr>
<td>10079.0f</td>
<td>当前单位移动目标点x坐标
</td></tr>
<tr>
<td>10080.0f</td>
<td>当前单位移动目标点y坐标
</td></tr>
<tr>
<td>10081.0f</td>
<td>当前单位移动目标点z坐标
</td></tr>
<tr>
<td>10082.0f</td>
<td>随机角度
</td></tr>
<tr>
<td>10083.0f</td>
<td>上一帧造成的伤害
</td></tr>
<tr>
<td>10084</td>
<td>boss号
</td></tr>
<tr>
<td>10085.0f</td>
<td>当前单位相对上一帧x坐标的差值
</td></tr>
<tr>
<td>10086.0f</td>
<td>当前单位相对上一帧y坐标的差值
</td></tr>
<tr>
<td>10087.0f</td>
<td>当前单位相对上一帧z坐标的差值
</td></tr>
<tr>
<td>10087.0f</td>
<td>当前单位相对上一帧z坐标的差值
</td></tr>
<tr>
<td>10088</td>
<td>????
</td></tr>
<tr>
<td>10089</td>
<td>????
</td></tr>
<tr>
<td>10090</td>
<td>????
</td></tr>
<tr>
<td>10091</td>
<td>????
</td></tr>
<tr>
<td>10092</td>
<td>????
</td></tr>
<tr>
<td>10093</td>
<td>????
</td></tr>
<tr>
<td>10094.0f</td>
<td>可供随意使用的全局整数变量
</td></tr>
<tr>
<td>10095.0f</td>
<td>可供随意使用的全局整数变量
</td></tr>
<tr>
<td>10096</td>
<td>使魔数
</td></tr>
<tr>
<td>10097</td>
<td>自机是否为妖（通常为低速开启）
</td></tr>
<tr>
<td>10098</td>
<td>????
</td></tr>
<tr>
<td>10099</td>
<td>????
</td></tr>
<tr>
<td>10100</td>
<td>boss的计时器（？）
</td>
</tr>
</tbody></table>






---

此文档由 [THBWiki-Markdown-Builder](https://github.com/Delsin-Yu/THBWiki-Markdown-Builder) 构建。

文档中的所有内容除特殊注明外，均在 [**知识共享(Creative Commons) 署名-非商业性使用-相同方式共享 3.0 协议**](https://creativecommons.org/licenses/by-sa/3.0/deed.zh-hans) 下提供，附加条款亦可能应用。

引用类型与其他类型作品版权归原作者所有，如有作者授权则遵照授权协议使用。

详细请查阅 [THBWiki：免责声明](https://thbwiki.cc/THBWiki:%E5%85%8D%E8%B4%A3%E5%A3%B0%E6%98%8E)。

