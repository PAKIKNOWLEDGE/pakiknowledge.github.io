# 地雷：


# 1.Github桌面端报错（本文头图状况）

在push的时候出现：
![q1](/img1/pSkMy11.png)
---
解决：**重新配置SSH**

```
 在git里
 ssh-keygen -t rsa -C "your_email@example.com"
 到”C:\Users\用户名\.ssh“，用编辑器打开id_rsa.pub文件，复制里面的一串代码（全部都要复制）。
```

 登录GitHub账户，单击右上角的头像，选择Settings,选择SSH and GPG keys，然后单击绿色的“New SSH key”，标题随便起一个名字，key就是上面一步复制的id_rsa.pub文件里的代码.

```
测试SSH
 ssh -T git@github.com
```



再次push后正常。

---

# 2.图床出毛病

头图糊成屎了，更换图床后解决。

---

# 3.与Git相关的一大票问题：

大部分转用Github桌面端后就省去了很多问题，放着GUI不用非得用Bash你觉得你这样很帅吗？

（你别说，我之前还真的这样认为。很遗憾！）

---

# 4.Typora图片插入格式有误

背一下图片语法很难吗？

```
![image name](image link)
```

盒盒，我只能说，盒盒。

---

FIN
