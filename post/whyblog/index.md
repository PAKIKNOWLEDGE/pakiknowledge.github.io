# 为什么重拾博客？

# 为什么重新想起了博客？
  会想起这个东西，主要是因为某个契机。在谷歌找galgame资讯的时候误入了一个[博客](https://plumz.me/)，看着人家从2011年一直坚持到现在一直在坚持写，而反观自己，人生的断片就这样被自己在不经意间抛弃了，而回首过往，只剩下的很模糊的混沌一片。这是多么可惜啊!幸福往往就是这一个个断片拼接而成的，而我却抛弃了她。我以为是琐事，我拒绝了繁琐，从而我也丢弃了绚烂。人真的会麻木，而回首这些断片，却可以让你接触生活真正的色彩。不知道这次开始写博客能坚持多久呢？比起2020年，我已变了太多。在夕阳下拾遗，让我们对着晚霞不回头的向前走吧。

-----

# 重启博客的心路历程



## 1.原有架构  

介绍一下原有架构。原先的博客域名是*pakiknowledge.gitee.io*，托管在**gitee**（OSChina所属的一个开源平台，已变质，实质就是依托答辩。）**我只能说这里先不喷gitee后面有的喷好吧，感觉称其为屎都是屎被侮辱了。而博客生成框架是Jekyll*（已举办）* ，Jekyll之前我只是觉得很方便，但是**结合我手头的开发环境来看，这玩意也是差不多屎。总的来说原先的博客就是用一个屎框架托管在答辩平台上的超现实主义赛博乐色。好的那么为什么gitee是一坨屎，首先开源搞什么审批我就不予评价了，因为不是利益相关，但是为什么我开个pages都要实名认证？？？呃呃呃，我只能说你是？还有Jekyll，配置前置ruby+gem环境不挂代理几乎无法进行，好的就算恁克服了九九八十一难终于满怀希望开始`jekyll new`了我只能说你太天真了，因为如果你ruby gem没换源的话你只会卡死在这只能强行终止然后止步于此。我靠到这还得抗压？我真的是啥也不想说了，我之前还觉得Jekyll不错能说出诸多优点，这样看来hexo除了迁移git分支不方便以外是不是全是优点啊？我靠，还真是？？呃呃呃呃呃呃，总的来说Jekyll就是不适合我，用着有一种便秘的痛苦！！！111


![screenshot](/img1/pSkKxQx.png)
----

## 2.新征程

  于是我们就不得不寻找新的框架的托管平台。走GitHub总会是死路的。因为将还要面临GitHub pages的DNS污染。这里特别感谢[huakula](https://space.bilibili.com/3507112)佬百忙之中抽出时间指导我，他向我推荐了hugo+GitHub pages转发部署到cloudflare的方案。（hakula佬也是早期在我bms入门的时候提供了非常大的帮助！这次找他其实是缘起于GitHub使用镜像之后gitee的异常问题，他**现场谷歌**并帮助我解决了后面一系列问题！虽然说他大概率不会看到这篇文章但是还是在这里表达衷心的感谢！合十！）所以本来我们这里有很长的关于gitee异常部署的经验总结，但是由于我们弃用了答辩，所以在这里我们将所有和屎有关的内容全部略去！

---

  稍微有价值的内容也就是hugo框架的使用了。首先是hugo的安装使用方法，是直接添加进环境变量中。在cmd中

`hugo version`

如果正常输出那么就是配置成功了。

而启用一个新博客可以用

`hugo new <博客位置>`

来使用。

而目前遇到比较大的问题是**不会使用配置主题**，那么最后得出的结论是：

> 把主题根目录下的`examplesite`的东西复制到根目录再结合**readme文件**进行配置比较方便。

其中有一个小技巧，就是一边`hugo server`在浏览器监视本地服务器，一边修改本地文件内容，修改会实时的反映的网页上。

最后修改完了检查无误直接在根目录

`hugo`

然后把根目录下的`public`文件夹内的内容push上GitHub就可以了！111

最后我还是要说**这不是薄纱Jekyll？？**



因为很晚了就写到这里吧

FIN!

