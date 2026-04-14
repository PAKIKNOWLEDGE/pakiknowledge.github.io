# 在LR2中使用GAS方法的相关问题




> 前言：本文涉及的绝大部分操作如果不使用代理软件将无法完成，请自行准备相关工具。强烈建议在代理打开的情况下完成所有操作。

# 1 GAS是什么



就是自动灯，这里不再赘述。

---

# 2 在LR2中使用GAS的方法：

首先，这个GAS似乎是与[Bokutachi IR](https://bokutachi.xyz/)绑定使用的，在使用GAS之前你需要先连上这个IR。这个IR的官网直连是可以进入的，但是仍然需要代理。

![1](/img1/pSEV4sO.png)

点击注册会提示你看规则，需要看30秒，这里还告诉你禁止创建小号，看完进行注册的时候**坑就来了**。

![2](/img1/pSEZiYn.md.png)

哈哈！如果你这时候没用挂代理的话就会发现**Captcha failed**了！那么这是怎么回事呢？其实就是因为没挂代理谷歌验证码加载不出来。这个问题在你裸连登录的时候同样会遇到，所以前言就建议全程挂代理。

---

注册完之后需要去邮箱里点确认链接，请确保你的代理还是开着的情况下去邮箱验证。验证完登录你就会看到类似的界面：

![pSEZcnS.png](/img1/pSEZcnS.png)



这个时候在确保IR已登录的情况下去[这里](https://bokutachi.xyz/client-file-flow/CXLR2Hook)，你会下载到一个叫`BokutachiAuth.json`的文件，请把他放到LR2的根目录。

这时候你基本已经要成功了！

然后再去[这里](https://github.com/MatVeiQaaa/BokutachiHook/releases)下载bokutachi IR的启动器，再去[这里](https://github.com/MatVeiQaaa/LR2GAS/releases)得到`LR2GAS.dll`把所有文件放在LR2的根目录。

然后这时候你的LR2目录大概是这样子：

[![pSEZbBF.png](/img1/pSEZbBF.png)]

这之后，用BokutachiLauncher.exe启动LR2就可以使用GAS插件了！然后这里笔者遇到了个坑，那就是直接点击BokutachiLauncher.exe启动会直接闪退，但是对这个程序使用**LEGUI**之后就正常了，推测是转区一类的问题，请各位自行避雷。还有一个好消息是你现在可以把你的代理关掉了，在裸连的情况下你依然可以正常连上bokutachiIR并使用GAS插件。

---

![1](/img1/QQ图片20230106184017.png)

最后经过群友提醒，该IR的管理员似乎极度反感二次元，那么笔者是不是很二次元呢？显然是，看那个banner是不是二次元？然而这种”尺度“的图片会不会被该管理员认定为**nsfw**呢？由于《**最终解释权**》归他，所以笔者倡议大家**索性不要上传头像了**。

FIN!
