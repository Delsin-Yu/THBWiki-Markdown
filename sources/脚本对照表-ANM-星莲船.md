# 脚本对照表/ANM/星莲船

<!-- source html: G:\repos\THBWiki-Markdown-Builder\THBWikiMarkdown\Temp\main\2\29\ns0%3A%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8%2FANM%2F%E6%98%9F%E8%8E%B2%E8%88%B9.html -->

脚本对照表

## 目录

- [1 概述](#概述)
- [2 指令范例](#指令范例)
- [3 变量及特殊变量表](#变量及特殊变量表)
- [4 运算指令](#运算指令)

  - [4.1 双变量操作](#双变量操作)
  - [4.2 三变量操作](#三变量操作)



- [5 指令表](#指令表)




### 概述
  
本对照表是Zun的ANM描述文件中的脚本的对照表,适用于风地星
  
  
  

提取zun脚本的工具是touhou toolkit.
  

### 指令范例
  
Sprite: 0 64*112+0+0 这部分是分配png文件的贴图 并赋予序号  0代表序号，64*112代表大小，+0+0代表贴图左上角的坐标
  
  
  

Script: 54 // 54代表 脚本序号号 类似于 ECl中的sub
  
  
Instruction: 0 0 68 12     // 其中第一个数字为 第X帧执行，第二个0 的作用详见运算指令部分,第三个数字即是命令序号,之后数字皆为参数
  

### 变量及特殊变量表
```
  anm中变量是由数字来表示的
  浮点变量应从10004.0f开始
  整数变量从10000开始
  特殊变量表：
  10010:[-π,π];
  10011:[0.0f,1.0f];
  10012:[-1.0f,1.0f];
  10013:该贴图中循环完成的次数;
  10022:随机整数
```

### 运算指令
  
在使用运算指令和调用运算的时候要将instruction中的第二个数设置成其中变量所对应的二进制
  
  
例如：
  
  
Instruction: 0 12 407 10 0 10004.0f 10005.0f 0.0f （这句指令摘自第四世代anm描述文件，第三世代与其原理相同）
  
  
这句中变量分别在第三位和第四位，因此第二个参数数为4+8=12.
  

##### 双变量操作
  
 **example: 6(int a,int b)变量a=b** 
  


<table>

<tbody><tr>
<th>ins号</th>
<th>作用（int）</th>
<th>ins号</th>
<th>作用（float）</th>
<th>ins号</th>
<th>作用（int）</th>
<th>ins号</th>
<th>作用（float）
</th></tr>
<tr>
<td>6</td>
<td>=</td>
<td>7</td>
<td>=</td>
<td>8</td>
<td>+</td>
<td>9</td>
<td>+
</td></tr>
<tr>
<td>10</td>
<td>-</td>
<td>11</td>
<td>-</td>
<td>12</td>
<td>*</td>
<td>13</td>
<td>*
</td></tr>
<tr>
<td>14</td>
<td>/</td>
<td>15</td>
<td>/</td>
<td>16</td>
<td>mod</td>
<td>17</td>
<td>mod
</td></tr></tbody></table>


##### 三变量操作
  
 **example:18(int a,int b,int c)       变量a=b+c** 
  


<table>

<tbody><tr>
<th>ins号</th>
<th>作用（int）</th>
<th>ins号</th>
<th>作用（float）</th>
<th>ins号</th>
<th>作用（int）</th>
<th>ins号</th>
<th>作用（float）
</th></tr>
<tr>
<td>18</td>
<td>+</td>
<td>19</td>
<td>+</td>
<td>20</td>
<td>-</td>
<td>21</td>
<td>-
</td></tr>
<tr>
<td>22</td>
<td>*</td>
<td>23</td>
<td>*</td>
<td>24</td>
<td>/</td>
<td>25</td>
<td>/
</td></tr>
<tr>
<td>26</td>
<td>mod</td>
<td>27</td>
<td>mod</td>
<td>-</td>
<td>-</td>
<td>-</td>
<td>-
</td></tr></tbody></table>


### 指令表
  
1()
  

```
   返回/结束
```

  
3(int a)
  

```
   选择贴图号
```

  
4(int a, int t)
  

```
   跳转;a为字节数,ins名8字节一个参数4字节,ins名前的两个参数不算在内;在跳转的时候帧数会改变为t,当以字节数跳转的语句的时间大于t的时候,t无效，反之t有效,因此大多数时候可以直接把a设置成0,用t调整跳转到哪条语句
```

  
6~27见运算指令
  
  
48(float,x,y,z)  
  

```
   设置初始位置
```

  
49(float,x,y,z)  
  

```
   旋转角度
```

  
50(float,x,y) 
  

```
   设置贴图的横竖缩放比例
```

  
51(float,x) 
  

```
   设置贴图的alpha,透明度
```

  
52(int R,int G,int B)
  

```
   赋予贴图颜色为 RGB
```

  
53 (float,x,y,z)  
  

```
   设置自转角速度
```

  
56 (int time ,int mode,float,x,y,z)  
  

```
   time帧内 以mode方式移动到x y z位置
```

  
57 (int time ,int mode,int R,int G,int B)  
  

```
   time帧内 以mode方式 改变贴图颜色
```

  
58 (int time ,int mode,int alpha)  
  

```
   time帧内 以mode方式 改变贴图透明度
```

  
60 (int time ,int mode,float,x,y)
  

```
   time帧内 以mode方式 改变贴图大小比例  
```

  
61()
  

```
   设置此贴图为2d图片(不能被用在3d背景)
```

  
63()
  

```
   暂停之后的ins
```

  
64(int a) 
  

```
   一种switch 根据外部条件选择一个执行
    
```

  
  

65(int a)
  

```
   设置贴图中心点 
   a=65536 时 以最上方的中心为中心点
   a=131072时 以最下方的中心为中心点
```

  
66
  

```
   开关 addictive blending 
```

  
67(int)
  

```
   设置贴图属性,已知
   0 2D贴图
   1 2d ?1
   2 2d ?2
   3 2d ?3
   4 3d billboard
   5 3d smallhill
   6 3d billboard
   7 3d smallhill
   8 3d 平面
```

  
68 (int a)
  

```
   设置 图层 ,0是最底层
```

  
70(float x) 
  

```
   使贴图像走马灯一样运动，x为图像在x轴上运动速度，向左为正方向
```

  
71(float y) 
  

```
   使贴图像走马灯一样运动，y为图像在y轴上运动速度，向上为正方向
  
```

  
75(int x)
  

```
   x后开始
```

  
76(int R,int G,int B)
  

```
   设置渐变色的RGB值
```

  
77(int alpha)
  

```
   设置渐变色的透明度
```

  
79(int time,int mode,int alpha)
  

```
   在time帧内，以mode方式改变渐变色透明度为alpha
```

  
88(int x)
  

```
   选择 Script x
```

  
101(int 10000)
  

```
   example:0 0 6 10000 x
           0 0 6 10001 y
           0 1 101 10000
   将贴图扭曲为正(x-1)边形，使用y张贴图铺满，使用49x参数设置多边形范围，z设置多边形方向，50设置大小，可配合70和71使用（具体效果自己试试就知道了）
```

  
102(float a,float b)
  

```
   创建一个大小为a*b的白色矩形
```

  
104(float a,int b)
  

```
   创建一个大小为a,角数为b的正多边形,使用ins52设置中心颜色,ins51设置中心透明度，ins76设置边沿颜色，ins77设置边沿透明度,由中心向边沿渐变
```

  
105(float a,int b)
  

```
   创建一个大小为a,角数为b的正多边形边框
```





---

此文档由 [THBWiki-Markdown-Builder](https://github.com/Delsin-Yu/THBWiki-Markdown-Builder) 构建。

文档中的所有内容除特殊注明外，均在 [**知识共享(Creative Commons) 署名-非商业性使用-相同方式共享 3.0 协议**](https://creativecommons.org/licenses/by-sa/3.0/deed.zh-hans) 下提供，附加条款亦可能应用。

引用类型与其他类型作品版权归原作者所有，如有作者授权则遵照授权协议使用。

详细请查阅 [THBWiki：免责声明](https://thbwiki.cc/THBWiki:%E5%85%8D%E8%B4%A3%E5%A3%B0%E6%98%8E)。

