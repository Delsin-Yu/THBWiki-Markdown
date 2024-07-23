# 脚本对照表/ECL

<!-- source html: G:\repos\THBWiki-Markdown-Builder\THBWikiMarkdown\Temp\main\0\0f\ns0%3A%E8%84%9A%E6%9C%AC%E5%AF%B9%E7%85%A7%E8%A1%A8%2FECL.html -->

脚本对照表 | 资料

本页是整理东方Project  
 **相关资料** 的词条

## 目录

- [1 概述](#概述)
- [2 分类](#分类)
- [3 基本语法](#基本语法)
- [4 Instruction表](#Instruction表)
- [5 系统和运算](#系统和运算)
- [6 音效](#音效)
- [7 特殊变量表](#特殊变量表)





### 概述
  
ECL（Enemy Control Language，敌人控制语言）是所有Zun正作及部分STG小数点作内部使用的一种脚本语言。
  
  
ECL最初由[pbg](./ぽんち.md)开发[秋霜玉](./秋霜玉.md)时发明，在[红魔乡](./东方红魔乡.md)时期连同秋霜玉的其它代码一起被ZUN引入正作并不断改进 ~~魔改~~ ，目前在正作内主要负责控制关卡流程，弹幕样式，敌人行为等。
  
  
使用TouHou ToolKit（[THTK](https://github.com/thpatch/thtk)）中的thecl工具可以将ECL字节码文件（即.ECL文件）反编译回ECL代码（但可能无法还原出原始代码），或者将ECL代码编译成可以被游戏执行的字节码文件。
  
  
需要注意的是，THTK所用的ECL和ZUN所用的ECL在语法上并不相同，例如ZUN的ECL语言中，可以使用&lt;==运算符来根据难度对一个变量进行赋值，而THTK的ECL语言并没有类似的运算符（但仍然可以通过其它语法实现）。
  
  
要入门ECL，可以阅读[priw8网站上的ECL教程（英文）](https://priw8.github.io/#b=ecl-tutorial/&amp;p=1)，或阅读翻译后的[ECL入门指南](https://pan.baidu.com/s/1P040qCT1mpGU3cSgeoRQzw?pwd=nmnb)。
  
  
以下为该语言相关的参考资料[。](./脚本对照表-ECL-后户之国.md)
  


### 分类
  
ECL总大体来讲，可以分成四个世代。
  
  
[第一世代](./脚本对照表-ECL-第一世代.md)ecl脚本红妖永花,文花帖。
  

```
    此世代脚本资料甚少，且与后作差异巨大，国内暂时没有人破译这方面内容。
    网上有关这部分的可靠参考请看[PyTouhou的文档](https://pytouhou.linkmauve.fr/doc/)与[TouhouWiki的资料](https://en.touhouwiki.net/wiki/User:Mddass/Touhou_File_Format_Specification/ECL)
```

  
[第二世代](./脚本对照表-ECL-第二世代.md)ecl脚本对应风神录和地灵殿
  
  
[第三世代](./脚本对照表-ECL-第三世代.md)ecl脚本对应星莲船，文花帖DS以及大战争
  
  
[第四世代](./脚本对照表-ECL-第四世代.md)ecl脚本对应神灵庙，辉针城，天邪鬼，绀珠传，天空璋，鬼形兽，虹龙洞
  

```
二三四代开始ECL文件的格式基本被固定下来，各世代的差异只有instruction的数量以及编号的差异
```

  
ECL文件由各个sub（routine）和instruction构成，sub表示一个函数（子例程），instruction为一条指令
  
  
ECL的基本类型只有两种：整数（有符号）和浮点数（单精度）。字符串虽然在指令中有所出现但是无法参与运算。
  
  
第二世代之后ECL引入了sub符号表，使部分指令从传入sub号变为了传入sub名，并且也能在反编译时获得原始sub名。
  


### 基本语法
  
var xxx
  

```
 定义名称为xxx的局部变量（不区分类型）
 xxx可以以任意英文字母或下划线（_）开头，并在之后可以接任意数量的英文字母、下划线或数字
 反编译的脚本中大部分变量都会变为此种形式
```

  
int xxx = value
  
  
float xxx = value
  

```
 同为定义变量，但是带有类型且可以指定初始值（value，可选）
 好处在于可以无需在引用时添加$和%前缀来指示变量类型
 反编译的脚本通常不会出现
```

  
0, 123, -123, 0xff, -0xff
  

```
 整数常量
```

  
1.0，1.0f，3.14159265，3.14159265f
  

```
 浮点数常量
```

  
$xxx
  

```
 将名称为xxx的变量引用为整数
```

  
%xxx
  

```
 将名称为xxx的变量引用为浮点数
```

  
_SS
  

```
 ins_11及ins_15等指令传递整数参数时使用
```

  
_ff
  

```
 ins_11及ins_15等指令传递浮点数参数时使用
```

  
_f(n)
  
  
_Sf(n)
  

```
 强制将n转换为浮点数
```

  
_S(n)
  
  
_fS(n)
  

```
 强制将n转换为整数
```

```
 !EN
     1; // 对应Easy和Normal难度
 !H
     2; // 对应Hard难度
 !LO
     3; // 对应Lunatic和Overdrive难度
&#160;!*
 一种根据难度选择的switch，ENHLXO分别代表Easy，Normal，Hard，Lunatic，Extra和Overdrive。
 以!开头的每行中，每个字母表示一个难度，例如N表示匹配Normal难度，要对多个难度进行匹配可以使用多个字母，例如LO表示匹配Lunatic和Overdrive难度
```

  
xxxx:
  

```
 xxxx为标识符，则此为标签，配合goto使用
```

  
+xxxx:
  

```
 xxxx为整数，表示该操作需要占用的时间，执行到此处时会把xxxx赋值给计时器，在计时器归零之后才会继续执行下一条指令
 通常配合ins_0使用，作为除ins_23以外的另一种暂停方式
```

  
goto xxxx
  

```
 跳转到名为xxxx的标签
```

  
goto xxxx @ n
  

```
 跳转到名为xxxx的标签并将计时器设置为n，通常用于跳转后需要暂停n帧的场合
```

  
[-n]
  

```
 表示读取距离栈顶n个值的内容，n为整数则读取一个整数，n为浮点数则读取一个浮点数
 当n为特殊值时引擎会识别这些特殊值并当作特殊变量处理，见下方特殊变量表
```

  
func(arg1, arg2, ...)
  
  
@func(arg1, arg2, ...)
  

```
 调用函数，func为函数名，arg1和arg2为参数
 在调用前加@表示无视函数是否在前面已经声明（例如调用在之后定义的函数）
```

  
func(arg1, arg2, ...) async
  
  
@func(arg1, arg2, ...) async
  

```
 创建一个新的子线程并在线程中调用函数
```

  
func(arg1, arg2, ...) async n
  
  
@func(arg1, arg2, ...) async n
  

```
 创建一个ID为n的子线程并在线程中调用函数，n必须为整数
```

  
while(condition) { ... }
  

```
 循环执行语句块中的内容直到condition不成立
 反编译的脚本通常不会出现，且通常会变为类似如下的形式：
 goto xxxx_5678 @ 0;
 xxxx_1234:
 ...
 xxxx_5678:
 if (condition) goto xxxx_1234 @ 0;
```

  
times(n) { ... }
  

```
 循环执行语句块中的内容n次
 反编译的脚本中通常不会出现，且通常会变为类似如下的形式：
 var A;
 $A = n; // n为循环次数且通常为整数
 xxxx_1234:
 ...
 if ($A--) goto xxxx_1234 @ 0;
```

```
 switch(expr) {
     case n:
         ...
     case m:
         ...
     default:
         ...
 }
 switch语句，与C中的switch类似
 将expr的值与case列表中的值逐个匹配，当符合时执行对应的语句
 执行到case末尾后不会自动跳出switch而是会继续执行下面的所有语句，需要跳出时可以用break
 当无法匹配任何case时会执行default中的语句
 反编译的脚本中通常不会出现
```

  
sin(n)
  
  
cos(n)
  

```
 sin运算和cos运算
```

  
rad(n)
  

```
 将n转换为弧度制，n必须为编译期浮点常量
```

  
deg(n)
  

```
 将n转换为角度制，n必须为编译期浮点常量
```

  
type funcName(param_type param, ...);
  

```
 声明一个名为funcName的函数，函数返回值类型为type
 param_type param表示定义一个类型为param_type，名称为param的参数（可以在参数列表中出现多次，用逗号分隔）
 ...表示可变个数参数，必须出现在参数列表末尾
```

  
type funcName(param_type param, ...) { ... }
  

```
 声明并定义一个名为funcName，函数返回值类型为type的函数，整数返回值会被存储到[-9985]
```

  
inline type funcName(param_type param, ...) { ... }
  

```
 声明并定义一个名为funcName，函数返回值类型为type的内联函数（即会在被调用处展开的函数）
 截至THTK13，THECL对内联函数的支持存在一些问题，因此不建议使用
```

  
return value
  

```
 从函数返回并将value作为返回值
 当函数的返回类型为void时，value必须置空
```

  
&#35;include "filename"
  

```
 将文件名为filename的文件插入当前位置并作为源文件的一部分编译
```

  
&#35;n
  

```
 将当前源代码函数设置为n行（不影响编译，只影响消息输出），n为整数
```


### Instruction表
```
  Instruction有 ins_xx（arg1，arg2，arg3.。。。） 表示，其中xx代表Instruction的编号，不同编号有不同的功能，
  每个Instruction需要的参数也不同/
```

  
下表展示了各种Instruction的功能
  

```
  Instruction大致可以分为 5大类
  即运算和系统，贴图和创建单位， 移动，单位属性，弹幕相关
  每一做的运算和系统部分基本相同，其他部分请参考各世代的独立的页面
  [第二世代](./脚本对照表-ECL-第二世代.md)
  [第三世代](./脚本对照表-ECL-第三世代.md)
  [第四世代](./脚本对照表-ECL-第四世代.md)
  以下部分，黑字为从风神录就开始存在
  蓝色部分是地灵殿新增
  紫色部分是星莲船新增
  棕色部分是文花帖DS新增
  青色部分是妖精大战争新增
  绿色部分是神灵庙新增
  浅紫色部分为天空璋之后作(考虑到作数较多不设其它颜色)
```

```
  注：本表仅负责收录风神录后编号为200以前的指令，其余请到对应世代页面，对应世代通常也不会收录此处已有的指令。
      第一世代由于差异过大，故独立收录。
```


### 系统和运算
  
ins_0()
  

```
 空指令，通常main开始会调用一次，常搭配计时器使用作为ins_23的替代
 例如：
 +60: ins_0()
 等同于：
 ins_23(60);
 在[2un的采访](./ZUN-游戏的修罗场6.md)中有所出现
```

  
ins_1()
  

```
 清除当前单位，不会有任何奖励或死亡特效，以及死尸弹
 也称大return
```

  
ins_10()
  

```
 返回到调用当前sub的地方，不清除当前单位，也称小return
 对应的语句为return;
```

  
ins_11(CString Subroutine, member1, member2, ...)
  

```
 调用函数，Subroutine的值为函数名称，若有需要传递参数，必须要在整数前加上_SS，浮点数前加上_ff，在子线程结束后返回
 对应的语句为@Subroutine(member1, member2, ...);
```

  
ins_12(label,int b),
  

```
 跳转到label并将计时器设为b
 对应的语句为goto label @ b;
```

  
ins_13(label,int b),
  

```
 栈顶为0则跳转到label并将计时器设置为b（if语句使用）
 对应的语句为
 unless ([-1]) goto label @ b;
```

  
ins_14(label,int b),
  

```
 栈顶为1则跳转到label并将计时器设置为b（循环使用）
 对应的语句为
 if ([-1]) goto label @ b;
```

  
ins_15(CString Subroutine, member1, member2, ...) 
  

```
 在当前单位创建一个ID为-1的子线程，并行运行
 对应的语句为@Subroutine(member1, member2, ...) async;
```

  
ins_16(CString Subroutine,int id) 
  

```
 在当前单位创建一个带id的子线程，并行运行
 对应的语句为@Subroutine(member1, member2, ...) async id;
```

  
ins_17(int id) 
  

```
 关闭ins_16创建的带指定id的子线程
```

  
ins_18(?)
  
  
ins_19(?)
  
  
ins_20(?)
  
  
ins_21()
  

```
 关闭所有子线程
```

  
ins_22(int id, CString name)
  

```
 zun调试用指令，作用疑为调试目标序号与id相等时跳转到名为name的函数，release版本无作用
```

  
ins_23(int n)
  

```
 神灵庙起为等待N帧（原ins_83）
```

  
ins_24(float n)
  

```
 ins_23的浮点数版本
```

  
ins_30
  

```
 空指令
```

  
ins_31
  

```
 空指令
```

  
ins_40(int size)
  

```
 分配局部变量用，等价于Var
```

  
ins_41()
  

```
 销毁40分配的局部变量
```

  
ins_42(int n)
  

```
 将整数压入栈，例如ins_42(1)等价于1;
```

  
ins_43(int) 
  

```
 使栈顶内容出栈并将其写入变量，例如将整数5写入名称为C的变量：
 5;
 ins_43($C);
 等同于
 5;
 $C = [-1];
 等同于
 $C = 5;
 以上三种写法效果一致
```

  
ins_44(float) 同ins_42，但是操作目标为浮点数
  
  
ins_45(float) 同ins_43，但是操作目标为浮点数
  
  
运算符号表
ins_50 开始至ins_72为各种基础运算，相同功能的一对中，第一个为整数版本，第二个为浮点数版本
  


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
<td>50</td>
<td>+</td>
<td>51</td>
<td>+</td>
<td>52</td>
<td>-</td>
<td>53</td>
<td>-
</td></tr>
<tr>
<td>54</td>
<td>*</td>
<td>55</td>
<td>*</td>
<td>56</td>
<td>/</td>
<td>57</td>
<td>/
</td></tr>
<tr>
<td>58</td>
<td>%</td>
<td>-</td>
<td>-</td>
<td>59</td>
<td>==</td>
<td>60</td>
<td>==
</td></tr>
<tr>
<td>61</td>
<td>!=</td>
<td>62</td>
<td>!=</td>
<td>63</td>
<td>&lt;</td>
<td>64</td>
<td>&lt;
</td></tr>
<tr>
<td>65</td>
<td>&lt;=</td>
<td>66</td>
<td>&lt;=</td>
<td>67</td>
<td>&gt;</td>
<td>68</td>
<td>&gt;
</td></tr>
<tr>
<td>69</td>
<td>&gt;=</td>
<td>70</td>
<td>&gt;=</td>
<td>71</td>
<td>!</td>
<td>72</td>
<td>!
</td></tr></tbody></table>


  
ins_73()
  

```
 逻辑or（||）
```

  
ins_74()
  

```
 逻辑and（&amp;&amp;）
```

  
ins_75()
  

```
 按位xor（^）
```

  
ins_76()
  

```
 按位or（|）
```

  
ins_77()
  

```
 按位and（&amp;）
```

  
ins_78(int i)
  

```
 循环i次后返回1，用于控制循环次数。
```

  
ins_79()
  

```
 sin
```

  
ins_80()
  

```
 cos
```

  
ins_81(float A,float B,float x,float y)
  

```
  A=ycosx ,B=ysinx
```

  
ins_82(float A)
  

```
 +-2π的整数倍以至于A落入（-π，π）这个区间
 加减的次数有限制,最多34次(见th15 sub_403920),例如当a=2000时,ins_82(%a) 则a变为1786.3710而非1.94707
 在地灵殿四面道中二非有使用这一技巧(弹幕先有序排列,随后变得无序)  *发现:YukariM
```

  
  

ins_83(int n)
  
  
ins_83()
  

```
 神灵庙前为等待n帧
 神灵庙后为整数取负
```

  
ins_84()
  
  
ins_84()
  

```
 神灵庙前为整数取负
 神灵庙后为浮点数取负
```

  
ins_85()
  
  
ins_85(float &amp;dest, float x, float y)
  

```
 神灵庙前为浮点数取负
 神灵庙后等同于dest = x * x + y * y;（将dest设为x²+y²）
```

  
ins_86(float &amp;dest, float x, float y)
  
  
ins_86(float dest, float x, float y)
  

```
 神灵庙前等同于dest = x * x + y * y;（将dest设为x²+y²）
 神灵庙后等同于dest = sqrt(x * x + y * y);（将dest设为(x²+y²)的平方根，即两点间距离）
```

  
ins_87(float &amp;dest,float x1,float y1,float x2,float y2)
  

```
 将dest设为点(x1,y1)至点（x2,y2）的方向
```

  
ins_88()
  

```
 对栈顶的数进行平方根运算
```

  
ins_89(float &amp;dest, float x float y)
  

```
 将dest设为y - x
```

  
ins_90(float &amp;A,float &amp;B,float x,float y，float z)
  

```
  将点(x,y)旋转z度之后获得坐标(x1,y1);(A,B)=(x1,y1)
```

  
ins_91(int A,float %B,int T int d,float a,float b)
  

```
执行代码之后的T帧内，将%B由a变化到b(也可能是根据b变化),缓动曲线的类型为d,A为slot,一个变量占用一个slot,每个单位有0-7的八个可用slot
以下是所有类型的描述,其中8和17与ins_92有关,函数表达式yn(a,b,t)中t∈[0,1],为该变换已经进行的时刻与总时间的比;此外所有函数均为拟合所得,不保证一定准确
```

  
注意：d=22及以后的凹凸性是对a&lt;b时描述的，a&gt;b时凹凸性相反
  


<table>

<tbody><tr>
<th>d</th>
<th>description</th>
<th>function
</th></tr>
<tr>
<td>0</td>
<td>线性变换</td>
<td>y0=(b-a)*t+a
</td></tr>
<tr>
<td>1</td>
<td>二次函数，变化率增大</td>
<td>y1=(b-a)*t²+a
</td></tr>
<tr>
<td>2</td>
<td>三次函数，变化率增大</td>
<td>y2=(b-a)*t³+a
</td></tr>
<tr>
<td>3</td>
<td>四次函数，变化率增大</td>
<td>y3=(b-a)*t<sup>4</sup>+a
</td></tr>
<tr>
<td>4</td>
<td>二次函数，变化率减小</td>
<td>y4=(a-b)*(1-t²)+b
</td></tr>
<tr>
<td>5</td>
<td>三次函数，变化率减小</td>
<td>y5=(a-b)*(1-t³)+b
</td></tr>
<tr>
<td>6</td>
<td>四次函数，变化率减小</td>
<td>y6=(a-b)*(1-t<sup>4</sup>)+b
</td></tr>
<tr>
<td>7</td>
<td>一次函数</td>
<td>y7=bx+a
</td></tr>
<tr>
<td>8</td>
<td>特定贝塞尔曲线</td>
<td>见下方ins_92
</td></tr>
<tr>
<td>9</td>
<td>双二次函数(变化率先增大后减小)</td>
<td>y9=y1(a,(a+b)/2,2*t)(其中t&lt;0.5);y9=y4((a+b)/2,b,2*t-1)(其中t&gt;=0.5)
</td></tr>
<tr>
<td>10</td>
<td>双三次函数(变化率先增大后减小)</td>
<td>y10=y2(a,(a+b)/2,2*t)(其中t&lt;0.5);y10=y5((a+b)/2,b,2*t-1)(其中t&gt;=0.5)
</td></tr>
<tr>
<td>11</td>
<td>双四次函数(变化率先增大后减小)</td>
<td>y11=y3(a,(a+b)/2,2*t)(其中t&lt;0.5);y11=y6((a+b)/2,b,2*t-1)(其中t&gt;=0.5)
</td></tr>
<tr>
<td>12</td>
<td>双二次函数(变化率先增大后减小)</td>
<td>y12=y4(a,(a+b)/2,2*t)(其中t&lt;0.5);y12=y1((a+b)/2,b,2*t-1)(其中t&gt;=0.5)
</td></tr>
<tr>
<td>13</td>
<td>双三次函数(变化率先增大后减小)</td>
<td>y13=y5(a,(a+b)/2,2*t)(其中t&lt;0.5);y13=y2((a+b)/2,b,2*t-1)(其中t&gt;=0.5)
</td></tr>
<tr>
<td>14</td>
<td>双四次函数(变化率先增大后减小)</td>
<td>y14=y6(a,(a+b)/2,2*t)(其中t&lt;0.5);y14=y3((a+b)/2,b,2*t-1)(其中t&gt;=0.5)
</td></tr>
<tr>
<td>15</td>
<td>常函数</td>
<td>y15=a
</td></tr>
<tr>
<td>16</td>
<td>常函数</td>
<td>y16=b
</td></tr>
<tr>
<td>17</td>
<td>特定二次函数</td>
<td>y=bt²/2+a
</td></tr>
<tr>
<td>18</td>
<td>三角函数，变化率减小</td>
<td>sin(t*π/2)*(b-a)+a;
</td></tr>
<tr>
<td>19</td>
<td>三角函数，变化率增大</td>
<td>(1-cos(t*π/2))*(b-a)+a;
</td></tr>
<tr>
<td>20</td>
<td>双三角函数(变化率先减小后增大)</td>
<td>y20=y18(a,(a+b)/2,2*t)(其中t&lt;0.5);y20=y19((a+b)/2,b,2*t-1)(其中t&gt;=0.5)
</td></tr>
<tr>
<td>21</td>
<td>双三角函数(变化率先增大后减小)</td>
<td>y21=y19(a,(a+b)/2,2*t)(其中t&lt;0.5);y20=y18((a+b)/2,b,2*t-1)(其中t&gt;=0.5)
</td></tr>
<tr>
<td>22</td>
<td>二次凹函数(插值最低-1/8)</td>
<td>y22=(2t²-t)*(b-a)+a
</td></tr>
<tr>
<td>23</td>
<td>二次凹函数(插值最低-9/40)</td>
<td>y23=(2.5t²-1.5t)*(b-a)+a
</td></tr>
<tr>
<td>24</td>
<td>二次凹函数(插值最低-25/56)</td>
<td>y24=(3.5t²-2.5t)*(b-a)+a
</td></tr>
<tr>
<td>25</td>
<td>二次凹函数(插值最低-169/272)</td>
<td>y25=(4.25t²-3.25t)*(b-a)+a
</td></tr>
<tr>
<td>26</td>
<td>二次凹函数(插值最低-289/336)</td>
<td>y26=(5.25t²-4.25t)*(b-a)+a
</td></tr>
<tr>
<td>27</td>
<td>二次凸函数(插值最高9/8)</td>
<td>y27=(-2t²+3t)*(b-a)+a
</td></tr>
<tr>
<td>28</td>
<td>二次凸函数(插值最高49/40)</td>
<td>y28=(-2.5t²+3.5t)*(b-a)+a
</td></tr>
<tr>
<td>29</td>
<td>二次凸函数(插值最高81/56)</td>
<td>y29=(-3.5t²+4.5t)*(b-a)+a
</td></tr>
<tr>
<td>30</td>
<td>二次凸函数(插值最高441/272)</td>
<td>y30=(-4.25t²+5.25t)*(b-a)+a
</td></tr>
<tr>
<td>31</td>
<td>二次凸函数(插值最高625/336)</td>
<td>y31=(-5.25t²+6.25t)*(b-a)+a
</td></tr></tbody></table>


  
ins_92(int A,float &amp;B,int T int d,float a,float b,float m,float n)
  

```
  自定义缓动曲线
  多了两个参数m,n,除了「mode=8需要m,n；mode17需要n」外与ins_91相同
  当mode=8时,记曲线中点的坐标为(t,y),(其中s∈[0,1]为经过的时间/总时间,y为%B在该时刻的值),则该曲线为一个贝塞尔曲线,起点p0(0,a),终点p3(1,b),两锚点为p1(1/3,a+m/3),p2(2/3,b-n/3)
  当mode=17时,Δ²y=b,Δy｜(t=0)=n,y｜(t=0)=a
```

  
ins_93(float &amp;x,float &amp;y,float r1,float r2)
  

```
  (float &amp;A,float &amp;B,float x,float y) 生成(A,B)为从半径为y的圆边上开始生成的16条顺时针旋转的触手内均匀分布的随机点，x大于y则向外生长，x小于y则向内生长，x过小（如=0.0f）可能长过圆心
  上面那个不要看,看下面这个解释
  记R=rnd(-1,1)*(r2-r1)+r1 ,则返回x=cos(rnd(-pi,pi))*R;y=sin(rnd(-pi,pi))*R
  也就是对于一个环面,环面的中位圆的半径为r1,最大半径为r2,在这个环内内随机获取点(x,y)返回
  备注:产生触手的原因是2un的伪随机数(zundom)特性
  原理如下:zundom函数中两个相邻随机数之间具有很强的相关性;具体来说,对于两个定义域为[0,1]的相邻随机数r[n]和r[n+1],有
  r[n+1]≈-r[n]/16.05 - floor(-r[n]/16.05)
  因此如果先取随机角度，则距离也就大约确定,就产生了"触手"
  可以通过先去距离再取角度(此时距离随机性减少),或在两次取随机值的中间加入一个无用随机量更新随机数等方法增强随机性(但是ins_93的代码是确定的,没法这么做)
```

  
ins_94(float&amp; resX,float&amp; resY,float phi,float radiusY,float angle,float aspectRatio)
  

```
   虹龙洞新增
   构造一个x轴上轴半长为a=radiusY*aspectRatio,y轴的半轴长为b=radiusY的椭圆}}
   在其离心角上的角度theta=phi-angle处选择一点(即x=a*cos(theta),y=b*sin(theta))}}
   随后将整个椭圆旋转angle的角度}}
   最终得到的x,y输出为resX,resY}}
    **离心角选择的是(phi-angle)这点就非常的神奇,可能2un想要的是在最终变换出的(旋转了angle度的)椭圆与直线y=tan(phi)x的交点,但是除非aspectRatio=1,不然这点和2un实际选择的点并不重合** 
```


### 音效
  
本表是ECL脚本中播放音效相关函数的参数与实际音效的对应关系表。
  
  
星莲船
  


<table>

<tbody><tr>
<th>编号</th>
<th>音效名</th>
<th>编号</th>
<th>音效名
</th></tr>
<tr>
<td>0</td>
<td><a href="./文件-se_plst00.mp3.md" title="文件:se plst00.mp3">se_plst00.mp3</a><br><audio src="https://upload.thwiki.cc/b/b4/se_plst00.mp3" loop="" controls="" preload="none"></audio></td>
<td>1</td>
<td><a href="./文件-se_plst00.mp3.md" title="文件:se plst00.mp3">se_plst00.mp3</a><br><audio src="https://upload.thwiki.cc/b/b4/se_plst00.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>2</td>
<td><a href="./文件-se_pldead00.mp3.md" title="文件:se pldead00.mp3">se_pldead00.mp3</a><br><audio src="https://upload.thwiki.cc/c/c9/se_pldead00.mp3" loop="" controls="" preload="none"></audio></td>
<td>3</td>
<td><a href="./文件-se_enep00.mp3.md" title="文件:se enep00.mp3">se_enep00.mp3</a><br><audio src="https://upload.thwiki.cc/4/4e/se_enep00.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>4</td>
<td><a href="./文件-se_enep00.mp3.md" title="文件:se enep00.mp3">se_enep00.mp3</a><br><audio src="https://upload.thwiki.cc/4/4e/se_enep00.mp3" loop="" controls="" preload="none"></audio></td>
<td>5</td>
<td><a href="./文件-se_enep01.mp3.md" title="文件:se enep01.mp3">se_enep01.mp3</a><br><audio src="https://upload.thwiki.cc/8/84/se_enep01.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>6</td>
<td><a href="./文件-se_enep02.mp3.md" title="文件:se enep02.mp3">se_enep02.mp3</a><br><audio src="https://upload.thwiki.cc/0/08/se_enep02.mp3" loop="" controls="" preload="none"></audio></td>
<td>7</td>
<td><a href="./文件-se_ok00.mp3.md" title="文件:se ok00.mp3">se_ok00.mp3</a><br><audio src="https://upload.thwiki.cc/b/bf/se_ok00.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>8</td>
<td><a href="./文件-se_ok00.mp3.md" title="文件:se ok00.mp3">se_ok00.mp3</a><br><audio src="https://upload.thwiki.cc/b/bf/se_ok00.mp3" loop="" controls="" preload="none"></audio></td>
<td>9</td>
<td><a href="./文件-se_cancel00.mp3.md" title="文件:se cancel00.mp3">se_cancel00.mp3</a><br><audio src="https://upload.thwiki.cc/7/7e/se_cancel00.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>10</td>
<td><a href="./文件-se_select00.mp3.md" title="文件:se select00.mp3">se_select00.mp3</a><br><audio src="https://upload.thwiki.cc/2/28/se_select00.mp3" loop="" controls="" preload="none"></audio></td>
<td>11</td>
<td><a href="./文件-se_timeout.mp3.md" title="文件:se timeout.mp3">se_timeout.mp3</a><br><audio src="https://upload.thwiki.cc/1/1c/se_timeout.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>12</td>
<td><a href="./文件-se_timeout2.mp3.md" title="文件:se timeout2.mp3">se_timeout2.mp3</a><br><audio src="https://upload.thwiki.cc/b/bc/se_timeout2.mp3" loop="" controls="" preload="none"></audio></td>
<td>13</td>
<td><a href="./文件-se_powerup.mp3.md" title="文件:se powerup.mp3">se_powerup.mp3</a><br><audio src="https://upload.thwiki.cc/3/3b/se_powerup.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>14</td>
<td><a href="./文件-se_pause.mp3.md" title="文件:se pause.mp3">se_pause.mp3</a><br><audio src="https://upload.thwiki.cc/3/3a/se_pause.mp3" loop="" controls="" preload="none"></audio></td>
<td>15</td>
<td><a href="./文件-se_cardget.mp3.md" title="文件:se cardget.mp3">se_cardget.mp3</a><br><audio src="https://upload.thwiki.cc/1/1f/se_cardget.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>16</td>
<td><a href="./文件-se_option.mp3.md" title="文件:se option.mp3">se_option.mp3</a><br><audio src="https://upload.thwiki.cc/6/6a/se_option.mp3" loop="" controls="" preload="none"></audio></td>
<td>17</td>
<td><a href="./文件-se_invalid.mp3.md" title="文件:se invalid.mp3">se_invalid.mp3</a><br><audio src="https://upload.thwiki.cc/b/b3/se_invalid.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>18</td>
<td><a href="./文件-se_extend.mp3.md" title="文件:se extend.mp3">se_extend.mp3</a><br><audio src="https://upload.thwiki.cc/9/9d/se_extend.mp3" loop="" controls="" preload="none"></audio></td>
<td>19</td>
<td><a href="./文件-se_lazer00.mp3.md" title="文件:se lazer00.mp3">se_lazer00.mp3</a><br><audio src="https://upload.thwiki.cc/c/cc/se_lazer00.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>20</td>
<td><a href="./文件-se_lazer01.mp3.md" title="文件:se lazer01.mp3">se_lazer01.mp3</a><br><audio src="https://upload.thwiki.cc/5/57/se_lazer01.mp3" loop="" controls="" preload="none"></audio></td>
<td>21</td>
<td><a href="./文件-se_lazer02.mp3.md" title="文件:se lazer02.mp3">se_lazer02.mp3</a><br><audio src="https://upload.thwiki.cc/0/03/se_lazer02.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>22</td>
<td><a href="./文件-se_plst00.mp3.md" title="文件:se plst00.mp3">se_plst00.mp3</a><br><audio src="https://upload.thwiki.cc/b/b4/se_plst00.mp3" loop="" controls="" preload="none"></audio></td>
<td>23</td>
<td><a href="./文件-se_tan01.mp3.md" title="文件:se tan01.mp3">se_tan01.mp3</a><br><audio src="https://upload.thwiki.cc/8/8b/se_tan01.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>24</td>
<td><a href="./文件-se_tan02.mp3.md" title="文件:se tan02.mp3">se_tan02.mp3</a><br><audio src="https://upload.thwiki.cc/f/f4/se_tan02.mp3" loop="" controls="" preload="none"></audio></td>
<td>25</td>
<td><a href="./文件-se_tan00.mp3.md" title="文件:se tan00.mp3">se_tan00.mp3</a><br><audio src="https://upload.thwiki.cc/1/15/se_tan00.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>26</td>
<td><a href="./文件-se_tan01.mp3.md" title="文件:se tan01.mp3">se_tan01.mp3</a><br><audio src="https://upload.thwiki.cc/8/8b/se_tan01.mp3" loop="" controls="" preload="none"></audio></td>
<td>27</td>
<td><a href="./文件-se_tan02.mp3.md" title="文件:se tan02.mp3">se_tan02.mp3</a><br><audio src="https://upload.thwiki.cc/f/f4/se_tan02.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>28</td>
<td><a href="./文件-se_tan00.mp3.md" title="文件:se tan00.mp3">se_tan00.mp3</a><br><audio src="https://upload.thwiki.cc/1/15/se_tan00.mp3" loop="" controls="" preload="none"></audio></td>
<td>29</td>
<td><a href="./文件-se_power0.mp3.md" title="文件:se power0.mp3">se_power0.mp3</a><br><audio src="https://upload.thwiki.cc/6/63/se_power0.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>30</td>
<td><a href="./文件-se_power1.mp3.md" title="文件:se power1.mp3">se_power1.mp3</a><br><audio src="https://upload.thwiki.cc/e/e7/se_power1.mp3" loop="" controls="" preload="none"></audio></td>
<td>31</td>
<td><a href="./文件-se_ch00.mp3.md" title="文件:se ch00.mp3">se_ch00.mp3</a><br><audio src="https://upload.thwiki.cc/0/05/se_ch00.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>32</td>
<td><a href="./文件-se_ch01.mp3.md" title="文件:se ch01.mp3">se_ch01.mp3</a><br><audio src="https://upload.thwiki.cc/2/2d/se_ch01.mp3" loop="" controls="" preload="none"></audio></td>
<td>33</td>
<td><a href="./文件-se_gun00.mp3.md" title="文件:se gun00.mp3">se_gun00.mp3</a><br><audio src="https://upload.thwiki.cc/1/18/se_gun00.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>34</td>
<td><a href="./文件-se_cat00.mp3.md" title="文件:se cat00.mp3">se_cat00.mp3</a><br><audio src="https://upload.thwiki.cc/8/82/se_cat00.mp3" loop="" controls="" preload="none"></audio></td>
<td>35</td>
<td><a href="./文件-se_damage00.mp3.md" title="文件:se damage00.mp3">se_damage00.mp3</a><br><audio src="https://upload.thwiki.cc/8/83/se_damage00.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>36</td>
<td><a href="./文件-se_damage01.mp3.md" title="文件:se damage01.mp3">se_damage01.mp3</a><br><audio src="https://upload.thwiki.cc/4/40/se_damage01.mp3" loop="" controls="" preload="none"></audio></td>
<td>37</td>
<td><a href="./文件-se_nodamage.mp3.md" title="文件:se nodamage.mp3">se_nodamage.mp3</a><br><audio src="https://upload.thwiki.cc/d/dd/se_nodamage.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>38</td>
<td><a href="./文件-se_item00.mp3.md" title="文件:se item00.mp3">se_item00.mp3</a><br><audio src="https://upload.thwiki.cc/7/70/se_item00.mp3" loop="" controls="" preload="none"></audio></td>
<td>39</td>
<td><a href="./文件-se_item01.mp3.md" title="文件:se item01.mp3">se_item01.mp3</a><br><audio src="https://upload.thwiki.cc/8/8f/se_item01.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>40</td>
<td><a href="./文件-se_kira00.mp3.md" title="文件:se kira00.mp3">se_kira00.mp3</a><br><audio src="https://upload.thwiki.cc/d/da/se_kira00.mp3" loop="" controls="" preload="none"></audio></td>
<td>41</td>
<td><a href="./文件-se_kira01.mp3.md" title="文件:se kira01.mp3">se_kira01.mp3</a><br><audio src="https://upload.thwiki.cc/0/09/se_kira01.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>42</td>
<td><a href="./文件-se_kira02.mp3.md" title="文件:se kira02.mp3">se_kira02.mp3</a><br><audio src="https://upload.thwiki.cc/4/4f/se_kira02.mp3" loop="" controls="" preload="none"></audio></td>
<td>43</td>
<td><a href="./文件-se_kira00.mp3.md" title="文件:se kira00.mp3">se_kira00.mp3</a><br><audio src="https://upload.thwiki.cc/d/da/se_kira00.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>44</td>
<td><a href="./文件-se_graze.mp3.md" title="文件:se graze.mp3">se_graze.mp3</a><br><audio src="https://upload.thwiki.cc/9/97/se_graze.mp3" loop="" controls="" preload="none"></audio></td>
<td>45</td>
<td><a href="./文件-se_graze.mp3.md" title="文件:se graze.mp3">se_graze.mp3</a><br><audio src="https://upload.thwiki.cc/9/97/se_graze.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>46</td>
<td><a href="./文件-se_slash.mp3.md" title="文件:se slash.mp3">se_slash.mp3</a><br><audio src="https://upload.thwiki.cc/5/59/se_slash.mp3" loop="" controls="" preload="none"></audio></td>
<td>47</td>
<td><a href="./文件-se_slash.mp3.md" title="文件:se slash.mp3">se_slash.mp3</a><br><audio src="https://upload.thwiki.cc/5/59/se_slash.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>48</td>
<td><a href="./文件-se_cardget.mp3.md" title="文件:se cardget.mp3">se_cardget.mp3</a><br><audio src="https://upload.thwiki.cc/1/1f/se_cardget.mp3" loop="" controls="" preload="none"></audio></td>
<td>49</td>
<td><a href="./文件-se_bonus.mp3.md" title="文件:se bonus.mp3">se_bonus.mp3</a><br><audio src="https://upload.thwiki.cc/a/ae/se_bonus.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>50</td>
<td><a href="./文件-se_bonus2.mp3.md" title="文件:se bonus2.mp3">se_bonus2.mp3</a><br><audio src="https://upload.thwiki.cc/d/d1/se_bonus2.mp3" loop="" controls="" preload="none"></audio></td>
<td>51</td>
<td><a href="./文件-se_nep00.mp3.md" title="文件:se nep00.mp3">se_nep00.mp3</a><br><audio src="https://upload.thwiki.cc/8/89/se_nep00.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>52</td>
<td><a href="./文件-se_timeout.mp3.md" title="文件:se timeout.mp3">se_timeout.mp3</a><br><audio src="https://upload.thwiki.cc/1/1c/se_timeout.mp3" loop="" controls="" preload="none"></audio></td>
<td>53</td>
<td><a href="./文件-se_timeout2.mp3.md" title="文件:se timeout2.mp3">se_timeout2.mp3</a><br><audio src="https://upload.thwiki.cc/b/bc/se_timeout2.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>54</td>
<td><a href="./文件-se_ufoalert.mp3.md" title="文件:se ufoalert.mp3">se_ufoalert.mp3</a><br><audio src="https://upload.thwiki.cc/e/e3/se_ufoalert.mp3" loop="" controls="" preload="none"></audio></td>
<td>55</td>
<td><a href="./文件-se_piyo.mp3.md" title="文件:se piyo.mp3">se_piyo.mp3</a><br><audio src="https://upload.thwiki.cc/0/04/se_piyo.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>56</td>
<td><a href="./文件-se_boon00.mp3.md" title="文件:se boon00.mp3">se_boon00.mp3</a><br><audio src="https://upload.thwiki.cc/e/e7/se_boon00.mp3" loop="" controls="" preload="none"></audio></td>
<td>57</td>
<td><a href="./文件-se_boon01.mp3.md" title="文件:se boon01.mp3">se_boon01.mp3</a><br><audio src="https://upload.thwiki.cc/e/e1/se_boon01.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>58</td>
<td>????</td>
<td>
</td></tr></tbody></table>


  
虹龙洞
  


<table>

<tbody><tr>
<th>编号</th>
<th>音效名</th>
<th>编号</th>
<th>音效名
</th></tr>
<tr>
<td>0</td>
<td><a href="./文件-se_plst00.mp3.md" title="文件:se plst00.mp3">se_plst00.mp3</a><br><audio src="https://upload.thwiki.cc/b/b4/se_plst00.mp3" loop="" controls="" preload="none"></audio></td>
<td>1</td>
<td><a href="./文件-se_enep00.mp3.md" title="文件:se enep00.mp3">se_enep00.mp3</a><br><audio src="https://upload.thwiki.cc/4/4e/se_enep00.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>2</td>
<td><a href="./文件-se_pldead00.mp3.md" title="文件:se pldead00.mp3">se_pldead00.mp3</a><br><audio src="https://upload.thwiki.cc/c/c9/se_pldead00.mp3" loop="" controls="" preload="none"></audio></td>
<td>3</td>
<td><a href="./文件-se_power0.mp3.md" title="文件:se power0.mp3">se_power0.mp3</a><br><audio src="https://upload.thwiki.cc/6/63/se_power0.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>4</td>
<td><a href="./文件-se_power1.mp3.md" title="文件:se power1.mp3">se_power1.mp3</a><br><audio src="https://upload.thwiki.cc/e/e7/se_power1.mp3" loop="" controls="" preload="none"></audio></td>
<td>5</td>
<td><a href="./文件-se_tan00.mp3.md" title="文件:se tan00.mp3">se_tan00.mp3</a><br><audio src="https://upload.thwiki.cc/1/15/se_tan00.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>6</td>
<td><a href="./文件-se_tan01.mp3.md" title="文件:se tan01.mp3">se_tan01.mp3</a><br><audio src="https://upload.thwiki.cc/8/8b/se_tan01.mp3" loop="" controls="" preload="none"></audio></td>
<td>7</td>
<td><a href="./文件-se_tan02.mp3.md" title="文件:se tan02.mp3">se_tan02.mp3</a><br><audio src="https://upload.thwiki.cc/f/f4/se_tan02.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>8</td>
<td><a href="./文件-se_ok00.mp3.md" title="文件:se ok00.mp3">se_ok00.mp3</a><br><audio src="https://upload.thwiki.cc/b/bf/se_ok00.mp3" loop="" controls="" preload="none"></audio></td>
<td>9</td>
<td><a href="./文件-se_cancel00.mp3.md" title="文件:se cancel00.mp3">se_cancel00.mp3</a><br><audio src="https://upload.thwiki.cc/7/7e/se_cancel00.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>10</td>
<td><a href="./文件-se_select00.mp3.md" title="文件:se select00.mp3">se_select00.mp3</a><br><audio src="https://upload.thwiki.cc/2/28/se_select00.mp3" loop="" controls="" preload="none"></audio></td>
<td>11</td>
<td><a href="./文件-se_gun00.mp3.md" title="文件:se gun00.mp3">se_gun00.mp3</a><br><audio src="https://upload.thwiki.cc/1/18/se_gun00.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>12</td>
<td><a href="./文件-se_cat00.mp3.md" title="文件:se cat00.mp3">se_cat00.mp3</a><br><audio src="https://upload.thwiki.cc/8/82/se_cat00.mp3" loop="" controls="" preload="none"></audio></td>
<td>13</td>
<td><a href="./文件-se_lazer00.mp3.md" title="文件:se lazer00.mp3">se_lazer00.mp3</a><br><audio src="https://upload.thwiki.cc/c/cc/se_lazer00.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>14</td>
<td><a href="./文件-se_lazer01.mp3.md" title="文件:se lazer01.mp3">se_lazer01.mp3</a><br><audio src="https://upload.thwiki.cc/5/57/se_lazer01.mp3" loop="" controls="" preload="none"></audio></td>
<td>15</td>
<td><a href="./文件-se_enep01.mp3.md" title="文件:se enep01.mp3">se_enep01.mp3</a><br><audio src="https://upload.thwiki.cc/8/84/se_enep01.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>16</td>
<td><a href="./文件-se_damage00.mp3.md" title="文件:se damage00.mp3">se_damage00.mp3</a><br><audio src="https://upload.thwiki.cc/8/83/se_damage00.mp3" loop="" controls="" preload="none"></audio></td>
<td>17</td>
<td><a href="./文件-se_item00.mp3.md" title="文件:se item00.mp3">se_item00.mp3</a><br><audio src="https://upload.thwiki.cc/7/70/se_item00.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>18</td>
<td><a href="./文件-se_kira00.mp3.md" title="文件:se kira00.mp3">se_kira00.mp3</a><br><audio src="https://upload.thwiki.cc/d/da/se_kira00.mp3" loop="" controls="" preload="none"></audio></td>
<td>19</td>
<td><a href="./文件-se_kira01.mp3.md" title="文件:se kira01.mp3">se_kira01.mp3</a><br><audio src="https://upload.thwiki.cc/0/09/se_kira01.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>20</td>
<td><a href="./文件-se_kira02.mp3.md" title="文件:se kira02.mp3">se_kira02.mp3</a><br><audio src="https://upload.thwiki.cc/4/4f/se_kira02.mp3" loop="" controls="" preload="none"></audio></td>
<td>21</td>
<td><a href="./文件-se_timeout.mp3.md" title="文件:se timeout.mp3">se_timeout.mp3</a><br><audio src="https://upload.thwiki.cc/1/1c/se_timeout.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>22</td>
<td><a href="./文件-se_graze.mp3.md" title="文件:se graze.mp3">se_graze.mp3</a><br><audio src="https://upload.thwiki.cc/9/97/se_graze.mp3" loop="" controls="" preload="none"></audio></td>
<td>23</td>
<td><a href="./文件-se_powerup.mp3.md" title="文件:se powerup.mp3">se_powerup.mp3</a><br><audio src="https://upload.thwiki.cc/3/3b/se_powerup.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>24</td>
<td><a href="./文件-se_pause.mp3.md" title="文件:se pause.mp3">se_pause.mp3</a><br><audio src="https://upload.thwiki.cc/3/3a/se_pause.mp3" loop="" controls="" preload="none"></audio></td>
<td>25</td>
<td><a href="./文件-se_cardget.mp3.md" title="文件:se cardget.mp3">se_cardget.mp3</a><br><audio src="https://upload.thwiki.cc/1/1f/se_cardget.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>26</td>
<td><a href="./文件-se_damage01.mp3.md" title="文件:se damage01.mp3">se_damage01.mp3</a><br><audio src="https://upload.thwiki.cc/4/40/se_damage01.mp3" loop="" controls="" preload="none"></audio></td>
<td>27</td>
<td><a href="./文件-se_timeout2.mp3.md" title="文件:se timeout2.mp3">se_timeout2.mp3</a><br><audio src="https://upload.thwiki.cc/b/bc/se_timeout2.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>28</td>
<td><a href="./文件-se_invalid.mp3.md" title="文件:se invalid.mp3">se_invalid.mp3</a><br><audio src="https://upload.thwiki.cc/b/b3/se_invalid.mp3" loop="" controls="" preload="none"></audio></td>
<td>29</td>
<td><a href="./文件-se_slash.mp3.md" title="文件:se slash.mp3">se_slash.mp3</a><br><audio src="https://upload.thwiki.cc/5/59/se_slash.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>30</td>
<td><a href="./文件-se_ch00.mp3.md" title="文件:se ch00.mp3">se_ch00.mp3</a><br><audio src="https://upload.thwiki.cc/0/05/se_ch00.mp3" loop="" controls="" preload="none"></audio></td>
<td>31</td>
<td><a href="./文件-se_ch01.mp3.md" title="文件:se ch01.mp3">se_ch01.mp3</a><br><audio src="https://upload.thwiki.cc/2/2d/se_ch01.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>32</td>
<td><a href="./文件-se_extend.mp3.md" title="文件:se extend.mp3">se_extend.mp3</a><br><audio src="https://upload.thwiki.cc/9/9d/se_extend.mp3" loop="" controls="" preload="none"></audio></td>
<td>33</td>
<td><a href="./文件-se_cardget.mp3.md" title="文件:se cardget.mp3">se_cardget.mp3</a><br><audio src="https://upload.thwiki.cc/1/1f/se_cardget.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>34</td>
<td><a href="./文件-se_nep00.mp3.md" title="文件:se nep00.mp3">se_nep00.mp3</a><br><audio src="https://upload.thwiki.cc/8/89/se_nep00.mp3" loop="" controls="" preload="none"></audio></td>
<td>35</td>
<td><a href="./文件-se_bonus.mp3.md" title="文件:se bonus.mp3">se_bonus.mp3</a><br><audio src="https://upload.thwiki.cc/a/ae/se_bonus.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>36</td>
<td><a href="./文件-se_bonus2.mp3.md" title="文件:se bonus2.mp3">se_bonus2.mp3</a><br><audio src="https://upload.thwiki.cc/d/d1/se_bonus2.mp3" loop="" controls="" preload="none"></audio></td>
<td>37</td>
<td><a href="./文件-se_enep02.mp3.md" title="文件:se enep02.mp3">se_enep02.mp3</a><br><audio src="https://upload.thwiki.cc/0/08/se_enep02.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>38</td>
<td><a href="./文件-se_lazer02.mp3.md" title="文件:se lazer02.mp3">se_lazer02.mp3</a><br><audio src="https://upload.thwiki.cc/0/03/se_lazer02.mp3" loop="" controls="" preload="none"></audio></td>
<td>39</td>
<td><a href="./文件-se_nodamage.mp3.md" title="文件:se nodamage.mp3">se_nodamage.mp3</a><br><audio src="https://upload.thwiki.cc/d/dd/se_nodamage.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>40</td>
<td><a href="./文件-se_boon00.mp3.md" title="文件:se boon00.mp3">se_boon00.mp3</a><br><audio src="https://upload.thwiki.cc/e/e7/se_boon00.mp3" loop="" controls="" preload="none"></audio></td>
<td>41</td>
<td><a href="./文件-se_don00.mp3.md" title="文件:se don00.mp3">se_don00.mp3</a><br><audio src="https://upload.thwiki.cc/d/da/se_don00.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>42</td>
<td><a href="./文件-se_boon01.mp3.md" title="文件:se boon01.mp3">se_boon01.mp3</a><br><audio src="https://upload.thwiki.cc/e/e1/se_boon01.mp3" loop="" controls="" preload="none"></audio></td>
<td>43</td>
<td><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_ch02.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se ch02.mp3（页面不存在）">se_ch02.mp3</a><br><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_ch02.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se ch02.mp3（页面不存在）">文件:se ch02.mp3</a>
</td></tr>
<tr>
<td>44</td>
<td><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_ch03.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se ch03.mp3（页面不存在）">se_ch03.mp3</a><br><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_ch03.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se ch03.mp3（页面不存在）">文件:se ch03.mp3</a></td>
<td>45</td>
<td><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_extend2.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se extend2.mp3（页面不存在）">se_extend2.mp3</a><br><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_extend2.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se extend2.mp3（页面不存在）">文件:se extend2.mp3</a>
</td></tr>
<tr>
<td>46</td>
<td><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_pin00.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se pin00.mp3（页面不存在）">se_pin00.mp3</a><br><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_pin00.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se pin00.mp3（页面不存在）">文件:se pin00.mp3</a></td>
<td>47</td>
<td><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_pin01.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se pin01.mp3（页面不存在）">se_pin01.mp3</a><br><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_pin01.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se pin01.mp3（页面不存在）">文件:se pin01.mp3</a>
</td></tr>
<tr>
<td>48</td>
<td><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_lgods1.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se lgods1.mp3（页面不存在）">se_lgods1.mp3</a><br><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_lgods1.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se lgods1.mp3（页面不存在）">文件:se lgods1.mp3</a></td>
<td>49</td>
<td><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_lgods2.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se lgods2.mp3（页面不存在）">se_lgods2.mp3</a><br><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_lgods2.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se lgods2.mp3（页面不存在）">文件:se lgods2.mp3</a>
</td></tr>
<tr>
<td>50</td>
<td><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_lgods3.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se lgods3.mp3（页面不存在）">se_lgods3.mp3</a><br><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_lgods3.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se lgods3.mp3（页面不存在）">文件:se lgods3.mp3</a></td>
<td>51</td>
<td><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_lgods4.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se lgods4.mp3（页面不存在）">se_lgods4.mp3</a><br><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_lgods4.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se lgods4.mp3（页面不存在）">文件:se lgods4.mp3</a>
</td></tr>
<tr>
<td>52</td>
<td><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_lgodsget.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se lgodsget.mp3（页面不存在）">se_lgodsget.mp3</a><br><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_lgodsget.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se lgodsget.mp3（页面不存在）">文件:se lgodsget.mp3</a></td>
<td>53</td>
<td><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_msl.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se msl.mp3（页面不存在）">se_msl.mp3</a><br><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_msl.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se msl.mp3（页面不存在）">文件:se msl.mp3</a>
</td></tr>
<tr>
<td>54</td>
<td><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_msl2.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se msl2.mp3（页面不存在）">se_msl2.mp3</a><br><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_msl2.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se msl2.mp3（页面不存在）">文件:se msl2.mp3</a></td>
<td>55</td>
<td><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_pldead01.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se pldead01.mp3（页面不存在）">se_pldead01.mp3</a><br><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_pldead01.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se pldead01.mp3（页面不存在）">文件:se pldead01.mp3</a>
</td></tr>
<tr>
<td>56</td>
<td><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_heal.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se heal.mp3（页面不存在）">se_heal.mp3</a><br><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_heal.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se heal.mp3（页面不存在）">文件:se heal.mp3</a></td>
<td>57</td>
<td><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_msl3.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se msl3.mp3（页面不存在）">se_msl3.mp3</a><br><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_msl3.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se msl3.mp3（页面不存在）">文件:se msl3.mp3</a>
</td></tr>
<tr>
<td>58</td>
<td><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_fault.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se fault.mp3（页面不存在）">se_fault.mp3</a><br><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_fault.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se fault.mp3（页面不存在）">文件:se fault.mp3</a></td>
<td>59</td>
<td><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_noise.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se noise.mp3（页面不存在）">se_noise.mp3</a><br><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_noise.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se noise.mp3（页面不存在）">文件:se noise.mp3</a>
</td></tr>
<tr>
<td>60</td>
<td><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_etbreak.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se etbreak.mp3（页面不存在）">se_etbreak.mp3</a><br><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_etbreak.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se etbreak.mp3（页面不存在）">文件:se etbreak.mp3</a></td>
<td>61</td>
<td><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_tan03.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se tan03.mp3（页面不存在）">se_tan03.mp3</a><br><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_tan03.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se tan03.mp3（页面不存在）">文件:se tan03.mp3</a>
</td></tr>
<tr>
<td>62</td>
<td><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_wolf.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se wolf.mp3（页面不存在）">se_wolf.mp3</a><br><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_wolf.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se wolf.mp3（页面不存在）">文件:se wolf.mp3</a></td>
<td>63</td>
<td><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_bonus4.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se bonus4.mp3（页面不存在）">se_bonus4.mp3</a><br><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_bonus4.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se bonus4.mp3（页面不存在）">文件:se bonus4.mp3</a>
</td></tr>
<tr>
<td>64</td>
<td><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_big.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se big.mp3（页面不存在）">se_big.mp3</a><br><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_big.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se big.mp3（页面不存在）">文件:se big.mp3</a></td>
<td>65</td>
<td><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_item1.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se item1.mp3（页面不存在）">se_item1.mp3</a><br><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_item1.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se item1.mp3（页面不存在）">文件:se item1.mp3</a>
</td></tr>
<tr>
<td>66</td>
<td><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_release.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se release.mp3（页面不存在）">se_release.mp3</a><br><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_release.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se release.mp3（页面不存在）">文件:se release.mp3</a></td>
<td>67</td>
<td><a href="./文件-se_changeitem.mp3.md" title="文件:se changeitem.mp3">se_changeitem.mp3</a><br><audio src="https://upload.thwiki.cc/c/cf/se_changeitem.mp3" loop="" controls="" preload="none"></audio>
</td></tr>
<tr>
<td>68</td>
<td><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_trophy.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se trophy.mp3（页面不存在）">se_trophy.mp3</a><br><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_trophy.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se trophy.mp3（页面不存在）">文件:se trophy.mp3</a></td>
<td>69</td>
<td><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_warpl.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se warpl.mp3（页面不存在）">se_warpl.mp3</a><br><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_warpl.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se warpl.mp3（页面不存在）">文件:se warpl.mp3</a>
</td></tr>
<tr>
<td>70</td>
<td><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_warpr.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se warpr.mp3（页面不存在）">se_warpr.mp3</a><br><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_warpr.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se warpr.mp3（页面不存在）">文件:se warpr.mp3</a></td>
<td>71</td>
<td><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_notice.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se notice.mp3（页面不存在）">se_notice.mp3</a><br><a href="/index.php?title=%E6%96%87%E4%BB%B6:se_notice.mp3&amp;action=edit&amp;redlink=1" class="new" title="文件:se notice.mp3（页面不存在）">文件:se notice.mp3</a>
</td></tr></tbody></table>



### 特殊变量表
  
[-9898] (hld+)舞台上的弹幕数量
  
  
[-9899] (gxs+)如果在成就模式中打开游戏章节则设1,否则设-1
  
  
[-9900] (gxs)是否在hyper模式
  
  
[-9901] (gxs)舞台上的动物灵数
  
  
[-9902] (gxs+)前20帧内的擦弹
  
  
[-9903] (tkz,gxs) tkz中为副机选择,0为 春,1为夏,以此类推;gxs中也为副机
  
  
[-9904] 绀珠传中为miss次数，与9949不同的是该计数不会清零（其他作品暂未测试）
  
  
[-9905] (gzz+)chapter数,由ins_524控制
  
  
[-9906] (gzz+)当单位反转时 (例如使用ins_304进行单位生成时) 为1,否则为0
  
  
[-9907] 未知全局变量 SLM(4BE7D4) HZC中代表符卡练习模式中的符卡序号
  
  
[-9908] 同屏单位数单数不包含还有单位flag.1,16,32的单位
  
  
[-9909] 单位未知参数 SLM(11E8) DZZ 11c4
  
  
[-9910] boss未知参数，同9969 SLM(128c)
  
  
[-9911.0f] boss最终位移的方向，停下后变成0
  
  
[-9912] 文花帖DS中有特别意义，SLM之后固定放弃使用为0
  
  
[-9913] 文花帖DS中为已拍照张数，SLM之后固定放弃使用为0
  
  
[-9914] (SLM以后)该单位的编号(主要在8系ins中使用)
  
  
[-9915.0f] 可供随意使用的全局变量
  
  
[-9916.0f] 可供随意使用的全局变量
  
  
[-9917.0f] 可供随意使用的全局变量
  
  
[-9918.0f] 可供随意使用的全局变量
  
  
[-9919.0f] 可供随意使用的全局变量
  
  
[-9920.0f] 可供随意使用的全局变量
  
  
[-9921.0f] 可供随意使用的全局变量
  
  
[-9922.0f] 可供随意使用的全局变量
  
  
[-9923] 可供随意使用的全局变量
  
  
[-9924] 可供随意使用的全局变量
  
  
[-9925] 可供随意使用的全局变量
  
  
[-9926] 可供随意使用的全局变量
  
  
[-9927] SLM:[4C2194] +74==0且 4DCC30&#160;!=0时 为1，否则0
  
  
[-9928] 文花帖DS中有特别意义，SLM之后固定放弃使用为0
  
  
[-9929] 文花帖DS中有特别意义，SLM之后固定放弃使用为0
  
  
[-9930] 自机当前火力
  
  
[-9931] 已经出现单位数量-1,包含main
  
  
[-9932.0f] 可供随意使用的每个单位自身的局部变量
  
  
[-9933.0f] 可供随意使用的每个单位自身的局部变量
  
  
[-9934.0f] 可供随意使用的每个单位自身的局部变量
  
  
[-9935.0f] 可供随意使用的每个单位自身的局部变量
  
  
[-9936.0f] BOSS的局部变量
  
  
[-9937.0f] BOSS的局部变量
  
  
[-9938.0f] BOSS的局部变量
  
  
[-9939.0f] BOSS的局部变量
  
  
[-9940]	   BOSS的局部变量
  
  
[-9941]	   BOSS的局部变量
  
  
[-9942]    BOSS的局部变量
  
  
[-9943]    BOSS的局部变量
  
  
[-9944.0f] =单位至自机的距离
  
  
[-9945] = 机体序号，0=灵梦a
  
  
[-9946] = 同屏单位数,由于隐藏着main和mapleenemy,所以始终比可见的单位数量多出来2个
  
  
[-9947] = 判断上1符卡是否收取，收则是1
  
  
[-9948] = 已丢的b的数量
  
  
[-9949] = 已miss数，与9904不同的是每个章节结束时该值会重置为0
  
  
[-9950] = 当难度为L时，为1。否则为0
  
  
[-9951] = 当难度为H时，为1。否则为0
  
  
[-9952] = 当难度为N时，为1。否则为0
  
  
[-9953] = 当难度为E时，为1。否则为0
  
  
[-9954] =单位当前血量
  
  
单位坐标和速度拥有最终，目前，和相对 三种参考 移动相关ins
  
  
[-9955.0f] =单位相对坐标至自机位置的方向
  
  
[-9956.0f] =单位绝对至自机位置的方向
  
  
[-9957] = 1
  
  
[-9958.0f] =单位最终位移的方向，停下后变成0
  
  
[-9959] 难度,0123分别为ENHL
  
  
[-9960]Rank
  
  
[-9961]未知  （地址1120）
  
  
[-9962.0f]当前bossy坐标，
  
  
[-9963.0f] 当前bossx坐标，
  
  
[-9964.0f] 自机y坐标，与9990完全相同 
  
  
[-9965.0f] 自机x坐标，与9991完全相同 
  
  
[-9966.0f] 单位相对曲线运动时的运动半径
  
  
[-9967.0f] 单位绝对曲线运动时的运动半径
  
  
[-9968.0f] 单位相对速度大小  
  
  
[-9969.0f] 单位绝对速度大小
  
  
[-9970.0f] 单位相对移动速度的方向
  
  
[-9971.0f] 单位绝对移动速度的方向，
  
  
[-9972.0f]=单位相对坐标y 与9992完全相同
  
  
[-9973.0f]=单位相对坐标x 与9993完全相同
  
  
[-9974.0f]=单位绝对坐标的y值,与9994完全相同
  
  
[-9975.0f]=单位绝对坐标的x值,与9995完全相同
  
  
[-9976.0f]=单位最终坐标的y值,与9996完全相同
  
  
[-9977.0f]=单位最终坐标的x值,与9997完全相同
  
  
以下8个变量在创建子单位的时候，子单位将继承
并且某些特殊函数会收这写变量影响
  
  
[-9978.0f] 每个单位自身的局部变量 
  
  
[-9979.0f] 每个单位自身的局部变量 
  
  
[-9980.0f] 每个单位自身的局部变量 
  
  
[-9981.0f] 每个单位自身的局部变量 
  
  
[-9982]	   每个单位自身的局部变量 
  
  
[-9983]	   每个单位自身的局部变量 
  
  
[-9984]    每个单位自身的局部变量 
  
  
[-9985]    每个单位自身的局部变量
  
  
[-9986]    判定是否全避时使用，若不为0则是全避，实际可能有其他含义,经测试并非boss血量  
  
  
[-9987.0f]=-1.0至1.0之间的随机浮点数
  
  
[-9988]    已经过的时间 
  
  
[-9989.0f]=单位最终坐标至自机位置的方向
  
  
[-9990.0f]= 自机y坐标  
  
  
[-9991.0f]= 自机x坐标   
  
  
[-9992.0f]=单位相对坐标y  
  
  
[-9993.0f]=单位相对坐标x  
  
  
[-9994.0f]=单位绝对坐标的y值  
  
  
[-9995.0f]=单位绝对坐标的x值 
  
  
[-9996.0f]=单位最终坐标的y值, 
  
  
[-9997.0f]=单位最终坐标的x值，
  
  
[-9998.0f]=-π至π之间的随机浮点数
  
  
[-9999.0f]=0至 1.0之间的随机浮点数
  
  
[-10000]=随机整数，范围非常大
  





---

此文档由 [THBWiki-Markdown-Builder](https://github.com/Delsin-Yu/THBWiki-Markdown-Builder) 构建。

文档中的所有内容除特殊注明外，均在 [**知识共享(Creative Commons) 署名-非商业性使用-相同方式共享 3.0 协议**](https://creativecommons.org/licenses/by-sa/3.0/deed.zh-hans) 下提供，附加条款亦可能应用。

引用类型与其他类型作品版权归原作者所有，如有作者授权则遵照授权协议使用。

详细请查阅 [THBWiki：免责声明](https://thbwiki.cc/THBWiki:%E5%85%8D%E8%B4%A3%E5%A3%B0%E6%98%8E)。

