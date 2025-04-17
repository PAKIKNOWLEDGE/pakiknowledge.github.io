# LR2自动灯简易配置方法




> 前言：由于笔者在访问GitHub仍然遇到诸多困难，所以请确保在开始配置之前您可以顺利的访问GitHub，此外仍然强烈建议开启或者保留代理软件作为最后手段。

----

# 1 GAS是什么，以及为什么这篇教程会有V2

GAS就是自动灯，这里不再赘述。那么之前已经写过一篇有关的教程了，为什么会有第二版呢？首先是次要的，就是原先的配置流程相对较为麻烦，而现在有了更简易方法。（特别感谢BMS群群友[quailty](https://space.bilibili.com/17747138)，是他发现了绕过IR使用插件的方法）之后是**主要原因，就是原先这个插件需要配合[Bokutachi IR](https://bokutachi.xyz/)进行使用，而该网站的规则中居然骂萝莉是乐色，我觉得这是不可接受了，因为首先笔者就是萝莉控，这种IR不如别用了！** 

![QQ截图20230106211804.png](/img1/QQ截图20230106211804.png)



---

# 2 怎样使用



最新版经过群友不懈努力已更新：由[quailty](https://space.bilibili.com/17747138)强力驱动

[简易整合补丁](https://wwrg.lanzouy.com/ipWju0kpcb2b)

这里顺便贴一段README

> 使用说明
>   1. 解压所有文件到 LR2body.exe / LRHbody.exe 的同级目录中
>   2. 运行 BokutachiLauncher.exe，会优先启动 LR2body.exe，如需启动 LRHbody.exe，请先删除 LR2body.exe
>   3. 设置 Gauge 类型作为自动灯的最高等级，比如设置 EASY 那么最高就是 EASY，设置 HARD 那么最高就是 HARD
>   4. 尽可能点出最好的灯，享受自动灯带来的愉快点灯体验
>
> 注意事项
>   1. 自动灯对 段位认定 /  NONSTOP / COURSE 不生效，对 BATTLE 和 G-BATTLE 不生效，对 G-ATTACK Gauge 不生效
>   2. 使用自动灯时如果设置初始 Gauge 类型为 GROOVE，在任意判定后 Gauge < 80 就会变为 EASY Gauge
>   3. 使用自动灯打出的 Replay 如果 Gauge 类型中途降低，在不使用自动灯时也会结算 Failed
>   4. 如果希望将分数上传至 Bokutachi IR（同时也会上传至 LR2 IR），需要到 https://bokutachi.xyz/ 注册并下载 BokutachiAuth.json 进行替换
>   5. 如在使用自动灯游玩时 LR2 本体闪退或无响应的问题，请删除 BokutachiHook.dll 后重试，分数将无法上传至 Bokutachi IR，但仍能上传至 LR2 IR
>
> 补丁说明
>   1. 基于 BokutachiHook v1.5.3，绕过 BokutachiLauncher 本地鉴权，无需注册 Bokutachi IR 即可使用 LR2 自动灯插件
>   2. 基于 LR2GAS v1.1 进行二次开发，对齐 LR2 原生 Gauge 机制，优化自动灯插件使用体验
>
> 重要声明
>   1. 支持原作者 MatVeiQaaa！
>   2. 自动灯插件涉及 DLL 注入，本质上属于外挂，请谨慎使用！
>
> 开发说明
>   1. BokutachiHook 代码仓库 https://github.com/MatVeiQaaa/BokutachiHook
>   2. 原版 LR2GAS 代码仓库 https://github.com/MatVeiQaaa/LR2GAS
>   3. 优化版 LR2GAS 代码仓库 https://github.com/quailty2020/LR2GAS
>
> 版本说明
>   v1.2.1 released by quailty on 2023.01.10

---



## 比较关键的一步（已过时）

在LR2游戏目录创建一个叫`BokutachiAuth.json`(请注意后缀！！)的文件，之后在里面填入：

```json
{
   "apiKey":"xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
   "url":"xxxxxx"
}
```



只要apiKey恰好40字节，url不是空就可以过校验(**也就是说url填lolisaiko都行，哈哈！**)

再次感谢[quailty](https://space.bilibili.com/17747138)，他伟大的贡献了这部分决定性的内容。

这之后，启动`BokutachiLauncher.exe`就可以体验自动灯了！

----



然后贴一个上一篇文章的避雷部分，懒得重写直接复制了：

> 直接点击BokutachiLauncher.exe启动会直接闪退，但是对这个程序使用**LEGUI**之后就正常了，推测是转区一类的问题，请各位自行避雷。

---

# 3. tips（已过时）

> 在使用场景中，如果您打开HARD选项，那么当你hard血归0后，gsm插件会帮您过渡到Groove/Easy血，但是你完成游戏后，**灯的选项会回到你clear的那个选项**，比如说你开着白进去落到easy并EC了，你的灯会变成绿灯，如果还想凹白就得手动调回来。（这里群友建议，想凹白就不要开自动灯了。）而且当你快速重开游戏之后，**灯无论如何都会变成easy gauge**，这里敬请各位注意！
>
> > 【★】练了 ★8 / st1 - 139324 2023/1/6 21:43:46
> > 严谨来说，hard gauge 死了就会变成 easy gauge 或者 groove gauge，重开会带着最后用的 gauge
> >
> > 
> >
> > 【★】练了 ★8 / st1 - 139324 2023/1/6 21:44:09
> > 如果还是 hard gauge 的时候退出重开，进去还是 hard gauge
> >
> > 
> >
> > 【★】练了 ★8 / st1 - 139324 2023/1/6 21:44:25
> > 但是一般没有人没死的时候重开吧
>

最后感谢BMS群提供帮助的各位，也感谢代码作者，请不要吝啬您的star。希望大家都能愉快的使用自动灯插件，祝大家生活愉快！

![1](/img1/QQ图片20230106215503.png)


