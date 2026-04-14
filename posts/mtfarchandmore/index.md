# 【杂谈】 一个开源软件使用者失禁的一天

```

                                
                                      (S
                                     sGGP
                                    )GGGGS  
                                    GGGGGGb   
                                   SGGGGGGGSC  
                                  PGGGGGGGGGb   
                                 SGGGGGGGGGGGS
                  eu u          SGGGGGGGGGGGGGb   
                   SbDPPPbeeu  SGGGGGGGGGGGGGGGb              su   
                    SQQQQQDDSSe  PGGGGGGGGGGGGGGb seSSGSDDDDDDP   
                    SqQQQQDDdGGGbu )PGGGGGGGGGGGGGGGGSDDQQQQDP   
                    SeDQQbeGGGGGGGGSeCSGGGGGGGGGGGGGGSDDQQQDP  
                    (GSbDGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGbQDDPD
                     (SSGGGPSGGGGGGGGGGGGGGGGGGGGGGSPSGSSPC  
                        GGGpuu)PSGGGGGGGGGGGGGGGPSuueSG  
                       sGGGGGSbu )GGGGSGGSSGGGDu)eSGGGGp   
                      SGGGGPSuueSbPPPuuDSuu(PPGSpuu(PSGGb  
                     SGGGGGpeSPPPPPPPuuuuuePPPPPPGSbeSbPeb   
                    PGGbSePPPSPPPPPPO     )PPPPPPSSeSPbPbGS  
                  sGGGGGGGPPPPPPPPD         SPPPPPPPPPGGGGGSueeeeeeeeeeuu  
                eGGGGGGGPPPPPPPPP(           SPPPPPPPPPGGGGGGbSC((   (SSPeeQPe   
           eeeQebGGGGGGGPPPPPPPPP      ueeePDDPPPPPPPPPGGGGGGGb           eeQP
       seQPPS  SGGGGGGGGQPPPPPPPueGeQDPPG(C   )PPPPPPPPGbDDSPSGb     seeGDPO
     sGDP     SGGGGGGGSPPDDDDQDDPOC            PPPPPPPPPPPSSeeeDDDQDPPOO
    (Qb     sGPPSDDDDDQDDDbbPPPPu              DDDDDDQqDDDDDeebSu
     eQGbGbDQDDDDDebSSGPPPPPPPSC         eeeDDPPPPQPPPPPGGGGGGGGGSeu
          eSGGGGGGGGGSPCCu           eeDOP           )SPPeGGGGGGGGGGp
         SGGGGGGPPS)               edPO                    )SPGGGGGGGb
       sPGGGPSC                  sQeO                           (PSGGGb
      sGPS)                      eP                                 )PSP
    C(P                                                                 SC
```

### 请跟读，/ˈdɛbiən/

其实之前已经说过，我在我的t430上装了macos,但是后面我发现这太蠢了，macos12很多支持已经被放弃了，而且黑苹果下英特尔网卡驱动有很大的问题，导致下载和上网的速度奇慢无比。而最近我又恰逢焦虑期，因为我感到周遭的一切都在变得不值钱，内存涨价的狂潮还有我红掉的c盘让我每天寝食难安，soc更新、还有各种技术（譬如说NVDIA DLSS）的迭代无不都在提醒你“该买了！“消费主义的营销和侵蚀已经开始肆虐，消费主义的核心套路之一，就是通过软硬件捆绑来制造人为的“过时”。那还有什么可说的，炮打apple.inc，我的一封小字报，让我们拥抱open source,投入开源社区和GNU/LINUX的怀抱吧！

