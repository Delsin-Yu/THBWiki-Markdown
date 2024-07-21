# 脚本对照表/MUAECL

<!-- source html: G:\repos\THBWiki-Markdown-Builder\THBWikiMarkdown\Temp\main\8\88\ns0%3A%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8%2FMUAECL.html -->

脚本对照表 | 资料

本页是整理东方Project  
 **相关资料** 的词条
## 目录

- [1 概述](#概述)
- [2 Instruction表](#Instruction表)
- [3 系统和运算](#系统和运算)
- [4 设置贴图，播放特效动画，创建单位](#设置贴图，播放特效动画，创建单位)
- [5 单位移动](#单位移动)
- [6 单位固有属性](#单位固有属性)
- [7 弹幕相关](#弹幕相关)
- [8 激光相关](#激光相关)
- [9 其他](#其他)
- [10 集成语句](#集成语句)
- [11 特殊变量表](#特殊变量表)
- [12 609-612指令详解](#609-612指令详解)
- [13 Flag表](#Flag表)




### 概述
  
请至少先了解ecl为何物。点这里 (未找到链接)
  
  
为应对ecl汇编似的语言结构，表达式需要堆栈运算，记不住的数字指令等一系列缺点，MUA组少量参照了zun在某次访谈 (未找到链接)中给出的zun所使用的脚本， ~~编写了一个相对较好使用的ecl语言~~ 准备编写一套新的MUAECL2.0。
  
  
目前暂时以辉针城和绀珠传为基础。以后会用不同颜色加入对于其余作品的支持。
  
  
想下载MUAECL的脚本翻译器请加入MUA组（如想加入在此版块回复即可）
  
  
[MUAECL基本句法结构](./脚本对照表-MUAECL-MUAECL基本规范.md)
  

### Instruction表
```
  Instruction有 ins_xx（arg1，arg2，arg3.。。。） 表示，其中xx代表Instruction的编号，不同编号有不同的功能，
  每个Instruction需要的参数也不同/
```

  
下表展示了各种Instruction的功能
  

```
  Instruction大致可以分为 5大类
  即运算和系统，贴图和创建单位， 移动，单位属性，弹幕相关
```

  
以下每个ins，格式为名字 编号 作用详解
  

### 系统和运算
  
begin() 0 空指令，main开始调用一次
  
  
end() 1 大return，会清除当前单位
  
  
return() 10 小return，返回到调用这个过程的地方，不清除当前单位
  
  
ins_11(CString Subroutine,member 1,member 2.....)
  

```
 调用过程，若有需要传递参数，必须要在整数前加上_SS，浮点数前加上_ff，在子线程结束后返回
 已废 请直接调用。
```

  
ins_12(label,int b),已废
  
  
ins_13(label,int b),已废
  
  
ins_14(label,int b),已废
  

```
 12-14三者皆为goto 到对应label处，b为时间值。
 12为无条件goto
 13 if条件用goto
 判断当前栈顶是否为0 如果是0，则执行，不是0则不执行.
 14 循环用goto 判断当前栈顶是否为1,如果是1，就执行
 已废请直接使用Jmp,Jz,Jnz
 
```

  
ins_15(CString Subroutine,member 1,member 2.....) 
  

```
 在当前单位创建一个ID为-1的子线程，并行运行
 已废请直接调用
```

  
thread(CString Subroutine,int id) 16
  

```
 在当前单位创建一个子线程，并行运行
```

  
term(int id) 17
  

```
 关闭16的子线程
```

  
simu_term(int) 802 参数为0，立即击破场上boss当前阶段（用于多boss同台时，击破一个boss时另一个boss也同时击破，例hzcex道中2，3符）
  
  
ins_21()&#160;???
  
  
ins_22(anything) zun debug用，release版本是空指令
  
  
wait(int time) 23 等待xx帧。可以使用冒号，使用冒号之后会变成548。
  
  
ins_40(int size)
  

```
 分配局部变量用，等价于Var
```

  
ins_41 销毁40分配的局部变量
  
  
pushI(int) 42
  

```
 整数写入堆栈顶；
```

  
popI(int) 43
  

```
 将运算结果储存到变量中。相当于等号，
 即 
 pushI(5);
 popI(C);
 等价于
 C=5;
    
```

  
pushF(float) 44 pushI的浮点数版本
  
  
popF(float) 45 popI的浮点数版本
  
  
运算符号表
ins_50 开始至ins_69为各种基础运算，相同功能的一对中，第一个为整数版本，第二个为浮点数版本
不建议使用，请直接用运算
  


<table>

<tbody><tr>
<th>名字</th>
<th>编号</th>
<th>作用</th>
<th>名字</th>
<th>编号</th>
<th>作用</th>
<th>
</th></tr>
<tr>
<td>operator_add_int</td>
<td>50</td>
<td>+</td>
<td>operator_add_float</td>
<td>51</td>
<td>+
</td></tr>
<tr>
<td>operator_sub_int</td>
<td>52</td>
<td>-</td>
<td>operator_sub_float</td>
<td>53</td>
<td>-
</td></tr>
<tr>
<td>operator_mul_int</td>
<td>54</td>
<td>*</td>
<td>operator_mul_float</td>
<td>55</td>
<td>*
</td></tr>
<tr>
<td>operator_div_int</td>
<td>56</td>
<td>/</td>
<td>operator_div_float</td>
<td>57</td>
<td>/
</td></tr>
<tr>
<td>operator_mod</td>
<td>58</td>
<td>mod</td>
<td>-</td>
<td>-</td>
<td>-
</td></tr>
<tr>
<td>operator_equal_int</td>
<td>59</td>
<td>==</td>
<td>operator_equal_float</td>
<td>60</td>
<td>==
</td></tr>
<tr>
<td>operator_notequal_int</td>
<td>61</td>
<td>!=</td>
<td>operator_notequal_float</td>
<td>62</td>
<td>!=
</td></tr>
<tr>
<td>operator_less_int</td>
<td>63</td>
<td>&lt;</td>
<td>operator_less_float</td>
<td>64</td>
<td>&lt;
</td></tr>
<tr>
<td>operator_lessequal_int</td>
<td>65</td>
<td>&lt;=</td>
<td>operator_lessequal_float</td>
<td>66</td>
<td>&lt;=
</td></tr>
<tr>
<td>operator_large_int</td>
<td>67</td>
<td>&gt;</td>
<td>operator_large_float</td>
<td>68</td>
<td>&gt;
</td></tr>
<tr>
<td>operator_largeequal_int</td>
<td>69</td>
<td>&gt;=</td>
<td>operator_largeequal_float</td>
<td>70</td>
<td>&gt;=
</td></tr>
<tr>
<td>operator_not_int</td>
<td>71</td>
<td>!</td>
<td>operator_not_float</td>
<td>72</td>
<td>!
</td></tr>
<tr>
<td>operator_or_logic</td>
<td>73</td>
<td><div class="poem">
<p>||
</p>
</div></td>
<td>operator_and_logic</td>
<td>74</td>
<td>&amp;&amp;
</td></tr>
<tr>
<td>operator_xor_bit</td>
<td>75</td>
<td>^(xor)</td>
<td>operator_or_bit</td>
<td>76</td>
<td><div class="poem">
<p>|
</p>
</div>
</td></tr>
<tr>
<td>operator_and_bit</td>
<td>77</td>
<td>&amp;</td>
<td>-</td>
<td>-</td>
<td>-
</td></tr>
<tr>
<td>operator_sin</td>
<td>79</td>
<td>sin</td>
<td>operator_cos</td>
<td>80</td>
<td>cos
</td></tr>
<tr>
<td>operator_minus_int</td>
<td>83</td>
<td>(-)</td>
<td>operator_minus_float</td>
<td>84</td>
<td>(-)
</td></tr>
<tr>
<td>operator_sqrt</td>
<td>88</td>
<td>sqrt</td>
<td>-</td>
<td>-</td>
<td>-
</td></tr></tbody></table>


  
dec(int i) 78 将i自减并塞入堆栈。配合Jnz用于控制循环次数。
  
  
pol_to_right(float A,float B,float x,float y) 81
  

```
  A=ycosx ,B=ysinx
```

  
normalize(float A) 82 +-π的整数倍以至于A落入（-π，π）这个区间
  
  
sqrsum(float A,float x,float y) 85
  

```
     A=x平方+y平方
```

  
right_to_dist(float A,float x,float y) 86
  

```
     A平方=根号（X平方+y平方）
```

  
  

right_to_ang(float %A,float x1,float y1,float x2,float y2,) 87
  

```
     计算点(x1,y1)至点（x2,y2）的方向并存入浮点变量A中
```

  
ang_aim(N,float x,float y) 623 计算点x,y到自机到角度并存入N中
  
  
ins_89(float A, float x float y)
  

```
   A=y-x 
```

  
ins_90(float A,float B,float x,float y，float z)
  

```
  A=?? B=??
```

  
ins_91(int A,float B,int c int d,float x,float y)
  

```
  执行代码之后的c帧内，将%B由x变化到y，变化的曲线的参数为A和D
```

  
ins_92(int A,float B,int c int d,float x,float y,float m,float n)
  

```
  ?????
```

  
ins_93(float A,float B,float x,float y)
  

```
  根据x和y,分别赋予A,B一个随机数，和正态分布相关
  例若a=b,则随机范围是-a&lt;A&lt;a, 呈两边概率大于中间
  若a=0则则随机范围是-b&lt;A&lt;b，呈两边概率小于中间
  若b=0则则随机范围是-2a&lt;A&lt;2a，呈两边概率小于中间
```

### 设置贴图，播放特效动画，创建单位
  
这些obj型的指令，在创建单位的时候会自动执行与该单位同名的sub。
  
  
obj("xxx", float x, float y, int life, int bonus, int item) 300
  

```
 以相对召唤者为基准点在位置xy，创建一个单位xxx，设置血量，分数以及基本掉落。
```

  
objAbs("xxx", float x, float y, int life, int bonus, int item) 301
  

```
 在绝对位置xy，创建一个单位xxx，设置血量，分数以及基本掉落。用于boss
```

  
objRvs("xxx", float x, float y, int life, int bonus, int item) 304
  

```
  和obj的基本功能一样，但是移动方式为左右镜像。
```

  
objRvsAbs("xxx", float x, float y, int life, int bonus, int item) 305
  

```
 和objAbs的基本功能一样，但是移动方式为左右镜像。
```

  
objRei("xxx", float x, float y, int life, int bonus, int item) 309
  

```
 用于增员(boss存在时不执行)，其余和obj一样
```

  
objReiAbs("xxx", float x, float y, int life, int bonus, int item) 310
  

```
 用于增员，其余和objAbs一样
```

  
objReiRvs("xxx", float x, float y, int life, int bonus, int item) 311
  

```
 用于增员，其余和objRvs一样
```

  
objReiRvsAbs("xxx", float x, float y, int life, int bonus, int item) 312
  

```
 用于增员，其余和objRvsAbs一样
```

  
anim_file(int) 302
  

```
  选择ANM文件。一般来说0即是Bullet.anm，1即是Enemy.anm,2开始就是当面的boss相关anm
```

  
layer_set(int layer,int a) 303
  

```
  在相应layer上,设置单位贴图,a对应由上一个302选择的ANM文件中的SCRIPT号
 若使用529则单位不会因为左右移动而改变贴图
```

  
layer_set_mov(int layer,int a) 306
  

```
 在相应layer上,设置单位贴图,a对应由上一个302选择的ANM文件中的SCRIPT号
 若使用306且layer 0，则单位会因为左右移动而改变贴图
 a为静止贴图，a+1，a+2为向左，右走，a+3，a+4为左面回来，右面回来
 若layer不为0，则和303无区别.
```

  
anim_at_file(int a,int b) 307
  

```
 在单位当前位置播放ANM文件a的第b个动画效果，b对应由上一个302选择的ANM文件的 script号
```

  
anim_at0_file(int a,int b) 308
  

```
 在左上角播放ANM文件a的第b个动画效果，b对应由上一个302选择的ANM文件的 script号 
```

  
  

anim_at(int a) 313
  

```
 在单位当前位置播放之前选择的ANM文件的第a个动画效果，a对应由上一个302选择的ANM文件的 script号  
```

  
ins_314(int a, b) 
  
  
ins_315(int a, b)
  
  
anim_at2(int a, b)
  
  
ins_317(int a, b)
  
  
restore_anime_flag() 318
  

```
 重置动画相关,移除单位作用移动时贴图变化的flag
```

  
layer_rot(int layer,float b) 319
  

```
  旋转在相应layer的贴图至b方向。
```

  
layer_offset(int layer,float x,float y) 320
  

```
  用于改变layer位置贴图的位置 x和y
```

  
maple("MapleEnemy", 0, 0, 100, 1000, 0) 321 插入mapleenemy专用
  
  
  

  
  
ins_322(int a,int b)
  
  
  

ins_323(int a,int b)
  
  
ins_324()
  
  
  

layer_RGB(int layer,int R,int G,int B) 325
  

```
  设置贴图颜色,若RGB为255 255 255（白），则维持原颜色
```

  
ins_326(int layer,int a,b,c,d,e,f)
  
  
ins_327(int layer,int a)
  
  
layer_RGB_trans(int layer,int R,int G,int B) 328
  

```
  设置颜色透明度,若RGB为255 255 255,则100%原图显示
```

  
  

layer_zoom(int layer,float lengthrate,float widthrate) 329
  

```
  设置单位位于layer的贴图的大小比例,1.0f为正常大小，替换anmins里的402等anmins设置的倍数 
```

  
layer_zoom_chg(int layer,int time,int mode,float lengthrate,float widthrate) 330
  

```
  time帧内改变单位位于layer的贴图的大小比例为lengthrate,float widthrate.
```

  
layer_zoom_add(int layer,float lengthrate,float widthrate) 335
  

```
  设置位于layer的贴图的大小比例,1.0f为正常大小，与anmins里的402等anmins设置的倍数叠加
```

  
ins_331(int layer,int a)
  
  
ins_332(int layer,int a,b,c)
  
  
ins_333(int layer,int a,b.float c,d)
  
  
anim_obj(int a) 334 播放单位的动画效果，神灵庙娘娘的邪魂球附近的雷电效果使用
  
  
ins_336 绀珠传中出现
  
  
ins_337 绀珠传中出现
  

### 单位移动
  
每一个单位都有三套坐标. 
即最终实际坐标,绝对坐标以及相对坐标,任何时候最终实际坐标=绝对坐标+相对坐标
  
  
单位被创建出来时,那个坐标即是绝对坐标,初始相对坐标为(0,0)
  
  
所有移动相关函数都是一对一对的
基本功能相同以外,第一个是改变绝对坐标,第二个改变相对坐标
  
  
  

mov(float x,float y) 400 
  

```
改变目标坐标为x,y.
```

  
mov_chg(int time,int mode,float x,float y) 401
  

```
  将目标移动到,x,y位置.持续time帧，mode为移动方式
```

  
mov2(float x,float y) 402  和mov成对
  
  
mov_chg2(int time,int mode,float x,float y) 403 和mov_chg成对
  
  
spd(float direction, float speed) 404
  

```
 设置移动方向以及速度
```

  
spd_chg(int time, int mode, float direction, float speed) 405
  

```
   改变移动方式为某个方向以某个速度移动移动。改变时间为time 改变方式为mode
   mode有四种
   0---线性  1----加速   4----减速  9----平滑 
```

  
spd2(float direction, float speed) 406 和spd成对
  
  
spd_chg2(int time, int mode, float direction, float speed) 407 和spd_chg成对
  
  
mov_cir(float θ,float speed,float radius,float,rspeed) 408
  

```
   使单位进行圆周运动,曲线的极坐标（原点为单位之前的位置）(radius,θ)
   θ的增速为speed，radius增速为 rspeed 
```

  
mov_cir_chg(int time,int mode, float speed, float radius, float rspeed) 409
  

```
    time帧之内改变单位圆周运动的参数,方式为mode.各参数参考mov_cir
```

  
mov_cir2(float θ,float speed,float radius,float,rspeed) 410 和mov_cir成对
  
  
mov_cir_chg2(int time,int mode, float speed, float radius, float rspeed) 411 和mov_cir_chg成对
  
  
mov_ran(int time,int mode,float speed) 412 
  

```
    目标向随机点移动一次，持续time帧，速度为speed,移动方式为mode。mode和405相同
  
```

  
mov_ran2(int time,int mode,float speed) 413 和mov_ran成对
  
  
mov_to_boss() 414 将单位移动至boss的位置,此函数若在无boss时使用会导致严重误访问而爆炸
  
  
mov_to_boss2() 415 和mov_to_boss成对
  
  
mov_z(float x,float y,float height) 416 瞬间移动到与当前位置偏移x,y的位置,并且改变单位深度，此深度只适用于风神录（296）四面的潜水怪
  
  
mov_z2(float x,float y,float height) 417 和mov_z成对
  
  
ins_418(float x,float y)仅在前作FSL（298）6面神妈的圈圈移动上使用
  
  
ins_419(float x,float y)和ins_418成对
  
  
mov_ellipse(float θ,float speed,float radius,float,rspeed,float dir,float rate) 420
  

```
    使单位进行椭圆运动,曲线的极坐标（原点为单位之前的位置）(radius,θ)
    θ的增速为speed，radius增速为 rspeed,dir为 椭圆偏离的方向，rate为长半轴与短半轴的比例
```

  
mov_ellipse_chg(int time,int mode, float speed, float radius, float rspeed,float dir,float rate) 421
  

```
    time帧之内改变单位圆周运动的参数,方式为mode.各参数参考mov_ellipse
```

  
mov_ellipse2(float θ,float speed,float radius,float,rspeed,float dir,float rate) 422 和mov_ellipse成对 
  
  
mov_ellipse_chg2(int time,int mode, float speed, float radius, float rspeed,float dir,float rate) 423 和mov_ellipse_chg成对
  
  
rvs(int a) 424
  

```
  当a =1的时候赋予单位某flag(参考flag表),a=0的是消除
  此flag会影响spd和spd_chg等ins,效果为左右翻转
  
```

  
mov_curve(int time,float x1,float y1,float x2,float y2,float x3,float y3) 425
  

```
  在time时间内将单位最终移动至点x2,y2.
  期间首先向点x1,y1移动和一点时间再向
  终点偏差x3,y3移动一段时间再移动至终点x2,y2.
```

  
mov_curve2(int time,float x1,float y1,float x2,float y2,float x3,float y3) 426 和mov_curve成对
  
  
  

mov_init() 427
  

```
  初始化和清零移动相关参数
```

  
spd_correct(int) 428 spd的无视左右翻转版
  
  
spd_chg_correct(int) 429 spd_chg的无视左右翻转版
  
  
spd_correct2(int) 430 spd2的无视左右翻转版
  
  
spd_chg_correct2(int) 431 spd_chg2无视左右翻转版
  
  
ins_432(int)未知
  
  
ins_433(int)未知
  
  
ins_434(int a,int b,int c ,float x,float y) 未知移动函数
  
  
ins_435(int a,int b,int c ,float x,float y) 和ins_434成对
  
  
mov_chg_correct(int time,int mode,float x,float y) 436 mov_chg的无视左右翻转版
  
  
mov_chg_correct2(int time,int mode,float x,float y) 437 mov_chg2的无视左右翻转版
  
  
  

ins_434_correct(int a,int b,int c ,float x,float y) 438 ins_434的无视左右翻转版
  
  
ins_435_correct(int a,int b,int c ,float x,float y) 439 ins_435的无视左右翻转版
  
  
ins_441(int time,int mode,float dir)
  

```
    time帧后移动方向角增加dir，方式为mode
```

  
ins_445(int time,int mode,float s)
  

```
    time帧内速度增加至s，方式为mode
```

  
ins_446 绀珠传中出现
  
  
ins_447 绀珠传中出现
  

### 单位固有属性
  
hitbox(float width,float height) 500  目标被弹判定
  
  
killbox(float width,float height) 501  目标体术判定
  
  
option(int flag) 502
  

```
 设置单位的一些特定参数,a为2个4字节的开关参数0000000000000000
 详细参考下方FLAG表
```

  
option_unset(int a) 503
  

```
 取消option设置的参数,和option刚好相反
```

  
clip(float x,float y,float m,float n) 504
  

```
 限制boss的移动范围，以x,y为基准+- n 和m的范围
```

  
clip_unset() 505 移除移动范围限制
  
  
drop_clear() 506 清除掉落
  
  
drop_set(int type,int amount) 507
  

```
 目标掉落道具及数量
 1.p点 2蓝点 3.大p 4.残碎片 5残机，6B碎片 7Bomb 8大F 9小最大得点，获得时无音效，每个增加2最大得点，
 10.中最大得点，获取时有音效，每个增加2最大得点.11.中最大得点，获取时有音效，每个增加20最大得点.
 12.B碎片(参与hzc收点系统的循环)
```

  
drop_area(float width,float height) 508 设置掉落区域
  
  
drop() 509 掉落所有道具
  
  
drop_basic(int type) 510 设置目标基本掉落，数量是1.
  
  
set_life(int life) 511  更改单位血量
  
  
bossmode(int a) 512
  

```
 a=0，设为boss战模式（血条，名字等），a=-1，结束boss。
```

  
time_reset() 513
  

```
 重置时间
```

  
interrupt(int a，血量，时间，“阶段变量名”) 514
  

```
 当血量和或时间达到此数值时 载入下一阶段（符卡或非符）
  *a的作用未知* 
```

  
invincible(int time) 515 无敌时间
  
  
playSE(int) 516 播放音效 
  
  
vibration(int a，int b，int c) 517 震屏特效。a为持续时间（帧），bc均与震屏强度有关，都是越大震动越强，区别不明。
  
  
talk(int) 518 读取对话，参数对应msg文件,同时执行525
  
  
after_talk() 519 对话后进行下一条
  
  
after_kill() 520 击破后进行下一条 
  
  
timeout(int a,"func") 521
  

```
 时间到0时进行func的内容，a作用未知
```

  
cardX(int a, int life, int score, "X符:XXXX") 522
  

```
 进入符卡模式，设置符卡宣言后右上角 符卡时间，scb，符卡名，a和符卡序号有关
 Ex面使用
```

  
card0(int a, int life, int score, "X符:XXXX") 528 
  

```
 进入符卡模式，设置符卡宣言后右上角 符卡时间，scb，符卡名，a和符卡序号有关
 未使用  
```

  
cardE(int a, int life, int score, "X符:XXXX") 537
  

```
进入符卡模式，设置符卡宣言后右上角 符卡时间，scb，符卡名，a和符卡序号有关
 非ex面关底使用
```

  
card1(int a, int life, int score, "X符:XXXX") 538
  

```
进入符卡模式，设置符卡宣言后右上角 符卡时间，scb，符卡名，a和符卡序号有关
 HZC中未使用.
```

  
cardM(int a, int life, int score, "X符:XXXX") 539 
  

```
进入符卡模式，设置符卡宣言后右上角 符卡时间，scb，符卡名，a和符卡序号有关
 非ex面道中使用
```

  
endSC() 523
  

```
 结束符卡模式
```

  
chapter(float) 524
  

```
 设置章节数,影响即将出现的符卡立绘,背景以及左上角boss的名字
 在设置gzz里的结算点，
```

  
clear_unit() 525
  

```
 清除所有单位，有某些flag的不会被清除.
```

  
protect_area(float) 526
  

```
设置弹幕生成保护范围（距离）自机在此范围内时不发弹
```

  
lifebar(int a, float life, int c) 527
  

```
 设置血条上的标记点，a是标记序号，life对应血量，
c是RGB值
```

  
RANK一直存在于游戏程序中，收点+rank miss减rank
  

```
 理论来讲应该是a:b,a:b:c,a:b:c:d:e代表rank然后a:b:c:d代表难度的，然而作者懒得做这个功能了因为没人用rank了
```

  
rank3F(N，float a,b,c) 529 根据RANK决定变量N
  
  
rank5F(N，float a,b,c,d,e) 530 根据RANK决定变量N
  
  
rank2F(N，float a,b) 531 根据RANK决定变量N
  
  
rank3I(M，int a,b,c) 532 根据RANK决定变量M
  
  
rank5I(M，int a,b,c,d,e) 533根据RANK决定变量M
  
  
rank2I(M，int a,b) 534 根据RANK决定变量M
  
  
ins_535(M,int a,b,c,d)根据难度将数据写入整数M中 已废请使用冒号
  
  
ins_536(N,float a,b,c,d)根据难度将数据写入浮点数N中 已废请使用冒号
  
  
star(int) 540设置剩余阶段数(左上角的星星数)
  
  
ins_541(int)仅在风神录(对应ins_361)使用过,为4,5,6面某些效果设置,效果不明.之后被zun遗弃
  
  
time_card() 542 设置符卡为时符
  
  
ins_543()某些时符使用
  
  
ins_544(int)
  

```
当a=1时赋予单位某flag(参考下方flag表),a=0时取消
雷鼓的使魔们使用
```

  
reset() 545
  

```
 重置boss一些参数，除了boss1非以外，每一张非和卡都出现和,boss逃跑和死亡也会出现
```

  
ins_546(int,int)
  

```
  当a =1的时候赋予单位某flag,a=0的是消除
  此flag会使boss对Bomb免疫,并且由b来决定放b时的播放的动画 同时会消除某单位flag
  具体参照下方flag表
```

  
droprate(float) 547  设置时间倍率，1.0是正常，击破后减速可以设成0.5，咲夜时停是设成0.0
  
  
ins_548(int a, b, c, d);wait(等待)的难度选择版 已废请使用wait+冒号
  
  
ins_549(int)
  

```
  当a =1的时候赋予单位某flag,a=0的是消除,参照下方flag表
  仅在地灵殿(对应ins_369)四面使用过,效果不明.之后被zun遗弃
```

  
ins_550(int)仅在地灵殿(对应ins_370)四面使用过,效果不明.之后被zun遗弃
  
  
ins_551(int)仅在地灵殿(对应ins_371)四面使用过,效果不明.之后被zun遗弃
  
  
ins_552(int)仅在星莲船(对应ins_452)一面使用过,效果不明.之后被zun遗弃
  
  
hit_SE(int) 553 设置被打击的音效
  
  
logoenemy() 554 显示logoenemy
  
  
dead_attack("DeadAttack1") 556 设置死尸弹
  
  
ins_557(int, int,int, float, float) 一些道中boss死亡时使用，效果未知
  
  
ins_558(int)
  

```
 a=1则赋予单位某flag,a=0消除,具体参照下方flag表
 和424功能完全一样,此flag控制左右移动翻转
```

  
ins_559(int)未知
  
  
ins_560(float a,flaot b)未知
  
  
ins_561() 放出单位死亡特效（实际不死亡）庙道中击破大蝴蝶之后鬼火爆炸时发现
  
  
ins_562()未知
  
  
ins_563(???)
  
  
ins_564(???)
  
  
bomb_damage_rate(float a) 565
  

```
 设置b伤害的倍率，0.0的话就是炸不掉血，1.0就是全额伤害
```

  
ins_566(???)没有在任何位置发现,可能zun设计之后未使用
  
  
  

ins_567(int)正邪使用，效果未知
  
  
damage_rate(int) 568 设置boss的伤害倍率，0为谱模式，1为符卡模式（用于双boss同时在场时，设置副boss的倍率）
  
  
kill_rate(int) 569 绀珠传新增，用来设置击破率
  
  
ins_570 绀珠传中出现
  
  
ins_571 绀珠传中出现
  

### 弹幕相关
  
et_ini(int a) 600 创建一个弹幕，编号为a 请直接使用set_et
  
  
et_shoot(int a) 601 发射a号子弹
  
  
et_shape(弹幕编号,int a,int b) 602 设置弹幕贴图,a b 对应 bullet.Anm文件中description文件的内容。
  


<table>

<tbody><tr>
<th>子弹名</th>
<th>子弹编号</th>
<th>弹型</th>
<th>子弹名</th>
<th>子弹编号</th>
<th>弹型</th>
<th>子弹名</th>
<th>子弹编号</th>
<th>弹型
</th></tr>
<tr>
<td>ET_dot</td>
<td>0</td>
<td>点弹</td>
<td>ET_dot2</td>
<td>1</td>
<td>点弹</td>
<td>ET_mold</td>
<td>2</td>
<td>葡萄弹/霉菌弹
</td></tr>
<tr>
<td>ET_tiny</td>
<td>3</td>
<td>粒弹</td>
<td>ET_small</td>
<td>4</td>
<td>小玉</td>
<td>ET_small2</td>
<td>5</td>
<td>小玉
</td></tr>
<tr>
<td>ET_ring</td>
<td>6</td>
<td>环玉</td>
<td>ET_ring2</td>
<td>7</td>
<td>环玉</td>
<td>ET_grain</td>
<td>8</td>
<td>米弹
</td></tr>
<tr>
<td>ET_kunai</td>
<td>9</td>
<td>链弹/苦无</td>
<td>ET_needle</td>
<td>10</td>
<td>针弹</td>
<td>ET_square</td>
<td>11</td>
<td>札弹
</td></tr>
<tr>
<td>ET_triangle</td>
<td>12</td>
<td>鳞弹</td>
<td>ET_bullet</td>
<td>13</td>
<td>铳弹</td>
<td>ET_sb</td>
<td>14</td>
<td>消弹效果
</td></tr>
<tr>
<td>ET_long_mold</td>
<td>15</td>
<td>杆菌弹</td>
<td>ET_small_star</td>
<td>16</td>
<td>顺时针旋转小星弹</td>
<td>ET_money</td>
<td>17</td>
<td>钱币
</td></tr>
<tr>
<td>ET_middle</td>
<td>18</td>
<td>中玉</td>
<td>ET_high_middle</td>
<td>19</td>
<td>高光中玉</td>
<td>ET_ellipse</td>
<td>20</td>
<td>椭弹
</td></tr>
<tr>
<td>ET_knife</td>
<td>21</td>
<td>刀弹</td>
<td>ET_butterfly</td>
<td>22</td>
<td>蝶弹</td>
<td>ET_big_star</td>
<td>23</td>
<td>顺时针旋转大星弹
</td></tr>
<tr>
<td>ET_red_fire</td>
<td>24</td>
<td>红色炎弹</td>
<td>ET_purple_fire</td>
<td>25</td>
<td>紫色炎弹</td>
<td>ET_blue_fire</td>
<td>26</td>
<td>蓝紫炎弹
</td></tr>
<tr>
<td>ET_yellow_fire</td>
<td>27</td>
<td>黄色炎弹</td>
<td>ET_heart</td>
<td>28</td>
<td>心弹</td>
<td>ET_eye</td>
<td>29</td>
<td>伸缩中玉
</td></tr>
<tr>
<td>ET_arrow</td>
<td>30</td>
<td>矢弹</td>
<td>ET_big</td>
<td>31</td>
<td>大玉</td>
<td>ET_light</td>
<td>32</td>
<td>光玉
</td></tr>
<tr>
<td>ET_drop</td>
<td>33</td>
<td>滴弹</td>
<td>ET_spin_grain</td>
<td>34</td>
<td>旋转米弹</td>
<td>ET_spin_needle</td>
<td>35</td>
<td>旋转针弹
</td></tr>
<tr>
<td>ET_reverse_small_star</td>
<td>36</td>
<td>逆时针旋转小星弹</td>
<td>ET_laser</td>
<td>37</td>
<td>激光段</td>
<td>ET_red_music</td>
<td>38</td>
<td>红色音符弹
</td></tr>
<tr>
<td>ET_blue_music</td>
<td>39</td>
<td>蓝色音符弹</td>
<td>ET_yellow_music</td>
<td>40</td>
<td>黄色音符弹</td>
<td>ET_purple_music</td>
<td>41</td>
<td>紫色音符弹
</td></tr>
<tr>
<td>ET_silence</td>
<td>42</td>
<td>休止符弹</td>
<td>???</td>
<td>43</td>
<td>空白（仍有极小判定）
</td></tr></tbody></table>


  
绀珠传里24是逆时针旋转大星弹，25之后顺延，相对顺序不变
  
  
由于对于不同大小的弹幕，颜色编号不一样，请对照bullet.anm里的图片使用。
大小16x16或以下的：
  


<table>

<tbody><tr>
<th>颜色名</th>
<th>颜色编号</th>
<th>颜色名</th>
<th>颜色编号</th>
<th>颜色名</th>
<th>颜色编号</th>
<th>颜色名</th>
<th>颜色编号
</th></tr>
<tr>
<td>BLACK16</td>
<td>0</td>
<td>DARK_RED16</td>
<td>1</td>
<td>RED16</td>
<td>2</td>
<td>DARK_PURPLE16</td>
<td>3
</td></tr>
<tr>
<td>PURPLE16</td>
<td>4</td>
<td>DARK_BLUE16</td>
<td>5</td>
<td>BLUE16</td>
<td>6</td>
<td>DARK_CYAN16</td>
<td>7
</td></tr>
<tr>
<td>CYAN16</td>
<td>8</td>
<td>DARK_GREEN16</td>
<td>9</td>
<td>BLUE_GREEN16</td>
<td>10</td>
<td>GREEN16</td>
<td>11
</td></tr>
<tr>
<td>GREEN_YELLOW16</td>
<td>12</td>
<td>YELLOW16</td>
<td>13</td>
<td>ORANGE16</td>
<td>14</td>
<td>WHITE16</td>
<td>15
</td></tr></tbody></table>


  
大小32x32的：
  


<table>

<tbody><tr>
<th>颜色名</th>
<th>颜色编号</th>
<th>颜色名</th>
<th>颜色编号</th>
<th>颜色名</th>
<th>颜色编号</th>
<th>颜色名</th>
<th>颜色编号
</th></tr>
<tr>
<td>BLACK32</td>
<td>0</td>
<td>RED32</td>
<td>1</td>
<td>PURPLE32</td>
<td>2</td>
<td>BLUE32</td>
<td>3
</td></tr>
<tr>
<td>CYAN32</td>
<td>4</td>
<td>GREEN32</td>
<td>5</td>
<td>YELLOW32</td>
<td>6</td>
<td>WHITE32</td>
<td>7
</td></tr></tbody></table>


  
大小64x64的（大玉）：
  


<table>

<tbody><tr>
<th>颜色名</th>
<th>颜色编号</th>
<th>颜色名</th>
<th>颜色编号</th>
<th>颜色名</th>
<th>颜色编号</th>
<th>颜色名</th>
<th>颜色编号
</th></tr>
<tr>
<td>RED64</td>
<td>0</td>
<td>BLUE64</td>
<td>1</td>
<td>GREEN64</td>
<td>2</td>
<td>YELLOW64</td>
<td>3
</td></tr></tbody></table>


  
钱币弹：
  


<table>

<tbody><tr>
<th>颜色名</th>
<th>颜色编号</th>
<th>颜色名</th>
<th>颜色编号</th>
<th>颜色名</th>
<th>颜色编号
</th></tr>
<tr>
<td>GOLD</td>
<td>0</td>
<td>SILVER</td>
<td>1</td>
<td>BRONZE</td>
<td>2
</td></tr></tbody></table>


  
et_offset(弹幕编号，float x，float y) 603 以基准发弹点用直角坐标的方式偏移发弹点。基准发弹点默认是单位目前坐标
  
  
et_dir(弹幕编号, float dir, float r) 604
  

```
  设置弹幕方向为 dir，每way之间的角度差为r
```

  
et_speed(弹幕编号, float speed, float s) 605
  

```
   设置弹幕速度为 speed，其中最慢一层的速度为s
```

  
et_num(弹幕编号，int way，int ceng) 606
  

```
    设置弹幕的way数和层数，
```

  
et_style(弹幕编号，int style) 607
  

```
  根据style设置弹幕展开的形状，若此弹幕是1way 1层的，则无影响 
```


<table>

<tbody><tr>
<th>常量名</th>
<th>序号</th>
<th>功能
</th></tr>
<tr>
<td>ET_AIM_NORM</td>
<td>0</td>
<td>自机狙普通
</td></tr>
<tr>
<td>ET_NORM</td>
<td>1</td>
<td>普通
</td></tr>
<tr>
<td>ET_AIM_CIR</td>
<td>2</td>
<td>自机狙右偏开花
</td></tr>
<tr>
<td>ET_CIR</td>
<td>3</td>
<td>右偏开花
</td></tr>
<tr>
<td>ET_AIM_CIR2</td>
<td>4</td>
<td>自机狙左偏开花
</td></tr>
<tr>
<td>ET_CIR2</td>
<td>5</td>
<td>左偏开花：开花即为速度最慢一层方向普通，每向外一层，方向偏转每way角度差（右偏为逆时针左偏为顺时针），此时所有way数自动排成一个圆，不再受每way角度差限制
</td></tr>
<tr>
<td>ET_RAN2</td>
<td>6</td>
<td>一坨：方向普通。每层在 弹幕方向+-每way角度差 的角度内随机分布，层之间不随机。
</td></tr>
<tr>
<td>ET_RAN_CIR</td>
<td>7</td>
<td>散开一坨：每颗弹幕均在 speed~speed+2*s 360度 范围内随机分布。
</td></tr>
<tr>
<td>ET_RAN</td>
<td>8</td>
<td>一坨：每颗弹幕均在 speed~speed+2*s dir+-r 范围内随机分布。
</td></tr>
<tr>
<td>ET_AIM_STAR</td>
<td>9</td>
<td>自机狙金字塔开花
</td></tr>
<tr>
<td>ET_STAR</td>
<td>10</td>
<td>金字塔开花：金字塔开花即为首先层数总数除以2，速度最快1~2颗弹幕方向普通，之后速度每慢1层，有两颗弹幕，方向向两侧偏转每way角度差
</td></tr>
<tr>
<td>ET_PEANUT</td>
<td>11</td>
<td>上下？：方向普通。所有子弹排成一个花生状（360度分布），花生顶尖的一way弹幕速度为设定值（花生的每way弹速是固定的，具体弹速-角度关系待测）
</td></tr>
<tr>
<td>ET_PEANUT2</td>
<td>12</td>
<td>开花：与11类似。11与12的每way角度刚好成间隔排布。弹速-角度关系与11相同。
</td></tr></tbody></table>


```
 9与10金字塔开花型子弹若想脑补，请参考en难度风神录一面道中二非
```

  
et_SE(弹幕编号, int a,int b) 608
  

```
  设置弹幕音效，a是发弹音效，b是变向音效。不设置的话就是默认。-1代表没有音效
```

  
609-612为设置弹幕各种变速等复杂的属性，具体请翻至最下面[这里](#609-612.E6.8C.87.E4.BB.A4.E8.AF.A6.E8.A7.A3)查阅。教程点击[这里](./脚本对照表-MUAECL-MUAECL基本规范.md)。
  
  
et_clear_all() 613 全屏消弹,不增加得点
  
  
et_copy(int a,int b) 614 复制弹幕b到a中,弹幕属性仅复制这个函数使用之前设定的，
  
  
et_clear(float r) 615 消掉半径为r范围内的弹幕,消掉的弹幕变为最大得点
  
  
et_clear0(float r) 616 消掉半径为r范围内的弹幕,不增加得点
  
  
et_speed_rank3(弹幕编号，float a,b,c,d,e,f) 617 根据rank的值来决定弹速
  
  
et_speed_rank5(弹幕编号，float a,b,c,d,e,f,g,h,i,j) 618 根据rank的值来决定弹速
  
  
et_speed_rank2(弹幕编号，float a,b,c,d) 619 根据rank的值来决定弹速
  
  
et_amount_rank3(弹幕编号，int a,b,c,d,e,f) 620 根据rank的值来决定way数和层数
  
  
et_amount_rank5(弹幕编号，int a,b,c,d,e,f,g,h,i,j) 621 根据rank的值来决定way数和层数
  
  
et_amount_rank2(弹幕编号，int a,b,c,d) 622 根据rank的值来决定way数和层数
  
  
ins_624(弹幕编号，float a,b,c,d,e,f,g,h)
  

```
 et_speed的难度结合版，即如果难度为Easy 则相当于et_speed(弹幕编,a,e) 已废请使用et_speed+冒号
```

  
ins_625(弹幕编号，int a,b,c,d,e,f,g,h)
  

```
 et_num的难度结合版，即如果难度为Easy 则相当于et_num(弹幕编,a,e) 已废请使用et_num+冒号
```

  
et_offset_polar(弹幕编号，float o，float r) 626 以基准发弹点用极坐标的方式偏移发弹点，角度为o，半径为r。
  
  
et_nearby(弹幕编号，float dis) 627 设置发弹点。以boss为半径为dis的圆形边上发弹。
  
  
et_base(弹幕编号，float x，float y) 628 设置发弹基准点 
  
  
texture(flout r,int color) 629
  

```
 设置boss周围的纹理变化特性，影响半径为r，颜色为 color，对应RGB颜色，
```

  
ins_630(int)6和7boss使用，用途未知
  
  
ins_631(???)
  
  
ins_632(int)
  

```
 boss每身重置为0，有些特殊攻击模式时启用，于变换mode32768配合使用
 具体请阅读下方表格mode32768部分
```

  
ins_633(int)神灵庙布嘟嘟的船使用，用途未知
  
  
ins_634(???)
  
  
ins_635(???)
  
  
ins_636(???)
  
  
ins_637(int)
  

```
 使用各boss独有的特殊变化。如雷鼓震屏，正邪翻转
 只有特定boss才能使用特定变化.
```

  
ins_638(???)
  
  
ins_639(???)
  
  
et_obj(弹幕编号,int a,"func") 640 由弹幕召唤使魔的时候使用，需要a= mode 16777216的弹幕编号2
  
  
ins_641(弹幕编号)hzc6面时符大型刀弹使用，用途未知
  

### 激光相关
  
et_ls_length(弹幕编号,float a,float length,float b,float width) 700
  

```
 使弹幕变成激光，设置长度和宽度，a和b是开始位置的参数，一般激光设成0就行
 17条爆弹那种预警线+直接生产的设置成和长度一样
 若要发射曲线激光，则a,length,b 都是无关参数，设成-1.0f,曲线激光只可以设置宽度.
```

  
et_ls_time(弹幕编号,int a,int b,int c,int d, int e) 701
  

```
  设置预警线持续时间a和激光的持续时间c. b和d分别是从预警线变为实际激光和激光消失过程需要的时间，e一般为0
   用途未知
   若发射曲线激光则，则b,c,d,都是无关参数，a是激光发射持续时间（决定其长度） e仍然是迷之0
```

  
et_ls_shoot(弹幕编号) 702 普通激光的发弹函数
  
  
et_ls(弹幕编号,int a) 703 发射预警线激光专用，a为激光编号，区别于弹幕编号
  
  
ls_pos(激光编号,float x,float y) 704 改变激光的起点为x,y
  
  
ls_move(激光编号,float x,float y) 705 赋予激光起点一个速度
  
  
ins_706(???)
  
  
ls_width(激光编号,float width) 707 改变激光的宽度为width
  
  
ls_dir(激光编号,float a) 708 改变激光的角度为a
  
  
ls_rotate(激光编号,float a) 709 
  

```
赋予激光一个顺时针的角速度a
```

  
ls_clr(激光编号) 消除激光 710
  
  
et_bentls_shoot(弹幕编号) 711 曲线激光用发弹函数
  
  
obj_ls(float length,float width) 712 改变单位判定，使其变成类似于激光的东西，天邪鬼新增
  
  
ins_713 绀珠传中出现
  
  
ins_714 绀珠传中出现
  

### 其他
  
simu(int,"subroutin"); 800 推测是同时开启另一个人的"subroutin"，第一个int参数与编号有关，不明。eg.比如绀珠传ex的纯狐与赫卡互动。
  
  
if_alive(int A,int b) 555
  

```
 检查第b号单位是否存活，若存活测A=1,否则A=0.单位的编号就是单位登场的顺序.main为0号
```

  
test_pos(float %X,float %Y,int n); 801
  

```
 返回(X,Y)等于第n号小怪的坐标。eg.比如神灵庙6道中判断大蝴蝶如果出屏则幽灵就不因大蝴蝶出屏消失而死亡
```

  
simu_term(int); 802 参数为0，立即击破场上boss当前阶段（用于多boss同台时，击破一个boss时另一个boss也同时击破，例hzcex道中2，3符）
  
  
ins_900() 仅仅在一面道中的GirlTest中出现一次，zun测试用
  
  
ins_901() 仅在DebugSkipFunc 使用，zun用来跳过Debug
  
  
ins_902() 仅在五面道中使用，作用未知，即使删除对游戏毫无影响，推测zun为debug用。
  
  
ins_1001(int);迷
  
  
ins_1002(int);迷
  
  
ins_1003(int);迷
  
  
ins_1004();迷
  

### 集成语句
  
CardStart() 开卡时用。
  

```
   time_reset();
   ins_21();
   clear_unit();
   obj("Ecl_EtBreak", 0., 0., 9999, 0, 0);//这个是消弹圈，在default.ecl里
   endSC();
   ins_632(0);
   reset();
   playSE(27);
   spd(0., 0.);
   spd_chg(0, 0, 0., 0.);
   mov_chg(0, 0, 0., 0.);
   MNum = 0;
   BNum = 0;
   ifSCB = 1;
```

  
CardEnd() 开非符时用。
  

```
   time_reset();
   ins_21();
   clear_unit();
   if(ifNotEscape==0){
       et_clear(640.0f);
   }
   else{
       et_clear0(640.0f);
   }
   endSC();
   ins_632(0);
   reset();
   playSE(27);
   spd(0., 0.);
   spd_chg(0, 0, 0., 0.);
   mov_chg(0, 0, 0., 0.);
   MNum = 0;
   BNum = 0;
   ifSCB = 1;
```

  
set_et(int 弹幕编号, int style, int 弹幕类型, int 弹幕颜色, int way, int ceng, float 方向, float 角度差, float speed, float 速度差) 初始化弹幕。其中弹幕样式，弹幕类型和弹幕颜色可以使用常量。
  

```
   et_ini(弹幕编号);
   et_style(弹幕编号, style);
   et_shape(弹幕编号, 弹幕类型, 弹幕颜色);
   et_num(弹幕编号, way, ceng);
   et_dir(弹幕编号, 方向, 角度差);
   et_speed(弹幕编号, speed, 速度差);
```

### 特殊变量表
  
SCNum int 9907 未知全局变量 SLM(4BE7D4) HZC中代表符卡练习模式中的符卡序号
  
  
OBJNumNoFlag int 9908 同屏单位数单数不包含还有单位flag.1,16,32的单位
  
  
Var_9909 int 9909 单位未知参数 SLM(11E8) DZZ 11c4
  
  
Var_9910 int 9910 boss未知参数，同9969 SLM(128c)
  
  
DIRBoss float 9911 boss最终位移的方向，停下后变成0
  
  
Var_9912 int 9912 文花帖DS中有特别意义，SLM之后固定放弃使用为0
  
  
hasShotNum int 9913 文花帖DS中为已拍照张数，SLM之后固定放弃使用为0
  
  
NUM int 9914 当前单位的单位编号
  
  
GF7 float 9915 可供随意使用的全局变量
  
  
GF6 float 9916 可供随意使用的全局变量
  
  
GF5 float 9917 可供随意使用的全局变量
  
  
GF4 float 9918 可供随意使用的全局变量
  
  
GF3 float 9919 可供随意使用的全局变量
  
  
GF2 float 9920 可供随意使用的全局变量
  
  
GF1 float 9921 可供随意使用的全局变量
  
  
GF0 float 9922 可供随意使用的全局变量
  
  
GI3 int 9923 可供随意使用的全局变量
  
  
GI2 int 9924 可供随意使用的全局变量
  
  
GI1 int 9925 可供随意使用的全局变量
  
  
GI0 int 9926 可供随意使用的全局变量
  
  
Var_9927 int 9927 SLM:[4C2194] +74==0且 4DCC30&#160;!=0时 为1，否则0
  
  
Var_9928 int 9928 文花帖DS中有特别意义，SLM之后固定放弃使用为0
  
  
Var_9929 int 9929 文花帖DS中有特别意义，SLM之后固定放弃使用为0
  
  
shotPower int 9930 自机当前火力
  
  
objHasAppearedNum int 9931 已经出现单位数量-1,包含main
  
  
F7 float 9932 可供随意使用的每个单位自身的局部变量
  
  
F6 float 9933 可供随意使用的每个单位自身的局部变量
  
  
F5 float 9934 可供随意使用的每个单位自身的局部变量
  
  
F4 float 9935 可供随意使用的每个单位自身的局部变量
  
  
BF3 float 9936 BOSS的局部变量
  
  
BF2 float 9937 BOSS的局部变量
  
  
BF1 float 9938 BOSS的局部变量
  
  
BF0 float 9939 BOSS的局部变量
  
  
BI3 int 9940 BOSS的局部变量
  
  
BI2 int 9941 BOSS的局部变量
  
  
BI1 int 9942 BOSS的局部变量
  
  
BI0 int 9943 BOSS的局部变量
  
  
DISPlayer float 9944 单位至自机的距离
  
  
PlayerID int 9945 机体序号，0=灵梦a
  
  
OBJNum int 9946 同屏单位数,由于隐藏着main和mapleenemy,所以始终比可见的单位数量多出来2个
  
  
ifSCB int 9947 判断上1符卡是否收取，收则是1
  
  
BNum int 9948 已丢的b的数量
  
  
MNum int 9949 已miss数
  
  
ifL int 9950 当难度为L时，为1。否则为0
  
  
ifH int 9951 当难度为H时，为1。否则为0
  
  
ifN int 9952 当难度为N时，为1。否则为0
  
  
ifE int 9953 当难度为E时，为1。否则为0
  
  
LIFE int 9954 单位当前血量
  
  
单位坐标和速度拥有最终，目前，和相对 三种参考 移动相关ins
  
  
AIM_relat float 9955 单位相对坐标至自机位置的方向
  
  
AIM_absol float 9956 单位绝对至自机位置的方向
  
  
Var_9957 int 9957 = 1
  
  
DIR int 9958 单位最终位移的方向，停下后变成0
  
  
DIFF int 9959 难度,0123分别为ENHL
  
  
RANK int 9960 Rank
  
  
Var_9961 int 9961 未知  （地址1120）
  
  
YBoss float 9962 当前bossy坐标，
  
  
XBoss float 9963 当前bossx坐标，
  
  
YPlayer2 float 9964 自机y坐标，与YPlayer完全相同 
  
  
XPlayer2 float 9965 自机x坐标，与XPlayer完全相同 
  
  
R_relat float 9966 单位相对曲线运动时的运动半径
  
  
R_absol float 9967 单位绝对曲线运动时的运动半径
  
  
V_relat float 9968 单位相对速度大小  
  
  
V_absol float 9969 单位绝对速度大小
  
  
VDIR_relat float 9970 单位相对移动速度的方向
  
  
VDIR_absol float 9971 单位绝对移动速度的方向，
  
  
Y2_relat float 9972 单位相对坐标y 与Y_relat完全相同
  
  
X2_relat float 9973 单位相对坐标x 与X_relat完全相同
  
  
Y2_absol float 9974 单位绝对坐标的y值,与Y_absol完全相同
  
  
X2_absol float 9975 单位绝对坐标的x值,与X_absol完全相同
  
  
Y2 float 9976 单位最终坐标的y值,与Y完全相同
  
  
X2 float 9977 单位最终坐标的x值,与X完全相同
  
  
以下8个变量在创建子单位的时候，子单位将继承
并且某些特殊函数会收这写变量影响
  
  
F3 float 9978 每个单位自身的局部变量 
  
  
F2 float 9979 每个单位自身的局部变量 
  
  
F1 float 9980 每个单位自身的局部变量 
  
  
F0 float 9981 每个单位自身的局部变量 
  
  
I3 int 9982 每个单位自身的局部变量 
  
  
I2 int 9983 每个单位自身的局部变量 
  
  
I1 int 9984 每个单位自身的局部变量 
  
  
I0 int 9985 每个单位自身的局部变量
  
  
ifNotEscape int 9986 判定是否全避时使用，若不为0则是全避，实际可能有其他含义,经测试并非boss血量  
  
  
RanF2 float 9987.0f -1.0至1.0之间的随机浮点数
  
  
TIME int 9988 已经过的时间 
  
  
AIM float 9989 单位最终坐标至自机位置的方向
  
  
YPlayer float 9990 自机y坐标  
  
  
XPlayer float 9991 自机x坐标   
  
  
Y_relat float 9992 单位相对坐标y  
  
  
X_relat float 9993 单位相对坐标x  
  
  
Y_absol float 9994 单位绝对坐标的y值  
  
  
X_absol float 9995 单位绝对坐标的x值 
  
  
Y float 9996 单位最终坐标的y值, 
  
  
X float 9997 单位最终坐标的x值，
  
  
RanDEG float 9998 -π至π之间的随机浮点数
  
  
RanF float 9999 0至 1.0之间的随机浮点数
  
  
RanI int 10000 随机整数，范围非常大
  

### 609-612指令详解
  
mode表
  
  
注意此表是以hzc为准，如gzz中 mode8192的用法明显有改变
  
  
spddown() 1 弹幕生成时向前蹿一小段距离
  
  
eff(int a) 2 根据a设置弹雾
  
  
spdup(int a, float r, float s) 4 设置加速度为r，加速时间a，s为加速度的角度
  
  
rot(int a, int b, float r, float s) 8 设置切向加速度为r，s自转角速度，持续时间为a，b一般情况下不使用,当变换对象是曲线激光时，各个变换将会同时进行，此时b来设置b帧后执行.
  
  
jump(int a, int b, int c, int d, float r, float s) 16 a帧后停顿，之后方向+r，速度变为s，变化次数为b,变换的了类型为c,d用途未知的,具体变换类型在表格下方.
  
  
32(anything) 未使用,保留
  
  
reflect(int a, int b, float r)触壁反弹，a为反弹次数，b是一个6位的2进制数来设置可反弹墙壁，从右到左依次为上下左右，为1则为反弹+变速，为0则只变速，即如果b=001111则4面全可以反弹，b=000000则碰到四面就改变速度（变速后再碰到反弹墙则不变速），r为接触墙壁后的速度
  
  
reflect-wall(int a, int b, float r, float s, float m) 64 当b前第六位为1时，改变反弹墙位置，s,m分别代表左右，上下方的反弹壁与屏幕中心的距离。
  
  
not_clear(int a) 128 设置弹幕不可消弹时间为a帧，这段时间内无法消取本弹幕
  
  
not_out(int a, int b) 256  设置子弹可以在屏幕外持续的时间为a帧,.b作用未知
  
  
change(int a, int b) 512  改变弹幕形状为a，b
  
  
clear(int a) 1024 消除子弹，a为消弹效果，有0和1两种形式，
  
  
se(int a) 2048 播放音效a
  
  
through(int a, int b, float r) 4096 穿墙，参数用法和弹墙reflect相同.
  
  
shoot(int a, int b, int c, int d, float r, float s, float m, float n) 8192 在当前弹幕的位置新子弹,a是展开形式，即et_style的参数，跳跃至变换序号b，c为way数，d为层数，r为方向角度(若=-999.则保持原方向)，s为角度差，m为速度(若=-999.则保持原速度)n为速度差
  
  
shoot_par(int a, int b, int c, int d, float r, float s, float m, float n) 16384 设置shoot产生的子弹的属性，ab是设置弹幕形状和颜色，c来设置是否消去原先的子弹，1为消，0则保留，d为消弹效果，其他参数暂时不明
  
  
32768(int a) 根据指令632的参数赋予弹幕不同效果.具体参见下方。
  
  
goto(int a) 65536 跳到变换a执行（用来循环）
  
  
131072(anything) 未使用,保留
  
  
262144(anything) 未使用,保留
  
  
spdadd2(int a, float r, float s) 524288 给子弹叠加一个与et_speed原弹速独立的速度，服从平行四边形定则。r角度，s速度，a作用未知，但是需要是正整数。
  
  
light(int a) 1048576 根据a改变弹幕为高亮弹幕，a=1则是亮弹幕,a=0则普通
  
  
spdadd(int a, float r, float s) 2097152 在a帧时间内，给予弹幕一个独立于原速度的速度，朝向为s,速度为(r-原速度),服从平行四边形原则(此函数只调用一次，因此使用-9989.0f来瞄准自机则会到时只有调用这个函数瞬间的自机位置有效，此后子弹将一直瞄准这个位置.若想实时瞄准自机，需让s=999.0f,-999999.0f则不改变角度，同时要让弹幕原本的速度为0.0f，不然因为速度叠加的关系，弹幕的角度和自机狙会有所差异)
  
  
size(int a, int b, float r, float s) 4194304 改变弹幕大小，a为变化时间，b为变化模式(b=0则是匀速变化）r为初始倍率，s为最终倍率.
  
  
8388608(???) GZZ二面终符发现，效果未知
  
  
obj() 16777216 由子弹生成使魔的时候使用，和et_obj配合，因需要使用参数变换编号，必须明确写出编号
  
  
layer(int a) 33554432 设置此子弹的图层为a。（图层大的在上面）
  
  
delay_shoot(int a) 67108864 子弹延时a帧后生成
  
  
shootls(int a, int b, int c, int d, float r, float s, float m, float n) 134217728 未使用，保留(在GZZ中，此mode和8192类似)
  
  
268435456(anything) 未使用,保留
  
  
536870912(anything) 未使用,保留
  
  
1073741824(anything) 未使用,保留
  
  
delay(int a) -2147483648 a帧后执行下一个变换
  
  
  

  

```
 当mode是jump时根据c改变的形式不同
 0方向为原方向+r，速度变为s
 1.一直奇怪的自机相关的改变方式
 2.自机相关+r的改变方式
 3.方向变为-r,速度变为s
 4.方向变为r,速度变为s
 5.所有子弹随机在原方向±r范围内随机
 6.所有子弹随机变向为±r范围内泛狙（未测试
 7.方向不变，速度变为s。
```

```
 当mode使用32768时，根据弹幕发出者的ins_632(int flag)的参数不同而不同.
 若flag=0,则无任何效果
 1.使单位本身可以对弹幕靠近产生反应.（hzc4a线2卡）
   通过[-9978.0f]来决定受影响的范围
   [-9985]会根据弹幕接近与否改变数值,弹幕接近时会变成1.
 5.使弹幕对自机的接近或者离开产生反应（hzc6面5卡） 
   接近则跳转到变换编号5，离开则跳转到14.接触范围[-9980.0f]和[9981.0f]设置，此时一般a=1，a的具体功能尚不明
```

### Flag表
  
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
<td>隐藏单位，并使单位不会被525及518消除
</td></tr>
<tr>
<td>6</td>
<td>64</td>
<td><span style="color:red;">boss最开始都有，迷</span>
</td></tr>
<tr>
<td>7</td>
<td>128</td>
<td>使单位不会被525()及518消除，
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
<td>隐藏单位，并使单位不会被525及518消除
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
<td>
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
<td><span style="color:red;">功能未知，由544赋予和消除</span>
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
<td><span style="color:red;">功能未知，由549赋予和消除</span>
</td></tr></tbody></table>






---

此文档由 [THBWiki-Markdown-Builder](https://github.com/Delsin-Yu/THBWiki-Markdown-Builder) 构建。

文档中的所有内容除特殊注明外，均在 [**知识共享(Creative Commons) 署名-非商业性使用-相同方式共享 3.0 协议**](https://creativecommons.org/licenses/by-sa/3.0/deed.zh-hans) 下提供，附加条款亦可能应用。

引用类型与其他类型作品版权归原作者所有，如有作者授权则遵照授权协议使用。

详细请查阅 [THBWiki：免责声明](https://thbwiki.cc/THBWiki:%E5%85%8D%E8%B4%A3%E5%A3%B0%E6%98%8E)。

