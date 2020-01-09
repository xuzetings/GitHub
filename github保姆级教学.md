首先确保你的mac上已经安装好了git，可以打开终端后，通过敲上git来查看，也可以用

```
git -version
```

来查看git版本

由于mac使用的是linux命令，所以没有提示就是好事，就代表是成功的，所以下面的所有操作如果没有提示不要担心，意味着一切顺利！！！！
首先我们来到GitHub首页，然后点击右上方的+号进行创建仓库
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200109233530874.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80Mzc1MTE2MQ==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200109233540876.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80Mzc1MTE2MQ==,size_16,color_FFFFFF,t_70)
接下来就要先配置你的GitHub账户

```
git config --global user.name "xuzetings"
git config --global email.name "2773989609@qq.com"
```

然后cd到你需要上传的文件

例如我这样

```
cd Desktop/创业基础
```

然后对本地进行初始(建立暂存区)

```
git init
```

原则上我们还需要对上传到github上的文件有一个说明文件，这个文件一般为名叫readme的md格式的文档，所以在此之前最好学习一下markdown的相关知识

进行上述操作后，我们的文件夹内就会增加一个隐藏文件，名为.git。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200109232554317.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80Mzc1MTE2MQ==,size_16,color_FFFFFF,t_70)

这里先明确一个概念，就是我们的本地文件我假设它为工作区，那么刚刚创建的区域就是暂存区，本地文件必须先由工作区添加到暂存区，在能最后上传到云端。![在这里插入图片描述](https://img-blog.csdnimg.cn/20200109232733990.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80Mzc1MTE2MQ==,size_16,color_FFFFFF,t_70)

我们可以通过

```sh
git add * //提交所有文件
git add readme.md //提交指定文件
git add . //提交当前cd到的文件
```

接下来进行实际操作先提交

```
git add *
```

接下来可以通过以下命令来查看是否提交成功

```
git status
```

如果成功，则会显示

```
On branch master
nothing to commit, working tree clean
```

之后你可以修改你的文件夹中的文件，比如像我这样修改一下readme.md文件。

然后在此通过一下命令查看状态

```
git status
```

此时会显示如下，代表你修改了文件

之后，你可以通过如下命令来恢复文件,即把暂存区文件覆盖工作区文件

```
git checkout readme.md
```

如果操作成功你就会发现你原来的修改又回到了原来的样子

但是我们并不是为了把修改改回来，而是把修改保存传上去。所以我们应该在修改之后继续使用如下代码

```
git add *
git commit -m "这是第二次提交，修改了readme.md"
```

我们尝试着在此修改一下readme.md中的内容，可以随便加一些文字或者删除一些文字都可以。

然后在终端敲

```
git status
```

我们发现终端又提醒我们又文件发生了修改

我们可以通过如下命令查看工作区和暂存区的版本区别

```
git diff
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200109233122921.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80Mzc1MTE2MQ==,size_16,color_FFFFFF,t_70)
然后我们继续按照以下操作进行提交

```
git add *
git commit -m "这是第三次提交，再次修改了readme.md"
```

当我们发现终端命令太多很碍眼的时候，可以通过clear进行清屏

```
clear
```

这时我们尝试在文件夹内创建一份a.txt文件和b.txt文件

然后在此提交

```
git add*
git commit 0-m "这时第四次提交，提交了两个文本文件"
```

然后我们彻底删除a.txt和b.txt(用于模拟我们不小心删除了文件)

然后在终端使用如下操作查看之前提交的所有版本

```
git log
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200109233227567.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80Mzc1MTE2MQ==,size_16,color_FFFFFF,t_70)
我们有如下的回退版本的命令

```
git reset --hard HEAD^//退回到上一个版本，相当退到第三次提交
git reset --hard HEAD^^//退回到上上个版本，相当于退到第二次提交
```

但是我们发现上述命令都无法恢复到第四次提交，没关系，我们可以通过版本号来恢复，