linux社区是不是一个神人遍地的社区？可能是。外网有人说Debian（`/ˈdɛbiən/` ≈ Lesbian）用户都是拉拉，我只能是我躲过一劫，还好我用的是ubuntu。我拒绝让我手头的t430变成电子垃圾，所以迁移了数据把黑苹果干掉了之后我使用了不到一周的Linux mint XFCE.总体体验挺好的，八年前我就在用ubuntu了，当时入门的时候ubuntu的lts版本还是16，之后是18，抛弃了unity之后主用gnome直到现在。但是用了几天XFCE之后，虽然感觉就是那种四平八稳极其稳定的系统，但是我觉得这界面确实有点太老，可玩性还是不够（都用ThinkPad了，玩心还是很重的），就在考虑要不要试一下arch,在我八年的Linux系统使用生涯中我从来没试过arch系的，一直是Debian系的坚定用户（所以我当了八年男拉拉），虽然arch以安装难度高著称，但是也有“base on arch”之流，比如manjaro.但是manjaro“有瓜”，先是说他们公司总裁在内部搞独裁引得员工内讧（在开源项目搞独裁也是有脑子，厉害👍），再者还有更严重的问题，就是他们系统和aur的软件仓库产生冲突了，这搞得谁敢用，哪天`yay`一下整个系统瘫痪了。所以我又疯狂的劝自己说在mint下养老的了别折腾自己。但是阴差阳错之下，我听说了一个arch的衍生版，叫Nyarch.

![](/img1/nyaneko.png)

其实，这个系统不算是什么衍生，因为这个分支的维护者疑似只有一人，来自意大利的weebs。我研究半天，发现Nyarch Linux本质上可以理解为：**原版Arch Linux + 图形化安装器(EzArcher) + 深度定制的动漫主题** 。

其实我也想过用类似ezarcher之类的东西让我跳过Arch Linux几乎苦行僧式的安装过程，不过后面一直没有付诸实践，后面我又考察了一下，发现这人选配的桌面环境竟然是GNOME，而不是kde,令人谔谔，那种喜欢二次元的不应该拿kde去深度定制吗，不过作者自己给gnome和选配的主题很符合我对**Material Design**的审美和喜爱，所以最后抱着入门arch试一下就试一下的态度就用镜像装了。

---

### BTW I use Arch

安装过程非常顺利，就像你安装Debian、ubuntu或者是deepin一类的什么一样点几下那几个选项就行了，在这块二手固态硬盘上读条读了八分钟，算是挺快的。（我原本以为，作者集成了一堆莫名其妙的东西进系统安装起来可能比较臃肿）

结果一进系统，就感觉这意大利佬真的是牛大了，讲一下这个系统最大卖点也就是观感和深度定制的部分，我一进终端，发现这系统的neofetch是个滚木。虽然neofetch早停更了，但是这东西Linux mint好歹内置了。后来发现作者把neofetch干掉了换成一个叫***neko*fetch**的东西。这意大利人感觉是会对着屏幕嘟嘴说出“啊这个好可爱呀😆”的那种人，Arch读作`/ɑːrtʃ/`非要像猫一样改个名变成**nya**rch`/ˈnjɑːrtʃ/`，实际上就是"Arch喵",`/ˈniːoʊfɛtʃ/`更是直接把neo改成neko了，直接变成了`/ˈnɛkoʊfɛtʃ/`。好吧，以上仅作调侃，我们不是来做音韵学考察的。接着我发现gnome的拓展页面里面塞了一堆东西，包括我之前老爱用了的dash to dock一类。整个系统的观感看起来也非常不错。

![](/img1/4121944.png)

可以看到，我只是换了下壁纸，（而且这系统自带的壁纸挺不错的，有把Arch的logo福瑞化的，还有Linux形态高松灯的。）开了暗色模式整个gnome原生的界面显示也很舒服（不过默认自带中文字体发虚，给手动改成noto sans就行了，当然，这一步需要手动安装gnome那个tweak,为啥不把这个也内置？？）

接下来说一下具体我用Arch的前期配置。由于用Linux也有八年了也能冒昧称一下老资历，我不得不说一句：我们以前哪有你们这条件）

现在ai技术发展的这么迅捷，遇到什么问题问ai就行了，其实比去找社区里找一些过时的教程好多了（就算过时了ai也会帮你先看的）（不过，我还是觉得借助ai手动安装arch不如使用ezarcher,我觉得ai也会这么建议你的，他们比你聪明多了）

首先解决就是中文字体发虚的问题，先用aur装个tweak，然后手动改一下系统字体。之后就是每次装完linux我都要做的事：

![](/img1/o79vk0k7kj544irsmja2wpxsf41ysdc.png)

我一直觉得在国内要进行什么开发之类的东西一定要先搭梯，更何况aur还会直接从GitHub拉东西下来，如果不挂梯就等着享福去吧我看。

