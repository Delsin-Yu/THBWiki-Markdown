# 脚本对照表/ECL/第三世代

<!-- source html: G:\repos\THBWiki-Markdown-Builder\THBWikiMarkdown\Temp\main\0\0d\ns0%3A%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8%2FECL%2F%E7%AC%AC%E4%B8%89%E4%B8%96%E4%BB%A3.html -->

脚本对照表


## 目录

- [1 概述](#概述)
- [2 2系 设置贴图，播放特效动画，创建单位](#2系_设置贴图，播放特效动画，创建单位)
- [3 3系 单位移动](#3系_单位移动)
- [4 4系  单位固有属性](#4系_单位固有属性)
- [5 5系  弹幕相关](#5系_弹幕相关)
- [6 6系  激光相关](#6系_激光相关)
- [7 7 Debug](#7_Debug)
- [8 509指令详解](#509指令详解)
- [9 FLAG表](#FLAG表)





### 概述
  
本对照表是Zun的第三代ecl脚本的对照表,适用于星，ds，dzz3作
以下均是基于th12 星莲船的脚本制成，
文花帖DS和妖精大战争与有一小部分不同
  
  
对于其他作的参考
  
  
第一代ecl脚本红妖永花,文花帖.由于与此表差异很大,故不能作任何参考.
  
  
第二代ecl脚本对应风地
  

```
   第二代中280对应此表中300，320对应此表中400，400对应此表中500，其余大体可以按顺序对照.
```

  
第三代ecl脚本对应星，文花帖ds和大战争
  
  
第四代ecl脚本对应城，天邪鬼，绀珠传
  

```
   第四代中300对应此表中256,400对应此表中300，500对应此表中400，600对应此表中500，其余大体可以按顺序对照.
```

  
提取zun脚本的工具是touhou toolkit.
  
  
以下即是所有存在的ins,是读取汇编所获得的
  
  
红色代表功能未知，需要测试和研究
  
  
蓝色代表虽然并未完全解读，但是大体功能已经知道，且此函数用途十分有限
  
  
灰色代表是前作特殊地点使用过之后完全被抛弃的
  
  
棕色部分是文花帖DS新增
  
  
青色部分是妖精大战争新增
  


### 2系 设置贴图，播放特效动画，创建单位
  
与256类似的这类ins，在创建单位的时候会自动执行与该单位同名的sub。
  
  
256("xxx", float x, float y, int life, int bonus, int item);
  

```
 以相对召唤者为基准点在位置xy，创建一个单位xxx，设置血量，分数以及基本掉落。
 
```

  
257("xxx", float x, float y, int life, int bonus, int item);
  

```
 在绝对位置xy，创建一个单位xxx，设置血量，分数以及基本掉落。用于boss
```

  
258(int); 
  

```
  选择ANM文件。一般来说0即是Bullet.anm，1即是Enemy.anm,2开始就是当面的boss相关anm
```

  
259(int slot,int a) 
  

```
  在相应slot上,设置单位贴图,a对应由上一个258选择的ANM文件中的SCRIPT号
 若使用529则单位不会因为左右移动而改变贴图
```

  
260("xxx", float x, float y, int life, int bonus, int item);
  

```
  和256的基本功能一样，但是移动方式为左右镜像。
```

  
261("xxx", float x, float y, int life, int bonus, int item);
  

```
 和257的基本功能一样，但是移动方式为左右镜像。
```

  
262(int slot,int a) 
  

```
 在相应slot上,设置单位贴图,a对应由上一个258选择的ANM文件中的SCRIPT号
 若使用262且slot 0，则单位会因为左右移动而改变贴图,
 若slot不为0，则和259无区别.
```

  
263(int a,int b) 
  

```
 在单位当前位置播放ANM文件a的第b个动画效果，b对应由上一个258选择的ANM文件的 script号
```

  
264(int a,int b) 
  

```
 在左上角播放ANM文件a的第b个动画效果，b对应由上一个258选择的ANM文件的 script号 
```

  
265("xxx", float x, float y, int life, int bonus, int item);
  

```
 用于增员(boss存在时不执行)，其余和256一样
```

  
266("xxx", float x, float y, int life, int bonus, int item);
  

```
 用于增员，其余和257一样
```

  
267("xxx", float x, float y, int life, int bonus, int item);
  

```
 用于增员，其余和260一样
```

  
268("xxx", float x, float y, int life, int bonus, int item);
  

```
 用于增员，其余和261一样
 
```

  
269(int a) 
  

```
 在单位当前位置播放之前选择的ANM文件的第a个动画效果，a对应由上一个258选择的ANM文件的 script号
```

  
270("xxx", float x, float y, int life, int bonus, int item);
  

```
 一种未知的创建单位函数
```

  
271("xxx", float x, float y, int life, int bonus, int item);
  

```
 用于增员,其余和270一样
```

  
272(int a,int b)
  

```
  和263功能基本一样,区别未知
```

  
273(int a,int b,float c)
  

```
 选择a号贴图文件的b号单位贴，旋转至c方向贴出。此贴图不会消失而是一直存在于屏幕上。（配合自带延迟消失指令的单位贴可以做出类似残影效果。）
```

  
274(int slot,int b)
  

```
   发弹时(应为循环时)，在相应slot播放动作 b，b对应由上一个258选择的ANM文件的 script号
```

  
275(int slot,int b)
  

```
   播放slot预选好的动画,并且遇到anmins_64时,选择b号执行
   注：anmins_64是一种switch分支结构,默认选择0号。
```

  
276()重置所有动画相关.移除flag0x80000
  
  
277(int slot,float b)
  

```
 旋转在相应slot的贴图至b方向。会旋转方形判定和612的方形消弹。
```

  
278(int slot,float b,float c)
  

```
  用于改变slot位置贴图的大小 倍率为 b和c
```

  
279(int slot,float x,float y)
  

```
  把相应slot的贴图移动到相对位置,x,y.高速来回运动可制造震动效果
```

  
280("xxx", float x, float y, int life, int bonus, int item);
  

```
  用于创建mapleenemy,即背景的枫叶动画效果
```

  
281(int slot,int b)
  

```
  只有在莲妈身后的花和翅膀使用，用途不明
```

  
282(int slot,int b)
  

```
  文花帖DS新增，设置本单位被拍掉时候显示的动画，从bullet.anm里的script b号
```

  
283(float a,float b,int c)
  

```
  DZZ新增
```


### 3系 单位移动
  
每一个单位都有三套坐标. 
即最终实际坐标,绝对坐标以及相对坐标,任何时候最终实际坐标=绝对坐标+相对坐标
  
  
单位被创建出来时,那个坐标即是绝对坐标,初始相对坐标为(0,0)
  
  
所有移动相关函数都是一对一对的
基本功能相同以外,第一个是改变绝对坐标,第二个改变相对坐标
  
  
  

300
MoveDirect(float x,float y);  
  

```
改变,目标作为,x,y.
```

  
301
MoveByTime(int time,int mode,float x,float y);
  

```
  将目标移动到,x,y位置.持续time帧，mode为移动方式，
```

  
302
MoveDirect2(float x,float y);  和300成对
  
  
303
MoveByTime2(int time,int mode,float x,float y);和301成对
  
  
  

304
SetUnitSpeed(float direction, float speed);
  

```
  设置移动方向以及速度
```

  
305
ChangeUnitSpeed(int time, int mode, float direction, float speed);
  

```
   改变移动方式为某个方向以某个速度移动移动。改变时间为time 改变方式为mode
   mode有四种
   0---线性  1----加速   4----减速  9----平滑 
```

  
306
SetUnitSpeed2(float direction, float speed);和304成对
  
  
307
ChangeUnitSpeed2(int time, int mode, float direction, float speed);和305成对
  
  
308
CircleMove(float θ,float speed,float radius,float,rspeed);
  

```
   使单未进行圆周运动,曲线的极坐标（原点为单位之前的位置）(radius,θ)
   θ的增速为speed，radius增速为 rspeed 
```

  
309
CircleMoveChange(int time,int mode, float speed, float radius, float rspeed);
  

```
    time帧之内改变单位圆周运动的参数,方式为mode.各参数参考308
```

  
310
CircleMove(float θ,float speed,float radius,float,rspeed);; 和318成对
  
  
311
CircleMoveChange(int time,int mode, float speed, float radius, float rspeed);和309成对
  
  
312
MoveRandom(int time,int mode,float speed); 
  

```
    目标向随机点移动一次，持续time帧，速度为speed,移动方式为mode。mode和305相同
  
```

  
313
MoveRandom(int time,int mode,float speed); 和312成对
  
  
314()将单位移动至boss的位置,此函数若在无boss时使用会导致严重误访问而爆炸
  
  
315()和314成对
  
  
316(float x,float y,float height)瞬间移动到与当前位置偏移x,y的位置,并且改变单位深度，此深度只适用于风神录（296）四面的潜水怪
  
  
317(float x,float y,float height))和316成对
  
  
318(float x,float y)仅在前作FSL（298）6面神妈的圈圈移动上使用
  
  
319(float x,float y)和318成对
  
  
320(float θ,float speed,float radius,float,rspeed,float dir,float rate)
  

```
    使单未进行椭圆运动,曲线的极坐标（原点为单位之前的位置）(radius,θ)
    θ的增速为speed，radius增速为 rspeed,dir为 椭圆偏离的方向，rate为长半轴与短半轴的比例
```

  
321(int time,int mode, float speed, float radius, float rspeed,float dir,float rate)
  

```
    time帧之内改变单位圆周运动的参数,方式为mode.各参数参考320
```

  
322(float θ,float speed,float radius,float,rspeed,float dir,float rate);和320成对 
  
  
323(int time,int mode, float speed, float radius, float rspeed,float dir,float rate);和321成对
  
  
324(int a)
  

```
  当a =1的时候赋予单位flag（ins_402中的）0x00040000,a=0的是消除
  此flag会赢304和305,效果为左右翻转
  
```

  
325(int time,float x1,float y1,float x2,float y2,float x3,float y3)
  

```
  在time时间内将单位最终移动至点x2,y2.
  期间首先向点x1,y1移动和一点时间再向
  终点偏差x3,y3移动一段时间再移动至终点x2,y2.
```

  
326(int time,float x1,float y1,float x2,float y2,float x3,float y3)和325成对
  
  
  

327()
  

```
  初始化和清零移动相关参数有关
```

  
328(int)304的无视flag0x40000(左右翻转)版
  
  
329(int)305的无视flag0x40000(左右翻转)版
  
  
330(int)306的无视flag0x40000(左右翻转)版
  
  
331(int)307的无视flag0x40000(左右翻转)版
  
  
332(int)未知
  
  
333(int)未知
  


### 4系  单位固有属性
  
400
HitBox(float width,float height)  目标被弹判定
  
  
401
KillBox(float width,float height)  目标体术判定
  
  
402
SetUnitOptions(int flag) 
  

```
 设置单位的一些特定参数,a为一个16字节的开关参数0000000000000000
```

  
  

  
  
  
 
  
  
403
UnSetUnitOptions(int a)
  

```
 取消402设置的参数,和402刚好相反
```

  
404
SetMoveArea(float x,float y,float m,float n,);
  

```
 限制boss的移动范围，以x,y为基准+- n 和m的范围
 注.此函数在thtk解出来的文件里第一个参数被误解成整数，实际为浮点
```

  
405()
  

```
 移除boss移动范围限制
```

  
406
ClearDrops()清除掉落
  
  
407
SetDrops(int type,int amount)
  

```
 目标掉落道具及数量
 1.p点 2蓝点 3.大p 4.残碎片 5B碎片，6残机 7Bomb 8大F 9小最大得点，每100个加10得点
  10固红11固蓝12固绿13变红14变蓝15变绿
   16是击破碟给的那一坨红点，没东西估计还要加别的参数，17是那一坨蓝点，里面也没东西，18是一坨红蓝点
```

  
  

408
SetDropArea(float width,float height)设置掉落区域
  
  
409
Drop()掉落所有道具
  
  
410
SetBasicDrop(int type) 设置目标基本掉落，数量是1.
  
  
411
SetLife(int life)  更改单位血量
  
  
412(int a)
  

```
 a=0，设为boss战模式（血条，名字等），赋予单位flag0x00400000
 
```

  
，a=-1，结束boss。消除单位flag0x00400000
  
  
  

413()boss 重置时间
  
  
414
SetNextPattern(int a，血量，时间，“阶段变量名”),
  

```
 当血量和或时间达到此数值时 载入下一阶段（符卡或非符）
  *a的作用未知* 
```

  
415
Invisible(int time) 无敌时间，
  
  
416
PlaySE(int)播放音效 
  
  
417(int a，int b，int c) 
震屏特效。a为持续时间（帧），bc均与震屏强度有关，都是越大震动越强，区别不明。
  
  
  

418
Talk（int） 读取对话，参数对应msg文件
  
  
419
AfterTalk（）对话后进行下一条
  
  
420
AfterKill（）击破后进行下一条 
  
  
421
TimeOut（int a，“func”）
  

```
 时间到0时进行func的内容，a作用未知
```

  
422
SetSpellCard(int a, int life, int score, "X符:XXXX"); 
  

```
 进入符卡模式，设置符卡宣言后右上角 符卡时间，scb，符卡名，a和符卡序号有关
 EX面使用
```

  
  

423
EndSpellCard()
  

```
 结束符卡模式
```

  
424
SetChapter(int)
  

```
 设置gzz里的结算点，从xlc就开始使用过
```

  
425
ClearUnits()
  

```
 清除该单位创建的子单位.
```

  
426
SetProtectArea(float)
  

```
设置弹幕生成保护范围（距离）自机在此范围内时不发弹
```

  
427
SetLifeBar(int a, float life, int color); 
  

```
 设置血条上的标记点，a是标记序号，life对应血量，
  *color 是RGB三个字节连在一起的数* 
```

  
428
SetSpellCard(int a, int life, int score, "X符:XXXX"); 
  

```
 进入符卡模式，设置符卡宣言后右上角 符卡时间，scb，符卡名，a和符卡序号有关
 未使用 
```

  
RANK一直存在于游戏程序中，收点+rank miss减rank
  
  
429(%N，float a,b,c)根据RANK决定变量N
  
  
430(%N，float a,b,c,d,e)根据RANK决定变量N
  
  
431(%N，float a,b)根据RANK决定变量N
  
  
432($M，int a,b,c)根据RANK决定变量M
  
  
433($M，int a,b,c,d,e)根据RANK决定变量M
  
  
434($M，int a,b)根据RANK决定变量M
  
  
  

435($M,int a,b,c,d)根据难度将数据写入整数M中
  
  
436(%N,float a,b,c,d)根据难度将数据写入浮点数N中
  
  
437
SetSpellCard(int a, int time, int score, "X符:XXXX"); 
  

```
 进入符卡模式，设置符卡宣言后右上角 符卡时间，scb，符卡名，a和符卡序号有关
 非EX面关底使用 
```

  
438
SetSpellCard(int a, int time, int score, "X符:XXXX"); 
  

```
 进入符卡模式，设置符卡宣言后右上角 符卡时间，scb，符卡名，a和符卡序号有关
 未使用 
```

  
439
SetSpellCard(int a, int time, int score, "X符:XXXX"); 
  

```
 进入符卡模式，设置符卡宣言后右上角 符卡时间，scb，符卡名，a和符卡序号有关
 非EX面道中使用
```

  
440
SetBossStar(int)设置剩余阶段数(左上角的星星数)
  
  
441(int)仅在风神录(对应ins_361)使用过,为4,5,6面某些效果设置,
和415(int)无敌类似
  
  
442
  

```
  Survival() 设置符卡为时符
```

  
443()
  

```
  星莲船的三个时符均使用.具体效果未知
```

  
444(int a)
  

```
  当a =1的时候赋予单位flag（ins_402中的）0x04000000,a=0的是消除
```

  
445()
  

```
  清楚特定内存并重置boss一些参数，
  除了boss1非以外，每一张非和卡都出现和,boss逃跑和死亡也会出现
```

  
446(int a,int b)
当a =1的时候赋予单位flag（ins_402中的）0x08000000,a=0的是消除
此flag会使boss对Bomb免疫,并且由b来决定放b时的播放的动画
同时会消除单位flag（ins_402中的）0x10000000,
  
  
  

447(float)设置时间倍率，1.0是正常，击破后减速可以设成0.5，咲夜时停是设成0.0
  
  
448(int a,b,c,d)
  

```
 根据难度等待x帧
```

  
449(int a)
  

```
  当a =1的时候赋予单位flag（ins_402中的）0x40000000,a=0的是消除
```

  
450(int a)仅在地灵殿(对应ins_370)四面道中boss的鬼火使用过,效果不明.即使删除也没有任何影响.之后被zun遗弃 ebx+234= a
  
  
451(int a)仅在地灵殿(对应ins_371)四面道中2boss离场时使用.之后被zun遗弃,ebx+238= a
  
  
452(int a)
  

```
 提高贴图图层a层,对时间值为0的贴图没用
```

  
453(int a)
设置打击音效
  
  
454() 显示logoenemy
  
  
455(int %A,int b)
  

```
  检查第b号单位是否存活，若存活测A=1,否则A=0.单位的编号就是单位登场的顺序.main为0号，
```

  
456(float %A,float %B,int c)
  

```
  将第c号单位的坐标存入A 和B
```

  
457()文花帖DS新增
  
  
458(int a)文花帖DS新增
  

```
  单个关卡的时间,a=时间,单位为帧,一般在开头就有宣称
```

  
459(int a)文花帖DS新增
  

```
  创建一个高分圈,高分圈起始半径大小为固定值,a=高分圈缩小速度.即a值越高,收缩速度越慢
```

  
460(float a)文花帖DS新增
  

```
  具体未知,跟分值有关.一般在DS的ecl开头设置,a的值越大分值（倍率）越高
```

  
461(float a)文花帖DS新增
  
  
462(int a)文花帖DS新增（注：灵梦大方札卡里有，不明）
  
  
463(CString)文花帖DS新增
  


### 5系  弹幕相关
  
500
CreateBullet(int a) 创建一个弹幕，编号为a，
  
  
501
Fire(int a) 发射a号子弹
  
  
502
BShape(弹幕编号,int a,int b) 设置弹幕贴图,a b 对应 bullet.Anm文件中description文件的内容。 表格中的子弹编号为a,b的形式,例如“0,0-15”表示a=0,b为0到15中间的任意整数。当a不为表格里数值时游戏会崩溃;当a确定后,b不为表格里数值的整数时弹型均为点弹。特殊的,当a为23,24,29,31时无论b取何值弹型均不变。
  


<table>

<tbody><tr>
<th>子弹编号</th>
<th>弹型</th>
<th>子弹编号</th>
<th>弹型</th>
<th>子弹编号</th>
<th>弹型</th>
<th>子弹编号</th>
<th>弹型
</th></tr>
<tr>
<td>0</td>
<td>点弹</td>
<td>1</td>
<td>点弹</td>
<td>2</td>
<td>葡萄弹</td>
<td>3</td>
<td>小玉
</td></tr>
<tr>
<td>4</td>
<td>小玉</td>
<td>5</td>
<td>环玉</td>
<td>6</td>
<td>环玉</td>
<td>7</td>
<td>米弹
</td></tr>
<tr>
<td>8</td>
<td>链弹</td>
<td>9</td>
<td>针弹</td>
<td>10</td>
<td>札弹</td>
<td>11</td>
<td>鳞弹
</td></tr>
<tr>
<td>12</td>
<td>铳弹</td>
<td>13</td>
<td>消弹效果</td>
<td>14</td>
<td>菌弹</td>
<td>15</td>
<td>小星弹
</td></tr>
<tr>
<td>16</td>
<td>钱币</td>
<td>17</td>
<td>中玉</td>
<td>18</td>
<td>中玉</td>
<td>19</td>
<td>椭弹
</td></tr>
<tr>
<td>20</td>
<td>刀弹</td>
<td>21</td>
<td>蝶弹</td>
<td>22</td>
<td>大星弹</td>
<td>23</td>
<td>水光弹
</td></tr>
<tr>
<td>24</td>
<td>火光弹</td>
<td>25</td>
<td>心弹</td>
<td>26</td>
<td>大玉</td>
<td>27</td>
<td>蔷薇弹
</td></tr>
<tr>
<td>28</td>
<td>水滴弹</td>
<td>29</td>
<td>紫光炎弹</td>
<td>30</td>
<td>激光段</td>
<td>31</td>
<td>空白
</td></tr></tbody></table>


  
503
BPositionXY(弹幕编号，float x，float y)  以基准发弹点用直角坐标的方式偏移发弹点。基准发弹点默认是单位目前坐标
  
  
504
BDirection(弹幕编号, float dir, float r);
  

```
  设置弹幕方向为 dir，每way之间的角度差为r
```

  
505
BSpeed(弹幕编号, float speed, float s); 
  

```
   设置弹幕速度为 speed，最后一层的速度为s
```

  
506
BAmount(弹幕编号，int way，int ceng)
  

```
    设置弹幕的way数和层数，
```

  
507
BStyle(弹幕编号，int style )
  

```
  根据style设置弹幕展开的形状，若此弹幕是1way 1层的，则无影响 
 （stlye =0 自机狙普通1 普通。2自机狙右偏开花，3右偏开花 4自机狙左偏开花，5左偏开花 6一坨 7散开一坨，8一 坨,9自机狙金字塔开花，10 金字塔开花 11 上下？ 12.开花）
  （这部分可能不完全准确）
```

  
508
BSE(弹幕编号, int a,int b);
  

```
  设置弹幕音效，a是发弹音效，b是变向音效。不设置的话就是默认。-1代表没有音效
```

  
509
BMode(弹幕编号，变换序号,通道,int mode,int a,int b,float r,float s)
  
  
510
Bclear()全屏消蛋,不增加得点
  
  
511
BCopy(int a,int b)复制弹幕b到a中,弹幕属性仅复制这个函数使用之前设定的，
  
  
512(float r)消掉半径为r范围内的弹幕,消掉的弹幕变为最大得点
  
  
513(float r)消掉半径为r范围内的弹幕,不增加得点
  
  
风开始zun放弃使用rank，但是rank这个变量依旧存在于程序中且和红魔乡的增减方法相同
故以下函数仍然可以使用
  
  
514(弹幕编号，float a,b,c,d,e,f)
  

```
 根据Rank的值512个-512比较来决定弹速
```

  
515(弹幕编号，float a,b,c,d,e,f,g,h,i,j)
  

```
 根据Rank，和各种值来决定弹速
```

  
516(弹幕编号，float a,b,c,d)
  

```
 未知,根据Rank决定弹速
```

  
517(弹幕编号，int a,b,c,d,e,f)
  

```
 根据Rank值和512个-512比较来决定way数和层数
```

  
518(弹幕编号，int a,b,c,d,e,f,g,h,i,j)
  

```
 和514类似,比较Rank，和各种值来决定way数和层数
```

  
519(弹幕编号，int a,b,c,d)
  

```
 未知,根据内存Rank决定way数和层数
```

  
520(%N,float x,float y) 计算 点x,y到 自机到角度并存入N中
  
  
  

521(弹幕编号，float a,b,c,d,e,f,g,h)
  

```
 505的难度结合版，即如果难度为Easy 则相当于ins_505(弹幕编,a,e)
```

  
522(弹幕编号，int a,b,c,d,e,f,g,h)
  

```
 506的难度结合版，即如果难度为Easy 则相当于ins_506(弹幕编,a,e)
```

  
523(弹幕编号，float o，float r)  以基准发弹点用极坐标的方式偏移发弹点，角度为o，半径为r。
  
  
524(弹幕编号，float dis) 设置发弹点。以boss为半径为dis的圆形边上发弹。
  
  
525(弹幕编号，float x，float y)设置发弹基准点 
  
  
526(flout r,int color)
  

```
 设置boss周围的纹理变化特性，影响半径为r，颜色为 color，对应RGB颜色，
```

  
527(int a)
  

```
 执行STD背景脚本a
```

  
528(int a)
  

```
 当a=1时 隐藏boss血量和 时间（是否无敌和锁时间待测试）
```

  
529(int a)
  

```
 根据a赋予某种特殊效果，和534使用同一列表
 534是一次性执行某种效果，而529是赋予一种属性
 具体参考534
```

  
530(int a)
  

```
 封装函数，当a=1时，单位的被弹判定采用特殊方式
```

  
531(int a)
  

```
 封装函数，当a=1时，单位的体术判定采用特殊方式
```

  
532(float r)
  

```
 消掉半径为r范围内的弹幕,消掉的弹幕变为最大得点,与512还有一处不同
```

  
533(float r)
  

```
 消掉半径为r范围内的弹幕,不增加得点,与513还有一处不同，仅在前作dld（447）三面勇仪1符圈圈消蛋使用，此圈圈不会消自身的大玉
```

  
534(int a)
  

```
 根据立即执行某种效果a=0,则无
 1.船长时符使用
         额外参数无
 2.exboss符卡中，显示飞碟击破后的分数
         额外参数9985=未知（例1）
 3.exboss 5卡弹幕奇美拉 激光变成光弹
         额外参数无,是个完全封装好没法修改的函数
 4.exboss 5卡弹幕奇美拉 光弹变成激光
         额外参数无,是个完全封装好没法修改的函数
 5.exboss终符恨弓激光变米蛋,
         额外参数9980.0f =弹速，9981.0f=未知（例40.0f），9985=未知（例60） 
 a =6，推测效果为飞钵子弹和线的互动相关（此由529赋予）
 a=7，生成ds里早苗的雷的周围的线（由529赋予）
```

  
535(int a)未知
  
  
536(int a)文花帖DS新增
  
  
537(int a,b,c,d,e,f,g,h,float i,l,k,l)DZZ新增
  
  
538(int a,int b)DZZ新增
  


### 6系  激光相关
  
600(弹幕编号,float a,float length,float b,float width)
  

```
 使弹幕变成激光，设置长度和宽度，a和b是开始位置的参数，一般激光设成0就行
 17条爆弹那种预警线+直接生产的设置成和长度一样
 若要发射曲线激光，则a,length,b 都是无关参数，设成-1.0f,曲线激光只可以设置宽度.
```

  
601(弹幕编号,int a,int b,int c,int d, int e)
  

```
  设置预警线持续时间a和激光的持续时间c. b和d分别是从预警线变为实际激光和激光消失过程需要的时间，e一般为0
   用途未知
   若发射曲线激光则，则b,c,d,都是无关参数，a是激光发射持续时间（决定其长度） e让然是迷之0
```

  
602(弹幕编号)普通激光的发弹函数
  
  
603(弹幕编号,int a) 发射预警线激光专用，a为激光编号，区别于弹幕编号
  
  
604(激光编号,float x,float y) 改变激光的起点为x,y
  
  
605(激光编号,float speed,float direction) 赋予激光起点一个速度和方向
  
  
606(激光编号,float lenth) 改变激光的宽度为lenth
  
  
607(激光编号,float width) 改变激光的宽度为width
  
  
608(激光编号,float a) 改变激光的角度为a
  
  
609(激光编号,float a) 
  

```
赋予激光一个顺时针的角速度a
```

  
610(激光编号) 消除激光
  
  
611(弹幕编号) 曲线激光用发弹函数
  
  
612(float length,float width) 文花帖DS新增 ，沿slot 0贴图方向length x width矩形范围内消弹
  
  
613(int a,?) DZZ新增
  
  
614(int a,int b) DZZ新增
  
  
615(int a,int b) DZZ新增
  


### 7 Debug
  
700(int a) Debug相关，我们用不到
  


### 509指令详解
  
mode
  

```
 这指令本质是弹幕的高级变换，这些变换根据mode不同而不同
 mode是一个32位的开关，
 例mode = 4，则2进制数为，
 0000 0000 0000 0000 0000 0000 0000 0100 
 即打开第三个开关，
 一次是你打开一个开关，因此mode只能是2的n次方.
 具体请查看下表
```

  
变换序号
  

```
 变换从变换序号0开始依次执行，
```

  
  

  

```
 例如
 509(弹幕编号,0.......)
 509(弹幕编号,1.......)
 509(弹幕编号,3,.......)
 509(弹幕编号,4,.......)
 这里少了序号2,所以后面两个不会执行
```

  
换
  
  
通道
  

```
 当通道为0的时候变换都是一个完成后执行下一个
 而同道为1的变换则会同时进行.
```

  
  
  
mode表
  

```
 O表示需要此参数,X表示无关参数
 注意此表是以xlc为准  dzz的mode表请以第四世代mode表为准
```


<table>

<tbody><tr>
<th>序号</th>
<th>10进制</th>
<th>16进制</th>
<th>参数a</th>
<th>参数b</th>
<th>参数r</th>
<th>参数s</th>
<th>功能
</th></tr>
<tr>
<td>0</td>
<td>1</td>
<td>0x1</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>弹幕生成时向前蹿一小段距离
</td></tr>
<tr>
<td>1</td>
<td>2</td>
<td>0x2</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>根据a设置弹雾
</td></tr>
<tr>
<td>2</td>
<td>4</td>
<td>0x4</td>
<td>O</td>
<td>X</td>
<td>O</td>
<td>O</td>
<td>设置加速度为r，加速时间a，s为加速度的角度，s=-999999.0f为初始方向
</td></tr>
<tr>
<td>3</td>
<td>8</td>
<td>0x8</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>设置切向加速度为r，s自转角速度，持续时间为a，b一般情况下不使用,当变换对象是曲线激光时，各个变换将会同时进行，此时b来设置b帧后执行.
</td></tr>
<tr>
<td>4</td>
<td>16</td>
<td>0x10</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>a帧后停顿，之后方向变为原方向+r，速度变为s，变化次数为b,
</td></tr>
<tr>
<td>5</td>
<td>32</td>
<td>0x20</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>a帧后停顿，之后方向变为自机狙+r，速度变为s，变化次数为b,,
</td></tr>
<tr>
<td>6</td>
<td>64</td>
<td>0x40</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>a帧后停顿，之后方向变为r，速度变为s，变化次数为b,,
</td></tr>
<tr>
<td>7</td>
<td>128</td>
<td>0x80</td>
<td>-</td>
<td>-</td>
<td>-</td>
<td>-</td>
<td>未使用，保留
</td></tr>
<tr>
<td>8</td>
<td>256</td>
<td>0x100</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>X</td>
<td>触壁反弹，a为反弹次数，b为一个4位的2进制数来设置可反弹墙壁，从左到右依次为右左下上，例如b=12(1100)则可以在左右版边反弹，r为反弹后的速度
</td></tr>
<tr>
<td>9</td>
<td>512</td>
<td>0x200</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>设置弹幕不可消弹时间为a帧，这段时间内无法消取本弹幕
</td></tr>
<tr>
<td>10</td>
<td>1024</td>
<td>0x400</td>
<td>O</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>设置子弹可以在屏幕外持续的时间为a帧,<span style="color:red;">b作用未知</span>.
</td></tr>
<tr>
<td>11</td>
<td>2048</td>
<td>0x800</td>
<td>O</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>改变弹幕形状为a，b 同16777216相比，改变形状时会生成弹雾
</td></tr>
<tr>
<td>12</td>
<td>4096</td>
<td>0x1000</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>a帧后执行下一个变换
</td></tr>
<tr>
<td>13</td>
<td>8192</td>
<td>0x2000</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>消除子弹
</td></tr>
<tr>
<td>14</td>
<td>16384</td>
<td>0x4000</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>播放音效a
</td></tr>
<tr>
<td>15</td>
<td>32768</td>
<td>0x8000</td>
<td>-</td>
<td>-</td>
<td>-</td>
<td>-</td>
<td>未使用，保留
</td></tr>
<tr>
<td>16</td>
<td>65536</td>
<td>0x10000</td>
<td>-</td>
<td>-</td>
<td>-</td>
<td>-</td>
<td>未使用，保留
</td></tr>
<tr>
<td>17</td>
<td>131072</td>
<td>0x20000</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td><span style="color:red;">未知</span>
</td></tr>
<tr>
<td>18</td>
<td>262144</td>
<td>0x40000</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td><span style="color:red;">未知</span>
</td></tr>
<tr>
<td>19</td>
<td>524288</td>
<td>0x80000</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>在当前子弹位置创建新的弹幕，a实际为4个1字节整数连在一起，从左到右分别为507的展开形式，502的形状和颜色，以及创建之后跳到的变换序号。b为way数，rs分别为速度和速度差
</td></tr>
<tr>
<td>20</td>
<td>1048576</td>
<td>0x100000</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>紧跟着1048576使用，a为层数，b用途未知，rs分别为角度和角度差
</td></tr>
<tr>
<td>21</td>
<td>2097152</td>
<td>0x200000</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td><span style="color:red;">跳转相关，功能尚不明确</span>
</td></tr>
<tr>
<td>22</td>
<td>4194304</td>
<td>0x400000</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>跳到变换a执行（用来循环）
</td></tr>
<tr>
<td>23</td>
<td>8388608</td>
<td>0x800000</td>
<td>O</td>
<td>X</td>
<td>O</td>
<td>O</td>
<td><span style="color:red;">只在文花贴DS--ecl24d内发现，待测试</span>
</td></tr>
<tr>
<td>24</td>
<td>16777216</td>
<td>0x1000000</td>
<td>O</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>改变弹幕形状为a,b 特别的，不会生成弹雾
</td></tr>
<tr>
<td>25</td>
<td>33554432</td>
<td>0x2000000</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td><span style="color:red;">子弹转向，原理不明，r,s表示子弹打向的方向,b的最大有效值为0x1FF,且第一位是不是很重要</span>
</td></tr>
<tr>
<td>26</td>
<td>67108864</td>
<td>0x4000000</td>
<td>X</td>
<td>X</td>
<td>O</td>
<td>O</td>
<td><span style="color:red;">未知</span>
</td></tr>
<tr>
<td>27</td>
<td>134217728</td>
<td>0x8000000</td>
<td>O</td>
<td>X</td>
<td>O</td>
<td>O</td>
<td>给子弹叠加一个与505原弹速独立的速度，服从平行四边形定则。r角度，s速度，持续a帧
</td></tr>
<tr>
<td>28</td>
<td>268435456</td>
<td>0x10000000</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>根据a改变弹幕为高亮弹幕，a=1则是亮弹幕,a=0则普通
</td></tr>
<tr>
<td>29</td>
<td>536870912</td>
<td>0x20000000</td>
<td>O</td>
<td>X</td>
<td>O</td>
<td>O</td>
<td>在a帧时间内，速度变为r，方向变为s，(此函数只调用一次，因此使用-9989.0f来瞄准自机则会到时只有调用这个函数瞬间的自机位置有效，此后子弹将一直瞄准这个位置.若想实时瞄准自机，需使用999.0f,-999999.0f则不改变角度.)
</td></tr>
<tr>
<td>30</td>
<td>1073741824</td>
<td>0x40000000</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td><span style="color:red;">只在文花贴DS--ecl2a内发现，待测试</span>
</td></tr>
<tr>
<td>31</td>
<td>-2147483648</td>
<td>0x80000000</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>未使用，保留
</td></tr>
</tbody></table>



### FLAG表
  
星莲船
  


<table>

<tbody><tr>
<th>序号</th>
<th>10进制</th>
<th>功能
</th></tr>
<tr>
<td>0</td>
<td>1</td>
<td>无被弹判定
</td></tr>
<tr>
<td>1</td>
<td>2</td>
<td>无体术判定
</td></tr>
<tr>
<td>2</td>
<td>4</td>
<td>当单位离开左右版面时不会立即消失
</td></tr>
<tr>
<td>3</td>
<td>8</td>
<td>当单位离开上下版面时不会立即消失
</td></tr>
<tr>
<td>4</td>
<td>16</td>
<td>隐藏boss血条并设为无敌
</td></tr>
<tr>
<td>5</td>
<td>32</td>
<td>隐藏单位
</td></tr>
<tr>
<td>6</td>
<td>64</td>
<td><span style="color:red;">boss最开始都有，迷</span>
</td></tr>
<tr>
<td>7</td>
<td>128</td>
<td>使单位不会被425()及418消除，
</td></tr>
<tr>
<td>8</td>
<td>256</td>
<td>保证此单位会被425以及418消除，无论拥有任何Flag
</td></tr>
<tr>
<td>9</td>
<td>512</td>
<td>设置是否可以擦弹，擦弹类似激光
</td></tr>
<tr>
<td>10</td>
<td>1024</td>
<td>使单位不会被425及418消除,遇到对话时会死亡.用于飞碟
</td></tr>
<tr>
<td>11</td>
<td>2048</td>
<td>设置是否会被消弹效果秒杀
</td></tr>
<tr>
<td>12</td>
<td>4096</td>
<td>
</td></tr>
<tr>
<td>13</td>
<td>8192</td>
<td>
</td></tr>
<tr>
<td></td>
<td></td>
<td>下列FLAG是由系统内部或者其他函数赋予和消除的
</td></tr>
<tr>
<td>15</td>
<td>0x00008000</td>
<td>进入过一次板内的单位就会被赋予，用于区别一开始就在板外的单位和从板内离场的单位。
</td></tr>
<tr>
<td>16</td>
<td>0x00010000</td>
<td>限制单位移动范围,由404赋予，405消除
</td></tr>
<tr>
<td>17</td>
<td>0x00020000</td>
<td><span style="color:grey;">引擎内部使用,标记单位使用被某个函数测验过</span>
</td></tr>
<tr>
<td>18</td>
<td>0x00040000</td>
<td>使单位移动方向左右翻转,由324赋予和消除
</td></tr>
<tr>
<td>19</td>
<td>0x00080000</td>
<td>单位左右移动是贴图会不会变化,由262赋予，276消除}}
</td></tr>
<tr>
<td>20</td>
<td>0x00100000</td>
<td><span style="color:grey;">引擎内部使用,非boss单位或隐藏单位此flag会被自动剔除</span>
</td></tr>
<tr>
<td>21</td>
<td>0x00200000</td>
<td>特殊单位，不会被425及418消除
</td></tr>
<tr>
<td>22</td>
<td>0x00400000</td>
<td>Boss模式单位，此flag要通过412赋予和消除
</td></tr>
<tr>
<td>23</td>
<td>0x00800000</td>
<td>判定是否全避（存在时就是全避）
</td></tr>
<tr>
<td>24</td>
<td>0x01000000</td>
<td>要被消除的单位，由425以及418赋予
</td></tr>
<tr>
<td>25</td>
<td>0x02000000</td>
<td><span style="color:red;">功能未知，影响256，263,272,273等函数</span>
</td></tr>
<tr>
<td>26</td>
<td>0x04000000</td>
<td><span style="color:red;">功能未知，由444赋予和消除</span>
</td></tr>
<tr>
<td>27</td>
<td>0x08000000</td>
<td>对BOMB免疫，由446赋予和消除
</td></tr>
<tr>
<td>28</td>
<td>0x10000000</td>
<td>boss开启b免状态时被赋予。用来控制b结束后删除无敌和b免动画,使用446会立即消除此flag
</td></tr>
<tr>
<td>29</td>
<td>0x20000000</td>
<td><span style="color:grey;">引擎内部使用</span>
</td></tr>
<tr>
<td>30</td>
<td>0x40000000</td>
<td><span style="color:red;">功能未知，由449赋予和消除</span>
</td></tr></tbody></table>


  
  

文花帖DS
  


<table>

<tbody><tr>
<th>序号</th>
<th>10进制</th>
<th>功能
</th></tr>
<tr>
<td>0</td>
<td>1</td>
<td>无被弹判定
</td></tr>
<tr>
<td>1</td>
<td>2</td>
<td>无体术判定
</td></tr>
<tr>
<td>2</td>
<td>4</td>
<td>当单位离开左右版面时不会立即消失
</td></tr>
<tr>
<td>3</td>
<td>8</td>
<td>当单位离开上下版面时不会立即消失
</td></tr>
<tr>
<td>4</td>
<td>16</td>
<td>隐藏boss血条并设为无敌
</td></tr>
<tr>
<td>5</td>
<td>32</td>
<td>隐藏单位
</td></tr>
<tr>
<td>6</td>
<td>64</td>
<td><span style="color:red;">boss最开始都有，迷</span>
</td></tr>
<tr>
<td>7</td>
<td>128</td>
<td>使单位不会被425()及418消除，
</td></tr>
<tr>
<td>8</td>
<td>256</td>
<td>保证此单位会被425以及418消除，无论拥有任何Flag
</td></tr>
<tr>
<td>9</td>
<td>512</td>
<td>设置是否可以擦弹，擦弹类似激光
</td></tr>
<tr>
<td>10</td>
<td>1024</td>
<td>使单位不会被425及418消除,遇到对话时会死亡.用于飞碟
</td></tr>
<tr>
<td>11</td>
<td>2048</td>
<td>设置是否会被消弹效果秒杀
</td></tr>
<tr>
<td>12</td>
<td>4096</td>
<td>
</td></tr>
<tr>
<td>13</td>
<td>8192</td>
<td>
</td></tr>
<tr>
<td>14</td>
<td>16384</td>
<td>改变体术判定为方形，否则为圆形
</td></tr>
<tr>
<td></td>
<td></td>
<td>下列FLAG是由系统内部或者其他函数赋予和消除的
</td></tr>
<tr>
<td>16</td>
<td>0x00010000</td>
<td>进入过一次板内的单位就会被赋予，用于区别一开始就在板外的单位和从板内离场的单位。
</td></tr>
<tr>
<td>17</td>
<td>0x00020000</td>
<td>限制单位移动范围,由404赋予，405消除
</td></tr>
<tr>
<td>18</td>
<td>0x00040000</td>
<td><span style="color:grey;">引擎内部使用,标记单位使用被某个函数测验过</span>
</td></tr>
<tr>
<td>19</td>
<td>0x00080000</td>
<td>使单位移动方向左右翻转,由324赋予和消除
</td></tr>
<tr>
<td>20</td>
<td>0x00100000</td>
<td>单位左右移动是贴图会不会变化,由262赋予，276消除}}
</td></tr>
<tr>
<td>21</td>
<td>0x00200000</td>
<td><span style="color:grey;">引擎内部使用,非boss单位或隐藏单位此flag会被自动剔除</span>
</td></tr>
<tr>
<td>22</td>
<td>0x00400000</td>
<td>特殊单位，不会被425及418消除
</td></tr>
<tr>
<td>23</td>
<td>0x00800000</td>
<td>Boss模式单位，此flag要通过412赋予和消除
</td></tr>
<tr>
<td>24</td>
<td>0x01000000</td>
<td>判定是否全避（存在时就是全避）
</td></tr>
<tr>
<td>25</td>
<td>0x02000000</td>
<td>要被消除的单位，由425以及418赋予
</td></tr>
<tr>
<td>26</td>
<td>0x04000000</td>
<td><span style="color:red;">功能未知，影响256，263,272,273等函数</span>
</td></tr>
<tr>
<td>27</td>
<td>0x08000000</td>
<td><span style="color:red;">功能未知，由444赋予和消除</span>
</td></tr>
<tr>
<td>28</td>
<td>0x10000000</td>
<td>对BOMB免疫，由446赋予和消除
</td></tr>
<tr>
<td>29</td>
<td>0x20000000</td>
<td>boss开启b免状态时被赋予。用来控制b结束后删除无敌和b免动画,使用446会立即消除此flag
</td></tr>
<tr>
<td>30</td>
<td>0x40000000</td>
<td><span style="color:grey;">引擎内部使用</span>
</td></tr>
<tr>
<td>31</td>
<td>0x80000000</td>
<td><span style="color:red;">功能未知，由449赋予和消除</span>
</td></tr></tbody></table>


  
大战争
  


<table>

<tbody><tr>
<th>序号</th>
<th>10进制</th>
<th>功能
</th></tr>
<tr>
<td>0</td>
<td>1</td>
<td>无被弹判定
</td></tr>
<tr>
<td>1</td>
<td>2</td>
<td>无体术判定
</td></tr>
<tr>
<td>2</td>
<td>4</td>
<td>当单位离开左右版面时不会立即消失
</td></tr>
<tr>
<td>3</td>
<td>8</td>
<td>当单位离开上下版面时不会立即消失
</td></tr>
<tr>
<td>4</td>
<td>16</td>
<td>隐藏boss血条并设为无敌
</td></tr>
<tr>
<td>5</td>
<td>32</td>
<td>隐藏单位
</td></tr>
<tr>
<td>6</td>
<td>64</td>
<td><span style="color:red;">boss最开始都有，迷</span>
</td></tr>
<tr>
<td>7</td>
<td>128</td>
<td>使单位不会被425()及418消除，
</td></tr>
<tr>
<td>8</td>
<td>256</td>
<td>保证此单位会被425以及418消除，无论拥有任何Flag
</td></tr>
<tr>
<td>9</td>
<td>512</td>
<td>设置是否可以擦弹，擦弹类似激光
</td></tr>
<tr>
<td>10</td>
<td>1024</td>
<td>使单位不会被425及418消除,遇到对话时会死亡.用于飞碟
</td></tr>
<tr>
<td>11</td>
<td>2048</td>
<td>设置是否会被消弹效果秒杀
</td></tr>
<tr>
<td>12</td>
<td>4096</td>
<td>
</td></tr>
<tr>
<td>13</td>
<td>8192</td>
<td>
</td></tr>
<tr>
<td></td>
<td></td>
<td>下列FLAG是由系统内部或者其他函数赋予和消除的
</td></tr>
<tr>
<td>17</td>
<td>0x00020000</td>
<td>进入过一次板内的单位就会被赋予，用于区别一开始就在板外的单位和从板内离场的单位。
</td></tr>
<tr>
<td>18</td>
<td>0x00040000</td>
<td>限制单位移动范围,由404赋予，405消除
</td></tr>
<tr>
<td>19</td>
<td>0x00080000</td>
<td><span style="color:grey;">引擎内部使用,标记单位使用被某个函数测验过</span>
</td></tr>
<tr>
<td>20</td>
<td>0x00100000</td>
<td>使单位移动方向左右翻转,由324赋予和消除
</td></tr>
<tr>
<td>21</td>
<td>0x00200000</td>
<td>单位左右移动是贴图会不会变化,由262赋予，276消除}}
</td></tr>
<tr>
<td>22</td>
<td>0x00400000</td>
<td><span style="color:grey;">引擎内部使用,非boss单位或隐藏单位此flag会被自动剔除</span>
</td></tr>
<tr>
<td>23</td>
<td>0x00800000</td>
<td>特殊单位，不会被425及418消除
</td></tr>
<tr>
<td>24</td>
<td>0x01000000</td>
<td>Boss模式单位，此flag要通过412赋予和消除
</td></tr>
<tr>
<td>25</td>
<td>0x02000000</td>
<td>判定是否全避（存在时就是全避）
</td></tr>
<tr>
<td>26</td>
<td>0x04000000</td>
<td>要被消除的单位，由425以及418赋予
</td></tr>
<tr>
<td>27</td>
<td>0x08000000</td>
<td><span style="color:red;">功能未知，影响256，263,272,273等函数</span>
</td></tr>
<tr>
<td>28</td>
<td>0x10000000</td>
<td><span style="color:red;">功能未知，由444赋予和消除</span>
</td></tr>
<tr>
<td>29</td>
<td>0x20000000</td>
<td>对BOMB免疫，由446赋予和消除
</td></tr>
<tr>
<td>30</td>
<td>0x40000000</td>
<td>boss开启b免状态时被赋予。用来控制b结束后删除无敌和b免动画,使用446会立即消除此flag
</td></tr>
<tr>
<td>31</td>
<td>0x80000000</td>
<td><span style="color:grey;">引擎内部使用</span>
</td></tr>
<tr>
<td></td>
<td></td>
<td>DZZ扩充了Flag,额外新增了4字节
</td></tr>
<tr>
<td>32</td>
<td>0x00000001</td>
<td><span style="color:red;">功能未知，由449赋予和消除</span>
</td></tr></tbody></table>






---

此文档由 [THBWiki-Markdown-Builder](https://github.com/Delsin-Yu/THBWiki-Markdown-Builder) 构建。

文档中的所有内容除特殊注明外，均在 [**知识共享(Creative Commons) 署名-非商业性使用-相同方式共享 3.0 协议**](https://creativecommons.org/licenses/by-sa/3.0/deed.zh-hans) 下提供，附加条款亦可能应用。

引用类型与其他类型作品版权归原作者所有，如有作者授权则遵照授权协议使用。

详细请查阅 [THBWiki：免责声明](https://thbwiki.cc/THBWiki:%E5%85%8D%E8%B4%A3%E5%A3%B0%E6%98%8E)。

