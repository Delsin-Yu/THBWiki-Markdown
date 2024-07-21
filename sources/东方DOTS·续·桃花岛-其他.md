# 东方DOTS·续·桃花岛/其他

<!-- source html: G:\repos\THBWiki-Markdown-Builder\THBWikiMarkdown\Temp\main\f\f8\ns0%3A%E4%B8%9C%E6%96%B9DOTS%C2%B7%E7%BB%AD%C2%B7%E6%A1%83%E8%8A%B1%E5%B2%9B%2F%E5%85%B6%E4%BB%96.html -->

东方DOTS玩家社群

##### 人人模式聊天指令

<table>
<caption>普通
</caption>
<tbody><tr>
<td>-urd</td>
<td>投降（15分钟才能使用）
</td></tr>
<tr>
<td>-rank</td>
<td>查询天梯分
</td></tr>
<tr>
<td>-bp</td>
<td>在队伍界面中输入可选禁英雄
</td></tr>
<tr>
<td>-rankdc</td>
<td>在队伍界面中输入可禁用天梯分（rank）及其他模式
</td></tr></tbody></table>



<table>
<caption>天梯分排名及胜率查询
</caption>
<tbody><tr>
<td><a rel="nofollow" class="external text" href="https://thd2.cc/datas/heroranklist.php?o=3&amp;/">英雄胜率查询</a></td>
<td>所有英雄的总出场及胜率；在网址末端输入?sid=玩家的steamUID，可查询该玩家的英雄出场及英雄胜率
</td></tr>
<tr>
<td><a rel="nofollow" class="external text" href="https://thd2.cc/api/ranklist.php?p=1/">天梯分排名</a></td>
<td>所有玩家的排名
</td></tr></tbody></table>



<table>
<caption>单机代码（在人人模式专属地图生效）
</caption>
<tbody><tr>
<td>--lvlup 数字</td>
<td>提升自己的英雄等级
</td></tr>
<tr>
<td>-lvlmax</td>
<td>除天赋外自己英雄满级满加点
</td></tr>
<tr>
<td>-levelbots 数字</td>
<td>提升全图的AI机器人等级
</td></tr>
<tr>
<td>-gold 数字</td>
<td>给予自己不可靠金钱
</td></tr>
<tr>
<td>-wtf</td>
<td>无限技能
</td></tr>
<tr>
<td>-unwtf</td>
<td>关闭无限技能
</td></tr>
<tr>
<td>-allvision</td>
<td>双方视野
</td></tr>
<tr>
<td>-normalvision</td>
<td>正常己方视野
</td></tr>
<tr>
<td>-createhero 英雄代码</td>
<td>创建一个英雄（英雄代码可在内部名称页面查询）
</td></tr>
<tr>
<td>-createhero 英雄代码 enemy</td>
<td>创建敌方英雄（英雄代码可在内部名称页面查询）
</td></tr>
<tr>
<td>-item 物品名称</td>
<td>给予玩家特定物品（物品名称可在内部名称页面查询）
</td></tr>
<tr>
<td>-givebots 物品名称</td>
<td>给予全图的AI机器人物品（物品名称可在内部名称页面查询）
</td></tr>
<tr>
<td>-refresh</td>
<td>刷新状态（无法刷新物品从背包取出的cd）
</td></tr>
<tr>
<td>-respawn</td>
<td>复活（没有死亡就移动到己方泉水）
</td></tr>
<tr>
<td>--spawncreeps</td>
<td>三路立即刷兵（刷的兵太多可能会占用大量的内存）
</td></tr>
<tr>
<td>--disablecreepspawn/-enablecreepspawn</td>
<td>开关刷兵（同时会关闭刷野）
</td></tr>
<tr>
<td>-spawnneutrals</td>
<td>刷新野区（无视封野）
</td></tr>
<tr>
<td>-spawnrune</td>
<td>符点刷新神符（赏金符在两分钟之前只会刷新出初始赏金符）
</td></tr>
<tr>
<td>-dumpbots</td>
<td>在右上角显示双方所有人当前状态
</td></tr>
<tr>
<td>-startgame</td>
<td>游戏时间变为0：00，立即开始，双方开始出兵，出兵后此指令无效
</td></tr></tbody></table>