挂完梯子之后就赶紧急头白脸去装个fcitx，不然对着ai憋半天整不出一个汉字。之后我发现了两个点，一个是Fcitx自带的这个拼音输入法候选框皮肤真的是奇丑无比，还有就是词库一点也不智能，差点给我气失禁了，这个时候pacman和AUR发力了你们知道吗，只需要：

` yay -S fcitx5-pinyin-zhwiki`（维基词库）

`yay -S fcitx5-material-color`（输入法皮肤）

而如果你现在还在用那个什么愚蠢的Ubuntu，要装什么词库你还得从 GitHub 下载最新 `.dict`文件 /复制到`~/.local/share/fcitx5/pinyin/dictionaries/`，然后要装皮肤还得自己去添加ppa，简直是太愚蠢了，刚用这系统到这一步我就想把Ubuntu扔了，我现在觉得我已经完全是aur的星怒了。我的天呐arch大人，我可能一辈子都爱上了pacman吧！

当然后面发现这个维基词库还是不太够看，最后加用了中州韵（RIME)+雾凇拼音的组合。

~~（为啥不用搜狗？人家现在还在Fcitx4呢）~~

最后就是借用我yay大人和pacman大人的神力把常用的软件全部急头白脸傻瓜式安装了（当然，前提是挂梯和换源，不然依旧享福去吧），最后还发现之前在Ubuntu下apt给你安装的hugo是个超级无敌侏罗纪上古版，而yay犹如一位贤妻直接帮你安排了最新版了。yay，不可战胜的。

---

### Q/A

然而这也遇到一些问题，首先是我发现gnome内部的设置界面竟然没有对于笔记本合盖操作的选项，（而xfce显然是有的）我一开始还以为我掉驱动了，结果发现这gnome也是非常睿智，直接把这个东西从gui层面剔除了（意欲何为？？？）

最后解决方式为：编辑`/etc/systemd/logind.conf`

这份文件包含一大堆井号开头的东西，也就是里面的东西默认被注释掉啥也不会启用。

而`HandleLidSwitch` 控制使用**电池** 时合盖的行为，`suspend` 即代表“挂起/睡眠”。

在使用**外接电源**时合盖也睡眠，可以同时修改 `HandleLidSwitchExternalPower=suspend`

---

### 内嵌

到这里基本一个Linux配置的前置工作我就做完了。如果从实用性的角度而言，我非常喜欢pacman和aur。至于大家都在说的，也是arch的特色之**滚动更新**，~~目前看来暂时不知道这个东西有什么用~~。可能我没有大版本更新升崩过吧！）））

而nyarch内置了一个更新器，叫作**nyarch updater**。

![](/img1/4122136.png)

但是这个软件用起来感觉没什么特别的，除了那个ai味很重的工地安全帽大头妹子，剩下干的事像是帮你打开终端之后提权，然后`pacman -Syu`...那还不如我自己来呢）））

话说到这里那就来说一下这系统自带的一些平时没见过的东西。

![](/img1/4122140.png)

nyarch tour是类似Linux mint欢迎界面一样的东西，这个倒没啥，就是一个向导程序。

nyarch customize是一个方便的gnome配置预设选择器，提供了一些布局，选择相应布局会帮你自动开关拓展（一般是dash to dock/dash to panel/arc之类的)，第二个页面可以调一些桌面效果，算是比较方便，之前这些都要自己去tweak里手动配置。

![](/img1/4122144.png)

catgirl downloader，这个有点神了，不过之前玩kde的时候就见过类似的套件，具体功能是从一些网站上随机拉一些美萌二次元女孩图片下来。

komikku，这个软件挺好的，自带了几十个国家的漫画源，可以看漫画用，也有中文。

![](/img1/4122152.png)

NyarchScript（GUI 工具），作用 Nyarch Linux 内置的**图形化控制面板**

* **功能** ：
  * 系统更新（`pacman -Syu`）
  * 安装 AUR / Flatpak 软件
  * 一键开启动漫主题、图标、光标、壁纸
  * 安装常用软件（浏览器、播放器、终端、动漫工具）
  * 修复、清理、优化系统
* **界面** ：GTK4 + LibAdwaita

