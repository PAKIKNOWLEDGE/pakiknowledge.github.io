# hugo0.144.2版把我害惨了？让我们来谈谈这个问题吧

## 0 问题复现和起因

偶然之下，我动用了**Chocolatey**这个运行在Windows平台上的包管理器来安装hugo。（当然，我也用这个来装git，这真方便。）这个包管理器给我装载了hugo0.144.2版，还不用我手动加环境变量。但是当我把数据迁过来之后，我像往常一样`hugo`跑了起来,然而...

```
WARN  DEPRECATED: Kind "taxonomyterm" used in outputs configuration is deprecated, use "taxonomy" instead.
ERROR deprecated: site config key paginate was deprecated in Hugo v0.128.0 and subsequently removed. Use pagination.pagerSize instead.  
WARN  deprecated: site config key privacy.twitter.enableDNT was deprecated in Hugo v0.141.0 and will be removed in a future release. Use privacy.x.enableDNT instead.
Watching for changes in D:\blog\{archetypes,assets,content,data,layouts,static,themes}
Watching for config changes in D:\blog\config.toml, D:\blog\themes\LoveIt\hugo.toml
```

问题：

### 1. `Kind "taxonomyterm" used in outputs configuration is deprecated, use "taxonomy" instead`

* **问题分析** ：在输出配置里运用了已弃用的 `taxonomyterm`，现在需要使用 `taxonomy` 来替代。
* **解决办法** ：打开你的配置文件（像 `config.toml`、`config.yaml` 或者 `config.json`），把所有 `taxonomyterm` 替换成 `taxonomy`。


---



### 2. `site config key paginate was deprecated in Hugo v0.128.0 and subsequently removed. Use pagination.pagerSize instead`

* **问题分析** ：`paginate` 这个配置项在 Hugo v0.128.0 版本被弃用且后续被移除，现在要使用 `pagination.pagerSize` 来替代。
* **解决办法** ：在配置文件里找到 `paginate` 配置项，将其替换成 `pagination.pagerSize`。

---


### 3. `site config key privacy.twitter.enableDNT was deprecated in Hugo v0.141.0 and will be removed in a future release. Use privacy.x.enableDNT instead`

* **问题分析** ：`privacy.twitter.enableDNT` 配置项在 Hugo v0.141.0 版本被弃用，未来版本会被移除，要使用 `privacy.x.enableDNT` 来替代。
* **解决办法** ：我弃用了这个模块。

---

4.然后又莫名其妙出现如果我不在文件头设立`author`参数，主题里一律显示成“xxxx” 令人忍俊不禁 但是我也不会改 在我失去所有力气和手段之后我选择老老实实一个个进去赋值那些漏掉的参数。



---

### 另一个问题

我的松下sz6电脑的日式ps/2键盘布局疑似和中文版Windows的默认布局混淆了 导致我没办法打出`号。具体在高人指点下，有：

reg**（注册表）

```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\Keyboard Layouts\00000804]
"Layout Display Name"=hex(2):40,00,25,00,53,00,79,00,73,00,74,00,65,00,6d,00,\
  52,00,6f,00,6f,00,74,00,25,00,5c,00,73,00,79,00,73,00,74,00,65,00,6d,00,33,\
  00,32,00,5c,00,69,00,6e,00,70,00,75,00,74,00,2e,00,64,00,6c,00,6c,00,2c,00,\
  2d,00,35,00,30,00,37,00,32,00,00,00
"Layout File"="kbd106.DLL"
"Layout Text"="Chinese (Simplified) - US Keyboard"


```


完。

