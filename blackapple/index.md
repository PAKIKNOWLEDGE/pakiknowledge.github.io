# only Panasonic can do！松下sz6双系统黑苹果记录

### 0 前言

时隔多年，终于用上黑苹果，感慨万千。松下sz6这机器体制挺好的，黑果完已经可以基本日用了。本篇文章就是在mac的环境下完成的。后来发现，黑果就是一个前人种树，后人乘凉的东西。有了前人的探索，才能有如今这么方便的经验和过程可以借鉴。

---

![](/img1/22.png)

### 1 原理

由于我是对黑苹果一窍不通的，所以对黑苹果的原理和概念一窍不通，在跟着教程走的过程中我也熟悉了大概的概念。

`EFI`:引导文件夹，包含引导程序，驱动程序，补丁文件。efi和系统上是独立开的，系统做完后变更efi文件是可行的，二者相互独立。能否拥有一个根据机型深度定制的efi很大程度影响能否顺利安装。

`opencore/clover`:两种主流的引导程序，现在oc较为主流，clover对大部分英特尔的机器具有通用性（然而.....）这两个引导程序由config.plast驱动配置，且具有自动读取的性能（这对双系统来讲很方便）

`KEXT`：黑苹果的驱动格式 装载在efi/boot/oc(或者clover）/kext里

---

### 2 系统制作与引导

#### 聚宝盆

黑苹果的第一步就是要制作系统，并做好引导。这一步关键点有两个，一个是做系统的方式，另一个是能不能开的起来。能否进入系统设置安装引导界面的关键在于基本的驱动能否驱起来。在系统制作的方面我选择了用恢复镜像的方式，这个方法相对于u盘启动安装更加简易，在Windows下留好分区之后恢复进去，并装载efi引导文件进esp分区就可以了。在efi选择上，我选择了三份，一份来自于[老张是大佬](https://space.bilibili.com/3070996)的sz6 efi，还有一份来自[黑苹果屋](https://space.bilibili.com/346147710?)的“东北乱炖”式的efi。最后还有一份GitHub上找到的[松下sz5的efi](https://github.com/waldoxhm/Panasonic_CF-SZ5_SZ5PDYVS_hackintosh_EFIhttps:/)。这时候有人就疑惑了，你这电脑不是sz6吗，咋整上sz5了？别急，因为我那个时候记错了）但是到后面这份efi还派上了妙用。

#### 好事多磨

一开始我恢复好系统进分区后，我先用sz5的efi去开了，但是直接卡系统校验开不起来了，按理来讲，同品牌同系列笔记本在硬件上拥有很大的硬件驱动通用性，但是sz5➡️sz6的迭代就是处理器架构从六代迭代到了七代，skylake变成kaby lake了，直接导致引导开不动。接下来我开始用黑苹果屋那一份clover efi去开，因为我听说（仅仅是听说）clover对英特尔机器有很好的通用性。结果开是开起来了，触控板和键盘也正常，但是奇卡无比，我一开始以为是我的电脑带不动Mac了，我还换了一个老版本的镜像又开了一次，还是奇卡无比，鼠标移都移不动的那种（当然，事实是七代i3对于macOS Monterey来说性能还是太过剩了），于是我走投无路，又换回了opencore，在“东北大乱炖锅”一样的config.plast里选择了一份文件名声称“Kaby lake通用”的文件去开，哎哟我去，居然给开起来了，而且非常流畅——这个时候我大概推测那份clover肯定是cpu或者显卡哪里驱动不起来了，性能释放0%导致系统都装不进去。但是很快这份“乱炖”efi又宣告出毛病，因为没声音，光感烂了，fn快捷键没有，没网。于是我又找到了那个完全同机型的sz6 efi来用，不出意料很完美，完美光感，完美快捷键，完美苹果触控手势，完美声卡。

#### 棋差一招

在更换efi的过程中，我竟然不小心将windows的引导误删，无奈之下我只能制作windowspe急救u盘去修复，修复完之后，opencore自动读取了Windows的引导，自动生成了启动项，双系统居然不费吹灰之力。

#### 网络之谜

但是，还是没网。几经排查，发现是英特尔万能网卡驱动对于macOS版本有等级森严的代码区分度，作者在kext列表里把他们全部装载进去，**然而全部不启用**，让你自己按你自己的情况去开（**事实上，这么干是对的**），所以没网的原因是因为我根本没装载网卡驱动。于是在我手动装载了Monterey版本的驱动之后Wi-Fi恢复正常了。

#### 决定性的问题

到这里系统基本已经可以正常日用了.......吗？并不能。因为这份efi有一个严重的问题，那就是进入合盖睡眠之后，键盘和触控板会完全失效。这个时候，还记得那份sz5的efi吗？在作者上传的第二个版本迭代里自述修复了睡眠唤醒的问题，然而代价是没办法使用鼠标手势。根据松下的产品迭代力，估计不至于说去迭代触控板驱动，我拿来替换试了一下，果不其然可用。 古人云，趋利避害，假死和没手势相比那我还是选个没手势吧，我这叫两害取其轻。

#### 余孽

```
2025-04-17 15:23:40 +0800 DarkWake            	DarkWake from Normal Sleep [CDN] : due to XDCI/ Using BATT (Charge:97%) 45 secs   
2025-04-17 15:24:37 +0800 DarkWake            	DarkWake from Normal Sleep [CDN] : due to XDCI/ Using BATT (Charge:97%) 45 secs   
2025-04-17 15:25:34 +0800 DarkWake            	DarkWake from Normal Sleep [CDN] : due to XDCI/ Using BATT (Charge:97%) 45 secs   
2025-04-17 15:26:30 +0800 DarkWake            	DarkWake from Normal Sleep [CDN] : due to XDCI/ Using BATT (Charge:97%) 45 secs   
2025-04-17 15:27:26 +0800 DarkWake            	DarkWake from Normal Sleep [CDN] : due to XDCI/ Using BATT (Charge:97%) 45 secs   
2025-04-17 15:28:22 +0800 DarkWake            	DarkWake from Normal Sleep [CDN] : due to XDCI/ Using BATT (Charge:97%) 45 secs   
2025-04-17 15:29:18 +0800 DarkWake            	DarkWake from Normal Sleep [CDN] : due to XDCI/ Using BATT (Charge:96%) 45 secs   
2025-04-17 15:30:14 +0800 DarkWake            	DarkWake from Normal Sleep [CDN] : due to XDCI/ Using BATT (Charge:96%) 45 secs   
2025-04-17 15:31:10 +0800 DarkWake            	DarkWake from Normal Sleep [CDN] : due to XDCI/ Using BATT (Charge:96%) 31 secs   
2025-04-17 15:31:53 +0800 DarkWake            	DarkWake from Normal Sleep [CDN] : due to XDCI/ Using BATT (Charge:96%) 45 secs   
2025-04-17 15:32:49 +0800 DarkWake            	DarkWake from Normal Sleep [CDN] : due to XDCI/ Using BATT (Charge:96%) 45 secs   
```

如上，这是睡眠唤醒的日志。可以看到，几乎每一分钟，电脑都被这个叫“xdci”的东西唤醒一次，导致这电脑没法深睡，这问题有待修复。

#### efi的独特性对机型配置的影响

显然，前面用clover和野鸡Kaby lake驱动开起来的案例，二者都有共同的特点，他们不是对于特定机型的深度定制，而是塞入许多通用性高的驱动去“模糊匹配”，有时候误打误撞居然开上了，实则后续要解决的问题更加多。

---

### 3 日用体验

在日常使用上，个人认为流畅度上远超Windows10，动画神奇效果也基本没有什么掉帧的现象，而Windows10在输入法输入经常出现输入粘滞卡顿掉帧的现象。多任务处理能力明显强于Windows，不插电续航体感上也还算优秀。mac相较于Windows还有一些先天优势，例如unix系的福报包管理器，还有其平台下的其他种种独占好用的工具，对于生产力和办公体验来讲是非常棒的。至于不适应之处当然也有，松下诡异的日式布局加上新加入的command健让人操作时有时候分不清，此外倒没有什么大问题存在。