```
git reset --hard ab396541fed00fd5f576f74486b31a8ac4484c74
```

此时再去看你的文件夹，你会惊奇的发现被你删除的两个文件又回来了！！！是不是很神奇，很好玩!!

通过上述的版本号恢复的方法，事实上可以恢复一切我们需要退回的版本。

好，结下来介绍提交到GitHub上的操作。

要上传到GitHub，我么首先需要生成一个ssh密钥

```
ssh-keygen -t rsa -C "2773989609@qq.com"
```

然后一路按enter键，最终就会在终端出现一个奇形怪状的图像。代表你成功了

通过finder我们直接搜索id_rsa.pub,直接打开这个文件，打开出现的内容就是密匙

，这里注意，如果你的mac没有吧隐藏文件设置成可见，你就找不到这个文件，因为这个文件是默认是隐藏文件。


在复制密匙之后，我们前往GitHub网页，点击头像，进入settings，然后找到一个叫SSH and gpg keys的选项，直接内容粘贴到key方框内，并在title处添加密匙名称。一般一台电脑就只需要一个密匙，也就是你完成这次操作后以后就不需要那么麻烦了。
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020010923334424.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80Mzc1MTE2MQ==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200109233408797.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80Mzc1MTE2MQ==,size_16,color_FFFFFF,t_70)
然后回到我们之前创建的GitHub仓库的那个网页，复制那串ssh码，在终端进行如下操作
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200109233603338.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80Mzc1MTE2MQ==,size_16,color_FFFFFF,t_70)
```
git remote add origin https://github.com/xuzetings/chuangye.git
git push -u origin master
```

等待提交完成就ok了。

注意，如果你是第一次提交到GitHub，那么你可能需要输入账号和密码，也就是你的GitHub的账号和密码。按照要求来就行了（如果我没记错应该是这样）

好了，现在刷新仓库页面，就会发现你的文件已经提交到GitHub上了，而readme.md文件，直接被解析出来显示在最下面。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200109233631512.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80Mzc1MTE2MQ==,size_16,color_FFFFFF,t_70)

这样，我们第一次利用git工具提交到GitHub就此结束了，虽然第一次有点复杂，但是一旦完成这一次，之后你的提交就会变得非常容易。

比如，你现在继续修改你的readme.md文件

然后

```
git add *
git commit -m "这时第五次提交"
git push
```

在此刷新我们的GitHub页面，我们发现第五次提交的内容已经提交到了GitHub覆盖掉了第四次的提交。

完成提交操作后，我门来学习如何从GitHub上下载到本地的操作。

我们假设自己是另一个人，使用了另外一台电脑。然后在桌面新建一个文件夹。

我这里把它取名为接受，然后cd到这个文件夹，进行克隆操作
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200109233724317.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80Mzc1MTE2MQ==,size_16,color_FFFFFF,t_70)
克隆地址为如图所示的地址
```
cd Desktop/接受
git clone https://github.com/xuzetings/chuangye.git
```

那么GitHub上的文件就已经克隆到本地了。

好了假设原来操作的那个人是A同学，第二个操作的是B同学，在B同学从A同学的GitHub上克隆了文件后，是可以在此提交来修改云端文件的。

这时候B同学在readme.md上又添加了一些文字，然后

```
cd Desktop/创业基础
git add *
git commit -m "这时第六次提交，B同学进行了修改"
git push
```

注意，为了操作方便，事实上我们是在A同学那里进行了修改操作。

当push完成之后，GitHub上的内容就更新了，但是注意，此时B同学克隆下来的版本还是上一个版本，需要更新为最新版本，则需要进行如下操作

```
cd ../接受/chuangye
git pull

```

这时候你发现文件已经更新了！！

上述内容皆经过本人测试，学习来自于一个b站up主，地址如下

[github教学视频](https://www.bilibili.com/video/av78802820?p=3)