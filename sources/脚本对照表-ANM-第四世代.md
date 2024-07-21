# 脚本对照表/ANM/第四世代

<!-- source html: G:\repos\THBWiki-Markdown-Builder\THBWikiMarkdown\Temp\main\0\0f\ns0%3A%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8%2FANM%2F%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3.html -->

脚本对照表

## 目录

- [1 概述](#概述)
- [2 ENTRY范例](#ENTRY范例)
- [3 指令范例](#指令范例)
- [4 随机数分类](#随机数分类)
- [5 变量及特殊变量表](#变量及特殊变量表)
- [6 运算指令(100系)](#运算指令(100系))

  - [6.1 单变量操作](#单变量操作)
  - [6.2 双变量操作](#双变量操作)



- [7 0系＆2系 控制贴图的运行](#0系＆2系_控制贴图的运行)
- [8 3系 贴图图像控制](#3系_贴图图像控制)
- [9 4系 贴图控制](#4系_贴图控制)
- [10 5系 多重贴图控制](#5系_多重贴图控制)
- [11 6系 贴图创建](#6系_贴图创建)




### 概述
  
本对照表是2un的ANM描述文件中的脚本的对照表,适用于神辉绀
未将所有的instruction放入在内，只写了已知的
  
  
提取zun脚本的工具是touhou toolkit.
  

### ENTRY范例
  
对应每个png文件的加载，最前面有几行ENTRY，格式如下（建议随便从附近复制一个改，因为这里大部分都没有研究明白）
  

```
 ENTRY 8                            //不懂，也有ENTRY别的数字的
 Name: loading/sig1280.png          //图片路径
 Format: 1                          //不懂，大的背景图用5可能出现失真
 Width: 256                         //截取图片的宽度，说是截取，也有可能这个数比下面的实际大小要大，具体用处不明
 Height: 1024                       //截取图片的高度
 X-Offset: 1024                     //截取图片的X偏置
 Y-Offset: xxx                      //截取图片的Y偏置
 Unknown1: 10                       //？？？
 Unknown2: 1                        //？？？
 HasData: 1                         //？？？
 THTX-Size: 983040                  //原图片的真实大小，等于真实宽度乘以真实高度乘以4
 THTX-Format: 1                     //建议和上面的Format一样
 THTX-Width: 256                    //原图片的真实宽度
 THTX-Height: 960                   //原图片的真实高度
 THTX-Zero: 0                       //Xnozero（划掉）？？？
```

### 指令范例
  
在每个ENTRY里面会有一些Sprite，截取图片的一部分分配编号
  
  
Sprite: 0 64*112+0+0 这部分是分配png文件的贴图 并赋予序号 0代表序号，64*112代表大小，+0+0代表贴图左上角的坐标
  
  
  

Script: 54 // 54代表 脚本序号号 类似于 ECl中的sub
  
  
Instruction: 0 0 300 12     // 其中第一个数字为 第X帧执行，第二个0 的作用详见运算指令部分
  
  
当第X帧执行的X为 -1(无符号则为65535)时,表明对任何贴图都相同效果(即如果时间为-1的指令中有随机要素,则随机要素只会随机一次)
  

### 随机数分类
```
  2un有两种不同随机数,称为算数随机数和几何随机数(暂定)
  算数随机数会记录在rep中,且在ecl等地方都用,修改后容易rep爆炸
  而几何随机数则不会记录在rep中,通常用于标题菜单,鬼火等无关紧要的随机
```

### 变量及特殊变量表
```
  anm中变量是由数字来表示的,不同于ecl,anm没有堆栈的设计,只有少量的变量可供使用,下列出各变量(由hld获得),其中带&amp;符号的代表可以读写,无&amp;的为只读
```

  
[10000] int&amp; 可随意使用的整数变量
  
  
[10001] int&amp; 可随意使用的整数变量
  
  
[10002] int&amp; 可随意使用的整数变量
  
  
[10003] int&amp; 可随意使用的整数变量
  
  
[10004.0f] float&amp; 可随意使用的浮点变量
  
  
[10005.0f] float&amp; 可随意使用的浮点变量
  
  
[10006.0f] float&amp; 可随意使用的浮点变量
  
  
[10007.0f] float&amp; 可随意使用的浮点变量
  
  
[10008] int&amp; 整数变量
  
  
[10009] int&amp; 整数变量
  
  
[10010.0f] float 随机浮点数,范围±[10028.0f](默认±π),为几何随机数,不被rep保存
  
  
[10011.0f] float 随机浮点数,范围0~[10027.0f](默认0~1),为几何随机数,不被rep保存
  
  
[10012.0f] float 随机浮点数,范围±[10027.0f](默认±1),为几何随机数,不被rep保存
  
  
[10013.0f] float&amp; x相对坐标,可以直接修改
  
  
[10014.0f] float&amp; y相对坐标,可以直接修改
  
  
[10015.0f] float&amp; z相对坐标,可以直接修改
  
  
[10016.0f] float 背景摄像机的x坐标(x轴控制摄像机向左右移动)
  
  
[10017.0f] float 背景摄像机的y坐标(y轴控制摄像机向上下移动)
  
  
[10018.0f] float 背景摄像机的z坐标(z轴控制摄像机向前后移动)
  
  
[10019.0f] float 背景摄像机的LookAt向量的x(即摄像机看向哪里)
  
  
[10020.0f] float 背景摄像机的LookAt向量的y(即摄像机看向哪里)
  
  
[10021.0f] float 背景摄像机的LookAt向量的z(即摄像机看向哪里)
  
  
[10022] int 随机整数,范围0~[10029],为几何随机数,不被rep保存
  
  
[10023.0f] float&amp; x角度,可以直接修改
  
  
[10024.0f] float&amp; y角度,可以直接修改
  
  
[10025.0f] float&amp; z角度,可以直接修改
  
  
[10026.0f] float 可能是使用了500系生成子贴图后子贴图相对的总旋转角
  
  
[10027.0f] float&amp; 用于标定随机浮点数上下限,默认为1.0f,可以修改
  
  
[10028.0f] float&amp; 用于标定随机浮点数上下限,默认为PI,可以修改
  
  
[10029] int&amp; 用于标定随机整数上下限,默认65536
  
  
[10030.0f] float 随机浮点数,范围±[10028.0f](默认±π),为算数随机数,可被rep保存
  
  
[10031.0f] float 随机浮点数,范围0~[10027.0f](默认0~1),为算数随机数,可被rep保存
  
  
[10032.0f] float 随机浮点数,范围±[10027.0f](默认±1),为算数随机数,可被rep保存
  
  
[10033.0f] float&amp; 浮点变量
  
  
[10034.0f] float&amp; 浮点变量
  
  
[10035.0f] float&amp; 浮点变量
  

### 运算指令(100系)
  
在使用运算指令和调用运算的时候要将instruction中的第二个数设置成其中变量所对应的二进制
  
  
例如：
  
  
Instruction: 0 12 407 10 0 10004.0f 10005.0f 0.0f
  
  
这句中变量分别在第三位和第四位，因此第二个参数数为4+8=12.
  

##### 单变量操作
  
100(int a,int b)    变量a=b
  
  
102(int a,int b)    变量a=a+b
  
  
104(int a,int b)    变量a=a-b
  
  
106(int a,int b)    变量a=a*b
  
  
108(int a,int b)    变量a=a/b
  
  
110(int a,int b)    变量a=a%b
  
  
101(float a,float b)    变量a=b
  
  
103(float a,float b)    变量a=a+b
  
  
105(float a,float b)    变量a=a-b
  
  
107(float a,float b)    变量a=a*b
  
  
109(float a,float b)    变量a=a/b
  
  
111(float a,float b)    变量a=a%b
  

##### 双变量操作
  
112(int a,int b,int c)变量a=b+c
  
  
114(int a,int b,int c)变量a=b-c
  
  
116(int a,int b,int c)变量a=b*c
  
  
118(int a,int b,int c)变量a=b/c
  
  
120(int a,int b,int c)变量a=b%c
  
  
113(float a,float b,float c)变量a=b+c
  
  
115(float a,float b,float c)变量a=b-c
  
  
117(float a,float b,float c)变量a=b*c
  
  
119(float a,float b,float c)变量a=b/c
  
  
121(float a,float b,float c)变量a=b%c
  

## 0系＆2系 控制贴图的运行
  
0()
似乎无任何效果
  
  
1()
结束
  
  
2()
将贴图静止化
  
  
3()
暂停之后的ins
  
  
4~8 未知
  
  
5(int n)
  

```
  switch语句(或许叫case语句更好?),用于菜单以及和菜单变化的东西只是改贴图一般也用不到(
  当exe内进行一个函数JmpAnmSwitch(AnmObj*)时,该anm就会跳到下一个ins_5处执行
```

  
10(int a)返回
  
  
101~132 未知
  
  
200(int a,int t)
  

```
  跳转;a为字节数,ins名8字节一个参数4字节,ins名前的两个参数不算在内;在跳转的时候帧数会改变为t,当以字节数跳转的语句的时间大于t的时候,t无效，反之t有效,因此大多数时候可以直接把a设置成0,用t调整跳转到哪条语句
```

  
201(int x,int a,int t)当x&gt;1时跳转(有何用?)
  
  
  

202-213为判断跳转语句相同功能的一对中，第一个为整数版本，第二个为浮点数版本
  
  
示例:ins_202(int x,int y,int a,int t)当x==y时,跳转到a字节,t时间
  


<table>

<tbody><tr>
<th>ins_</th>
<th>作用</th>
<th>ins_</th>
<th>作用</th>
<th>ins_</th>
<th>作用</th>
<th>ins_</th>
<th>作用
</th></tr>
<tr>
<td>202</td>
<td>==</td>
<td>203</td>
<td>==</td>
<td>204</td>
<td>!=</td>
<td>205</td>
<td>!=
</td></tr>
<tr>
<td>206</td>
<td>&lt;</td>
<td>207</td>
<td>&lt;</td>
<td>208</td>
<td>&lt;=</td>
<td>209</td>
<td>&lt;=
</td></tr>
<tr>
<td>210</td>
<td>&gt;</td>
<td>211</td>
<td>&gt;</td>
<td>212</td>
<td>&gt;=</td>
<td>213</td>
<td>&gt;=
</td></tr></tbody></table>


## 3系 贴图图像控制
  
300(int a)
  

```
  选择贴图号
```

  
301(int a,int b)
  

```
  随机选择贴图号a到(a+b),使用的是几何随机数
```

  
  

302(int a)
  

```
  a=0时不旋转,同时角度归零;a=1时贴图一直旋转;a=2时贴图变模糊;a=8:允许贴图3D旋转
```

  
303(int a)
  

```
  根据a设置使魔混合模式(注:此表仅代表和结果类似的混合模式)
  (th15中的测试结果(在游戏中截图与ps比对)：0:无,1:线性减淡;2:减去,3:溶解?,4:差值(完全不准;ps内无类似混合模式),5:将上层贴图进行两次正片叠底,6:使RGB各颜色通过f(x)=sin(x/255*PI)*64变换(例如0xFF1233,经过变换后得到0x001438)(此模式只需一层贴图)7:将下层贴图染上上层贴图颜色其实就是雾霾(对于使魔贴图和背景图处理方式不同);8:正片叠底,9:变亮
  在th18中找到了对应的代码(.text 47D9BD)因此列表说明,但仍保留上面的部分是因为th15的实测有一定不同)
  公式中A为目标颜色向量(r,g,b),a为目标alpha通道向量(alpha,alpha,alpha),B,b为源(背景)的颜色向量/alpha通道向量,r,g,b,alpha∈[0,1],且乘法'*'均为对应分量相乘
```


<table>

<tbody><tr>
<th>类型</th>
<th>描述</th>
<th>公式
</th></tr>
<tr>
<td>0</td>
<td>默认</td>
<td>A*a+B*(1-a)
</td></tr>
<tr>
<td>1</td>
<td>线性减淡</td>
<td>A*a+B
</td></tr>
<tr>
<td>2</td>
<td>减去</td>
<td>B-A*a
</td></tr>
<tr>
<td>3</td>
<td>禁用alpha</td>
<td>A(此时ALPHATESTENABLE=0)
</td></tr>
<tr>
<td>4</td>
<td>排除</td>
<td>A*(1-B)+B*(1-A)
</td></tr>
<tr>
<td>5</td>
<td>正片叠底</td>
<td>A*B
</td></tr>
<tr>
<td>6</td>
<td>这是啥</td>
<td>A*(1-A)+B*(1-a)
</td></tr>
<tr>
<td>7</td>
<td>交换目标/源</td>
<td>A*(1-b)+B*b
</td></tr>
<tr>
<td>8</td>
<td>变暗</td>
<td>min(A*a,B)
</td></tr>
<tr>
<td>9</td>
<td>变亮</td>
<td>max(A*a,B)
</td></tr></tbody></table>


  
304(int a)
图层,a越小越下;当a=26时使魔的位置(0,0)由stage中上变为整个窗口的左上角
  
  
305~307 未知
  
  
308()
左右反转贴图
  
  
309()
上下反转贴图
  
  
310(int a)
贴图可见性,a=1时为可见,渲染时跳过不可见的贴图;每当成功转跳至ins_5处时a会自动被设置为1
  
  
311(int a)
  

```
  根据a设置贴图比例大于或小于1时如何对贴图进行重采样
```


<table>

<tbody><tr>
<th>类型</th>
<th>D3D常量</th>
<th>描述
</th></tr>
<tr>
<td>0</td>
<td>D3DTEXF_LINEAR</td>
<td>线性插值
</td></tr>
<tr>
<td>1</td>
<td>D3DTEXF_POINT</td>
<td>最近点采样
</td></tr></tbody></table>


  
312(int a, int b)
  

```
  根据a和b设置在执行ins_425,ins_426,ins_429,和ins_600等ins时对贴图源文件的寻址模式
```


<table>

<tbody><tr>
<th>类型</th>
<th>D3D常量</th>
<th>描述
</th></tr>
<tr>
<td>0</td>
<td>D3DTADDRESS_WRAP</td>
<td>纹理无限循环
</td></tr>
<tr>
<td>1</td>
<td>D3DTADDRESS_CLAMP</td>
<td>边缘处像素延伸到无穷大
</td></tr>
<tr>
<td>2</td>
<td>D3DTADDRESS_MIRROR</td>
<td>和0一样，但其他所有图像都是镜像翻转
</td></tr></tbody></table>


  
ins313~317 未知
  

## 4系 贴图控制
  
400(float x,float y,float z)
设置初始位置
  
  
401(float x,float y,float z)
  

```
  当302的a为1时，设置贴图角度为x,y,z,2D贴图只要填写z
```

  
402(float x,float y)
设置贴图的横竖缩放比例
  
  
403(int alpha)
改变贴图透明度
  
  
404(int r,int g,int b)
赋予贴图颜色为 rgb
  
  
405(int a)
设置600系渐变色的卜透明度
  
  
406(int r,int g,int b)
设置600系渐变色为rgb
  
  
407(int t,int mode,float x,float y,float z)
在t帧内,用mode方式将贴图移动到x,y,z
  
  
408(int t,int mode,int r,int g,int b)
t帧内赋予贴图颜色为 r g b
  
  
409(int t,int mode,int alpha)
t帧内以mode方式改变透明度alpha(范围0-255,0透明)
  
  
410(int t,int mode,float x,float y,float z)
  

```
  当302的a为1时,设置在t帧之内以mode方式改变角度，2d贴图只要z
```

  
411(int t,int mode,float z)
410阉割版，2D贴图使用,使用方法同410
  
  
412(int t,int mode,float x,float y)
让贴图在t帧以mode方式缩放x,y倍
  
  
413(int t,int mode,int r,int g,int b)
t帧内赋予600系渐变色为 r g b
  
  
414(int t,int mode,int a)
在t帧内以mode方式转换成透明度为a,颜色设置为ins406的贴图,对于600系渐变色只改变使用ins405赋予的渐变色
  
  
415(float x,float y,float z)
当302的a为1时,设置每帧旋转角度为x,y,z,2D贴图只要填写z
  
  
416(float x,float y)
设置贴图每帧横竖缩放比例增加倍率(和原贴图比较的倍率)
  
  
417(int alpha,int time)
在t帧内改变透明度(意义何在)(alpha,time确实是这样的顺序)
  
  
418~423 除421:未知
  
  
420(int t,float x1,float y1,float z1,float x2,float y2,float z2,float x3,float y3,float z3)
  

```
   将贴图在t时间内移动到(x2,y2,z2),(x1,y1,z1)(x3,y3,z3)为移动曲线的锚点
   (照搬ecl上的说明):
   (假设目前坐标为(x0,y0))运动轨迹实际是由(x0,y0)到(x2,y2)的贝塞尔曲线;
   曲线的P1坐标为((x1-x0)*1/3,(y1-y0)*1/3);P2坐标为(-(x3-x2)*1/3+x2,-(y3-y2)*1/3+x2)
   (因此(x3,y3)这个点的坐标实际上是向左x正方向,向上y正方向)
```

  
421(int a)
  

```
  改变贴图的原点
  注:二进制第0,1位决定左右,第16,17位决定上下
  a=0 贴图正中心(5)
  a=1 贴图左中心(4)
  a=2 贴图右中心(6)
  a=65536 贴图上中心(8)
  a=65537 贴图左上角(7)
  a=65538 贴图右上角(9)
  a=131072 贴图下中心(2)
  a=131073 贴图左下角(1)
  a=131074 贴图右下角(3)
```

  
424(int a)
当302的a=1,且该条代码的a=1时自动冲着运动方向旋转
  
  
425(float a)
控制贴图左右相位移动,正数向左
  
  
426(float a)
控制贴图上下相位移动,正数向上
  
  
426~435 未知
  
  
429(float a,float b)
  

```
  把贴图切割成百叶窗形,扇叶数+空格数为b(b可以不是整数),其扇叶长度变为贴图原长度的1/a
```

  
430(int t,int a,float x,float y)
  

```
  令贴图大小在t帧内以a模式缩小为1/x,1/y大小,不同于412的是它会同时显示出原sprite对应源文件中的其他图片
```

  
433(int t,int a,float angle,float r)
按照极坐标方式在t帧内以a方式移动贴图
  
  
436(float x,float y)
将坐标轴翻转之后移动贴图(即左,上为x,y正方向)
  
  
437(int a)
  

```
  改变3d旋转方向
  a=0 以原点为坐标原点,以竖直水平的方向为x,y建立x-y-z坐标转动
  a=1 以当前贴图旋转z角度为z轴,同面建立x坐标,建立坐标系转动
  a=2 是a=1的镜像(?)
  (总之自己到时候试试不就行了么)
```

  
438(int a)
a为2的倍数的时候贴图不显示,不为2倍数则显示
  

## 5系 多重贴图控制
  
500(int a)
在原本的贴图上再加载一个a号script，图层根据script号分配
  
  
501(int a)类似于500,但是不会因esc而停止加载,同时在最上层
  

```
  生成的贴图的x=（贴图使魔.x+192）/2
  y=（贴图使魔.y-224）/2+224
  贴图大小为原来的0.5倍
```

  
502(int a)
和500相同
  
  
503(int a)
和501相同
  
  
504(int a)
增加script a,该贴图不会随着单位运动而运动
  
  
505~509 未知
  

## 6系 贴图创建
  
600(int a)
  

```
   将整个图片(ins_300的sprite对应的整张图片)扭曲成一个(a-1)边的圆环(int a必须是变量10000)
   此时图片的由左向右变成由外而内,当超出图片部分时会自动再生成一个图片
   此时控制图片长宽(ins_402)则长变为圆环环径(大半径-小半径);宽为圆环半径((大半径+小半径)/2)
   此时[10001]为等角平铺次数,例如[10001]=3时,贴图会每120°重复一次
```

  
601(int a)
  

```
   将整个图片扭曲成一个扇环,边数(a-1),int a必须为变量10000
   该图片的长宽通过ins_402控制,长变为环径;宽为半径
   此时[10001]为平铺次数,x角度为扇形的张角
   该扇环中间的一条半径与该贴图的朝向(z旋转角度)相一致(即扇环覆盖了 z角度±x角度/2 的范围)
   由于x角度为[10023.0f],z角度为[10025.0f],因此可以使用ins_401(张角,0.0f,朝向)指定图片朝向,也可以用{ins_101([10023.0f],张角)+ins_101([10025.0f],朝向)}指定
```

  
602(int a)   类似于ins_601,不同之处在于扇环的逆时针方向的一条半径与贴图朝向(z旋转角度)一致(即扇环覆盖了 z角度 到 (z角度+x角度)的范围)
  
  
注:以下创建ins都会覆盖原有贴图,且原本没有贴图则不会生成(所以建议在前面加ins300 -1)
  
  
603(float a,float b)　创建一个大小为a*b的白色矩形(棱角更分明,比607更像p的)(估计是浮点数运算造成的)
  
  
604(float a,int b)　创建一个大小为a,角数为b的星形,其的光晕和内层颜色可控
  
  
605(float a,int b)　创建一个大小为a,角数为b的星形边框
  
  
606(float a,float b)　创建一个a*b的渐变矩形(区别同603,607)
  
  
607(float a,float b)　创造一个大小为a*b的白色矩形
  
  
608(float a,float b)　创建一个a*b的渐变矩形
  
  
612(float a,float b)　创建一个a*b的矩形边框
  
  
613(float a,float b)　创建一个长度为a的线段(b不知道啥用)
  
  
614(float a,float b)　创建一个长度为a的,高度为b的渐变三角形(左为底,右为顶,自底向顶渐变)
  





---

此文档由 [THBWiki-Markdown-Builder](https://github.com/Delsin-Yu/THBWiki-Markdown-Builder) 构建。

文档中的所有内容除特殊注明外，均在 [**知识共享(Creative Commons) 署名-非商业性使用-相同方式共享 3.0 协议**](https://creativecommons.org/licenses/by-sa/3.0/deed.zh-hans) 下提供，附加条款亦可能应用。

引用类型与其他类型作品版权归原作者所有，如有作者授权则遵照授权协议使用。

详细请查阅 [THBWiki：免责声明](https://thbwiki.cc/THBWiki:%E5%85%8D%E8%B4%A3%E5%A3%B0%E6%98%8E)。