##### 人机模式聊天指令

<table>
<caption>难度调整
</caption>
<tbody><tr>
<td>-easy</td>
<td>该难度下Bot会平地摔，适合没有或缺少MOBA经验的玩家
</td></tr>
<tr>
<td>-normal</td>
<td>该难度下Bot没有Buff修正，适合没有或缺少Dota2及THD2经验的玩家
</td></tr>
<tr>
<td>-hard</td>
<td>该难度下Bot有回蓝、经济经验和属性Buff，适合想要全面了解THD2少女和装备的玩家
</td></tr>
<tr>
<td>-lunatic</td>
<td>该难度下Bot所有Buff进一步提高，适合进阶玩家游玩
</td></tr>
<tr>
<td>-extra</td>
<td>选择任意难度后，在此难度上额外增加extra难度:bot复活后40秒内再次死亡会马上重置买活cd并获得买活钱，并且增加全属性。
</td></tr></tbody></table>



<table>
<caption>人数调整
</caption>
<tbody><tr>
<td>-setmaxplayer X</td>
<td>设置每队最大的人数，最大值为12
</td></tr>
<tr>
<td>-setmaxbot X</td>
<td>设置Bot的人数，最大值为12
</td></tr>
<tr>
<td>-banbots 英雄代码</td>
<td>禁用bot机体，多个机体用空格隔开（英雄代码可在内部名称页面查询）
</td></tr></tbody></table>



<table>
<caption>其他
</caption>
<tbody><tr>
<td>-fastcd</td>
<td>无限火力模式，CD减少，回蓝增加
</td></tr>
<tr>
<td>-unfastcd</td>
<td>关闭无限火力模式
</td></tr>
<tr>
<td>-respawn X</td>
<td>增加或减少复活时间，X为数字，范围不限
</td></tr>
<tr>
<td>-gaishi</td>
<td>盖世模式，bot只会选择平A英雄。
</td></tr>
<tr>
<td>-ayayayaya</td>
<td>bot全是射命丸文
</td></tr>
<tr>
<td>-ordinary</td>
<td>复原
</td></tr>
<tr>
<td>-checkmap</td>
<td>查看难度、模式和人数
</td></tr>
<tr>
<td>-dota</td>
<td>使用后会有DOTA英雄乱入
</td></tr>
<tr>
<td>-undota</td>
<td>关闭DOTA英雄乱入
</td></tr></tbody></table>


##### 通用聊天指令

<table>
<caption>
</caption>
<tbody><tr>
<td>L键</td>
<td>桃花岛的轮盘，可发送不同的轮盘语音
</td></tr>
<tr>
<td>-allsame</td>
<td>己方队伍所有人使用同一英雄
</td></tr>
<tr>
<td>-allowsame</td>
<td>己方队伍可重复选择一个英雄
</td></tr>
<tr>
<td>-strawberry</td>
<td>可提前了解英雄改动、装备改动等内容（特殊情况下某个英雄选取要开启此模式）
</td></tr>
<tr>
<td>-allpick</td>
<td>可以选择所有隐藏英雄
</td></tr>
<tr>
<td>-yaw X</td>
<td>旋转0°-360°的视角
</td></tr>
<tr>
<td>-pause</td>
<td>暂停
</td></tr></tbody></table>






---

此文档由 [THBWiki-Markdown-Builder](https://github.com/Delsin-Yu/THBWiki-Markdown-Builder) 构建。

文档中的所有内容除特殊注明外，均在 [**知识共享(Creative Commons) 署名-非商业性使用-相同方式共享 3.0 协议**](https://creativecommons.org/licenses/by-sa/3.0/deed.zh-hans) 下提供，附加条款亦可能应用。

引用类型与其他类型作品版权归原作者所有，如有作者授权则遵照授权协议使用。

详细请查阅 [THBWiki：免责声明](https://thbwiki.cc/THBWiki:%E5%85%8D%E8%B4%A3%E5%A3%B0%E6%98%8E)。

