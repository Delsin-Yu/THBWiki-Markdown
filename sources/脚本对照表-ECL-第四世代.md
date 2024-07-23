# 脚本对照表/ECL/第四世代

<!-- source html: G:\repos\THBWiki-Markdown-Builder\THBWikiMarkdown\Temp\main\5\5e\ns0%3A%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8%2FECL%2F%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3.html -->

脚本对照表


## 目录

- [1 概述](#概述)
- [2 3系 设置贴图，播放特效动画，创建单位](#3系_设置贴图，播放特效动画，创建单位)
- [3 4系 单位移动](#4系_单位移动)
- [4 5系  单位固有属性](#5系_单位固有属性)
- [5 6系  弹幕相关](#6系_弹幕相关)
- [6 7系  激光相关](#7系_激光相关)
- [7 8系 单位互动](#8系_单位互动)
- [8 9系 Debug相关](#9系_Debug相关)
- [9 10系 备用](#10系_备用)

  - [9.1 辉针城](#辉针城)
  - [9.2 天邪鬼](#天邪鬼)
  - [9.3 绀珠传](#绀珠传)
  - [9.4 天空璋](#天空璋)
  - [9.5 噩梦日记](#噩梦日记)
  - [9.6 兽王园](#兽王园)



- [10 609-612指令详解](#609-612指令详解)
- [11 Flag表](#Flag表)





### 概述
  
本对照表是ZUN的第四代ECL脚本的对照表,适用于神之后的所有作品
红色代表功能未知，需要测试和研究
  
  
蓝色代表虽然并未完全解读，但是大体功能已经知道，且此函数用途十分有限
  
  
灰色代表是前作特殊地点使用过之后完全被抛弃的
  
  
棕色部分是辉针城新增
  
  
青色部分是天邪鬼新增
  
  
绿色部分是绀珠传新增
  
  
紫色部分是天空璋新增
  
  
洋红部分是鬼形兽新增
  


### 3系 设置贴图，播放特效动画，创建单位
  
与300类似的这类ins，在创建单位的时候会自动执行与该单位同名的sub。
  
  
300("xxx", float x, float y, int life, int bonus, int item);
  

```
   以相对召唤者为基准点在位置xy，创建一个单位xxx，设置血量，分数以及基本掉落。
```

  
301("xxx", float x, float y, int life, int bonus, int item);
  

```
   在绝对位置xy，创建一个单位xxx，设置血量，分数以及基本掉落。用于boss
```

  
302(int); 
  

```
   选择ANM文件。一般来说0即是Bullet.anm，1即是Enemy.anm,2开始就是当面的boss相关anm
```

  
303(int slot,int a) 
  

```
   在相应slot上,设置单位贴图,a对应由上一个302选择的ANM文件中的SCRIPT号
   一个单位拥有若干slot，每个slot对应一个SCRIPT，显示单位时所有slot会同时参与显示（参考神灵庙四面邪魂球，设置了多个slot以实现子弹前景和特效背景同时显示）
   若使用529则单位不会因为左右移动而改变贴图
```

  
304("xxx", float x, float y, int life, int bonus, int item);
  

```
   和300的基本功能一样，但是移动方式为左右镜像。
```

  
305("xxx", float x, float y, int life, int bonus, int item);
  

```
   和301的基本功能一样，但是移动方式为左右镜像。
```

  
306(int slot,int a) 
  

```
   在相应slot上,设置单位贴图,a对应由上一个302选择的ANM文件中的SCRIPT号
   若使用306且slot 0，则单位会因为左右移动而改变贴图
   a为静止贴图，a+1，a+2为向左，右走，a+3，a+4为左面回来，右面回来
   若slot不为0，则和303无区别.
```

  
307(int a,int b) 
  

```
   在单位当前位置播放ANM文件a的第b个动画效果，b对应由上一个302选择的ANM文件的 script号
```

  
308(int a,int b) 
  

```
   在左上角播放ANM文件a的第b个动画效果，b对应由上一个302选择的ANM文件的 script号 
```

  
309("xxx", float x, float y, int life, int bonus, int item);
  

```
   用于增员(boss存在时不执行)，其余和300一样
```

  
310("xxx", float x, float y, int life, int bonus, int item);
  

```
   用于增员，其余和301一样
```

  
311("xxx", float x, float y, int life, int bonus, int item);
  

```
   用于增员，其余和304一样
```

  
312("xxx", float x, float y, int life, int bonus, int item);
  

```
   用于增员，其余和305一样
```

  
313(int a) 
  

```
   在单位当前位置播放之前选择的ANM文件的第a个动画效果，a对应由上一个302选择的ANM文件的 script号  
```

  
314(int a, b) 
  
  
315(int a, b)
  
  
316(int a, b)
  

```
   播放boss施法动作
```

  
317(int a, b)
  
  
318()
  

```
   重置动画相关,移除单位作用移动时贴图变化的flag
```

  
319(int slot,float b)
  

```
   旋转在相应slot的贴图至b方向。
```

  
320(int slot,float x,float y)
  

```
   用于改变slot位置贴图的位置 x和y
```

  
321("MapleEnemy", 0, 0, 100, 1000, 0);
  

```
   插入mapleenemy专用
```

  
322(int a,int b)
  
  
323(int a,int b)
  

```
   设置单位死亡效果，a为ANM编号，b为script号
```

  
324()
  
  
325 -333 以及335第一个参数一定是slot
  
  
325(int slot,int R,int G,int B)
  

```
   设置贴图颜色,若RGB为255 255 255（白），则维持原颜色
```

  
326(int slot,int time,int mode,int R,int G,int B)
  

```
   time帧内以mode方式改变单位位于slot的贴图颜色为rgb
```

  
327(int slot,int a)
  

```
   改变单位位于slot的贴图的不透明度为alpha.
```

  
328(int slot,int time,int mode,int alpha)
  

```
   time帧内改变单位位于slot的贴图的不透明度为alpha.
```

  
  

329(int slot,float lengthrate,float widthrate)
  

```
   设置单位位于slot的贴图的大小比例,1.0f为正常大小，替换anmins里的402等anmins设置的倍数 
```

  
330(int slot,int time,int mode,float lengthrate,float widthrate)
  

```
   time帧内改变单位位于slot的贴图的大小比例为lengthrate,float widthrate.
```

  
331(int slot,int a)
  
  
332(int slot,int a,b,c)
  
  
333(int slot,int a,b.float c,d)
  
  
334(int a) 
  

```
   播放单位的动画效果，神灵庙娘娘的邪魂球附近的雷电效果使用
```

  
335(int slot,float lengthrate,float widthrate)
  

```
   设置位于slot的贴图的大小比例,1.0f为正常大小，与anmins里的402等anmins设置的倍数叠加
```

  
336（int int）
  
  
337（int int float float float）
  
  
337（int int） 
  

```
   天空璋新337，和之前不同
```

  
338（int int float float float） 
  

```
   天空璋新338，就是之前的337
```

  
339（int int int）
  
  
340（int）
  


### 4系 单位移动
  
每一个单位都有三套坐标. 
即最终实际坐标,绝对坐标以及相对坐标,任何时候最终实际坐标=绝对坐标+相对坐标
  
  
单位被创建出来时,那个坐标即是绝对坐标,初始相对坐标为(0,0)
  
  
所有移动相关函数都是一对一对的
基本功能相同以外,第一个是改变绝对坐标,第二个改变相对坐标
  
  
  

400
MoveDirect(float x,float y);  
  

```
改变目标坐标为x,y.
```

  
401
MoveByTime(int time,int mode,float x,float y);
  

```
  将目标移动到,x,y位置.持续time帧，mode为移动方式，
```

  
402
MoveDirect2(float x,float y);  和400成对
  
  
403
MoveByTime2(int time,int mode,float x,float y);和401成对
  
  
  

404
SetUnitSpeed(float direction, float speed);
  

```
 设置移动方向以及速度
```

  
405
ChangeUnitSpeed(int time, int mode, float direction, float speed);
  

```
   改变移动方式为某个方向以某个速度移动移动。改变时间为time 改变方式为mode
   mode有四种
   0---线性  1----加速   4----减速  9----平滑 
```

  
406
SetUnitSpeed2(float direction, float speed);和404成对
  
  
407
ChangeUnitSpeed2(int time, int mode, float direction, float speed);和405成对
  
  
408
CircleMove(float θ,float speed,float radius,float,rspeed);
  

```
   使单位进行圆周运动,曲线的极坐标（原点为单位之前的位置）(radius,θ)
   θ的增速为speed，radius增速为 rspeed 
```

  
409
CircleMoveChange(int time,int mode, float speed, float radius, float rspeed);
  

```
    time帧之内改变单位圆周运动的参数,方式为mode.各参数参考408
```

  
410
CircleMove(float θ,float speed,float radius,float,rspeed);; 和408成对
  
  
411
CircleMoveChange(int time,int mode, float speed, float radius, float rspeed);和409成对
  
  
412
MoveRandom(int time,int mode,float speed); 
  

```
    目标向随机点移动一次，持续time帧，速度为speed,移动方式为mode。mode和405相同
  
```

  
413
MoveRandom(int time,int mode,float speed); 和412成对
  
  
414()将单位移动至boss的位置,此函数若在无boss时使用会导致严重误访问而爆炸
  
  
415()和414成对
  
  
416(float x,float y,float height)瞬间移动到与当前位置偏移x,y的位置,并且改变单位深度，此深度只适用于风神录（296）四面的潜水怪
  
  
417(float x,float y,float height))和416成对
  
  
418(float x,float y)仅在前作FSL（298）6面神妈的圈圈移动上使用
  
  
419(float x,float y)和418成对
  
  
420(float θ,float speed,float radius,float,rspeed,float dir,float rate)
  

```
    使单位进行椭圆运动,曲线的极坐标（原点为单位之前的位置）(radius,θ)
    θ的增速为speed，radius增速为 rspeed,dir为 椭圆偏离的方向，rate为长半轴与短半轴的比例
```

  
421(int time,int mode, float speed, float radius, float rspeed,float dir,float rate)
  

```
    time帧之内改变单位圆周运动的参数,方式为mode.各参数参考420
```

  
422(float θ,float speed,float radius,float,rspeed,float dir,float rate);和420成对 
  
  
423(int time,int mode, float speed, float radius, float rspeed,float dir,float rate);和421成对
  
  
424(int a)
  

```
  当a =1的时候赋予单位某flag(参考flag表),a=0的是消除
  此flag会影响404和405等ins,效果为左右翻转
  
```

  
425(int time,float x1,float y1,float x2,float y2,float x3,float y3)
  

```
  在time时间内将单位最终移动至点x2,y2.
  期间首先向点x1,y1移动和一点时间再向
  终点偏差x3,y3移动一段时间再移动至终点x2,y2.
  注:(假设目前坐标为(x0,y0))运动轨迹实际是由(x0,y0)到(x2,y2)的贝塞尔曲线;
  曲线的P1坐标为((x1-x0)*1/3,(y1-y0)*1/3);P2坐标为(-(x3-x2)*1/3+x2,-(y3-y2)*1/3+x2)
  (因此(x3,y3)这个点的坐标实际上是向左x正方向,向上y正方向)
  2un你为啥要把坐标先乘上1/3啊,为啥坐标倒着的啊
```

  
426(int time,float x1,float y1,float x2,float y2,float x3,float y3)和425成对
  
  
  

427()
  

```
  初始化和清零移动相关参数
```

  
428(int)404的无视左右翻转版
  
  
429(int)405的无视左右翻转版
  
  
430(int)406的无视左右翻转版
  
  
431(int)无视左右翻转版
  
  
432(int)未知
  
  
433(int)未知
  
  
434(int a,int b,int c ,float x,float y); 未知移动函数
  
  
435(int a,int b,int c ,float x,float y); 和434成对
  
  
436(int time,int mode,float x,float y); 401的无视左右翻转版
  
  
437(int time,int mode,float x,float y); 403的无视左右翻转版
  
  
  

438(int a,int b,int c ,float x,float y); 434的无视左右翻转版
  
  
439(int a,int b,int c ,float x,float y); 435的无视左右翻转版
440(float)
  
  
441(int time,int mode,float dir)
  

```
    time帧后移动方向角增加dir，方式为mode
```

  
442(float)
  
  
443(int time,int mode,float dir)
  

```
    time帧后移动方向角增加dir，方式为mode
```

  
444(float)
  
  
445(int time,int mode,float s)
  

```
    time帧内速度增加至s，方式为mode
```

  
446(float)
  
  
447(int time,int mode,float s)
  

```
    time帧内速度增加至s，方式为mode
```


### 5系  单位固有属性
  
500(float width,float height)  目标被弹判定
  
  
501(float width,float height)  目标体术判定
  
  
502(int flag) 
  

```
 设置单位的一些特定参数,a为2个4字节的开关参数0000000000000000
 详细参考下方FLAG表
```

  
503(int a)
  

```
 取消502设置的参数,和502刚好相反
```

  
504(float x,float y,float m,float n);
  

```
 限制boss的移动范围，以x,y为基准+- n 和m的范围
```

  
505()移除移动范围限制
  
  
506()清除掉落
  
  
507(int type,int amount)
  

```
 目标掉落道具及数量
 1.p点 2蓝点 3.大p 4.残碎片 5残机，6B碎片 7Bomb 8大F 9小最大得点，获得时无音效，每个增加2最大得点，
 10.中最大得点，获取时有音效，每个增加2最大得点.11.中最大得点，获取时有音效，每个增加20最大得点.
 12.B碎片(参与hzc收点系统的循环)
 12.30得点 13.40得点 14.50得点 15.B碎片 16~22.固定狼獭鹰B残红蓝 23~29.七个隐藏灵
 30~32.变色狼獭鹰 33.变色随机初始 34.不明灵状特效
```

  
  

508(float width,float height)设置掉落区域
  
  
509()掉落所有道具
  
  
510(int type) 设置目标基本掉落(相当于ins_300的最后一个参数)，数量是1.
  
  
511(int life)  更改单位血量(总血量和当前血量)
  
  
512(int a)
  

```
 设为boss战模式（血条，名字等）并设置boss编号为a，a必须从0开始编号，否则爆炸（。a=-1，结束boss。
```

  
513()
  

```
 重置时间
```

  
514(int slot，int hp，int time, string name),
  

```
 在slot处插入一个中断,使得当boss血量和或时间达到此数值时 载入下一阶段（符卡或非符）
```

  
515(int time) 无敌时间，
  
  
516(int index_SE)播放音效 
  
  
517(int a，int b，int c) 震屏特效。a：持续时间（帧），b：震动强度从b逐渐减小到0，c：震动强度从0逐渐增加到c。
  
  
518(int nMSG) 读取对话，参数对应msg文件,同时执行525
  
  
519()对话后进行下一条
  
  
520()击破后进行下一条 
  
  
521(int a,string func)
  

```
 时间到0时进行func的内容，a作用未知
```

  
522(int a, int time, int score, string spellName); 
  

```
 进入符卡模式，设置符卡宣言后右上角 符卡时间，scb，符卡名，a和符卡序号有关
 Ex面使用
 在tkz后参数变为a,scbDec,anmSerial,具体见ins_539
```

  
523()
  

```
 结束符卡模式
```

  
524(int ch)
  

```
 设置章节数,影响即将出现的符卡立绘,背景以及左上角boss的名字
 在gzz里设置的结算点，影响全局变量[-9905]
```

  
525()
  

```
 清除所有单位，有某些flag的不会被清除.
```

  
526(float)
  

```
设置弹幕生成保护范围（距离）自机在此范围内时不发弹
```

  
527(int a, float b, int c); 
  

```
 设置血条上的标记点，a是标记序号，b是血量比例，c是RGB值
```

- 血量比例以5000为基数，从12点方向顺时针开始算，与血量无关

  
528
SetSpellCard(int a, int life, int score, string spellName); 
  

```
 进入符卡模式，设置符卡宣言后右上角 符卡时间，scb，符卡名，a和符卡序号有关
 未使用  
```

  
RANK一直存在于游戏程序中，收点+rank miss减rank
  
  
529(float&amp; N，float a,float b,float c)根据RANK决定变量N
  
  
530(float&amp; N，float a,float b,float c,float d,float e)根据RANK决定变量N
  
  
531(float&amp; N，float a,float b)根据RANK决定变量N
  
  
532(int&amp; M，int a,int b,int c)根据RANK决定变量M
  
  
533(int&amp; M，int a,int b,int c,int d,int e)根据RANK决定变量M
  
  
534(int&amp; M，int a,int b)根据RANK决定变量M
  
  
535(int&amp; M,int a,int b,int c,int d)根据难度将数据写入整数M中
  
  
536(float&amp; N,float a,float b,float c,float d)根据难度将数据写入浮点数N中
  
  
537(int a, int time, int score, string spellName);
  

```
进入符卡模式，设置符卡宣言后右上角 符卡时间，scb，符卡名，a和符卡序号有关
 非ex面关底使用
```

  
538(int a, int time, int score, string spellName);
  

```
进入符卡模式，设置符卡宣言后右上角 符卡时间，scb，符卡名，a和符卡序号有关
 HZC中未使用.
```

  
539(int a, int timeScbDec, int score, string spellName); 
  

```
进入符卡模式，设置符卡宣言后右上角 符卡时间，scb，符卡名，a和符卡序号有关
 非ex面道中使用
 在tkz后参数变为a,scbDec,anmSerial
   其中a与符卡序号有关,timeScbDec为scb降低到0的时间参数,约4/3(timeScbDec-300)帧后scb降低到0,具体为每帧执行: curSCB-=(maxSCB-maxSCB&gt;&gt;2)/(timeScbDec-300),curSCB-=curSCB%10,其中curSCB为当前SCB,maxSCB为硬编码的符卡分数
   anmSerial为硬编码的符卡背景/立绘参数,为0,1时分别对应关底/道中的符卡背景/立绘
```

  
540(int)设置剩余阶段数(左上角的星星数)
  
  
541(int)仅在风神录(对应ins_361)使用过,为4,5,6面某些效果设置,效果不明.之后被zun遗弃
  
  
542() 设置符卡为时符
  
  
543()某些时符使用
  
  
544(int a)
  

```
当a=1时赋予单位某flag(参考下方flag表),a=0时取消
雷鼓的使魔们使用
```

  
545()
  

```
 重置boss一些参数，除了boss1非以外，每一张非和卡都出现和,boss逃跑和死亡也会出现
```

  
546(int a,int b)
  

```
  当a =1的时候赋予单位某flag,a=0的是消除
  此flag会使boss对Bomb免疫,并且由b来决定放b时的播放的动画 同时会消除某单位flag
  具体参照下方flag表
```

  
547(float gameSpeed)  设置时间倍率，1.0是正常，击破后减速可以设成0.5，咲夜时停是设成0.0
  
  
548(int a,int b, int c, int d);23(等待)的难度选择版
  
  
549(int a)
  

```
  将某单位的flag 0x80000000设置为a
```

  
550(int)仅在地灵殿(对应ins_370)四面使用过,效果不明.之后被zun遗弃
  
  
551(int)仅在地灵殿(对应ins_371)四面使用过,效果不明.之后被zun遗弃
  
  
552(int a)
  

```
 提高贴图图层a层,对时间值为0的贴图没用
```

  
  

553(int index_SE) 设置被打击的音效
  
  
554() 显示logoenemy
  
  
555(int&amp; A,int b)
  

```
 检查第b号单位是否存活，若存活测A=1,否则A=0.单位的编号就是单位登场的顺序.main为0号，
```

  
556(string func);设置死尸弹为func
  
  
557(int, int,int, float, float) 一些道中boss死亡时使用，效果未知
  
  
558(int a)
  

```
 a=1则赋予单位某flag,a=0消除,具体参照下方flag表
 和424功能完全一样,此flag控制左右移动翻转
```

  
559(int)未知
  
  
560(float a,flaot b)未知
  
  
561() 放出单位死亡特效（实际不死亡）庙道中击破大蝴蝶之后鬼火爆炸时发现
  
  
562() (hld中为)掉落所有物品,与ins_509不同的是ins_509会判断一个结果是否为true才决定掉落,但是该函数绝对会掉落
  
  
563(int is_rect) 设置判定点是否为方形
  
  
564(float angle) 设置判定点角度
  
  
565(float dmg_rate)
  

```
 设置使用bomb时伤害倍率，0.0的话就是不掉血，1.0就是全额伤害（包括普通射击伤害与bomb伤害）
```

  
566()没有在任何位置发现,可能zun设计之后未使用
  
  
567(int)正邪使用，效果未知
  
  
568(int)设置boss的伤害倍率，0为谱模式，1为符卡模式（用于双boss同时在场时，设置副boss的倍率）
  
  
569(int)绀珠传新增，用来设置击破率
  
  
570()绀珠传新增
  
  
571()绀珠传新增
  
  
572(int hp)(tkz)设置当前血量为hp,不同于ins_511的是不会修改最大血量
  
  
573(int index,int value) (hld)修改关于时间减少的掉落类型index掉落为value,主要在boss处使用,控制boss随击破时间增加而减少的金数
  
  
574(int maxTime) (hld)修改随时间减少的掉落物的消失时间,设置后就会启动一计时器进行计时,当(击破/强制掉落)获得掉落时,会掉落ins_573设置的掉落物数量*max(0,1-当前时间/消失时间)
  


### 6系  弹幕相关
  
600(int num)
  

```
 创建一个弹幕，该弹幕编号为num。
```

  
601(int num)
  

```
 发射num号弹幕。
```

  
602(int num, int a, int b)
  

```
 给num号弹幕设置子弹类型和颜色，a和b与bullet.anm中的描述文件的内容存在对应关系。a为子弹类型，b为子弹颜色，详见下表：
```


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
<td>高光点弹</td>
<td>2</td>
<td>葡萄弹</td>
<td>3</td>
<td>粒弹
</td></tr>
<tr>
<td>4</td>
<td>小玉</td>
<td>5</td>
<td>高光小玉</td>
<td>6</td>
<td>环玉</td>
<td>7</td>
<td>高光环玉
</td></tr>
<tr>
<td>8</td>
<td>米弹</td>
<td>9</td>
<td>链弹</td>
<td>10</td>
<td>针弹</td>
<td>11</td>
<td>札弹
</td></tr>
<tr>
<td>12</td>
<td>鳞弹</td>
<td>13</td>
<td>铳弹</td>
<td>14</td>
<td>消弹效果</td>
<td>15</td>
<td>杆菌弹
</td></tr>
<tr>
<td>16</td>
<td>顺时针旋转小星弹</td>
<td>17</td>
<td>钱币</td>
<td>18</td>
<td>中玉</td>
<td>19</td>
<td>高光中玉
</td></tr>
<tr>
<td>20</td>
<td>椭弹</td>
<td>21</td>
<td>刀弹</td>
<td>22</td>
<td>蝶弹</td>
<td>23</td>
<td>顺时针旋转大星弹
</td></tr>
<tr>
<td>24</td>
<td>逆时针旋转大星弹</td>
<td>25</td>
<td>红色炎弹</td>
<td>26</td>
<td>紫色炎弹</td>
<td>27</td>
<td>蓝紫炎弹
</td></tr>
<tr>
<td>28</td>
<td>黄色炎弹</td>
<td>29</td>
<td>心弹</td>
<td>30</td>
<td>伸缩中玉</td>
<td>31</td>
<td>矢弹
</td></tr>
<tr>
<td>32</td>
<td>大玉</td>
<td>33</td>
<td>光玉</td>
<td>34</td>
<td>滴弹</td>
<td>35</td>
<td>旋转米弹
</td></tr>
<tr>
<td>36</td>
<td>旋转针弹</td>
<td>37</td>
<td>逆时针旋转小星弹</td>
<td>38</td>
<td>激光段</td>
<td>39</td>
<td>红色音符弹
</td></tr>
<tr>
<td>40</td>
<td>蓝色音符弹</td>
<td>41</td>
<td>黄色音符弹</td>
<td>42</td>
<td>紫色音符弹</td>
<td>43</td>
<td>休止符弹
</td></tr>
<tr>
<td>44</td>
<td>顺时针旋转小阴阳玉</td>
<td>45</td>
<td>逆时针旋转小阴阳玉</td>
<td>46</td>
<td>顺时针旋转大阴阳玉</td>
<td>47</td>
<td>逆时针旋转大阴阳玉
</td></tr></tbody></table>


  
[子弹类型与颜色图示](https://share.weiyun.com/HB9ULnSH)
  
  
绀珠传以前，24是红色炎弹，25为原26，以此类推，相对顺序不变。44-47为虹龙洞加入
  
  
以上标注为高光的实际并不会自带高光，只在使用了高光的弹幕内发现，推测为2un为编译器识别添加的样式
  
  
603(int num, float x, float y)
  

```
 以基准发弹点为基础，将num号弹幕的发弹点横纵坐标偏移x和y。基准发弹点默认为当前单位的位置。
```

  
604(int num, float dir, float dif);
  

```
 设置num号弹幕的角度参数：dir为方向参数，dif为角度差参数，参数作用多样，详见607下表格。
```

  
605(int num, float maxspd, float minspd); 
  

```
 设置num号弹幕的速度参数：详见607下表格，若无特别说明，则maxspd代表最大速度，minspd代表最小速度，各层的速度在[minspd, maxspd]内均匀分布，
 例如：对某一三层开花弹(style = 3)设定maxspd = 2.0，minspd = 1.0，则这三层子弹的速度分别为1.0、1.5、2.0。
 （注：一般情况下，这两个参数位置可以随意调换，计算速度时是按两个数形成的闭区间计算，但为了方便说明，用了最大最小的描述。对于上例，设定maxspd = 1.0，minspd = 2.0，则结果不变。）
```

  
606(int num, int way, int layer)
  

```
 详见607指令下的表格，若无特别说明，则该指令作用为设置num号弹幕的way数(way)和每way中含有的层数(layer)，
 way一般指大方向，层是way内部的概念，是指way内部速度不同（方向也可能不同）的子弹。因为速度不同的子弹发射后呈现分层的形态，所以得名层。
```

  
607(int num, int style)
  

```
 根据style设置num号弹幕的形状（展开方式），详见下表：
 表中“示例”列一般会提供两张示例图，分别是偶数way和奇数way时的情形。少数style对应的形状不分奇数和偶数way，此时只提供一张示例图。
 示例图中的中玉是札弹的发弹点。蓝色札弹表示本style下的示例子弹。
 有些示例图中含有粉色的札弹，这是为方便辨别某些速度和角度关系而设计的，粉色札弹的性质将在“描述”列中说明。
 表中第四列的参数列表中，如果含有“或”字，则表示此参数的值在奇数way和偶数way时不同。
```


<table>

<tbody><tr>
<th>style</th>
<th>描述</th>
<th>示例</th>
<th>示例所用参数值
</th></tr>
<tr>
<td>0</td>
<td>普通自机狙，<br>中心方向为(自机方向 + dir)，dif为各way间角度差。<br>偶数way时中心方向无子弹。<br>粉色札弹为自机狙。
</td>
<td>
<table class="mw-collapsible mw-collapsed wikitable">

<tbody><tr>
<th>点击显示示例图
</th></tr>
<tr>
<td><ul class="gallery mw-gallery-traditional"><li class="gallerybox" style="width: 375px"><div style="width: 375px"><div class="thumb" style="width: 370px;"><div style="margin:5px auto;"><a href="./文件-脚本对照表ECL第四世代示例0_偶数.png.md" class="image"><img alt="脚本对照表ECL第四世代示例0 偶数.png" src="https://upload.thwiki.cc/thumb/2/23/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B0_%E5%81%B6%E6%95%B0.png/360px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B0_%E5%81%B6%E6%95%B0.png" decoding="async" loading="lazy" width="360" height="270" srcset="https://upload.thwiki.cc/thumb/2/23/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B0_%E5%81%B6%E6%95%B0.png/540px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B0_%E5%81%B6%E6%95%B0.png 1.5x, https://upload.thwiki.cc/thumb/2/23/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B0_%E5%81%B6%E6%95%B0.png/720px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B0_%E5%81%B6%E6%95%B0.png 2x" data-file-width="1280" data-file-height="960"></a></div></div><div class="gallerytext"></div></div></li><li class="gallerybox" style="width: 375px"><div style="width: 375px"><div class="thumb" style="width: 370px;"><div style="margin:5px auto;"><a href="./文件-脚本对照表ECL第四世代示例0_奇数.png.md" class="image"><img alt="脚本对照表ECL第四世代示例0 奇数.png" src="https://upload.thwiki.cc/thumb/2/2e/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B0_%E5%A5%87%E6%95%B0.png/360px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B0_%E5%A5%87%E6%95%B0.png" decoding="async" loading="lazy" width="360" height="270" srcset="https://upload.thwiki.cc/thumb/2/2e/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B0_%E5%A5%87%E6%95%B0.png/540px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B0_%E5%A5%87%E6%95%B0.png 1.5x, https://upload.thwiki.cc/thumb/2/2e/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B0_%E5%A5%87%E6%95%B0.png/720px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B0_%E5%A5%87%E6%95%B0.png 2x" data-file-width="1280" data-file-height="960"></a></div></div><div class="gallerytext"></div></div></li></ul>
</td></tr></tbody></table>
</td>
<td>
<p>dir = 1.5708,<br>
dif = 3.1416 / 4.0<br>
或3.1416 / 5.0,<br>
way = 5 或 6,<br>
layer = 3。
</p>
</td></tr>
<tr>
<td>1</td>
<td>普通一般弹幕，<br>在0的基础上，中心方向改为dir。
</td>
<td>
<table class="mw-collapsible mw-collapsed wikitable">

<tbody><tr>
<th>点击显示示例图
</th></tr>
<tr>
<td><ul class="gallery mw-gallery-traditional"><li class="gallerybox" style="width: 375px"><div style="width: 375px"><div class="thumb" style="width: 370px;"><div style="margin:5px auto;"><a href="./文件-脚本对照表ECL第四世代示例1_偶数.png.md" class="image"><img alt="脚本对照表ECL第四世代示例1 偶数.png" src="https://upload.thwiki.cc/thumb/5/5f/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B1_%E5%81%B6%E6%95%B0.png/360px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B1_%E5%81%B6%E6%95%B0.png" decoding="async" loading="lazy" width="360" height="270" srcset="https://upload.thwiki.cc/thumb/5/5f/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B1_%E5%81%B6%E6%95%B0.png/540px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B1_%E5%81%B6%E6%95%B0.png 1.5x, https://upload.thwiki.cc/thumb/5/5f/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B1_%E5%81%B6%E6%95%B0.png/720px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B1_%E5%81%B6%E6%95%B0.png 2x" data-file-width="1280" data-file-height="960"></a></div></div><div class="gallerytext"></div></div></li><li class="gallerybox" style="width: 375px"><div style="width: 375px"><div class="thumb" style="width: 370px;"><div style="margin:5px auto;"><a href="./文件-脚本对照表ECL第四世代示例1_奇数.png.md" class="image"><img alt="脚本对照表ECL第四世代示例1 奇数.png" src="https://upload.thwiki.cc/thumb/1/19/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B1_%E5%A5%87%E6%95%B0.png/360px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B1_%E5%A5%87%E6%95%B0.png" decoding="async" loading="lazy" width="360" height="270" srcset="https://upload.thwiki.cc/thumb/1/19/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B1_%E5%A5%87%E6%95%B0.png/540px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B1_%E5%A5%87%E6%95%B0.png 1.5x, https://upload.thwiki.cc/thumb/1/19/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B1_%E5%A5%87%E6%95%B0.png/720px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B1_%E5%A5%87%E6%95%B0.png 2x" data-file-width="1280" data-file-height="960"></a></div></div><div class="gallerytext"></div></div></li></ul>
</td></tr></tbody></table>
</td>
<td>
<p>与0相同。
</p>
</td></tr>
<tr>
<td>2</td>
<td>左偏开花自机狙，<br>中心方向为(自机方向 + dir)，<br>每way内最快的那层方向为那一way的中心方向，<br>其他层依次向顺时针方向偏转dif角度，即为“左偏”。<br>弹幕的各way均匀分布在360度方向上，不受参数控制。<br>偶数way时中心方向有子弹。<br>粉色札弹为自机狙。
</td>
<td>
<table class="mw-collapsible mw-collapsed wikitable">

<tbody><tr>
<th>点击显示示例图
</th></tr>
<tr>
<td><ul class="gallery mw-gallery-traditional"><li class="gallerybox" style="width: 375px"><div style="width: 375px"><div class="thumb" style="width: 370px;"><div style="margin:5px auto;"><a href="./文件-脚本对照表ECL第四世代示例2_偶数.png.md" class="image"><img alt="脚本对照表ECL第四世代示例2 偶数.png" src="https://upload.thwiki.cc/thumb/5/54/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B2_%E5%81%B6%E6%95%B0.png/360px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B2_%E5%81%B6%E6%95%B0.png" decoding="async" loading="lazy" width="360" height="270" srcset="https://upload.thwiki.cc/thumb/5/54/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B2_%E5%81%B6%E6%95%B0.png/540px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B2_%E5%81%B6%E6%95%B0.png 1.5x, https://upload.thwiki.cc/thumb/5/54/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B2_%E5%81%B6%E6%95%B0.png/720px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B2_%E5%81%B6%E6%95%B0.png 2x" data-file-width="1280" data-file-height="960"></a></div></div><div class="gallerytext"></div></div></li><li class="gallerybox" style="width: 375px"><div style="width: 375px"><div class="thumb" style="width: 370px;"><div style="margin:5px auto;"><a href="./文件-脚本对照表ECL第四世代示例2_奇数.png.md" class="image"><img alt="脚本对照表ECL第四世代示例2 奇数.png" src="https://upload.thwiki.cc/thumb/e/e0/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B2_%E5%A5%87%E6%95%B0.png/360px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B2_%E5%A5%87%E6%95%B0.png" decoding="async" loading="lazy" width="360" height="270" srcset="https://upload.thwiki.cc/thumb/e/e0/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B2_%E5%A5%87%E6%95%B0.png/540px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B2_%E5%A5%87%E6%95%B0.png 1.5x, https://upload.thwiki.cc/thumb/e/e0/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B2_%E5%A5%87%E6%95%B0.png/720px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B2_%E5%A5%87%E6%95%B0.png 2x" data-file-width="1280" data-file-height="960"></a></div></div><div class="gallerytext"></div></div></li></ul>
</td></tr></tbody></table>
</td>
<td>
<p>dir = 1.5708,<br>
dif = 3.1416 / 20.0<br>
或3.1416 / 24.0,<br>
way = 5 或 6,<br>
layer = 3。
</p>
</td></tr>
<tr>
<td>3</td>
<td>左偏开花一般弹幕，<br>在2的基础上，中心方向改为dir。
</td>
<td>
<table class="mw-collapsible mw-collapsed wikitable">

<tbody><tr>
<th>点击显示示例图
</th></tr>
<tr>
<td><ul class="gallery mw-gallery-traditional"><li class="gallerybox" style="width: 375px"><div style="width: 375px"><div class="thumb" style="width: 370px;"><div style="margin:5px auto;"><a href="./文件-脚本对照表ECL第四世代示例3_偶数.png.md" class="image"><img alt="脚本对照表ECL第四世代示例3 偶数.png" src="https://upload.thwiki.cc/thumb/4/46/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B3_%E5%81%B6%E6%95%B0.png/360px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B3_%E5%81%B6%E6%95%B0.png" decoding="async" loading="lazy" width="360" height="270" srcset="https://upload.thwiki.cc/thumb/4/46/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B3_%E5%81%B6%E6%95%B0.png/540px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B3_%E5%81%B6%E6%95%B0.png 1.5x, https://upload.thwiki.cc/thumb/4/46/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B3_%E5%81%B6%E6%95%B0.png/720px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B3_%E5%81%B6%E6%95%B0.png 2x" data-file-width="1280" data-file-height="960"></a></div></div><div class="gallerytext"></div></div></li><li class="gallerybox" style="width: 375px"><div style="width: 375px"><div class="thumb" style="width: 370px;"><div style="margin:5px auto;"><a href="./文件-脚本对照表ECL第四世代示例3_奇数.png.md" class="image"><img alt="脚本对照表ECL第四世代示例3 奇数.png" src="https://upload.thwiki.cc/thumb/8/8f/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B3_%E5%A5%87%E6%95%B0.png/360px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B3_%E5%A5%87%E6%95%B0.png" decoding="async" loading="lazy" width="360" height="270" srcset="https://upload.thwiki.cc/thumb/8/8f/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B3_%E5%A5%87%E6%95%B0.png/540px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B3_%E5%A5%87%E6%95%B0.png 1.5x, https://upload.thwiki.cc/thumb/8/8f/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B3_%E5%A5%87%E6%95%B0.png/720px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B3_%E5%A5%87%E6%95%B0.png 2x" data-file-width="1280" data-file-height="960"></a></div></div><div class="gallerytext"></div></div></li></ul>
</td></tr></tbody></table>
</td>
<td>
<p>与2相同。
</p>
</td></tr>
<tr>
<td>4</td>
<td>与2方向相间的弹幕，<br>在2的基础上，中心方向改为(自机方向 + dir + 3.14 / way)。<br>粉色札弹为自机狙。
</td>
<td>
<table class="mw-collapsible mw-collapsed wikitable">

<tbody><tr>
<th>点击显示示例图
</th></tr>
<tr>
<td><ul class="gallery mw-gallery-traditional"><li class="gallerybox" style="width: 375px"><div style="width: 375px"><div class="thumb" style="width: 370px;"><div style="margin:5px auto;"><a href="./文件-脚本对照表ECL第四世代示例4_偶数.png.md" class="image"><img alt="脚本对照表ECL第四世代示例4 偶数.png" src="https://upload.thwiki.cc/thumb/a/a9/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B4_%E5%81%B6%E6%95%B0.png/360px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B4_%E5%81%B6%E6%95%B0.png" decoding="async" loading="lazy" width="360" height="270" srcset="https://upload.thwiki.cc/thumb/a/a9/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B4_%E5%81%B6%E6%95%B0.png/540px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B4_%E5%81%B6%E6%95%B0.png 1.5x, https://upload.thwiki.cc/thumb/a/a9/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B4_%E5%81%B6%E6%95%B0.png/720px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B4_%E5%81%B6%E6%95%B0.png 2x" data-file-width="1280" data-file-height="960"></a></div></div><div class="gallerytext"></div></div></li><li class="gallerybox" style="width: 375px"><div style="width: 375px"><div class="thumb" style="width: 370px;"><div style="margin:5px auto;"><a href="./文件-脚本对照表ECL第四世代示例4_奇数.png.md" class="image"><img alt="脚本对照表ECL第四世代示例4 奇数.png" src="https://upload.thwiki.cc/thumb/a/ab/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B4_%E5%A5%87%E6%95%B0.png/360px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B4_%E5%A5%87%E6%95%B0.png" decoding="async" loading="lazy" width="360" height="270" srcset="https://upload.thwiki.cc/thumb/a/ab/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B4_%E5%A5%87%E6%95%B0.png/540px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B4_%E5%A5%87%E6%95%B0.png 1.5x, https://upload.thwiki.cc/thumb/a/ab/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B4_%E5%A5%87%E6%95%B0.png/720px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B4_%E5%A5%87%E6%95%B0.png 2x" data-file-width="1280" data-file-height="960"></a></div></div><div class="gallerytext"></div></div></li></ul>
</td></tr></tbody></table>
</td>
<td>
<p>与2相同。
</p>
</td></tr>
<tr>
<td>5</td>
<td>与3方向相间的弹幕，<br>在3的基础上，中心方向改为(dir + 3.14 / way)。
</td>
<td>
<table class="mw-collapsible mw-collapsed wikitable">

<tbody><tr>
<th>点击显示示例图
</th></tr>
<tr>
<td><ul class="gallery mw-gallery-traditional"><li class="gallerybox" style="width: 375px"><div style="width: 375px"><div class="thumb" style="width: 370px;"><div style="margin:5px auto;"><a href="./文件-脚本对照表ECL第四世代示例5_偶数.png.md" class="image"><img alt="脚本对照表ECL第四世代示例5 偶数.png" src="https://upload.thwiki.cc/thumb/d/dc/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B5_%E5%81%B6%E6%95%B0.png/360px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B5_%E5%81%B6%E6%95%B0.png" decoding="async" loading="lazy" width="360" height="270" srcset="https://upload.thwiki.cc/thumb/d/dc/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B5_%E5%81%B6%E6%95%B0.png/540px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B5_%E5%81%B6%E6%95%B0.png 1.5x, https://upload.thwiki.cc/thumb/d/dc/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B5_%E5%81%B6%E6%95%B0.png/720px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B5_%E5%81%B6%E6%95%B0.png 2x" data-file-width="1280" data-file-height="960"></a></div></div><div class="gallerytext"></div></div></li><li class="gallerybox" style="width: 375px"><div style="width: 375px"><div class="thumb" style="width: 370px;"><div style="margin:5px auto;"><a href="./文件-脚本对照表ECL第四世代示例5_奇数.png.md" class="image"><img alt="脚本对照表ECL第四世代示例5 奇数.png" src="https://upload.thwiki.cc/thumb/5/57/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B5_%E5%A5%87%E6%95%B0.png/360px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B5_%E5%A5%87%E6%95%B0.png" decoding="async" loading="lazy" width="360" height="270" srcset="https://upload.thwiki.cc/thumb/5/57/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B5_%E5%A5%87%E6%95%B0.png/540px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B5_%E5%A5%87%E6%95%B0.png 1.5x, https://upload.thwiki.cc/thumb/5/57/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B5_%E5%A5%87%E6%95%B0.png/720px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B5_%E5%A5%87%E6%95%B0.png 2x" data-file-width="1280" data-file-height="960"></a></div></div><div class="gallerytext"></div></div></li></ul>
</td></tr></tbody></table>
</td>
<td>
<p>与2相同。
</p>
</td></tr>
<tr>
<td>6</td>
<td>分层随机弹，<br>way在此style值下意义不同，这时它表示每层随机弹的数量。<br>所有子弹的角度在(dir-dif)与(dir+dif)之间的范围内随机，<br>但速度不变。<br>粉色札弹标识了上述随机角度范围。
</td>
<td>
<table class="mw-collapsible mw-collapsed wikitable">

<tbody><tr>
<th>点击显示示例图
</th></tr>
<tr>
<td><ul class="gallery mw-gallery-traditional"><li class="gallerybox" style="width: 375px"><div style="width: 375px"><div class="thumb" style="width: 370px;"><div style="margin:5px auto;"><a href="./文件-脚本对照表ECL第四世代示例6.png.md" class="image"><img alt="脚本对照表ECL第四世代示例6.png" src="https://upload.thwiki.cc/thumb/9/95/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B6.png/360px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B6.png" decoding="async" loading="lazy" width="360" height="270" srcset="https://upload.thwiki.cc/thumb/9/95/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B6.png/540px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B6.png 1.5x, https://upload.thwiki.cc/thumb/9/95/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B6.png/720px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B6.png 2x" data-file-width="1280" data-file-height="960"></a></div></div><div class="gallerytext"></div></div></li></ul>
</td></tr></tbody></table>
</td>
<td>
<p>dir = 1.5708,<br>
dif = 1.5708 * 2.0 / 3.0<br>
way = 5,<br>
layer = 3。
</p>
</td></tr>
<tr>
<td>7</td>
<td>速度随机弹，<br>在3的基础上，每层速度不再按605指令的说明计算，<br>而是在maxspd与(maxspd+minspd)之间的范围内随机。<br>所有子弹的角度不变。<br>粉色札弹标识了上述速度范围。
</td>
<td>
<table class="mw-collapsible mw-collapsed wikitable">

<tbody><tr>
<th>点击显示示例图
</th></tr>
<tr>
<td><ul class="gallery mw-gallery-traditional"><li class="gallerybox" style="width: 375px"><div style="width: 375px"><div class="thumb" style="width: 370px;"><div style="margin:5px auto;"><a href="./文件-脚本对照表ECL第四世代示例7_偶数.png.md" class="image"><img alt="脚本对照表ECL第四世代示例7 偶数.png" src="https://upload.thwiki.cc/thumb/3/31/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B7_%E5%81%B6%E6%95%B0.png/360px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B7_%E5%81%B6%E6%95%B0.png" decoding="async" loading="lazy" width="360" height="270" srcset="https://upload.thwiki.cc/thumb/3/31/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B7_%E5%81%B6%E6%95%B0.png/540px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B7_%E5%81%B6%E6%95%B0.png 1.5x, https://upload.thwiki.cc/thumb/3/31/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B7_%E5%81%B6%E6%95%B0.png/720px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B7_%E5%81%B6%E6%95%B0.png 2x" data-file-width="1280" data-file-height="960"></a></div></div><div class="gallerytext"></div></div></li><li class="gallerybox" style="width: 375px"><div style="width: 375px"><div class="thumb" style="width: 370px;"><div style="margin:5px auto;"><a href="./文件-脚本对照表ECL第四世代示例7_奇数.png.md" class="image"><img alt="脚本对照表ECL第四世代示例7 奇数.png" src="https://upload.thwiki.cc/thumb/7/77/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B7_%E5%A5%87%E6%95%B0.png/360px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B7_%E5%A5%87%E6%95%B0.png" decoding="async" loading="lazy" width="360" height="270" srcset="https://upload.thwiki.cc/thumb/7/77/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B7_%E5%A5%87%E6%95%B0.png/540px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B7_%E5%A5%87%E6%95%B0.png 1.5x, https://upload.thwiki.cc/thumb/7/77/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B7_%E5%A5%87%E6%95%B0.png/720px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B7_%E5%A5%87%E6%95%B0.png 2x" data-file-width="1280" data-file-height="960"></a></div></div><div class="gallerytext"></div></div></li></ul>
</td></tr></tbody></table>
</td>
<td>
<p>maxspd = 1.0,<br>
minspd = 1.0,<br>
其他与2相同。
</p>
</td></tr>
<tr>
<td>8</td>
<td>完全随机弹，<br>向(dir-dif)与(dir+dif)之间的范围内，<br>以maxspd与(maxspd+minspd)之间的范围内随机的速度，<br>发射(way * layer)个子弹。<br>way和layer均失去原本意义。<br>粉色札弹标识了上述角度和速度范围。
</td>
<td>
<table class="mw-collapsible mw-collapsed wikitable">

<tbody><tr>
<th>点击显示示例图
</th></tr>
<tr>
<td><ul class="gallery mw-gallery-traditional"><li class="gallerybox" style="width: 375px"><div style="width: 375px"><div class="thumb" style="width: 370px;"><div style="margin:5px auto;"><a href="./文件-脚本对照表ECL第四世代示例8.png.md" class="image"><img alt="脚本对照表ECL第四世代示例8.png" src="https://upload.thwiki.cc/thumb/7/7b/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B8.png/360px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B8.png" decoding="async" loading="lazy" width="360" height="270" srcset="https://upload.thwiki.cc/thumb/7/7b/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B8.png/540px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B8.png 1.5x, https://upload.thwiki.cc/thumb/7/7b/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B8.png/720px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B8.png 2x" data-file-width="1280" data-file-height="960"></a></div></div><div class="gallerytext"></div></div></li></ul>
</td></tr></tbody></table>
</td>
<td>
<p>dir = 1.5708,<br>
dif = 1.5708 * 2.0 / 3.0<br>
way = 5,<br>
layer = 3,<br>
maxspd = 1.0,<br>
minspd = 1.0。
</p>
</td></tr>
<tr>
<td>9</td>
<td>双偏开花自机狙，<br>在2的基础上，不仅有“左偏”的子弹，<br>还增加了“右偏”的子弹，即为“双偏”。<br>“右偏”除了方向是逆时针偏转外，与“左偏”定义一致。<br>粉色札弹为自机狙。
</td>
<td>
<table class="mw-collapsible mw-collapsed wikitable">

<tbody><tr>
<th>点击显示示例图
</th></tr>
<tr>
<td><ul class="gallery mw-gallery-traditional"><li class="gallerybox" style="width: 375px"><div style="width: 375px"><div class="thumb" style="width: 370px;"><div style="margin:5px auto;"><a href="./文件-脚本对照表ECL第四世代示例9_偶数.png.md" class="image"><img alt="脚本对照表ECL第四世代示例9 偶数.png" src="https://upload.thwiki.cc/thumb/a/a6/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B9_%E5%81%B6%E6%95%B0.png/360px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B9_%E5%81%B6%E6%95%B0.png" decoding="async" loading="lazy" width="360" height="270" srcset="https://upload.thwiki.cc/thumb/a/a6/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B9_%E5%81%B6%E6%95%B0.png/540px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B9_%E5%81%B6%E6%95%B0.png 1.5x, https://upload.thwiki.cc/thumb/a/a6/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B9_%E5%81%B6%E6%95%B0.png/720px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B9_%E5%81%B6%E6%95%B0.png 2x" data-file-width="1280" data-file-height="960"></a></div></div><div class="gallerytext"></div></div></li><li class="gallerybox" style="width: 375px"><div style="width: 375px"><div class="thumb" style="width: 370px;"><div style="margin:5px auto;"><a href="./文件-脚本对照表ECL第四世代示例9_奇数.png.md" class="image"><img alt="脚本对照表ECL第四世代示例9 奇数.png" src="https://upload.thwiki.cc/thumb/d/d9/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B9_%E5%A5%87%E6%95%B0.png/360px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B9_%E5%A5%87%E6%95%B0.png" decoding="async" loading="lazy" width="360" height="270" srcset="https://upload.thwiki.cc/thumb/d/d9/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B9_%E5%A5%87%E6%95%B0.png/540px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B9_%E5%A5%87%E6%95%B0.png 1.5x, https://upload.thwiki.cc/thumb/d/d9/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B9_%E5%A5%87%E6%95%B0.png/720px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B9_%E5%A5%87%E6%95%B0.png 2x" data-file-width="1280" data-file-height="960"></a></div></div><div class="gallerytext"></div></div></li></ul>
</td></tr></tbody></table>
</td>
<td>
<p>与2相同。
</p>
</td></tr>
<tr>
<td>10</td>
<td>双偏开花一般弹幕，<br>在9的基础上，中心方向改为dir。
</td>
<td>
<table class="mw-collapsible mw-collapsed wikitable">

<tbody><tr>
<th>点击显示示例图
</th></tr>
<tr>
<td><ul class="gallery mw-gallery-traditional"><li class="gallerybox" style="width: 375px"><div style="width: 375px"><div class="thumb" style="width: 370px;"><div style="margin:5px auto;"><a href="./文件-脚本对照表ECL第四世代示例10_偶数.png.md" class="image"><img alt="脚本对照表ECL第四世代示例10 偶数.png" src="https://upload.thwiki.cc/thumb/5/5e/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B10_%E5%81%B6%E6%95%B0.png/360px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B10_%E5%81%B6%E6%95%B0.png" decoding="async" loading="lazy" width="360" height="270" srcset="https://upload.thwiki.cc/thumb/5/5e/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B10_%E5%81%B6%E6%95%B0.png/540px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B10_%E5%81%B6%E6%95%B0.png 1.5x, https://upload.thwiki.cc/thumb/5/5e/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B10_%E5%81%B6%E6%95%B0.png/720px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B10_%E5%81%B6%E6%95%B0.png 2x" data-file-width="1280" data-file-height="960"></a></div></div><div class="gallerytext"></div></div></li><li class="gallerybox" style="width: 375px"><div style="width: 375px"><div class="thumb" style="width: 370px;"><div style="margin:5px auto;"><a href="./文件-脚本对照表ECL第四世代示例10_奇数.png.md" class="image"><img alt="脚本对照表ECL第四世代示例10 奇数.png" src="https://upload.thwiki.cc/thumb/e/e6/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B10_%E5%A5%87%E6%95%B0.png/360px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B10_%E5%A5%87%E6%95%B0.png" decoding="async" loading="lazy" width="360" height="270" srcset="https://upload.thwiki.cc/thumb/e/e6/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B10_%E5%A5%87%E6%95%B0.png/540px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B10_%E5%A5%87%E6%95%B0.png 1.5x, https://upload.thwiki.cc/thumb/e/e6/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B10_%E5%A5%87%E6%95%B0.png/720px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B10_%E5%A5%87%E6%95%B0.png 2x" data-file-width="1280" data-file-height="960"></a></div></div><div class="gallerytext"></div></div></li></ul>
</td></tr></tbody></table>
</td>
<td>
<p>与2相同。
</p>
</td></tr>
<tr>
<td>11</td>
<td>扁开花弹，<br>中心方向为dir，dif在此style值下无意义。<br>在一般一层开花弹（style = 3, layer = 1）的基础上，<br>各层内各way的速度与角度呈以下函数关系：
<p>将速度和角度归一化，最慢层的速度为0，最快层的速度为1，<br>令与中心方向相差90度的角度为0，中心方向角度为1，<br>以速度v为因变量，角度x为自变量，<br>则有v = 0.75x² + 0.25x。
</p><p>无论是奇数还是偶数way，中心方向上均必有一颗子弹，<br>其他子弹的角度都均匀分布在360度方向上。<br>粉色札弹标识了速度和角度的关系，例如，根据上述函数，<br>x = 2/3时v = 1/2，<br>即偏离中心方向30度的子弹速度为中心方向子弹速度的1/2，<br>表现为这颗蓝色札弹与中间的粉色札弹重合。<br>layer &gt; 1时，不同层的速度关系仍满足605中描述，<br>例如图中内层的中心方向子弹速度为0.5。
</p>
</td>
<td>
<table class="mw-collapsible mw-collapsed wikitable">

<tbody><tr>
<th>点击显示示例图
</th></tr>
<tr>
<td><ul class="gallery mw-gallery-traditional"><li class="gallerybox" style="width: 375px"><div style="width: 375px"><div class="thumb" style="width: 370px;"><div style="margin:5px auto;"><a href="./文件-脚本对照表ECL第四世代示例11_偶数.png.md" class="image"><img alt="脚本对照表ECL第四世代示例11 偶数.png" src="https://upload.thwiki.cc/thumb/d/df/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B11_%E5%81%B6%E6%95%B0.png/360px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B11_%E5%81%B6%E6%95%B0.png" decoding="async" loading="lazy" width="360" height="270" srcset="https://upload.thwiki.cc/thumb/d/df/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B11_%E5%81%B6%E6%95%B0.png/540px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B11_%E5%81%B6%E6%95%B0.png 1.5x, https://upload.thwiki.cc/thumb/d/df/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B11_%E5%81%B6%E6%95%B0.png/720px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B11_%E5%81%B6%E6%95%B0.png 2x" data-file-width="1280" data-file-height="960"></a></div></div><div class="gallerytext"></div></div></li><li class="gallerybox" style="width: 375px"><div style="width: 375px"><div class="thumb" style="width: 370px;"><div style="margin:5px auto;"><a href="./文件-脚本对照表ECL第四世代示例11_奇数.png.md" class="image"><img alt="脚本对照表ECL第四世代示例11 奇数.png" src="https://upload.thwiki.cc/thumb/d/d0/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B11_%E5%A5%87%E6%95%B0.png/360px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B11_%E5%A5%87%E6%95%B0.png" decoding="async" loading="lazy" width="360" height="270" srcset="https://upload.thwiki.cc/thumb/d/d0/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B11_%E5%A5%87%E6%95%B0.png/540px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B11_%E5%A5%87%E6%95%B0.png 1.5x, https://upload.thwiki.cc/thumb/d/d0/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B11_%E5%A5%87%E6%95%B0.png/720px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B11_%E5%A5%87%E6%95%B0.png 2x" data-file-width="1280" data-file-height="960"></a></div></div><div class="gallerytext"></div></div></li></ul>
</td></tr></tbody></table>
</td>
<td>
<p>dir = 1.5708,<br>
way = 24或23,<br>
layer = 2,<br>
maxspd = 2.0,<br>
minspd = 0.5。
</p>
</td></tr>
<tr>
<td>12</td>
<td>与11方向相间的弹幕<br>各子弹速度仍由11中描述的函数决定，<br>无论奇数还是偶数way，中心方向上一定无子弹，<br>奇数way时中心方向的对称方向上一定有一颗子弹。
</td>
<td>
<table class="mw-collapsible mw-collapsed wikitable">

<tbody><tr>
<th>点击显示示例图
</th></tr>
<tr>
<td><ul class="gallery mw-gallery-traditional"><li class="gallerybox" style="width: 375px"><div style="width: 375px"><div class="thumb" style="width: 370px;"><div style="margin:5px auto;"><a href="./文件-脚本对照表ECL第四世代示例12_偶数.png.md" class="image"><img alt="脚本对照表ECL第四世代示例12 偶数.png" src="https://upload.thwiki.cc/thumb/0/0d/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B12_%E5%81%B6%E6%95%B0.png/360px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B12_%E5%81%B6%E6%95%B0.png" decoding="async" loading="lazy" width="360" height="270" srcset="https://upload.thwiki.cc/thumb/0/0d/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B12_%E5%81%B6%E6%95%B0.png/540px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B12_%E5%81%B6%E6%95%B0.png 1.5x, https://upload.thwiki.cc/thumb/0/0d/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B12_%E5%81%B6%E6%95%B0.png/720px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B12_%E5%81%B6%E6%95%B0.png 2x" data-file-width="1280" data-file-height="960"></a></div></div><div class="gallerytext"></div></div></li><li class="gallerybox" style="width: 375px"><div style="width: 375px"><div class="thumb" style="width: 370px;"><div style="margin:5px auto;"><a href="./文件-脚本对照表ECL第四世代示例12_奇数.png.md" class="image"><img alt="脚本对照表ECL第四世代示例12 奇数.png" src="https://upload.thwiki.cc/thumb/d/db/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B12_%E5%A5%87%E6%95%B0.png/360px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B12_%E5%A5%87%E6%95%B0.png" decoding="async" loading="lazy" width="360" height="270" srcset="https://upload.thwiki.cc/thumb/d/db/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B12_%E5%A5%87%E6%95%B0.png/540px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B12_%E5%A5%87%E6%95%B0.png 1.5x, https://upload.thwiki.cc/thumb/d/db/%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B12_%E5%A5%87%E6%95%B0.png/720px-%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8ECL%E7%AC%AC%E5%9B%9B%E4%B8%96%E4%BB%A3%E7%A4%BA%E4%BE%8B12_%E5%A5%87%E6%95%B0.png 2x" data-file-width="1280" data-file-height="960"></a></div></div><div class="gallerytext"></div></div></li></ul>
</td></tr></tbody></table>
</td>
<td>
<p>与11相同。
</p>
</td></tr></tbody></table>


  
608(int num, int a, int b);
  

```
 设置num号弹幕的音效，a表示发弹音效，b表示变速音效。参数为-1表示设置为无音效。
```

  
609(int num，变换序号,通道,int mode,int a,int b,float r,float s)
  
  
610(int num，变换序号,通道,int mode,int a,int b,int c,int d,float r,float s，float m,float n)
  
  
611(int num，通道,int mode,int a,int b,float r,float s)
  
  
612(int num，通道,int mode,int a,int b,int c,int d,float r,float s，float m,float n)
  

```
 609-612均为给弹幕设置变换的指令，具体解释请翻至最下面[这里](#609-612.E6.8C.87.E4.BB.A4.E8.AF.A6.E8.A7.A3)查看。
```

  
613()
  

```
 全屏消弹，消去的子弹不转化为绿点。
```

  
614(int numa, int numb)
  

```
 复制numb号弹幕的所有已设定的参数到numa号弹幕中。
```

  
615(float r)
  

```
 消掉以当前单位位置为中心，半径r的圆形范围内的子弹，消去的子弹转化为绿点。
```

  
616(float r)
  

```
 消掉以当前单位位置为中心，半径r的圆形范围内的子弹，但消去的子弹不转化为绿点。
```

  
617(弹幕编号，float a,b,c,d,e,f)根据rank的值来决定弹速
  
  
618(弹幕编号，float a,b,c,d,e,f,g,h,i,j)根据rank的值来决定弹速
  
  
619(弹幕编号，float a,b,c,d)根据rank的值来决定弹速
  
  
620(弹幕编号，int a,b,c,d,e,f)根据rank的值来决定way数和层数
  
  
621(弹幕编号，int a,b,c,d,e,f,g,h,i,j)根据rank的值来决定way数和层数
  
  
622(弹幕编号，int a,b,c,d)根据rank的值来决定way数和层数
  
  
623(%N,float x,float y) 计算 点x,y到 自机到角度并存入N中
  
  
624(int num, float a, b, c, d, e, f, g, h)
  

```
 605的难度融合版，在Easy难度下相当于执行ins_605(num, a, e)，Normal难度下相当于执行ins_605(num, b, f)，以此类推。
```

  
625(int num, int a, b, c, d, e, f, g, h)
  

```
 606的难度融合版，在Easy难度下相当于执行ins_606(num, a, e)，Normal难度下相当于执行ins_606(num, b, f)，以此类推。
```

  
626(int num, float o, float r)
  

```
 以基准发弹点为基础，将num号弹幕的发弹点偏移(o, r)，其中(o, r)为极坐标。基准发弹点默认为当前单位的位置。
```

  
627(int num, float dis)
  

```
 设置发弹方式为从以当前发弹点为圆心，半径为dis的圆周上发弹，而不是从发弹点发弹。
```

  
628(int num, float x, float y)
  

```
 设置基准发弹点为(x, y)。
```

  
629(flout r,int color)
  

```
 设置boss周围的纹理变化特性，影响半径为r，颜色为color，对应RGB颜色。
```

  
630(int a)
  

```
 执行STD脚本a。
```

  
631(int a)
  

```
 a=时,隐藏boss血条以及时间，是否无敌和锁时间待测试
```

  
632(int a)
  

```
 boss每身重置为0，有些特殊攻击模式时启用，
 使用一些封装函数，如雷鼓震屏，正邪翻转，和637共用一套函数，
 637多为一次性的效果，632为长久效果
```

  
633(int a)
  

```
 封装函数，当a=1时，将会每帧从[-9940]里取出值并作为伤害传递给Boss
```

  
634(int a)
  

```
 封装函数，当a=1时，单位的体术判定采用特殊方式
```

  
635(float r)
  

```
 消掉半径为r范围内的弹幕,消掉的弹幕变为最大得点,与615还有一处不同
```

  
636(float r)
  

```
 消掉半径为r范围内的弹幕,消掉的弹幕变为最大得点,与616还有一处不同
```

  
637(int)
  

```
 boss每身重置为0，有些特殊攻击模式时启用，
 使用一些封装函数，如雷鼓震屏，正邪翻转，和632 共用一套函数，
 637为一次性的效果，632为长久效果
```

  
638(int)未知
  
  
639(int)未知
  
  
640(弹幕编号,int a,"func"); 由弹幕召唤使魔的时候使用，需要a= mode 16777216的弹幕编号2
  
  
641(弹幕编号)hzc6面时符大型刀弹使用，用途未知
  


### 7系  激光相关
  
700(弹幕编号,float a,float length,float b,float width)
  

```
 使弹幕变成激光，设置长度和宽度，a和b是开始位置的参数，一般激光设成0就行
 17条爆弹那种预警线+直接生产的设置成和长度一样
 若要发射曲线激光，则a,length,b 都是无关参数，设成-1.0f,曲线激光只可以设置宽度.
```

  
701(弹幕编号,int a,int b,int c,int d, int e)
  

```
  设置预警线持续时间a和激光的持续时间c. b和d分别是从预警线变为实际激光和激光消失过程需要的时间，e一般为0
   用途未知
   若发射曲线激光则，则b,c,d,都是无关参数，a是激光发射持续时间（决定其长度） e让然是迷之0
```

  
702(弹幕编号)普通激光的发弹函数
  
  
703(弹幕编号,int a) 发射预警线激光专用，a为激光编号，区别于弹幕编号
  
  
704(激光编号,float x,float y) 改变激光的起点为x,y
  
  
705(激光编号,float x,float y) 赋予激光起点一个速度
  
  
707(激光编号,float width) 改变激光的宽度为width
  
  
708(激光编号,float a) 改变激光的角度为a
  
  
709(激光编号,float a) 
  

```
赋予激光一个顺时针的角速度a
```

  
710(激光编号) 消除激光
  
  
711(弹幕编号) 曲线激光用发弹函数
  
  
712(float length,float width) 改变单位判定，使其变成类似于激光的东西
  
  
713(int)
  
  
714(int int )
  


### 8系 单位互动
  
800(int,"subroutin");推测是同时开启另一个人的"subroutin"，第一个int参数与编号有关，不明。eg.比如绀珠传ex的纯狐与赫卡互动。
  
  
801(float %X,float %Y,int n); 返回(X,Y)等于第n号小怪的坐标。eg.比如神灵庙6道中判断大蝴蝶如果出屏则幽灵就不因大蝴蝶出屏消失而死亡
  
  
802(int);参数为0，立即击破场上boss当前阶段（用于多boss同台时，击破一个boss时另一个boss也同时击破，例hzcex道中1，2符）
  


### 9系 Debug相关
  
所有9系皆为debug相关，正是游戏中没有任何作用
9开头的函数一共只发现以下三种
  
  
900() 仅仅在一面道中的GirlTest中出现一次，zun测试用
  
  
901() 仅在DebugSkipFunc 使用，zun用来跳过Debug
  
  
902() zun为debug用。
  


### 10系 备用
  
10系在每作的作用大不相同，应该是zun备用的一个系
神灵庙中 有 
  
  
1000(int);直接掉落一个指定类型的灵，0为红灵、1为蓝灵、2为绿灵、3为白灵、4为蓝灵、5为隐形灵、6以后会播放奇怪的音效并产生一个隐形的灵
  
  
1001(int);设置掉落的灵衰减为0的帧数
  
  
1002(int);设置掉落的灵的数量的最大值
  
  
1003(int);设置单位受到伤害时是否掉灵，奇数不掉，偶数掉
  


##### 辉针城
  
1001(int);
  
  
1002(int);
  
  
1003(int)
  


##### 天邪鬼
  
1001(int);
  
  
1002(int);
  
  
1003(int);
  
  
  

1004();
  
  
1005();直接通关
  
  
1006();直接时间到gameover
  


##### 绀珠传
  
1001(int);
  
  
1002(int);
  


##### 天空璋
  
1000(int a, int b, int c):天空璋中出现，用于控制单位掉落的季节道具。a为变化帧数，b为初始季节道具数，c为最终季节道具数。单位掉落的季节道具会在a帧内从b变为c。
  
  
1001(int a); 天空璋中可用于控制单位掉落的季节道具。单位每减少a血量掉落一个季节点。
  


##### 噩梦日记
  
1000() 结束本关
  
  
1002(double a) 控制照片分数倍率
  
  
1008(int a) a=0 没收相机 a=1 归还相机
  
  
1009(int a) 控制照相机伤害
  


##### 兽王园
  
ins_1028(float a) 消弹圈大小
  
  
ins_1031(int a) 消弹圈扩张时间
  


### 609-612指令详解
  
mode
  

```
 这四个指令本质相同，都是弹幕的高级变换，这些变换根据mode不同而不同
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
 609，和610标明出来序号
 611和612省略了序号，但实际仍然存在
 例如
 611(弹幕编号,.......)
 611(弹幕编号,.......)
 609(弹幕编号,2,.......)
 610(弹幕编号,3,.......)
 这里虽然前两个611未省略了序号,实际系统会认为他们分别是0和1
 除非使用特别mode,这些变换不能跳过
 例如
 611(弹幕编号,.......)
 611(弹幕编号,.......)
 609(弹幕编号,3,.......)
 610(弹幕编号,4,.......)
 这里少了序号2,所以后面两个不会执行
 可以控制跳跃执行的有8192,32768,65536
```

```
 除了用特殊可控序号的mode以外,609/610和611/612,有个最大的区别就是可以放心写进循环当中
 倘若将611/612写入循环里，则每个循环都要执行一次，这样会列出非常多的变换导致bug
 而609/610自带变换序号，即使反复执行,也只会覆盖之前的变换，不会产生新的变换
 
```

  
通道
  

```
 当通道为0的时候变换都是一个完成后执行下一个
 而同道为1的变换则会同时进行.
 对于64弹墙和4096穿越若使用同一个通道则4096完全失效
 使用不同通道时,弹墙优先于穿越
 
```

  
剩余参数
  

```
 整数abcd，浮点数rsmn是根据mode用途都不同的参数
 有些mode只需要其中部分，比如mode1不需要任何参数，mode 8需要 a，r，s三个参数
 不需要使用的参数则写入-999999或-999999.0f
 大部分mode 只需要a，b，r，s四个参数，因此使用609和611即可
 有些mode需要8个参数，此时应使用610和612
 目前发现除mode16,8192，16384以外，均可用609和611
 
```

  
mode表
  

```
 O表示需要此参数,X表示无关参数
 注意此表是以hzc为准，如gzz中 mode8192的用法明显有改变
```


<table>
<tbody><tr>
<th scope="col" width="20">序号
</th>
<th scope="col" width="90">10进制
</th>
<th>参数a</th>
<th>参数b</th>
<th>参数c</th>
<th>参数d</th>
<th>参数r</th>
<th>参数s</th>
<th>参数m</th>
<th>参数n</th>
<th>功能
</th></tr>
<tr>
<td>0</td>
<td>1</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>弹幕生成时向前蹿一小段距离
</td></tr>
<tr>
<td>1</td>
<td>2</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>根据a设置弹雾
</td></tr>
<tr>
<td>2</td>
<td>4</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>O</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>设置加速度为r，加速时间a，s为加速度的角度，
</td></tr>
<tr>
<td>3</td>
<td>8</td>
<td>O</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>O</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>设置切向加速度为r，s自转角速度，持续时间为a，b一般情况下不使用,当变换对象是曲线激光时，各个变换将会同时进行，此时b来设置b帧后执行.（每帧速度大小增加r，速度角度增加s）
</td></tr>
<tr>
<td>4</td>
<td>16</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>a帧后停顿，变化次数为b,变换类型为c，d通常设置为0，用途未知，r、s用途取决于变换类型
<p>0方向为原方向+r，速度变为s<br>
1.一直奇怪的自机相关的改变方式<br>
2.自机相关+r的改变方式<br>
3.方向变为-r,速度变为s;配合8388608使用,将弹幕的方向变为8388608存储的方向+r<br>
4.方向变为r,速度变为s<br>
5.所有子弹随机在原方向±r范围内随机<br>
6.所有子弹随机变向为±r范围内泛狙<br>
7.方向不变，速度变为s(gzz后为速度变为随机±s)
</p>
</td></tr>
<tr>
<td>5</td>
<td>32</td>
<td>-</td>
<td>-</td>
<td>-</td>
<td>-</td>
<td>-</td>
<td>-</td>
<td>-</td>
<td>-</td>
<td>未使用,保留
</td></tr>
<tr>
<td>6</td>
<td>64</td>
<td>O</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>X</td>
<td>触壁反弹，a为反弹次数，b是一个6位的2进制数来设置可反弹墙壁，从右到左依次为上下左右，为1则为反弹+变速，为0则只变速，即如果b=001111则4面全可以反弹，b=000000则碰到四面就改变速度（变速后再碰到反弹墙则不变速），r为接触墙壁后的速度；s,m一般不使用；当b前第六位为1时，改变反弹墙位置，s,m分别代表左右，上下方的反弹壁与屏幕中心的距离。
</td></tr>
<tr>
<td>7</td>
<td>128</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>设置弹幕不可消弹时间为a帧，这段时间内无法消取本弹幕
</td></tr>
<tr>
<td>8</td>
<td>256</td>
<td>O</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>设置子弹可以在屏幕外持续的时间为a帧,.<span style="color:red;">b作用未知</span>
</td></tr>
<tr>
<td>9</td>
<td>512</td>
<td>O</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>改变弹幕形状位a，b
</td></tr>
<tr>
<td>10</td>
<td>1024</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>消除子弹，a为消弹效果，有0和1两种形式，
</td></tr>
<tr>
<td>11</td>
<td>2048</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>播放音效a
</td></tr>
<tr>
<td>12</td>
<td>4096</td>
<td>O</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>穿墙，参数用法和弹墙64相同.
</td></tr>
<tr>
<td>13</td>
<td>8192</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>在当前弹幕的位置新子弹,a是展开形式，即607的参数，跳跃至变换序号b，c为way数，d为层数，r为方向角度(若=-999.0f则保持原方向(gzz之后-999999.0f))，s为角度差，m为速度(若=-999.0f则保持原速度(gzz之后-999999.0f))n为速度差
</td></tr>
<tr>
<td>14</td>
<td>16384</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>设置8192产生的子弹的属性，ab是设置弹幕形状和颜色，c来设置是否消去原先的子弹，1为消，0则保留，d为消弹效果，其他参数为生成激光的参数,具体参照下方表格
</td></tr>
<tr>
<td>15</td>
<td>32768</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>根据指令632的参数赋予弹幕不同效果.具体参见下方。
</td></tr>
<tr>
<td>16</td>
<td>65536</td>
<td>O</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>跳到变换a执行（用来循环）(在th16中b的用处是设置循环次数)
</td></tr>
<tr>
<td>17</td>
<td>131072</td>
<td>O</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>O</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>变换执行时，子弹在a帧内，以b方式（b参数见405下面那个mode），向（r，s）坐标移动，最后速度恢复为原速度;这是独有的几个不受524288叠加效果的变换
</td></tr>
<tr>
<td>18</td>
<td>262144</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>O</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>子弹方向立即变为r，子弹速度立即变为s。（配合mode131072估计会很好用吧，比mode16纯粹多了）
</td></tr>
<tr>
<td>19</td>
<td>524288</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>O</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>给子弹叠加一个与605原弹速独立的速度，服从平行四边形定则。r角度，s速度，a作用未知，但是需要是正整数(已确认是2un写错了)
</td></tr>
<tr>
<td>20</td>
<td>1048576</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>根据a改变弹幕为高亮弹幕，a=1则是亮弹幕,a=0则普通(th16新增a=2为减去效果(2un你就不能把所有效果都放出来么)
</td></tr>
<tr>
<td>21</td>
<td>2097152</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>O</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>在a帧时间内，给予弹幕一个独立于原速度的速度，朝向为s,速度为(r-原速度),服从平行四边形原则(此函数只调用一次，因此使用-9989.0f来瞄准自机则会到时只有调用这个函数瞬间的自机位置有效，此后子弹将一直瞄准这个位置.若想实时瞄准自机，需让s=999.0f,-999999.0f则不改变角度，同时要让弹幕原本的速度为0.0f，不然因为速度叠加的关系，弹幕的角度和自机狙会有所差异)(GZZ后使用999999.0f替代999.0f，虹龙洞后3000000.0f为自机狙、4000000.0f为随机角度)
</td></tr>
<tr>
<td>22</td>
<td>4194304</td>
<td>O</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>O</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>改变弹幕大小，a为变化时间，b为变化模式(b=0则是匀速变化）r为初始倍率，s为最终倍率.
</td></tr>
<tr>
<td>23</td>
<td>8388608</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>标记当前弹幕的方向,和mode16,c=3配合使用
</td></tr>
<tr>
<td>24</td>
<td>16777216</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>由子弹生成使魔的时候使用，和640配合，因需要使用参数变换编号2，必须使用609
</td></tr>
<tr>
<td>25</td>
<td>33554432</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>设置此子弹的图层为a。（图层大的在上面）
</td></tr>
<tr>
<td>26</td>
<td>67108864</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>子弹延时a帧后生成
</td></tr>
<tr>
<td>27</td>
<td>134217728</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>(在th15之后出现)生成激光,参数为:a,弹幕类型,颜色,d,方向,速度,发射时长度,总长度;       激光的类别由a决定a=0发射型,a=1预警线;   d在激光类别为发射型时d=0保留原弹幕,1消弹;如果激光为预警线型时,d是一个flag,1位为是否在boss处(使用了ins_512的单位)发射,65536位为是否消弹;发射时长度指预警线激光的初始长度,建议设置为和总长度一致.有关16384的用法见下表
</td></tr>
<tr>
<td>28</td>
<td>268435456</td>
<td>-</td>
<td>-</td>
<td>-</td>
<td>-</td>
<td>-</td>
<td>-</td>
<td>-</td>
<td>-</td>
<td>未使用，保留
</td></tr>
<tr>
<td>29</td>
<td>536870912</td>
<td>-</td>
<td>-</td>
<td>-</td>
<td>-</td>
<td>O</td>
<td>-</td>
<td>-</td>
<td>-</td>
<td>(th16)将弹幕判定修改为r个像素,输入-1.0f恢复成原大小
</td></tr>
<tr>
<td>30</td>
<td>1073741824</td>
<td>O</td>
<td>-</td>
<td>-</td>
<td>-</td>
<td>O</td>
<td>O</td>
<td>O</td>
<td>-</td>
<td>(th17)在a帧内每帧执行以下操作: 考虑从弹幕坐标朝向自机坐标的角度α,构造向量 n = r * (cos(α + s),sin(α + s)),同时记弹幕的速度向量为v,则下一帧弹幕的速度v2 = v*(1-m) + n*m (即弹幕在a帧内具有向(自机方向+s)方向转动以及加速到速度r的趋势,且该趋势大小为m)
</td></tr>
<tr>
<td>31</td>
<td>-2147483648</td>
<td>O</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>X</td>
<td>a帧后执行下一个变换
</td></tr></tbody></table>


```
 当mode 使用32768时，根据弹幕发出者的ins_632(int flag)的参数不同而不同.
 若flag=0,则无任何效果
 1.使单位本身可以对弹幕靠近产生反应.（hzc4a线2卡）
   通过[-9978.0f]来决定受影响的范围
   [-9985]会根据弹幕接近与否改变数值,弹幕接近时会变成1.
 5.使弹幕对自机的接近或者离开产生反应（hzc6面5卡） 
   接近则跳转到变换编号5，离开则跳转到14.接触范围[-9980.0f]和[9981.0f]设置，此时一般a=1，a的具体功能尚不明
```

```
 当使用激光生成mode(mode=134217728),mode=16384时
 如果激光为发射型,参数为:发弹音效,未知,激光跳转至的变换序号,未知,移动长度(即运动了多少长度后消失,0.0f则无限长),宽度,相对弹幕位置(即相对于原弹幕再走出的一段距离),未知
 如果激光为预警线型,参数为,预警线时间,变激光时间,激光持续时间,消失时间,宽度,相对弹幕位置,未知,未知
```


## Flag表
  
神灵庙
  


<table>

<tbody><tr>
<th>序号</th>
<th>值</th>
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
<td>使单位无法与自机互相影响(无法被射中,无法体术)且不会被525及518消除
</td></tr>
<tr>
<td>6</td>
<td>64</td>
<td><span style="color:red;">boss最开始都有，迷</span>
</td></tr>
<tr>
<td>7</td>
<td>128</td>
<td>使单位不会被525()及518消除
</td></tr>
<tr>
<td>8</td>
<td>256</td>
<td>保证此单位会被525以及518消除，无论拥有任何Flag
</td></tr>
<tr>
<td>9</td>
<td>512</td>
<td>设置是否可以擦弹，擦弹类似激光
</td></tr>
<tr>
<td>10</td>
<td>1024</td>
<td>使单位不会被525及518消除,遇到对话时会死亡.曾用于XLC飞碟以及dld怨灵
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
<td>18</td>
<td>0x00040000</td>
<td>限制单位移动范围,由504赋予，505消除
</td></tr>
<tr>
<td>19</td>
<td>0x00080000</td>
<td><span style="color:grey;">引擎内部使用,标记单位使用被某个函数测验过</span>
</td></tr>
<tr>
<td>20</td>
<td>0x00100000</td>
<td>使单位移动方向左右翻转,由424赋予和消除
</td></tr>
<tr>
<td>21</td>
<td>0x00200000</td>
<td>单位左右移动是贴图会不会变化,由306赋予，318消除}}
</td></tr>
<tr>
<td>22</td>
<td>0x00400000</td>
<td><span style="color:grey;">引擎内部使用,非boss单位或隐藏单位此flag会被自动剔除</span>
</td></tr>
<tr>
<td>23</td>
<td>0x00800000</td>
<td>特殊单位，不会被525及518消除
</td></tr>
<tr>
<td>24</td>
<td>0x01000000</td>
<td>Boss模式单位，此flag要通过512赋予和消除
</td></tr>
<tr>
<td>25</td>
<td>0x02000000</td>
<td>判定是否全避（存在时就是全避）
</td></tr>
<tr>
<td>26</td>
<td>0x04000000</td>
<td>要被消除的单位，由525以及518赋予
</td></tr>
<tr>
<td>27</td>
<td>0x08000000</td>
<td><span style="color:red;">功能未知，影响300等函数</span>
</td></tr>
<tr>
<td>28</td>
<td>0x10000000</td>
<td><span style="color:red;">功能未知，由544赋予和消除</span>
</td></tr>
<tr>
<td>29</td>
<td>0x20000000</td>
<td>对BOMB免疫，由546赋予和消除
</td></tr>
<tr>
<td>30</td>
<td>0x40000000</td>
<td><span style="color:red;">功能未知，由546消除</span>
</td></tr>
<tr>
<td>31</td>
<td>0x80000000</td>
<td><span style="color:grey;">引擎内部使用</span>
</td></tr>
<tr>
<td></td>
<td></td>
<td>DZZ开始扩充了Flag,额外新增了4字节
</td></tr>
<tr>
<td>32</td>
<td>0x00000001</td>
<td><span style="color:red;">功能未知，由549赋予和消除</span>
</td></tr></tbody></table>


  
辉针城
  


<table>

<tbody><tr>
<th>DEC</th>
<th>HEX</th>
<th>功能
</th></tr>
<tr>
<td>1</td>
<td>0x0001</td>
<td>无被弹判定
</td></tr>
<tr>
<td>2</td>
<td>0x0002</td>
<td>无体术判定
</td></tr>
<tr>
<td>4</td>
<td>0x0004</td>
<td>当单位离开左右版面时不会立即消失
</td></tr>
<tr>
<td>8</td>
<td>0x0008</td>
<td>当单位离开上下版面时不会立即消失
</td></tr>
<tr>
<td>16</td>
<td>0x0010</td>
<td>隐藏boss血条并设为无敌
</td></tr>
<tr>
<td>32</td>
<td>0x0020</td>
<td>使单位无法与自机互相影响(无法被射中,无法体术)且不会被525及518消除
</td></tr>
<tr>
<td>64</td>
<td>0x0040</td>
<td><span style="color:red;">boss最开始都有，迷</span>
</td></tr>
<tr>
<td>128</td>
<td>0x0080</td>
<td>使单位不会被525()及518消除，
</td></tr>
<tr>
<td>256</td>
<td>0x0100</td>
<td>保证此单位会被525以及518消除，无论拥有任何Flag
</td></tr>
<tr>
<td>512</td>
<td>0x0200</td>
<td>设置是否可以擦弹，擦弹类似激光
</td></tr>
<tr>
<td>1024</td>
<td>0x0400</td>
<td>使单位不会被525及518消除,遇到对话时会死亡.曾用于XLC飞碟以及dld怨灵
</td></tr>
<tr>
<td>2048</td>
<td>0x0800</td>
<td>设置是否会被消弹效果秒杀
</td></tr>
<tr>
<td>4096</td>
<td>0x1000</td>
<td>gzz中，设置体术判定和被弹判定为方形
</td></tr>
<tr>
<td>8192</td>
<td>0x2000</td>
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
<td>限制单位移动范围,由504赋予，505消除
</td></tr>
<tr>
<td>18</td>
<td>0x00040000</td>
<td><span style="color:grey;">引擎内部使用,标记单位使用被某个函数测验过</span>
</td></tr>
<tr>
<td>19</td>
<td>0x00080000</td>
<td>使单位移动方向左右翻转,由424赋予和消除
</td></tr>
<tr>
<td>20</td>
<td>0x00100000</td>
<td>单位左右移动是贴图会不会变化,由306赋予，318消除}}
</td></tr>
<tr>
<td>21</td>
<td>0x00200000</td>
<td><span style="color:grey;">引擎内部使用,非boss单位或隐藏单位此flag会被自动剔除</span>
</td></tr>
<tr>
<td>22</td>
<td>0x00400000</td>
<td>特殊单位，不会被525及518消除
</td></tr>
<tr>
<td>23</td>
<td>0x00800000</td>
<td>Boss模式单位，此flag要通过512赋予和消除
</td></tr>
<tr>
<td>24</td>
<td>0x01000000</td>
<td>判定是否全避（存在时就是全避）
</td></tr>
<tr>
<td>25</td>
<td>0x02000000</td>
<td>要被消除的单位，由525以及518赋予
</td></tr>
<tr>
<td>26</td>
<td>0x04000000</td>
<td><span style="color:red;">功能未知，影响300等函数</span>
</td></tr>
<tr>
<td>27</td>
<td>0x08000000</td>
<td>使该使魔不会诱导灵梦的bomb和诱导弹幕,由544赋予和消除(gzz)
</td></tr>
<tr>
<td>28</td>
<td>0x10000000</td>
<td>对BOMB免疫，由546赋予和消除
</td></tr>
<tr>
<td>29</td>
<td>0x20000000</td>
<td><span style="color:red;">功能未知，由546消除</span>
</td></tr>
<tr>
<td>30</td>
<td>0x40000000</td>
<td><span style="color:grey;">引擎内部使用</span>
</td></tr>
<tr>
<td>31</td>
<td>0x80000000</td>
<td>当值为1时,击中使魔则使魔颜色闪烁后变紫且不恢复,为0则闪烁几下后恢复,由549赋予和消除(gzz)
</td></tr></tbody></table>






---

此文档由 [THBWiki-Markdown-Builder](https://github.com/Delsin-Yu/THBWiki-Markdown-Builder) 构建。

文档中的所有内容除特殊注明外，均在 [**知识共享(Creative Commons) 署名-非商业性使用-相同方式共享 3.0 协议**](https://creativecommons.org/licenses/by-sa/3.0/deed.zh-hans) 下提供，附加条款亦可能应用。

引用类型与其他类型作品版权归原作者所有，如有作者授权则遵照授权协议使用。

详细请查阅 [THBWiki：免责声明](https://thbwiki.cc/THBWiki:%E5%85%8D%E8%B4%A3%E5%A3%B0%E6%98%8E)。