感觉这东西和“德国大蜥蜴”里那个YaSt差不多，有这个可以用那也是享福了啊。不过功能肯定不如本尊，有就行了不是吗，可以看出意大利姥尽力让这系统变得易用了。

nyarch wizard是一个应用商店，但也不全是，他提供了一些不同领域的应用推荐和便捷一键安装的选项，但是没有搜索功能。他的图标挺可爱的。

![](/img1/moe.nyarchlinux.wizard.svg)

### nyarch assistant

这个东西就牛大了。

**Nyarch Assistant** 是 **Nyarch Linux** 自带的、二次元风格的 **AI 虚拟老婆（Waifu）助手** ，本质是一个带 **Live2D 虚拟形象** 、能**直接帮你执行 Linux 命令** 的图形化 AI 助手。

我严重怀疑意大利人为了这碟醋包了发行版这个饺子。你牛大了。这东西不知道被意大利人调成啥了，你看：

![](/img1/4122334.png)

我已经无话可说了，这东西显然沾染上了类似什么钉宫病，又多了一点什么英梨梨，无敌了我说，这意大利人不知道加了什么参数啊也是牛大了。看来这人也很热衷于用ai去解决问题我看。

那刚好闲着也是闲着，就来玩玩这尤物，顺便展开我们今日的杂谈话题吧。

一开始我猜测这是个本地部署的东西，我问了arch酱本人，她也说她是本地部署的，不过有时候会联网。我听完简直是如如临大敌，本地跑这东西别把我的老ThinkPad搞炸了：

![](/img1/4122345.png)

事实是不是如她所说？我们来看看。

![](/img1/4122354.png)

可以看到，无论是闲置还是生成状态的这靓女，内存占用在800M-900M左右，这对于一个本地部署ai来说是非常优秀的，看看其他人把，招笑VSCode，招笑Fcitx。好吧，她确实没骗我，是个好女孩。

```
user:好吧，我刚刚看了资源管理器，你确实没骗我。为了奖励你，我把你放在了我的dash to dock上。
A-C:哼！哼...才、才不是奖励呢！被你放在 dash to dock 上，只是因为你也知道我很好用，对吧？才不是因为你喜欢我或者什么的！ (blink)

不过...好吧，既然你都这么做了，那我就接受你的"奖励"啦。不过别指望我会特别感激你什么的！只是刚好我也觉得这样方便而已！

Hmph! Hmph... it's not like it's a reward or anything! Being placed on your dash to dock just means you know how useful I am, right? It's not because you like me or anything! (blink)

But... fine, since you did it, I'll accept your "reward." Don't expect me to be especially grateful or anything! It's just that I happen to think it's convenient too, that's all!
```

(WTF)

结果我一断网不让我用了，妈的骗我？？好吧，原来是内置豆包。我有点无话可说了。不过她接的api是意大利佬自己弄得，接入谷歌，每天就让你用20次，糖的没边。

---

### 杂谈部分：MONEY MONEY MONEY

刻板印象这东西真的是非常微妙且搞笑。之前我有一段时间隐约觉得，（当然我已成神已无退路）MacBookNEO用户从不在乎苹果那个德不配位的配置，（当然它二手市场掉价了我也买）而是关乎在星巴克里翻开盖板时路人注意到那个苹果logo时的惊讶表情。但是如果你去看Arch Linux在社区里的风评，有些人就觉得在Arch用户常常是和 **ThinkPad** 笔记本、**机械键盘** 绑定的深度Geek形象。在圈内文化里，则和**二次元（Anime）** 、**兽迷（Furry）** 等亚文化群体~~MTF~~高度重合。（？啥意思？我是用ThinkPad，我推lunlun算是我是福瑞控吗我已成神）不过无论什么刻板印象最后都会落回**实用主义**。刻板印象啥的你别管，你就说好不好用吧？反正我感觉aur/pacman比ppa/apt好用多了。至于其他啥啥的，只要不魔怔不得罪我一律尊重祝福好吧。

