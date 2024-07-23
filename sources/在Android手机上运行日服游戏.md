# 在Android手机上运行日服游戏

<!-- source html: G:\repos\THBWiki-Markdown-Builder\THBWikiMarkdown\Temp\main\a\af\ns0%3A%E5%9C%A8Android%E6%89%8B%E6%9C%BA%E4%B8%8A%E8%BF%90%E8%A1%8C%E6%97%A5%E6%9C%8D%E6%B8%B8%E6%88%8F.html -->

授权商业二次创作手机游戏 | 资料

本页是整理东方Project  
 **相关资料** 的词条
  
从2019年开始，东方官方逐渐放开了对于 **商业二次创作手机游戏** 的授权。到现在为止，在智能手机平台上已经有六款获得了授权，并处于开服运营状态的商业手游，分别是 ~~[东方CB](./东方大炮弹.md)~~ （已于2020年10月14日停服）、[东方LW](./东方LostWord.md)、 ~~[东方DD](./东方Dungeon_Dive.md)~~ （将于2024年5月15日停服）、 ~~[东方DK](./东方弹幕神乐.md)~~ （已于2022年10月28日停服）、[东方AR](./东方ArcadiaRecord.md)和[东方GL](./东方幻想Eclipse.md)。  

然而，这些手游大都只在日本地区运营，对于国内的玩家而言，它们的本地化程度等于零。因此想要玩到这些手机游戏可能会有些难度，而其中语言的隔阂则只是一小部分问题。  

这篇知识文章介绍如何在Android智能手机上运行日服手机游戏并实现相关功能。  

  


## 目录

