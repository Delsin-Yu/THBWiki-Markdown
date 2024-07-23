# 脚本对照表/ECL/第二世代

<!-- source html: G:\repos\THBWiki-Markdown-Builder\THBWikiMarkdown\Temp\main\2\21\ns0%3A%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8%2FECL%2F%E7%AC%AC%E4%BA%8C%E4%B8%96%E4%BB%A3.html -->

脚本对照表


## 目录

- [1 概述](#概述)
- [2 设置贴图，播放特效动画，创建单位](#设置贴图，播放特效动画，创建单位)
- [3 单位移动](#单位移动)
- [4 单位固有属性](#单位固有属性)
- [5 4系  弹幕相关](#4系_弹幕相关)
- [6 409指令详解](#409指令详解)
- [7 FLAG表](#FLAG表)





### 概述
  
本对照表是Zun的第二代ecl脚本的对照表,适用于风神录和地灵殿
  
  
对于其他作的参考
  
  
第一代ecl脚本红妖永花,文花帖.由于与此表差异很大,故不能作任何参考.
  
  
[第三代ECL脚本](./脚本对照表-ECL-第三世代.md)对应星，文花帖ds和大战争
  
  
[第四代ECL脚本](./脚本对照表-ECL-第四世代.md)对应城，天邪鬼，绀珠传
  

```
   第四代中300对应此表中256,400对应此表中300，500对应此表中400，600对应此表中500，其余大体可以按顺序对照.
```

  
以下即是所有存在的ins,是读取汇编所获得的
  
  
绿色代表地灵殿中新增，风神录中不存在
  
  
红色代表功能未知，需要测试和研究
  
  
蓝色代表虽然并未完全解读，但是大体功能已经知道，且此函数用途十分有限
  
  
灰色代表是前作特殊地点使用过之后完全被抛弃的
  


### 设置贴图，播放特效动画，创建单位
  
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
  和263功能基本一样,只用于风神录4面潜水怪
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

  
276()重置所有动画相关.移除flag0x10000
  


### 单位移动
  
所有移动相关函数都是一对一对的，它们基本功能相同，只是一个是绝对坐标和绝对方向，另一个则是相对自身的坐标和方向
对于大部分直线运动来说比如.284,285相对自身的方向和绝对方向无差别，所以
286 287的存在只是使得一个单位可以同时获得两个不同的速度
  
  
280
MoveDirect(float x,float y);  
  

```
  单位瞬移到(x,y)位置。
```

  
281
MoveByTime(int time,int mode,float x,float y);
  

```
  在time帧内，单位运动到到(x,y)位置（也就是将单位的横纵坐标在time帧内分别渐变到x和y），mode为运动的方式（即描述渐变过程的函数曲线），参见ins_91附表，
  例如：由ins_91附表和运动学知识知，
  当mode=0时，单位做匀速直线运动；
  当mode=1时，单位在横纵方向均做匀加速运动（到达目的地后停止）；
  当mode=4时，单位先获得初速度，然后在横纵方向均做末速度为0的匀减速运动；
  当mode=9时，单位在横纵方向上均先匀加速运动，运动到一半距离后再做末速度为0的匀减速运动。
```

  
282
MoveDirect2(float x,float y);  和280成对
  
  
283
MoveByTime2(int time,int mode,float x,float y);  和281成对
  
  
284
SetUnitSpeed(float direction, float speed);
  

```
  使单位以指定运动的方向和速度运动。
```

  
285
ChangeUnitSpeed(int time, int mode, float direction, float speed);
  

```
  在time帧内逐渐改变运动方向和速度，最终变为direction和speed值。改变的方式由mode指定。
```

  
286
SetUnitSpeed2(float direction, float speed);  和284成对
  
  
287
ChangeUnitSpeed2(int time, int mode, float direction, float speed);  和285成对
  
  
288
CircleMove(float dir,float speed,float r,float,rspeed);
  

```
   设定单位运动方式为圆周运动，初始方向为dir，半径为r，角速度为speed，半径增加的速度为rspeed
```

  
289
CircleMoveChange(int time,int mode, float speed, float radius, float rspeed);
  

```
    time帧之内改变单位圆周运动的参数,方式为mode.各参数参考308
```

  
290
CircleMove(float θ,float speed,float radius,float,rspeed);; 和318成对
  
  
291
CircleMoveChange(int time,int mode, float speed, float radius, float rspeed);和309成对
  
  
292
MoveRandom(int time,int mode,float speed); 
  

```
 向随机方向移动一次，持续time帧，速度为speed，移动方式为mode。mode和305相同
  
```

  
293
MoveRandom(int time,int mode,float speed); 和312成对
  
  
294()将单位移动至boss的位置,此函数若在无boss时使用会导致严重误访问而爆炸
  
  
295()和314成对
  
  
296(float x,float y,float height)瞬间移动到与当前位置偏移x,y的位置,并且改变单位深度，此深度只适用于风神录四面的潜水怪
  
  
297(float x,float y,float height))和316成对
  
  
298(float x,float y)6面神妈的圈圈移动上使用
  
  
299(float x,float y)和318成对
  
  
300(float θ,float speed,float radius,float,rspeed,float dir,float rate)
  

```
    使单未进行椭圆运动,曲线的极坐标（原点为单位之前的位置）(radius,θ).θ的增速为speed，radius增速为 rspeed,dir为 椭圆偏离的方向， rate为长半轴与短半轴的比例
```

  
301(int time,int mode, float speed, float radius, float rspeed,float dir,float rate)
  

```
    time帧之内改变单位圆周运动的参数,方式为mode.各参数参考320
```

  
302(float θ,float speed,float radius,float,rspeed,float dir,float rate);和320成对
  
  
303(int time,int mode, float speed, float radius, float rspeed,float dir,float rate);和321成对
  
  
304(int a)
  

```
  当a =1的时候赋予单位flag（ins_402中的）0x8000,a=0的是消除
  此flag会赢284和285,效果为左右翻转
```

  
305(int time,float x1,float y1,float x2,float y2,float x3,float y3)
  

```
  在time时间内将单位最终移动至点x2,y2.
  期间首先向点x1,y1移动和一点时间再向
  终点偏差x3,y3移动一段时间再移动至终点x2,y2.
```

  
306(int time,float x1,float y1,float x2,float y2,float x3,float y3)和325成对
  
  
307()
  

```
  初始化和清零移动相关参数有关
```


### 单位固有属性
  
320
HitBox(float width,float height)  目标被弹判定
  
  
321
KillBox(float width,float height)  目标体术判定
  
  
322
SetUnitOptions(int flag) 
  

```
 设置单位的一些特定FLAG,a为一个16字节的开关参数0000000000000000
 关于FLAG请参考词条最下方的表格
```

  
  

  
  
  
 
  
  
323
UnSetUnitOptions(int a)
  

```
 取消302设置的参数,和302刚好相反
```

  
324
SetMoveArea(float x,float y,float m,float n,);
  

```
 限制boss的移动范围，以x,y为基准+- n 和m的范围,赋予flag512
 注.此函数在thtk解出来的文件里第一个参数被误解成整数，实际为浮点
```

  
325()
  

```
 移除boss移动范围限制,移除flag 512
```

  
326
ClearDrops()清除掉落
  
  
327
SetDrops(int type,int amount)
  

```
 设定目标掉落道具及数量，风神录中type的含义详见下面表格（type大于11时，不掉落任何道具，是无效的type值）
```


<table>

<tbody><tr>
<th>type</th>
<th>道具</th>
<th>type</th>
<th>道具</th>
<th>type</th>
<th>道具</th>
<th>type</th>
<th>道具</th>
<th>type</th>
<th>道具</th>
<th>type</th>
<th>道具</th>
<th>type</th>
<th>道具</th>
<th>type</th>
<th>道具</th>
<th>type</th>
<th>道具</th>
<th>type</th>
<th>道具</th>
<th>type</th>
<th>道具
</th></tr>
<tr>
<td>1</td>
<td>小p点</td>
<td>2</td>
<td>蓝点</td>
<td>3</td>
<td>大绿点</td>
<td>4</td>
<td>大p点</td>
<td>5</td>
<td>金边蓝点</td>
<td>6</td>
<td>F点</td>
<td>7</td>
<td>1up</td>
<td>8</td>
<td>消弹点（+10信仰）</td>
<td>9</td>
<td>小绿点（+100信仰）</td>
<td>10</td>
<td>小p点</td>
<td>11</td>
<td>大p点
</td></tr></tbody></table>


  
328
SetDropArea(float width,float height)设置掉落区域
  
  
329
Drop()掉落所有道具
  
  
330
SetBasicDrop(int type) 设置目标基本掉落，数量是1.
  
  
331
SetLife(int life)  更改单位血量
  
  
332(int a)
  

```
 a=0，设为boss战模式（血条，名字等），赋予单位flag0x00400000
 
```

  
，a=-1，结束boss。消除单位flag0x00400000
  
  
  

333()boss 重置时间
  
  
334
SetNextPattern(int a，血量，时间，“阶段变量名”),
  

```
 当血量和或时间达到此数值时 载入下一阶段（符卡或非符）
  *a的作用未知* 
```

  
335
Invisible(int time) 无敌时间，
  
  
336
PlaySE(int)播放音效 
  
  
337(int a，int b，int c) 
震屏特效。a为持续时间（帧），bc均与震屏强度有关，都是越大震动越强，区别不明。
  
  
  

338
Talk（int） 读取对话，参数对应msg文件
  
  
339
AfterTalk（）对话后进行下一条
  
  
340
AfterKill（）击破后进行下一条 
  
  
341
TimeOut（int a，“func”）
  

```
 时间到0时进行func的内容，a作用未知
```

  
342
SetSpellCard(int a, int life, int score, "X符:XXXX"); 
  

```
 进入符卡模式，设置符卡宣言后右上角 符卡时间，scb，符卡名，a和符卡序号有关
 EX面使用
```

  
  

343
EndSpellCard()
  

```
 结束符卡模式
```

  
344
SetChapter(float)
  

```
 设置gzz里的结算点，从xlc就开始使用过
```

  
345
ClearUnits()
  

```
 清除该单位创建的子单位.
```

  
346
SetProtectArea(float)
  

```
设置弹幕生成保护范围（距离）自机在此范围内时不发弹
```

  
347
SetLifeBar(int a, float life, int color); 
  

```
 设置血条上的标记点，a是标记序号，life对应血量，
  *color 是RGB三个字节连在一起的数* 
```

  
348
SetSpellCard(int a, int life, int score, "X符:XXXX"); 
  

```
 进入符卡模式，设置符卡宣言后右上角 符卡时间，scb，符卡名，a和符卡序号有关
 未使用 
```

  
RANK一直存在于游戏程序中，收点+rank miss减rank
  
  
349(%N，float a,b,c)根据RANK决定变量N
  
  
350(%N，float a,b,c,d,e)根据RANK决定变量N
  
  
351(%N，float a,b)根据RANK决定变量N
  
  
352($M，int a,b,c)根据RANK决定变量M
  
  
353($M，int a,b,c,d,e)根据RANK决定变量M
  
  
354($M，int a,b)根据RANK决定变量M
  
  
  

355($M,int a,b,c,d)根据难度将数据写入整数M中
  
  
356(%N,float a,b,c,d)根据难度将数据写入浮点数N中
  
  
357
SetSpellCard(int a, int life, int score, "X符:XXXX"); 
  

```
 进入符卡模式，设置符卡宣言后右上角 符卡时间，scb，符卡名，a和符卡序号有关
 非EX面关底使用 
```

  
358
SetSpellCard(int a, int life, int score, "X符:XXXX"); 
  

```
 进入符卡模式，设置符卡宣言后右上角 符卡时间，scb，符卡名，a和符卡序号有关
 未使用 
```

  
359
SetSpellCard(int a, int life, int score, "X符:XXXX"); 
  

```
 进入符卡模式，设置符卡宣言后右上角 符卡时间，scb，符卡名，a和符卡序号有关
 非EX面道中使用
```

  
360
SetBossStar(int)设置剩余阶段数(左上角的星星数)
  
  
361(int)仅在风神录使用过,为4,5,6面某些效果设置,
和335(int)无敌类似
  
  
362
  

```
  Survival() 设置符卡为时符
```

  
363()
  

```
  星莲船的三个时符均使用.具体效果未知
```

  
364(int a)
  

```
  当a =1的时候赋予单位flag（ins_402中的）0x04000000,a=0的是消除
```

  
365()
  

```
  清楚特定内存并重置boss一些参数，
  除了boss1非以外，每一张非和卡都出现和,boss逃跑和死亡也会出现
```

  
366(int a,int b)
当a =1的时候赋予单位flag（ins_402中的）0x08000000,a=0的是消除
此flag会使boss对Bomb免疫,并且由b来决定放b时的播放的动画
同时会消除单位flag（ins_402中的）0x10000000,
  
  
  

367(float)设置时间倍率，1.0是正常，击破后减速可以设成0.5，咲夜时停是设成0.0
  
  
368(int a,b,c,d)
  

```
 根据难度等待x帧
```

  
369(int a) 当a =1的时候赋予单位flag（ins_402中的）0x08000000,a=0的是消除
  
  
370(int a)仅在地灵殿四面道中boss的鬼火使用过,效果不明.即使删除也没有任何影响.之后被zun遗弃 ebx+11c= a
  


### 4系  弹幕相关
  
400
CreateBullet(int a) 创建一个弹幕，编号为a，
  
  
401
Fire(int a) 发射a号子弹
  
  
402
BShape(弹幕编号,int a,int b) 设置弹幕贴图,a b 对应 bullet.Anm文件中description文件的内容。
  


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
<td>小玉</td>
<td>2</td>
<td>环玉</td>
<td>3</td>
<td>米弹
</td></tr>
<tr>
<td>4</td>
<td>链弹</td>
<td>5</td>
<td>针弹</td>
<td>6</td>
<td>札弹</td>
<td>7</td>
<td>鳞弹
</td></tr>
<tr>
<td>8</td>
<td>铳弹</td>
<td>9</td>
<td>消弹效果</td>
<td>10</td>
<td>杆菌弹</td>
<td>11</td>
<td>小星弹
</td></tr>
<tr>
<td>12</td>
<td>中玉</td>
<td>13</td>
<td>椭弹</td>
<td>14</td>
<td>刀弹</td>
<td>15</td>
<td>蝶弹
</td></tr>
<tr>
<td>16</td>
<td>大星弹</td>
<td>17</td>
<td>大玉</td>
<td>18</td>
<td>水光弹</td>
<td>19</td>
<td>高光中玉
</td></tr>
<tr>
<td>20</td>
<td>高光椭弹</td>
<td>21</td>
<td>高光刀弹</td>
<td>22</td>
<td>高光蝶弹</td>
<td>23</td>
<td>钱币弹
</td></tr>
<tr>
<td>24</td>
<td>葡萄弹</td>
<td>25</td>
<td>道具（迷）</td>
<td>25</td>
<td>火光弹</td>
<td>26</td>
<td>旋转米弹
</td></tr>
<tr>
<td>27</td>
<td>点弹</td>
<td>27</td>
<td>心弹（殿）</td>
<td>28</td>
<td>蔷薇弹（殿）</td>
<td>29</td>
<td>空白
</td></tr></tbody></table>


  
403
BPositionXY(弹幕编号，float x，float y)  
  

```
  以基准发弹点为基础对发弹点进行偏移，x和y为偏移量。基准发弹点默认是单位目前坐标
```

  
404
BDirection(弹幕编号, float dir, float r);
  

```
  设置弹幕基础方向为 dir，r为角度差参数（详见407）
```

  
405
BSpeed(弹幕编号, float speedmax, float speedmin); 
  

```
  设置弹幕速度范围为[speedmin，speedmax]（详见407）
```

  
406
BAmount(弹幕编号，int way，int num)
  

```
  设置弹幕的way数和每way中含有的弹幕个数（即层数）num（详见407）
```

  
407
BStyle(弹幕编号，int style )
  

```
  根据style设置弹幕展开的形状，详见下表。
```


<table>

<tbody><tr>
<th>style值</th>
<th>形状描述</th>
<th>各参数作用、形状详细描述
</th></tr>
<tr>
<td>0</td>
<td>一般自机狙</td>
<td>向“自机方向+dir”方向发出自机狙，各way之间角度差r，最快一层速度speedmax，最慢一层速度为speedmin+(speedmax-speedmin)/num（区间最左侧的num等分点）（如果405中两个速度的位置写反，即speedmin&gt;speedmax，则最慢一层速度是speedmin，最快一层速度是区间最右侧的num等分点）（当只有一层时，速度为speedmax）
</td></tr>
<tr>
<td>1</td>
<td>与0形状一致</td>
<td>与0形状一致，但是方向变为dir
</td></tr>
<tr>
<td>2</td>
<td>左偏开花自机狙</td>
<td>弹幕方向为“自机方向+dir”，各层之间角度差r，各way均匀分布，各层速度满足0中描述，最快一层的方向为弹幕方向，然后每向内（速度较慢）一层，该层弹幕向左（顺时针）偏转角度r
</td></tr>
<tr>
<td>3</td>
<td>与2形状一致</td>
<td>与2形状一致，但是“弹幕方向”变为dir
</td></tr>
<tr>
<td>4</td>
<td>与2形状一致</td>
<td>与2形状一致，但是“弹幕方向”正好和2相间（相差π/way数）
</td></tr>
<tr>
<td>5</td>
<td>与2形状一致</td>
<td>与2形状一致，但是“弹幕方向”正好和3相间（相差π/way数）
</td></tr>
<tr>
<td>6</td>
<td>范围随机弹</td>
<td>向r和dir方向之间（不限定r和dir的大小关系）发出way×num个随机弹，速度在速度范围区间内随机
</td></tr>
<tr>
<td>7</td>
<td>每way之内的随机弹</td>
<td>弹幕方向与3一致，但是每一颗子弹速度都在速度范围区间内随机
</td></tr>
<tr>
<td>8</td>
<td>与6完全一致</td>
<td>与6完全一致（未发现明显区别）
</td></tr>
<tr>
<td>其他值</td>
<td>形状等同于style=0，dir=0.0f，r=0.0f
</td></tr></tbody></table>


  
408
BSE(弹幕编号, int a,int b);
  

```
  设置弹幕音效，a是发弹音效，b是变向音效。不设置的话就是默认。-1代表没有音效
```

  
409
BMode(弹幕编号，变换序号,通道,int mode,int a,int b,float r,float s)
  

```
  对弹幕施加变换。详见后文“409指令详解”。
```

  
410
Bclear()
  

```
  全屏消弹,不增加得点
```

  
411
BCopy(int a,int b)复制弹幕b到a中,弹幕属性仅复制这个函数使用之前设定的，
  
  
激光相关函数和移动类似，很多是成对的
  
  
412(int a, b,float c,d,e,f,g,h) 激光相关
  

```
  发射激光，a,b是402参数，表示将哪种子弹的贴图拉伸成激光；c角度，d速度，f长度，g存活时间，h宽度
```

  
413(int a b,c float d,e,f int g,h,i,j float k,int l)
  

```
  发射预警线激光，a为此激光的弹幕编号，b，c为402参数，d为角度，e无用（猜测），f为长度，g，h，i，j为预警线激光四个阶段的时间，分别为预警线阶段、激光产生变粗直到指定宽度阶段、激光持续阶段和激光变细消失阶段，k为激光宽度。
```

  
414(int a, float b,c) 激光相关
  
  
415(int a, float b,c) 激光相关
  
  
416(int a,float b) 激光相关
  
  
417(int a,float b) 激光相关
  
  
418(int a,float b) 激光相关
  
  
419(int a,float b) 激光相关
  
  
420(float r)消掉半径为r范围内的弹幕,消掉的弹幕变为最大得点
  
  
421(float r)消掉半径为r范围内的弹幕,不增加得点
  
  
船开始zun放弃使用rank，但是rank这个变量依旧存在于程序中且和红魔乡的增减方法相同
故以下函数仍然可以使用
RANK =[474C98]
  
  
422(弹幕编号，float a,b,c,d,e,f)
  

```
 根据Rank的值512个-512比较来决定弹速
```

  
423(弹幕编号，float a,b,c,d,e,f,g,h,i,j)
  

```
 根据Rank，和各种值来决定弹速
```

  
424(弹幕编号，float a,b,c,d)
  

```
 未知,根据Rank决定弹速
```

  
425(弹幕编号，int a,b,c,d,e,f)
  

```
 根据Rank值和512个-512比较来决定way数和层数
```

  
426(弹幕编号，int a,b,c,d,e,f,g,h,i,j)
  

```
 和514类似,比较Rank，和各种值来决定way数和层数
```

  
427(弹幕编号，int a,b,c,d)
  

```
 未知,根据内存Rank决定way数和层数
```

  
428(int a b ,float c,d,e f,g,h) 激光相关
  
  
429(int a b,c float c,d,e, int f,g,h,i, float j,int k) 激光相关
  
  
430(int a, float b,c) 激光相关
  
  
431(int a,int b,float c,d,e,f,g,h) 和412成对
  
  
432(int a b,c float c,d,e, int f,g,h,i, float j,int k) 激光相关 和413成对
  
  
433(int a b ,float c,d,e f,g,h) 激光相关 和428成对
  
  
434(int a b,c float c,d,e, int f,g,h,i, float j,int k) 激光相关 和429成对
  
  
435(弹幕编号，float a,b,c,d,e,f,g,h)
  

```
 405的难度结合版，a和e对应e难度，b和f对应n难度，以此类推
```

  
436(弹幕编号，int a,b,c,d,e,f,g,h)
  

```
 406的难度结合版，a和e对应e难度，b和f对应n难度，以此类推
```

  
437(弹幕编号，float o，float r)  以基准发弹点用极坐标的方式偏移发弹点，角度为o，半径为r。
  
  
438(弹幕编号，float dis) 设置发弹点。以boss为半径为dis的圆形边上发弹。
  
  
439(弹幕编号，float x，float y)设置发弹基准点
  
  
440(flout r,int color)
  

```
 设置boss周围的纹理变化特性，影响半径为r，颜色为 color，对应RGB颜色，
```

  
441(int a)
  

```
 执行STD脚本A
```

  
  

442(int)
  

```
 隐藏boss血条以及时间（不使boss无敌，也不锁时间，只是不显示血条和时间）
```

  
443(int a)
  

```
主要用于某些特殊攻击模式时启用，作为zun的补充函数
补充函数变和449共用一套
a=0时无效果
在DLD
 小五1符激光使用了1，
 猫车怨灵使用了2,3 4(2和4实际有449调用)
 3的效果是是含有flag1024的单位的-9984的值变为1
 4的效果是 删除含有flag1024的单位的flag1024，并赋予flag256
 
地底太阳吸引使用了5,这三个在本作中是否有效需要测试
恋恋则使用了 6-12，其中6,9,11是由449调用
```

  
444(int a)
  

```
 封装函数，当a=1时，单位的被弹判定采用特殊方式
```

  
445(int a)
  

```
 封装函数，当a=1时，单位的体术判定采用特殊方式
```

  
446(float r)
  

```
 消掉半径为r范围内的弹幕,消掉的弹幕变为最大得点,与421还有一处不同
```

  
447(float r)
  

```
 消掉半径为r范围内的弹幕,不增加得点,与421还有一处不同，仅在dld三面勇仪1符圈圈消蛋使用，此圈圈不会消自身的大玉
```

  
448(int a)
  

```
 3面boss二非阴阳玉使用
```

  
449(int a)类似443， 立即执行一些特殊函数，具体参考443
  
  
450(int a)仅仅在猫车的怨灵使用
  


### 409指令详解
  
mode
  

```
  mode是一个32位的开关量，指定施加的变换的种类，
  在一条409指令中只能打开一个开关，即mode只能是2的整数次方（注意：这里和设定flag不同，一条322指令可以设置多个flag，参数可以不是2的整数次方），
  不同mode值的含义详见mode表。
```

  
变换序号
  

```
  指定变换的顺序。变换的顺序并不由409指令的顺序决定，而是由变换序号的大小关系决定。变换从变换序号0的变换开始依次执行，如果中间缺少某编号则不执行后面的变换，
  例如有以下指令序列
  409(弹幕编号,0.......);
  409(弹幕编号,1.......);
  409(弹幕编号,3,.......);
  409(弹幕编号,4,.......);
  这里少了序号2,所以后面两个不会执行。
  无论是通道0还是通道1（见下文“变换通道”）的变换，同一弹幕编号下两变换的变换序号不能相同，否则按照409指令的先后顺序，后面的会覆盖前面的变换。
```

  
变换通道
  

```
  指定变换执行的方式。当通道为0时，后面的变换会等待前面的变换执行完成后再执行，
  而通道为1的变换则不会等待前面的变换完成，直接按顺序全部执行。
```

  
mode表
  

```
  O表示此参数为必要参数，X表示此参数为无关参数，无关参数在解包出的程序中显示为实参-999999或-999999.0f。
  本表内容未得到完全确认，目前已确认的有（序号）：0,4,5,6,7,8,10,11,12,13,14,15,16,20,21,27
  
```

  
另注：地灵殿的变换与第三世代的相同
  


<table>

<tbody><tr>
<th>序号</th>
<th>mode(DEC)</th>
<th>mode(HEX)</th>
<th>参数a</th>
<th>参数b</th>
<th>参数r</th>
<th>参数s</th>
<th>功能描述
</th></tr>
<tr>
<td>0</td>
<td>1</td>
<td>0x1</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>弹幕向其前进方向高速窜出一小段距离，然后恢复原来速度
</td></tr>
<tr>
<td>1</td>
<td>2</td>
<td>0x2</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>未知
</td></tr>
<tr>
<td>2</td>
<td>4</td>
<td>0x4</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>未知
</td></tr>
<tr>
<td>3</td>
<td>8</td>
<td>0x8</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>未知
</td></tr>
<tr>
<td>4</td>
<td>16</td>
<td>0x10</td>
<td>O</td>
<td>X</td>
<td>O</td>
<td>O</td>
<td>设置加速度大小为r，加速度方向为s，持续时间为a（特殊：s=999.0f代表每帧都采样一次自机方向，使子弹具有实时追踪效果；=-999999.0f代表与弹幕原来方向一致）
</td></tr>
<tr>
<td>5</td>
<td>32</td>
<td>0x20</td>
<td>O</td>
<td>X</td>
<td>O</td>
<td>O</td>
<td>使弹幕圆周运动起来：设置切向加速度（即与弹幕运动方向相同的加速度）大小为r，角速度为s，持续时间为a
</td></tr>
<tr>
<td>6</td>
<td>64</td>
<td>0x40</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>a帧后停顿，之后方向变为原方向+r，速度变为s。以上重复b次
</td></tr>
<tr>
<td>7</td>
<td>128</td>
<td>0x80</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>a帧后停顿，之后方向变为自机方向+r，速度变为s。以上重复b次
</td></tr>
<tr>
<td>8</td>
<td>256</td>
<td>0x100</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>X</td>
<td>a帧后停顿，之后方向变为r，速度变为s。以上重复b次
</td></tr>
<tr>
<td>9</td>
<td>512</td>
<td>0x200</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>播放音效a
</td></tr>
<tr>
<td>10</td>
<td>1024</td>
<td>0x400</td>
<td>O</td>
<td>X</td>
<td>O</td>
<td>X</td>
<td>在上下左右均进行触壁反弹，a为反弹次数，r为反弹后的速度。注意：在通道0时，反弹a次后才继续执行其他变换
</td></tr>
<tr>
<td>11</td>
<td>2048</td>
<td>0x800</td>
<td>O</td>
<td>X</td>
<td>O</td>
<td>X</td>
<td>在上左右三方向进行触壁反弹，a为反弹次数，r为反弹后的速度
</td></tr>
<tr>
<td>12</td>
<td>4096</td>
<td>0x1000</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>设置弹幕不可消弹时间为a帧
</td></tr>
<tr>
<td>13</td>
<td>8192</td>
<td>0x2000</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>设置弹幕可在版外而不被消去的时间为a帧
</td></tr>
<tr>
<td>14</td>
<td>16384</td>
<td>0x4000</td>
<td>O</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>变换子弹贴图与颜色，但判定不变，a,b对应指令402中的a,b
</td></tr>
<tr>
<td>15</td>
<td>32768</td>
<td>0x8000</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>a帧后执行下一个变换
</td></tr>
<tr>
<td>16</td>
<td>65536</td>
<td>0x10000</td>
<td>-</td>
<td>-</td>
<td>-</td>
<td>-</td>
<td>消除子弹（见于ex关五符、八符等）
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
<td>X</td>
<td>X</td>
<td>X</td>
<td>在左右两方向进行穿墙，a为可穿墙的次数
</td></tr>
<tr>
<td>21</td>
<td>2097152</td>
<td>0x200000</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>只在板底进行触壁反弹
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
<td>X</td>
<td>X</td>
<td>在左右两个方向进行触壁反弹，a为反弹次数
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


  
注这部分结果是来自辉针城，故是否对星莲船适用需要测试
当mode 使用2097152时，根据弹幕发出者的ins_529(int flag)的参数不同而不同.
  

```
若flag=0,则无任何效果
1.使单位本身可以对弹幕靠近产生反应.（hzc4a线2卡）
  通过[-9978.0f]来决定受影响的范围
  [-9985]会根据弹幕接近与否改变数值,弹幕接近时会变成1.
5.使弹幕对自机的接近或者离开产生反应（hzc6面5卡） 
  接近则跳转到变换编号5，离开则跳转到14.接触范围[-9980.0f]和[9981.0f]设置，此时一般a=1，a的具体功能尚不明
```


### FLAG表
  
风神录： 
  


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
<td>隐藏boss血条并设为无敌
</td></tr>
<tr>
<td>4</td>
<td>16</td>
<td>隐藏单位
</td></tr>
<tr>
<td>5</td>
<td>32</td>
<td>
</td></tr>
<tr>
<td>6</td>
<td>64</td>
<td>使单位不会被345()及338消除，
</td></tr>
<tr>
<td>7</td>
<td>128</td>
<td>使单位保证被345()及338消除，无论拥有任何flag
</td></tr>
<tr>
<td>8</td>
<td>256</td>
<td>进入过一次板内的单位就会被赋予，用于区别一开始就在板外的单位和从板内离场的单位。
</td></tr>
<tr>
<td>9</td>
<td>512</td>
<td>限制单位移动范围,由324赋予，325消除
</td></tr>
<tr>
<td>10</td>
<td>1024</td>
<td><span style="color:grey;">引擎内部使用,标记单位使用被某个函数测验过</span>
</td></tr>
<tr>
<td>11</td>
<td>2048</td>
<td>使单位移动方向左右翻转,由304赋予和消除
</td></tr>
<tr>
<td>12</td>
<td>4096</td>
<td>单位左右移动是贴图会不会变化,由262赋予，
</td></tr>
<tr>
<td>13</td>
<td>8192</td>
<td><span style="color:grey;">引擎内部使用,非boss单位或隐藏单位此flag会被自动剔除</span>
</td></tr>
<tr>
<td>14</td>
<td>0x00004000</td>
<td>特殊单位，不会被使单位保证被345()及338消除
</td></tr>
<tr>
<td>15</td>
<td>0x00008000</td>
<td>Boss模式单位，此flag要通过332赋予和消除
</td></tr>
<tr>
<td>16</td>
<td>0x00010000</td>
<td>判定是否全避（存在时就是全避）
</td></tr>
<tr>
<td>17</td>
<td>0x00020000</td>
<td>要被消除的单位，由425以及418赋予
</td></tr>
<tr>
<td>18</td>
<td>0x00040000</td>
<td><span style="color:red;">功能未知，影响256，263,272,273等函数</span>
</td></tr>
<tr>
<td>19</td>
<td>0x00080000</td>
<td><span style="color:red;">功能未知，由364赋予和消除</span>
</td></tr>
<tr>
<td>20</td>
<td>0x00100000</td>
<td>对BOMB免疫，由366赋予和消除
</td></tr>
<tr>
<td>21</td>
<td>0x00200000</td>
<td>boss开启b免状态时被赋予。用来控制b结束后删除无敌和b免动画,使用366会立即消除此flag
</td></tr></tbody></table>


  
地灵殿： 
  


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
<td>
</td></tr>
<tr>
<td>7</td>
<td>128</td>
<td>使单位不会被345()及338消除，
</td></tr>
<tr>
<td>8</td>
<td>256</td>
<td>使单位保证被345()及338消除，无论拥有任何flag
</td></tr>
<tr>
<td>9</td>
<td>512</td>
<td>设置是否可以擦弹，擦弹类似激光
</td></tr>
<tr>
<td>10</td>
<td>1024</td>
<td>使单位不会被345()及338消除，主要用于5面猫车的怨灵，详细部分参考443
</td></tr>
<tr>
<td>11</td>
<td>2048</td>
<td>设置是否会被消弹效果秒杀
</td></tr>
<tr>
<td>12</td>
<td>4096</td>
<td>进入过一次板内的单位就会被赋予，用于区别一开始就在板外的单位和从板内离场的单位。
</td></tr>
<tr>
<td>13</td>
<td>8192</td>
<td>限制单位移动范围,由324赋予，325消除
</td></tr>
<tr>
<td>14</td>
<td>0x00004000</td>
<td><span style="color:grey;">引擎内部使用,标记单位使用被某个函数测验过</span>
</td></tr>
<tr>
<td>15</td>
<td>0x00008000</td>
<td>使单位移动方向左右翻转,由304赋予和消除
</td></tr>
<tr>
<td>16</td>
<td>0x00010000</td>
<td>单位左右移动是贴图会不会变化,由262赋予,276消除
</td></tr>
<tr>
<td>17</td>
<td>0x00020000</td>
<td><span style="color:grey;">引擎内部使用,非boss单位或隐藏单位此flag会被自动剔除</span>
</td></tr>
<tr>
<td>18</td>
<td>0x00040000</td>
<td>特殊单位，不会被使单位保证被345()及338消除
</td></tr>
<tr>
<td>19</td>
<td>0x00080000</td>
<td>Boss模式单位，此flag要通过332赋予和消除
</td></tr>
<tr>
<td>20</td>
<td>0x00100000</td>
<td>判定是否全避（存在时就是全避）
</td></tr>
<tr>
<td>21</td>
<td>0x00200000</td>
<td>要被消除的单位，由425以及418赋予
</td></tr>
<tr>
<td>22</td>
<td>0x00400000</td>
<td><span style="color:red;">功能未知，影响256，263,272,273等函数</span>
</td></tr>
<tr>
<td>23</td>
<td>0x00800000</td>
<td><span style="color:red;">功能未知，由364赋予和消除</span>
</td></tr>
<tr>
<td>24</td>
<td>0x01000000</td>
<td>对BOMB免疫，由366赋予和消除}
</td></tr>
<tr>
<td>25</td>
<td>0x02000000</td>
<td>boss开启b免状态时被赋予。用来控制b结束后删除无敌和b免动画,使用366会立即消除此flag
</td></tr>
<tr>
<td>27</td>
<td>0x08000000</td>
<td><span style="color:red;">功能未知，由369赋予和消除</span>
</td></tr></tbody></table>






---

此文档由 [THBWiki-Markdown-Builder](https://github.com/Delsin-Yu/THBWiki-Markdown-Builder) 构建。

文档中的所有内容除特殊注明外，均在 [**知识共享(Creative Commons) 署名-非商业性使用-相同方式共享 3.0 协议**](https://creativecommons.org/licenses/by-sa/3.0/deed.zh-hans) 下提供，附加条款亦可能应用。

引用类型与其他类型作品版权归原作者所有，如有作者授权则遵照授权协议使用。

详细请查阅 [THBWiki：免责声明](https://thbwiki.cc/THBWiki:%E5%85%8D%E8%B4%A3%E5%A3%B0%E6%98%8E)。