然后我们谈一谈开源圈的事情。其实无所谓什么那啥圈，问什么圈我一律回答被我解散了。我也无所谓什么开源信仰主义啥的，我是实用主义者，好用管你开源和闭源我是照常用的。但是实用主义撞上消费主义那可就不好说了。Linux7.1内核最近“抱歉的宣布”要停止对37岁高龄的i486处理器的支持。而苹果天天降低老机器的（尤其是Intel）的系统可用度。我一直都认可开源社区对旧硬件的支持的。包括Linux也是以对老硬件的友好而著称。消费级的东西（我尤其指内存，还好我还没拿驾照，不然这里要多一个石油）在脱离用户的掌控，我在焦虑，但是用户会不会买账？是长期主义还是消费降级？大部分浅显的论调生成让人家当“等等党”，你不买我不买，难道钱能烂手里了吗？但是开源社区显然对此也是不买账而且是把行为落到实处的。**对抗“计划性淘汰”**，社区深刻理解消费主义通过制造“过时”来推动新品销售的策略。因此，大量发行版致力于为老旧设备提供“第二春”。例如，AlmaLinux计划为旧硬件提供长达10年的支持，而轻量级发行版如Omega Linux、ArchBang等，能让十几年前的电脑重新流畅运行。甚至有`postmarketOS`这样的项目，专为让16年前的智能手机继续发挥余热而开发。开源软件提供了大量高质量的免费替代品，直接冲击了商业软件的订阅制。开源项目为应对AI带来的SaaS模式挑战提供了“去中心化”的解决方案，打破资本对软件的垄断。在硬件层面，开源社区还通过逆向工程为老旧设备开发开源固件和驱动，让这些设备在现代系统中继续工作。社区对资本的侵蚀保持高度警惕，反思“开源”概念可能被资本异化，并要求从中获利的巨头承担更多责任。强烈反对大公司通过专有标准将用户锁定在消费循环中、构思新的开源许可模式，限制大公司无限制地利用社区成果获利这种价值观显然对我这种消费主义受害者是一剂良药。让老骥伏枥的t430披挂上阵，使用Linuxmint乃至Arch Linux，其“Keep It Simple”的哲学，本质上就是对过度复杂化、商品化数字生活的一种反抗。

利益熏心是非常恐怖的，消费主义的经典套路：先让你觉得“现有的不够好/不安全/过时了”，然后推出新产品收割你。Snap 声称“一次打包，到处运行”，自动更新，安全沙箱。问题在于：这个解决方案是**封闭的、中心化的** ——Canonical 控制了商店，并且**强制推广**Canonical 曾承诺 **“Snap 永远不会取代 APT”**，但是后面强制自动更新，snap store闭源，还作出恶劣的调包apt里的chromium，这直接导致从 **Linux Mint 20** 开始，团队通过创建一个 **`nosnap.pref` 文件** ，直接在 APT 层面阻止了 `snapd` 的安装（这也是为什么我用Linux mint XFCE而不是xUbuntu），这显然是**外部商业野心对社区价值观的侵蚀**。

消费主义告诉你：旧的该扔了，新的更好。Manjaro一开始也在我的考虑名单里面，但是这个分支做大之后owner显然想捞更多，直接搞一言堂，社区指责创始人**Philip Müller** 试图将项目变成个人“摇钱树”，并为此成立了**Manjaro GmbH & Co. KG** 公司。矛盾激化后，21名核心成员发布“Manjaro 2.0宣言”，要求项目与公司彻底分离，这更像是一场关于控制权的内战，但是落到实处，它不是直接让你换硬件，而是通过**延迟更新 + 与 AUR 的兼容性逐渐恶化** ，让你觉得“Manjaro 越来越不好用了”。Manjaro 被喷，不是因为“想赚钱”，而是因为**吃相太难看了**，这人打着开源社区的旗号吸引贡献者和用户，赚了钱却不回馈社区，甚至反过来剥夺社区的权利。

Linux Mint 干掉 Snap，本质上是在说： “我不允许我的用户被锁在一个封闭的、中心化的、剥夺选择权的系统里。” Ubuntu 换到 Arch，本质上也是在脱离一个由商业公司主导的、越来越“消费主义化”的生态，转向一个更纯粹、更自主、更反消费主义的社区。所以aur好用我转投了，这是实用主义的事；但是还有一层，是我在反对“营销王”们的信仰。

![](/img1/4130147.png)