- [1 Google Play 组件](#Google_Play_组件)
- [2 Google Play 商店](#Google_Play_商店)
- [3 Google Pay](#Google_Pay)
- [4 Android模拟器](#Android模拟器)
- [5 引继](#引继)





## Google Play 组件
  
Google Play组件是国外Android手机出厂ROM中自带的系统组件，会连接谷歌的服务器自动更新。而在国内的Android手机上，由于用得到这一功能的人较少，并且它在手机后台反复重试连接谷歌服务会导致严重的耗电问题，大部分国产手机厂商都会选择不在自己的出厂ROM中内置该服务。而如果我们想在手机上正常运行外服手游和一些国外APP，则需要将这一环境装回来。  

  
  
在较新版本的Android系统上，Google Play组件包含以下内容：  

Google Services Framework（Google 服务框架）  

Google Play Services（Google Play 服务）  

Google Play Store（Google Play 商店）  

  
  
运行一些外服游戏时，可能还需要安装以下内容：  

Google Play Games（Google Play 游戏）  

  
  
而想要氪金的时候，还需要安装以下内容：  

Google Pay（Google Pay）  

  
  
需要注意的是， **不同Android手机所需要的Google Play组件版本都是不同的** ，安装包不能通用。  

确定自己的手机所需要的具体是哪个版本的Google Play组件，由以下三个因素决定：  

  

-  **处理器架构** （CPU Architecture）

  
对于安卓手机，现在常见的SoC架构有四种，分别是arm (armeabi, armeabi-v7a)，arm64 (arm64, arm64-v8a)，x86，x86_64 (x64)。具体由其指令集决定，详见[List of CPU architectures](https://en.wikipedia.org/wiki/List_of_CPU_architectures)。  

其中，最常见且较为现代的是arm64-v8a，绝大部分高通骁龙，华为海思麒麟，联发科，以及三星猎户座的较新处理器型号都是属于该架构。  

armeabi-v7a则是较老的手机处理器架构，一些旧手机，如某些联发科SoC的山寨手机可能属于该架构。  

x86与x86_64则是英特尔和AMD的处理器架构，是PC上最常使用的，而由于功耗等问题在手机上则相当罕见。不少应用完全没有针对其做任何适配。  

arm64-v8a处理器的手机能够向下兼容为armeabi-v7a开发的应用，同样x86_64处理器的手机能够向下兼容为x86开发的应用。但这样显然会无法发挥其最大性能，并可能会导致一些其他的问题。  

用户能够在手机系统设置中找到自己的处理器型号，而后可以网上搜索该型号以获知其属于哪一个架构。实在不确定时，arm64-v8a往往会是个正确的选择。  

谷歌公司有计划未来的Android不再提供32位的版本，彻底结束对于这类架构处理器的支持。此外，微软也宣布了Windows 10 2004会是32位Windows操作系统的最后一个主要功能更新版本。  

  

-  **最低Android版本** （Minimum Android Version）

  
用户能够在手机系统设置中看到自己的安卓系统版本，注意需要和手机厂商定制ROM的版本区分开来。Google Play 组件提供支持的最低Android版本是Android 4.1，而现在的不少应用都会要求Android 6.0或更高的版本。  

Android版本历史详见[Android version history](https://en.wikipedia.org/wiki/Android_version_history)。  

  

-  **屏幕DPI** （Screen DPI）

  
DPI（Dots Per Inch），是手机屏幕像素密度的衡量指标，单位是像素/英寸。  

从技术角度考虑，当涉及屏幕的像素密度时，更准确的术语应该是PPI（Pixels Per Inch），但DPI仍然是更为广泛使用的叫法。对于作为非专业用户的我们而言，这两者的含义大致是相同的，没必要做仔细区分。  

用户可以先访问自己手机厂商官网页面上有关的规格参数，或搜索手机型号以获知该信息；如未能找到，屏幕的DPI数据也可以由计算得出，非常简单。  

  
  
屏幕DPI计算公式：
  
  
[math]\displaystyle{ DPI = {\sqrt{X^2+Y^2} \over Z} }[/math]
  
  
其中，X与Y分别代表屏幕长和宽上的像素数，Z代表屏幕大小（英寸）。这些信息都可以很轻松地查找到。  

例如，Google Pixel 4 XL的屏幕分辨率是3200*1800像素，屏幕大小是6.3英寸，计算得到它的DPI约等于583，相当高；小米10 Pro的屏幕分辨率是2340*1080像素，屏幕大小是6.67英寸，计算得到它的DPI约等于386。当然，除根据计算得来的这个数字以外还有等效PPI等更复杂的概念，在此不多作介绍。  

2010年，时任苹果公司CEO史蒂夫·乔布斯在iPhone 4发布会上说：“当你所拿的东西距离你10-12英寸时，它的分辨率只要达到300ppi这个‘神奇数字’以上，你的视网膜就无法分辨出像素点了。”后来这个数字被精确定义到了326。而随着技术的不断发展，现在手机屏幕的DPI也已经大都超过了这个数字。  

选择自己所需要的APK时，应当选择尽量接近或略微超过手机实际DPI的安装包；如果不能完全匹配，则可以选择DPI更高的安装包。或者，部分应用会有“nodpi”的通用版本，所有用户都能正常使用。  

  
  
确认了这三个信息后，可以进入下一个步骤：寻找合适的Google Play 组件安装包。  

为了图省事，不少人可能会选择使用各种第三方的“谷歌安装器”进行安装。这一方法同样可行，虽然并不十分推荐。  

这里则以网站apkmirror提供的APK下载链接为例：  

[Google Services Framework](https://www.apkmirror.com/apk/google-inc/google-services-framework/)  

[Google Play Services](https://www.apkmirror.com/apk/google-inc/google-play-services/)  

[Google Play Store](https://www.apkmirror.com/apk/google-inc/google-play-store/)  

[Google Play Games](https://www.apkmirror.com/apk/google-inc/google-play-games/)  

[Google Pay](https://www.apkmirror.com/apk/google-inc/google-pay/)（需要翻墙）  

Android TV是适合Android电视使用的版本，Wear OS是适合Wear OS手表使用的版本。没有后缀的则是适合普通安卓手机的版本。  

  
  
这里还有一个简单的判断方法，谷歌对于多版本的应用会有一个统一的六位数编号，软件更新后这一编号不会发生变化。例如，对于Google Play Services，具体如下：  

  


<table>
<tbody><tr>
<td>编号</td>
<td>Android版本</td>
<td>架构</td>
<td>DPI
</td></tr>
<tr>
<td>000300</td>
<td>Android 4.1+</td>
<td>armeabi-v7a</td>
<td>nodpi
</td></tr>
<tr>
<td>000302</td>
<td>Android 4.1+</td>
<td>armeabi-v7a</td>
<td>160dpi
</td></tr>
<tr>
<td>000304</td>
<td>Android 4.1+</td>
<td>armeabi-v7a</td>
<td>240dpi
</td></tr>
<tr>
<td>000306</td>
<td>Android 4.1+</td>
<td>armeabi-v7a</td>
<td>320dpi
</td></tr>
<tr>
<td>000308</td>
<td>Android 4.1+</td>
<td>armeabi-v7a</td>
<td>480dpi
</td></tr>
<tr>
<td>020300</td>
<td>Android 5.0+</td>
<td>armeabi-v7a</td>
<td>nodpi
</td></tr>
<tr>
<td>020302</td>
<td>Android 5.0+</td>
<td>armeabi-v7a</td>
<td>160dpi
</td></tr>
<tr>
<td>020304</td>
<td>Android 5.0+</td>
<td>armeabi-v7a</td>
<td>240dpi
</td></tr>
<tr>
<td>020306</td>
<td>Android 5.0+</td>
<td>armeabi-v7a</td>
<td>320dpi
</td></tr>
<tr>
<td>020308</td>
<td>Android 5.0+</td>
<td>armeabi-v7a</td>
<td>480dpi
</td></tr>
<tr>
<td>040300</td>
<td>Android 6.0+</td>
<td>armeabi-v7a</td>
<td>nodpi
</td></tr>
<tr>
<td>040302</td>
<td>Android 6.0+</td>
<td>armeabi-v7a</td>
<td>160dpi
</td></tr>
<tr>
<td>040304</td>
<td>Android 6.0+</td>
<td>armeabi-v7a</td>
<td>240dpi
</td></tr>
<tr>
<td>040306</td>
<td>Android 6.0+</td>
<td>armeabi-v7a</td>
<td>320dpi
</td></tr>
<tr>
<td>040308</td>
<td>Android 6.0+</td>
<td>armeabi-v7a</td>
<td>480dpi
</td></tr>
<tr>
<td>110300</td>
<td>Android 8.1+</td>
<td>armeabi-v7a</td>
<td>nodpi
</td></tr>
<tr>
<td>110302</td>
<td>Android 8.1+</td>
<td>armeabi-v7a</td>
<td>160dpi
</td></tr>
<tr>
<td>110304</td>
<td>Android 8.1+</td>
<td>armeabi-v7a</td>
<td>240dpi
</td></tr>
<tr>
<td>110306</td>
<td>Android 8.1+</td>
<td>armeabi-v7a</td>
<td>320dpi
</td></tr>
<tr>
<td>110308</td>
<td>Android 8.1+</td>
<td>armeabi-v7a</td>
<td>480dpi
</td></tr>
<tr>
<td>100300</td>
<td>Android 9.0+</td>
<td>armeabi-v7a</td>
<td>nodpi
</td></tr>
<tr>
<td>100302</td>
<td>Android 9.0+</td>
<td>armeabi-v7a</td>
<td>160dpi
</td></tr>
<tr>
<td>100304</td>
<td>Android 9.0+</td>
<td>armeabi-v7a</td>
<td>240dpi
</td></tr>
<tr>
<td>100306</td>
<td>Android 9.0+</td>
<td>armeabi-v7a</td>
<td>320dpi
</td></tr>
<tr>
<td>100308</td>
<td>Android 9.0+</td>
<td>armeabi-v7a</td>
<td>480dpi
</td></tr>
<tr>
<td>120300</td>
<td>Android 10+</td>
<td>armeabi-v7a</td>
<td>nodpi
</td></tr>
<tr>
<td>120302</td>
<td>Android 10+</td>
<td>armeabi-v7a</td>
<td>160dpi
</td></tr>
<tr>
<td>120304</td>
<td>Android 10+</td>
<td>armeabi-v7a</td>
<td>240dpi
</td></tr>
<tr>
<td>120306</td>
<td>Android 10+</td>
<td>armeabi-v7a</td>
<td>320dpi
</td></tr>
<tr>
<td>120308</td>
<td>Android 10+</td>
<td>armeabi-v7a</td>
<td>480dpi
</td></tr>
<tr>
<td>150300</td>
<td>Android 11+</td>
<td>armeabi-v7a</td>
<td>nodpi
</td></tr>
<tr>
<td>150302</td>
<td>Android 11+</td>
<td>armeabi-v7a</td>
<td>160dpi
</td></tr>
<tr>
<td>150304</td>
<td>Android 11+</td>
<td>armeabi-v7a</td>
<td>240dpi
</td></tr>
<tr>
<td>150306</td>
<td>Android 11+</td>
<td>armeabi-v7a</td>
<td>320dpi
</td></tr>
<tr>
<td>150308</td>
<td>Android 11+</td>
<td>armeabi-v7a</td>
<td>480dpi
</td></tr>
<tr>
<td>190300</td>
<td>Android 12+</td>
<td>armeabi-v7a</td>
<td>nodpi
</td></tr>
<tr>
<td>190302</td>
<td>Android 12+</td>
<td>armeabi-v7a</td>
<td>160dpi
</td></tr>
<tr>
<td>190304</td>
<td>Android 12+</td>
<td>armeabi-v7a</td>
<td>240dpi
</td></tr>
<tr>
<td>190306</td>
<td>Android 12+</td>
<td>armeabi-v7a</td>
<td>320dpi
</td></tr>
<tr>
<td>190308</td>
<td>Android 12+</td>
<td>armeabi-v7a</td>
<td>480dpi
</td></tr>
<tr>
<td>000400</td>
<td>Android 4.1+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>nodpi
</td></tr>
<tr>
<td>000402</td>
<td>Android 4.1+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>160dpi
</td></tr>
<tr>
<td>000404</td>
<td>Android 4.1+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>240dpi
</td></tr>
<tr>
<td>000406</td>
<td>Android 4.1+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>320dpi
</td></tr>
<tr>
<td>000408</td>
<td>Android 4.1+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>480dpi
</td></tr>
<tr>
<td>020400</td>
<td>Android 5.0+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>nodpi
</td></tr>
<tr>
<td>020402</td>
<td>Android 5.0+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>160dpi
</td></tr>
<tr>
<td>020404</td>
<td>Android 5.0+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>240dpi
</td></tr>
<tr>
<td>020406</td>
<td>Android 5.0+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>320dpi
</td></tr>
<tr>
<td>020408</td>
<td>Android 5.0+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>480dpi
</td></tr>
<tr>
<td>040400</td>
<td>Android 6.0+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>nodpi
</td></tr>
<tr>
<td>040402</td>
<td>Android 6.0+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>160dpi
</td></tr>
<tr>
<td>040404</td>
<td>Android 6.0+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>240dpi
</td></tr>
<tr>
<td>040406</td>
<td>Android 6.0+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>320dpi
</td></tr>
<tr>
<td>040408</td>
<td>Android 6.0+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>480dpi
</td></tr>
<tr>
<td>110400</td>
<td>Android 8.1+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>nodpi
</td></tr>
<tr>
<td>110402</td>
<td>Android 8.1+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>160dpi
</td></tr>
<tr>
<td>110404</td>
<td>Android 8.1+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>240dpi
</td></tr>
<tr>
<td>110406</td>
<td>Android 8.1+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>320dpi
</td></tr>
<tr>
<td>110408</td>
<td>Android 8.1+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>480dpi
</td></tr>
<tr>
<td>100400</td>
<td>Android 9.0+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>nodpi
</td></tr>
<tr>
<td>100402</td>
<td>Android 9.0+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>160dpi
</td></tr>
<tr>
<td>100404</td>
<td>Android 9.0+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>240dpi
</td></tr>
<tr>
<td>100406</td>
<td>Android 9.0+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>320dpi
</td></tr>
<tr>
<td>100408</td>
<td>Android 9.0+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>480dpi
</td></tr>
<tr>
<td>120400</td>
<td>Android 10+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>nodpi
</td></tr>
<tr>
<td>120402</td>
<td>Android 10+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>160dpi
</td></tr>
<tr>
<td>120404</td>
<td>Android 10+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>240dpi
</td></tr>
<tr>
<td>120406</td>
<td>Android 10+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>320dpi
</td></tr>
<tr>
<td>120408</td>
<td>Android 10+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>480dpi
</td></tr>
<tr>
<td>150400</td>
<td>Android 11+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>nodpi
</td></tr>
<tr>
<td>150402</td>
<td>Android 11+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>160dpi
</td></tr>
<tr>
<td>150404</td>
<td>Android 11+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>240dpi
</td></tr>
<tr>
<td>150406</td>
<td>Android 11+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>320dpi
</td></tr>
<tr>
<td>150408</td>
<td>Android 11+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>480dpi
</td></tr>
<tr>
<td>190400</td>
<td>Android 12+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>nodpi
</td></tr>
<tr>
<td>190402</td>
<td>Android 12+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>160dpi
</td></tr>
<tr>
<td>190404</td>
<td>Android 12+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>240dpi
</td></tr>
<tr>
<td>190406</td>
<td>Android 12+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>320dpi
</td></tr>
<tr>
<td>190408</td>
<td>Android 12+</td>
<td>arm64-v8a + armeabi-v7a</td>
<td>480dpi
</td></tr>
<tr>
<td>000700</td>
<td>Android 4.1+</td>
<td>x86</td>
<td>nodpi
</td></tr>
<tr>
<td>020700</td>
<td>Android 5.0+</td>
<td>x86</td>
<td>nodpi
</td></tr>
<tr>
<td>040700</td>
<td>Android 6.0+</td>
<td>x86</td>
<td>nodpi
</td></tr>
<tr>
<td>110700</td>
<td>Android 8.1+</td>
<td>x86</td>
<td>nodpi
</td></tr>
<tr>
<td>100700</td>
<td>Android 9.0+</td>
<td>x86</td>
<td>nodpi
</td></tr>
<tr>
<td>120700</td>
<td>Android 10+</td>
<td>x86</td>
<td>nodpi
</td></tr>
<tr>
<td>150700</td>
<td>Android 11+</td>
<td>x86</td>
<td>nodpi
</td></tr>
<tr>
<td>190700</td>
<td>Android 12+</td>
<td>x86</td>
<td>nodpi
</td></tr>
<tr>
<td>000800</td>
<td>Android 4.1+</td>
<td>x86 + x86_64</td>
<td>nodpi
</td></tr>
<tr>
<td>020800</td>
<td>Android 5.0+</td>
<td>x86 + x86_64</td>
<td>nodpi
</td></tr>
<tr>
<td>040800</td>
<td>Android 6.0+</td>
<td>x86 + x86_64</td>
<td>nodpi
</td></tr>
<tr>
<td>110800</td>
<td>Android 8.1+</td>
<td>x86 + x86_64</td>
<td>nodpi
</td></tr>
<tr>
<td>100800</td>
<td>Android 9.0+</td>
<td>x86 + x86_64</td>
<td>nodpi
</td></tr>
<tr>
<td>120800</td>
<td>Android 10+</td>
<td>x86 + x86_64</td>
<td>nodpi
</td></tr>
<tr>
<td>150800</td>
<td>Android 11+</td>
<td>x86 + x86_64</td>
<td>nodpi
</td></tr>
<tr>
<td>190800</td>
<td>Android 12+</td>
<td>x86 + x86_64</td>
<td>nodpi
</td></tr>
</tbody></table>


  
某些国产手机ROM可能对Android系统底层做了深度修改，或有意阻止了用户使用谷歌服务，即便在安装了合适的Google Play组件后此服务也无法正常运行。这种情况下只能通过解锁BootLoader并刷入第三方ROM包的方式解决；或安装虚拟空间类软件，在有框架的"虚拟机"中运行。（注意，此方法有一定风险，可能会导致谷歌封号，或者是虚拟空间本身不干净，存在窃取数据等行为，使用时还需注意）  

  


## Google Play 商店
  
Google Play Store是Android系统唯一真正意义上的官方应用商店，地位相当于苹果App Store对于iOS，提供了应用下载更新和正版付费应用购买等服务。此外，部分通过[东方同人音乐流通](./东方同人音乐流通.md)发行了的东方同人音乐也可以在这里试听和购买。使用Google Play 商店需要登录Google账号。  

而对于一个外服手游来说，它们在安卓端上架即意味着登陆了Play 商店。但有些时候我们会遇到这样的问题：某个应用或游戏已经登陆了Play 商店，自己却就是怎么也搜索不到。  

会发生这种情况，一般是由于谷歌允许应用开发者自由地选择向哪些用户显示或不显示自己开发的APP，而他们决定了向你的设备隐藏该应用。应用是否显示通常取决于以下因素：  

  

-  **应用已锁区** 

  
这是最常见的一种情况，比如[东方CB](./东方大炮弹.md)和[东方LW](./东方LostWord.md)两款手游在Google Play Store上全部锁在了日区，只有登录了日区Google Play账号的用户能够看到。  

  

-  **应用处于内部测试状态** 

  
处于内测阶段的APP只有受开发者邀请的用户能够看见。可以从开发者那里找到内测邀请链接，注册后即可加入内测。  

  

-  **设备不兼容或不满足应用运行的最低要求** 

  
开发者没有对你的手机架构做适配，或者安卓版本太低，都可能导致这一情况。  

  

-  **设备未通过谷歌Play保护机制（Google Play Protect）认证或谷歌SafetyNet验证** 

- [](./文件-SafetyNet_Sample.jpg.md)某个SafetyNet验证测试样本

  
这是一种较为复杂的问题，Play保护机制与SafetyNet验证是谷歌的一组安全验证相关服务。谷歌的描述是`
设备制造商会与 Google 合作，以证明已安装 Google 应用的 Android 设备安全无虞，且能够正常运行应用。要获得 Play 保护机制认证，设备必须通过 Android 兼容性测试。`
；一些国产与测试版本的手机ROM，或系统被修改后会无法通过该验证。该功能常用于对版权问题有高度要求的应用，如Netflix。详见[Google Play Protect](https://www.android.com/certified)，[使用SafetyNet抵御安全威胁](https://developer.android.com/training/safetynet)。  

遇到这种情况并非无法破解，比如在解锁BootLoader并Root（或通过fastboot线刷第三方rec等）后使用某些Magisk模块能够通过SafetyNet验证中的ctsProfile验证。这一操作具体实现难度较高，且不适合普通用户进行，因此不多做介绍。  

对于这部分内容感兴趣的用户详细可以参考[少数派的这篇文章](https://sspai.com/post/55536)。  

  

- 对于使用模块或Xposed框架强行通过验证的方法仍不完美，可能出现显示已通过认证，但实际上仍然不能正常运行的情况。如果为了图方便（一般只是为了打外国游戏的普通用户可能不了解刷机之类的方法），最好还是购买非国行的手机，非国行基本上都有谷歌。
- 如果刷了机，修改了系统，那么可以在 [谷歌网站](https://www.google.com/android/uncertified/)（需要翻墙）上注册自己系统的Android ID（可通过ADB命令行或Devcheck等软件查看），这样的话 **也许** 会通过验证。
- 要检测自己的手机是否因为撞了SafetyNet而搜不到要找到APP，可以通过Play商店-&gt;设置-&gt;关于-&gt;Play保护机制认证中查看，或在手机上通过超链接打开受保护应用程序的商店界面（如[Netfilx](https://play.google.com/store/apps/details?id=com.netflix.mediaclient)（需要翻墙），如果看到“<font color="#7F0000">⚠您的设备与此版本不兼容。</font>”的红字，除了1%的真不兼容的情况外，剩下的99%则一定是未通过SafetyNet。如果提示的是“<font color="#7F0000">⚠此商品无法在您所在国家/地区购买或下载。</font>”，则是区域问题。

  
  

那么对于大多数的一般用户而言，遇到搜不到一些应用的情况，只需要换个区就可以了。以下介绍如何在Google Play Store上将自己账号的地区更改为日本。  

  

-  **此前没有在Play 商店进行过交易** 

  
将自己的代理IP地址更换到日本，清除Play 商店的数据后重新打开即可。
  

-  **此前已在Play 商店的其他地区进行过交易** 

  
第一次交易完成后，你的账号即会和第一次交易时的IP或填写的账单地址所在的地区绑定；即便将来更换代理IP地址到其他国家，也能并且只能显示原先地区的应用。这种情况下换区需要绑定一个新的交易方式。  

将自己的代理IP地址更换到日本后，在Google Play Store中依次选择账号→偏好设置→国家/地区和个人资料→切换到日本的Play商店，并按照页面提示绑定交易方式。
  

- [](./文件-切换到日本的Play商店.jpg.md)切换到美国的Play商店，反之亦然

  
支持绑定的交易方式包括账单地址填写到了日本（可以随便写，不一定得是真实地址）的信用卡与借记卡（可以是VISA、MasterCard、American Express、JCB等单卡标的外币卡，基本上不支持中国银联），以及日区的PayPal账号。我用虚拟卡也没问题，卡头是美国的，绑的日区，没氪过日元，但应该没问题。  

绑定成功需要进行一笔自动扣款（约1~2美元）以确认支付方式真实有效，扣款成功后这笔钱会自动退回，无需人工操作。  

每365天的时间内只能进行一次换区的操作。  

  
  
除此之外，还有一些问题可能会导致无法换区；这种情况下最简单的解决办法是在其他区重新注册一个谷歌账号。
  


## Google Pay
  
图省事的话可以直接在某购物平台寻找代充服务，虽然并不十分推荐这么做。  

不像我们通常使用支付宝和微信，外服Android手机游戏进行氪金购买时都会调用Google Pay的API进行交易。而Google Pay可以直接绑定银行卡，或者可以绑定PayPal，而PayPal再绑定银行卡进行扣款。  

上文中提到了，可能不少人并没有Google Pay所支持绑定的银行卡。这里可以使用一个简单的方法替代，即在任意购物平台上搜索“Play充值”等关键词购买Google Play礼品卡。礼品卡兑换后，它的面值会直接进入你的Play账户余额。  

这里同时需要注意，和类似Steam的充值码不仅不锁区还能自动按汇率进行兑换不同，Google Play的礼品卡是锁区的；日区的账号只能兑换日区的Google Play充值码，不要买错区了。换区方式见上文内容；换区后，账号原先所在地区的Play账户余额会被冻结。但余额并不会消失，如果未来将地区换回则可以解冻并继续使用。  

购买礼品卡的同时需要注意谨防上当受骗。  

  

- 自2021年6月起，谷歌公司对于礼品卡充值采取了更严格的限制措施。现除了要求礼品卡货币与账号所在区一致外，用户的IP地址同样需要在目标地区，并且封杀了部分常见的代理IP，购买礼品卡充值时需要更加谨慎。


## Android模拟器
  
在电脑上玩Android手游时会需要用到模拟器。这里推荐唯一一个受Android官方（谷歌公司）认可，运行在PC上的Android模拟器，[Android Studio](https://developer.android.com/studio)。  

Android Studio 是基于 IntelliJ IDEA 且适用于开发 Android 应用的官方集成开发环境 (IDE)。除了 IntelliJ 强大的代码编辑器和开发者工具，Android Studio 还提供了更多可提高 Android 应用编译效率的功能。  

Android Studio所支持的PC操作系统包括Windows，macOS，多种不同发行版的Linux以及Chrome OS。  

Android 模拟器则是Android Studio的可选功能之一。相比其他第三方安卓模拟器，具有高度可自定义，支持通过控制台进行ADB调试等优点。  

  

- [](./文件-studio-homepage-hero.jpg.md)- [](./文件-avd-coldboot-callout_2x.png.md)- [](./文件-snapshots-screenshot_2x.png.md)

  
详见[在 Android 模拟器上运行应用](https://developer.android.com/studio/run/emulator)。  

  


## 引继
  
国内手游常用的登陆方式是使用邮箱或手机号注册账号后登陆，以及第三方账号授权登录；对于日服手游，常用的同样有第三方账号授权登录（连携），除此之外还有引继的方式。  

引继的原理类似用户名和密码，但可以在开始游戏后执行，并且不需要使用邮箱或手机号等作为密保工具注册。进入游戏后，转到设置→引继，输入密码并确认，游戏会生成一个随机的“引继码”，这样就算是引继成功了。引继码相当于玩家的用户名，需要将其记下。  

更换设备或清除游戏数据后，在进入游戏前的初始页面找到“引继”选项，输入自己的引继码和对应的密码以继承存档。  

如果没有进行引继或绑定第三方登录账号，清除数据或卸载软件后玩家的游戏存档可能将永远无法找回。  

  





---

此文档由 [THBWiki-Markdown-Builder](https://github.com/Delsin-Yu/THBWiki-Markdown-Builder) 构建。

文档中的所有内容除特殊注明外，均在 [**知识共享(Creative Commons) 署名-非商业性使用-相同方式共享 3.0 协议**](https://creativecommons.org/licenses/by-sa/3.0/deed.zh-hans) 下提供，附加条款亦可能应用。

引用类型与其他类型作品版权归原作者所有，如有作者授权则遵照授权协议使用。

详细请查阅 [THBWiki：免责声明](https://thbwiki.cc/THBWiki:%E5%85%8D%E8%B4%A3%E5%A3%B0%E6%98%8E)。

