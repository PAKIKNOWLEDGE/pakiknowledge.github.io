# 【ArcadePC】頭文字D THE ARCADE HDD PATCH NOTE

# 0 丑话说在前

## 这是什么？

这是一篇街机游戏[頭文字D THE ARCADE｜ドライブゲーム｜セガ](https://initiald.sega.jp/inidac/)[](https://initiald.sega.jp/inidac/)[](https://initiald.sega.jp/inidac/)[](https://initiald.sega.jp/inidac/)在电脑上运行的开发笔记，属于纯纯的灰产，非法，如果您通过任何搜索引擎搜到该页面，请立刻通过

`2772962906@qq.com`联系笔者。

## 为什么会有这篇文章：

说实话，在**中国大陆地区**想要获得技术支持近乎非常难，暂且不说折腾Arcade PC最需要的电脑知识、编程基础、以及最重要的**耐心**，除去这些，你几乎也找不到这个游戏在本地运行的教程或者资源。（那我为什么会？日本人教的。大陆人要让他们教你？大多数让你**先掏钱**。）

## 诅咒

> It’s fascinating how some folks turn “community passion” into a side hustle, isn’t it? Charging entry fees for what’s meant to be shared joy, then padding pockets with “premium access” to bits and pieces that should’ve been open to all. Oh, and the extra flair of a “custom tool” that polices your files like a overzealous hall monitor—how creative, to weaponize convenience just to keep the cash flowing. One can’t help but admire the *commitment* to monetizing every little corner, even if it means souring the very thing people love. After all, nothing says “for the fans” like nickel-and-diming them into submission, then rigging the system to punish anyone who dares step outside the paywall. Bravo to the masterminds of this “innovative” business model—truly, they’ve redefined “giving back” in the most… unique way possible.
>
> Cruelly enough, the Goddess of Fate does not mete out her punishment the moment you commit your most egregious transgressions. Instead, she hoards this debt in the archives of destiny, biding her time until the interest has compounded to its bitterest peak—then demands repayment in full, principal and interest alike.

---

# 1 基础知识

游戏核心也就两个文件夹：`AMDaemon` 和 `WindowsNoEditor`

AMDaemon是放配置文件和一些管联网的东西的，`segatools`、`artemis` 也要放在里面。能否拿到让程序在Windows上启动的AMDaemon.exe非常关键。

`segatool` 是管启动的 还有虚拟aime卡 还有把 你的设备（可能是键盘 手柄 方向盘 这里是idac 其他家的就不列了 典型的有音击之类）的输入让街机程序认出来并反应你才能玩 此外 在idac如果你的segatool版本太老，会导致**油门失灵。 此外** 在idac segatool也是**装载绕检测补丁**的途径，否则idac会触发**pc check**，导致你在买车/进入比赛前被踢出游戏。

![img](/img1/image.png)

`artemis` 是管本地服的 可以让你在本地运行SEGA的东西并开卡 如果看的人搞过BEMANI的 HDD，就能理解这东西和隔壁的氧无差不多，同时也知道这东西等级森严，兼容性向下不向上。

在idac中，存储用户数据的形式是数据库，也就是Mysql，如果在本地运行，也要在本地部署本地数据库。（不过那个太基础了，几条命令的事，本文现在不会提及）（但是部署基础，修改数据库内容却不简单——没人教，你都不知道怎么填那些键值——哦不，你甚至理解不了那些数据结构）

**ICF1文件**是存在于segatool/amfs文件夹中的一个文件，这文件负责的是游戏的版本号，但是实测，这个文件与实际上并没有内容什么校验绑定之类的代码存在（也可能有？？谁想去测试呢，我不想徒增错误发生的概率），举个例子吧，载了旧的icf文件可能只会开机显示舞萌dx2022让人一头雾水，结果打开一看游戏实际上是舞萌dx2025一样。

**timeRelease文件** `是存在于 AMDaemon\artemis\titles\idac\data`的一批文件 其存在通常为：`timeRelease_vxxxx.json`的形式，其中xxx为版本号。头D和服务器返回内容强绑定，此文件夹让服务器鉴定你的游戏版本，如果版本过旧，就算游戏本体是新的，新要素，新地图也不会在游戏中向你开放。举个例子，大家都知道maimai BUDDiES 版宴会场复活了，但是如果你的release版本太旧了，或者没有用上新的，就算你的版本是最新最热，游戏中也不会有宴选项。

在日服，我经手的版本有1.7 此版本为东方project联动初出 但是由于物理引擎陈旧，且太老，不提及

2.3版本 该版本为season4

2.50版本 该版本为season4

2.71版本 该版本为season4 有MFG联动第二弹的内容

2.80版本 该版本为season4 有术力口联动第二弹

3.01版本 该版本为season5 物理引擎迎来变革 且有东方project联动第三弹和一个卡车联动

---

# 2 2.50版本为代表的配置流程基础

这个版本的配置难度非常之低，首先拿到脱壳的游戏文件，然后在[完全公开的地方](https://gitea.tendokyu.moe/puniru/artemis)得到Artemis文件，放入对应文件夹中之后只需要对config文件夹下的 `core.yml`稍加配置就行了主要有：

listen_address:0.0.0.0

hostname:填你ipv4

name是店铺名 可自定义建议全英文

```
aimedb:
  enable: True
  listen_address: ""
  loglevel: "info"
  port: 22345
  key: "Copyright(C)SEGA"
```

主要是key那一栏自己填

然后segatool的东西 dns直接填你ipv4 然后subnet那个照抄但是把你ip最后一组数字写成0就行了

然后有没有不会启动Artemis的 没有吧 目录下**`python index.py`**就行了

---

# 3 操蛋，大操天下的2.71（及以后）写死dns的变动

在2.50之后的游戏版本，可恶的SBGA公司写死了域名校验，这意味着你不能像上面提到的在配置文件里直接写入你的ipv4，只能写 `eac-fm01.sega-initiald.net`。那有人就要问了，这不是没法用我本地ip启动了吗？实则不然，可以用改hosts文件的方法把这个域名指向你自己的ipv4，只需要你在hosts里填上如下的东西：

```
10.0.0.254  tenporouter.loc
10.0.0.254  bbrouter.loc
your own ip eac-fm01.sega-initiald.net
```

虽然我不知道为什么上面两个域名也要填，但是就是要填。。所以我又要说了，没人教这些问题全是死局，感谢dc上的守序善良日本人吧。。

还有一件事，在这个版本之后artemis必须要加密启动了，但是core.yml里面一来是我托别人弄的，那些东西我实在看的头晕，于是我直接push到私有库了，然后在配置后续的3.01的时候我直接diff了之前push上去的东西，反正能用就行。

还有一个问题是，需要用证书来混淆域名，让域名认证通过。这里直接放傻瓜式命令了，当然首先你要安装好openssl

```
openssl req -x509 -newkey rsa:2048 -keyout title.key -out title.pem -days 365 -nodes -subj "/CN=<artemis_hostname_here>"
```

hostname填什么你懂的

填完在core里面把有指向“cert”的东西全部换成你自己签完的证书的名字和目录，不懂yml路径怎么写的问ai（我自己也这么干）

如果觉得一年太少了365后面加两0

当然如果你懒 神秘分支上我也给你签好了 但是不难 建议自己签 实在懒得联系我。

Artemis用加密模式启动请：`python index.py --ssl True`

---

# 4 守序善良日本人与3.01

其实后面复盘，除了我对dac运行原理一窍不通之外，还有一个是因为我白手起家，啥都没有，基本都是守序善良日本人给的。

首先本体和脱壳文件 自己想办法吧

之后Artemis修复后可以用于s5的版本 可以联系我要

然后这里我在配置Artemis的时候直接diff了2.71的东西 日本人说这部分没什么变动 我就直接开始diff照抄了

然后发现自己没有icf文件 日本人给了

自己没有timeRelease文件 日本人给了 t `imeRelease_v301.json` 此外，这部分由 `AMDaemon\artemis\config`里的idac.yml中的**timerelease_no:xxx**这个东西控制

只能说对面是我女的我直接嫁了吧 唉 但是你懂的 我不能说他的名字 感谢守序善良日本人

然后总结下来，这个版本如果你有对应的文件，突破完hosts问题后 那基本没什么太大的问题 剩下的都是小问题

那么....

## 小问题：数据库的报错

在启动完Artemis，涉及到aime的操作的时候出现了这样的一幕

![img](/img1/c593ba2a060047f2b50457d1b73043f3.png~tplv-a9rns2rl98-image.png)

### 核心错误信息

`pymysql.err.OperationalError (1054, "Unknown column 'idac_user_expansion._param_1' in 'field list'")`→ 翻译：**在查询的字段列表中，找不到 `idac_user_expansion` 表中的 `_param_1` 字段**

### 报错场景

代码执行了一条 `SELECT` 查询语句，尝试从 `idac_user_expansion` 表中读取包括 `_param_1` 在内的多个字段，但数据库里 **这个表根本没有 `_param_1` 这个字段** ，所以触发了 “字段不存在” 的错误。

1. **涉及的 SQL** ：查询语句中明确写了要获取 `idac_user_expansion._param_1`，但该字段在表中不存在；
2. **查询条件** ：`WHERE idac_user_expansion.user = 7`（是针对 `user=7` 的数据查询）。

user7是我为s5测试专门开的一张aime的用户ID（注意，不是叫“user7”，是数据库认他的id为7）!

![img](/img1/bd0f5bd4575146a2b445b945ebb1485a.png~tplv-a9rns2rl98-image.png)

代码逻辑确实需要这几个字段，就在 `idac_user_expansion`表中 **新增 `_param_1/_param_2/_param_3`字段** （字段选 `int`就行了）。在 Navicat 里操作：

1. 右键 `idac_user_expansion`表 → 设计表；
2. 点击 “添加字段”，依次添加 `_param_1`、`_param_2`、`_param_3`；
3. 保存表结构。

然后错误消失，数据也能正常存。

至于你说这个错误到底会不会影响存数据？我真不知道，我看到Artemis一片红了马上修了。

## 小补充

说一个自定义所属店铺名的事，在数据库表的 `arcade`表添加你要的店铺名，这里中文也行，记得打繁体，结果类似：

1	TAITO Station 従化ポートフューチャー店	TAITO Station 従化ポートフューチャー店	HKG				63	+0800

的东西 然后记住这个店铺id 我这里是1

然后打开idac_profile表 看你用户那一栏 把store这一项填上你上面那个id（数字id）

# 4 结语

> I’ve only heard of this phenomenon in IDAC—and specifically in mainland China.In China, there’s another rhythm game: Konami’s BEATMANIA IIDX (you’ve probably heard of it too). Someone set up a score-storing server at their own expense and doesn’t charge any fees at all (they don’t even provide a voluntary donation channel). This person is truly a hero among players.

![1](/img1/G7eXL18boAAerdY.png)

