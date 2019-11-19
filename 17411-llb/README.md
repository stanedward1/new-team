# **[stanedward1](http://www.jiangnanshaojiu.com/myself/index.html)**

## 本周的课外学习计划

购买一个腾讯云的服务器，然后安装好Apache和mysql，放一个网页上去，然后慢慢完成一个动态网站，满足条件的话，将自己在阿里云上买的域名弄到腾讯云上，解析，备案……

------

## 本学期的课外学习计划

重新过一遍计算机网络，算法课要加大学习力度，javaweb框架和基础项目的学习。

继续学python，包括

------

## git学习

 git是分布式版本控制系统，能记录每次文件的改动，这次学习主要看的是 https://www.liaoxuefeng.com/wiki/896043488029600 。



git国内下载地址： https://github.com/waylau/git-for-win 



**推荐看廖雪峰的git教程和菜鸟教程里的git教程。**



### git是个啥

- git是用c语言开发的。

- Linus一直痛恨的CVS及SVN都是集中式的版本控制系统，而Git是分布式版本控制系统 。

- git安装完成后，在开始菜单里找到“Git”->“Git Bash”，蹦出一个类似命令行窗口的东西，就说明Git安装成功！
- 什么是版本库呢？版本库又名仓库，英文名**repository**，你可以简单理解成一个目录 。
- **第一步是用`git add`把文件添加进去，实际上就是把文件修改添加到暂存区；**
- **第二步是用`git commit`提交更改，实际上就是把暂存区的所有内容提交到当前分支。**

### git的基本操作步骤

- 安装完成后，还需要最后一步设置，在命令行输入：

  ```
  $ git config --global user.name "Your Name"
  $ git config --global user.email "email@example.com"
  ```

- 注意`git config`命令的`--global`参数，用了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然也可以对某个仓库指定不同的用户名和Email地址。 

![image-20191112204917366](C:\江南烧酒的dell笔记本\文档\创客基地\17411的第一次任务文档\img\image-20191112204917366.png)

-  **通过`git init`命令把这个目录变成Git可以管理的仓库：** （忘了截图emmmmm）



- <u>目录下多了一个`.git`的目录，这个目录是Git来跟踪管理版本库的，没事千万不要手动修改这个目录里面的文件，不然改乱了，就把Git仓库给破坏了。</u>

  <u>如果你没有看到`.git`目录，那是因为这个目录默认是隐藏的，用`ls -ah`命令就可以看见。</u>

  

- 和把大象放到冰箱需要3步相比，把一个文件放到Git仓库只需要两步。

  第一步，用命令`git add`告诉Git，把文件添加到仓库：

  ```
  $ git add readme.txt
  ```

  执行上面的命令，没有任何显示，这就对了，Unix的哲学是“没有消息就是好消息”，说明添加成功。

  第二步，用命令`git commit`告诉Git，把文件提交到仓库：

  ```
  $ git commit -m "wrote a readme file"
  [master (root-commit) eaadf4e] wrote a readme file
   1 file changed, 2 insertions(+)
   create mode 100644 readme.txt
  ```

  简单解释一下`git commit`命令，`-m`后面输入的是本次提交的说明，可以输入任意内容，当然最好是有意义的，这样你就能从历史记录里方便地找到改动记录。

  

  ![image-20191112205300631](img\image-20191112205300631.png)

  

- **要随时掌握工作区的状态，使用`git status`命令。**



- 如果`git status`告诉你有文件被修改过，用`git diff`可以查看修改内容。



-  `git log`命令显示从最近到最远的提交日志 ， 如果嫌输出信息太多，看得眼花缭乱的，可以试试加上`--pretty=oneline`参数： 



-  在Git中，用`HEAD`表示当前版本，也就是最新的提交`1094adb...`（注意我的提交ID和你的肯定不一样），上一个版本就是`HEAD^`，上上一个版本就是`HEAD^^`，当然往上100个版本写100个`^`比较容易数不过来，所以写成`HEAD~100`。 



- 回退可以使用`git reset`命令 



-  Git提供了一个命令`git reflog`用来记录你的每一次命令： 

![image-20191112205448572](img\image-20191112205448572.png)

-  每次修改，如果不用`git add`到暂存区，那就不会加入到`commit`中。 



- 命令`git checkout -- readme.txt`意思就是，把`readme.txt`文件在工作区的修改全部撤销，这里有两种情况：

  一种是`readme.txt`自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；

  一种是`readme.txt`已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。

  

- 场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令`git checkout -- file`。

  场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令`git reset HEAD `，就回到了场景1，第二步按场景1操作。

  场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考[版本回退](https://www.liaoxuefeng.com/wiki/896043488029600/897013573512192)一节，不过前提是没有推送到远程库。



-  命令`git rm`用于删除一个文件。如果一个文件已经被提交到版本库，那么你永远不用担心误删，但是要小心，你只能恢复文件到最新版本，你会丢失**最近一次提交后你修改的内容**。 



- github提供Git仓库托管服务的，所以，只要注册一个GitHub账号，就可以免费获得Git远程仓库。

  在继续阅读后续内容前，请自行注册GitHub账号。由于你的本地Git仓库和GitHub仓库之间的传输是通过SSH加密的，所以，需要一点设置：

  第1步：创建SSH Key。在用户主目录下，看看有没有.ssh目录，如果有，再看看这个目录下有没有`id_rsa`和`id_rsa.pub`这两个文件，如果已经有了，可直接跳到下一步。如果没有，打开Shell（Windows下打开Git Bash），创建SSH Key：

  ```
  $ ssh-keygen -t rsa -C "youremail@example.com"
  ```

  你需要把邮件地址换成你自己的邮件地址，然后一路回车，使用默认值即可，由于这个Key也不是用于军事目的，所以也无需设置密码。

  如果一切顺利的话，可以在用户主目录里找到`.ssh`目录，里面有`id_rsa`和`id_rsa.pub`两个文件，这两个就是SSH Key的秘钥对，`id_rsa`是私钥，不能泄露出去，`id_rsa.pub`是公钥，可以放心地告诉任何人。

  第2步：登陆GitHub，打开“Account settings”，“SSH Keys”页面：

  然后，点“Add SSH Key”，填上任意Title，在Key文本框里粘贴`id_rsa.pub`文件的内容：

  

  ![image-20191112211004377](img\image-20191112211004377.png)



- 在github上新建仓库，然后根据GitHub的提示，在本地的`learngit`仓库下运行命令： 



![image-20191112212429212](img\image-20191112212429212.png)



- 然后推送

![image-20191112212621060](C:\江南烧酒的dell笔记本\文档\创客基地\17411的第一次任务文档\img\image-20191112212621060.png)

![image-20191112212641249](C:\江南烧酒的dell笔记本\文档\创客基地\17411的第一次任务文档\img\image-20191112212641249.png)

- 从现在起，只要本地作了提交，就可以通过命令：

  ```
  $ git push origin master
  ```

  把本地`master`分支的最新修改推送至GitHub，现在，你就拥有了真正的分布式版本库！

  

- 要关联一个远程库，使用命令`git remote add origin git@server-name:path/repo-name.git`；

  关联后，使用命令`git push -u origin master`第一次推送master分支的所有内容；

  此后，每次本地提交后，只要有必要，就可以使用命令`git push origin master`推送最新修改；

  分布式版本系统的最大好处之一是在本地工作完全不需要考虑远程库的存在，也就是有没有联网都可以正常工作，而SVN在没有联网的时候是拒绝干活的！当有网络的时候，再把本地提交推送一下就完成了同步，真是太方便了！

  

- git克隆一个仓库来本地



![image-20191112213714327](C:\江南烧酒的dell笔记本\文档\创客基地\17411的第一次任务文档\img\image-20191112213714327.png)



-  Git支持多种协议，包括`https`，但通过`ssh`支持的原生`git`协议速度最快。 



- 再把克隆到本地的gitskills推送到github



![image-20191112214624582](C:\江南烧酒的dell笔记本\文档\创客基地\17411的第一次任务文档\img\image-20191112214624582.png)

![image-20191112214645478](C:\江南烧酒的dell笔记本\文档\创客基地\17411的第一次任务文档\img\image-20191112214645478.png)

- 我们创建`dev`分支，然后切换到`dev`分支： `git checkout`命令加上`-b`参数表示创建并切换，相当于以下两条命令：

  ```
  $ git branch dev
  $ git checkout dev
  ```

- 然 后，用`git branch`命令查看当前分支： 用`git checkout`加上原分支名回去

![image-20191113152346902](C:\江南烧酒的dell笔记本\文档\创客基地\17411的第一次任务文档\img\image-20191113152346902.png)

- 把`dev`分支的工作成果合并到`master`分支上： ![image-20191113152430909](C:\江南烧酒的dell笔记本\文档\创客基地\17411的第一次任务文档\img\image-20191113152430909.png)

- 删除dev分支

- ![image-20191113152530359](C:\江南烧酒的dell笔记本\文档\创客基地\17411的第一次任务文档\img\image-20191113152530359.png)

- 解决冲突（当Git无法自动合并分支时，就必须首先解决冲突。解决冲突后，再提交，合并完成。

  解决冲突就是把Git合并失败的文件手动编辑为我们希望的内容，再提交。

  用`git log --graph`命令可以看到分支合并图。）

- ![image-20191113160405314](C:\Users\江南烧酒\AppData\Roaming\Typora\typora-user-images\image-20191113160405314.png)

  ![image-20191113160446137](C:\江南烧酒的dell笔记本\文档\创客基地\17411的第一次任务文档\img\image-20191113160446137.png)

- 

  

------

## markdown

 https://www.runoob.com/markdown/md-tutorial.html 

 https://www.markdown.cn/ 

 Markdown 是一种轻量级标记语言，它允许人们使用易读易写的纯文本格式编写文档。 

Markdown 编写的文档可以导出 HTML 、Word、图像、PDF、Epub 等多种格式的文档。

Markdown 编写的文档后缀为 **.md**, **.markdown**。

 当前许多网站都广泛使用 Markdown 来撰写帮助文档或是用于论坛上发表消息。例如：GitHub、简书 ……

 Markdown 的目标是实现「易读易写」。 

这里是一些免费编辑器： https://www.markdown.cn/#editor 

简书关于markdown的 一些链接：https://www.jianshu.com/p/q81RER 

一些主流markdown编辑器的推荐： https://zhuanlan.zhihu.com/p/69210764 

------

## 资源推荐

强烈推荐headfirst系列和机械工业出版社的小黑书系列

headfirst系列对阅读者来说特别友好，机械工业出版社的小黑书系列大部分都是国外一流大学的计算机教材，如《深入理解计算机系统》，《计算机网络-自顶向下方法》等。

然后网易的mooc也比较不错，大部分都是项目实战部分的。

中国大学mooc里浙江大学的翁恺老师讲的c语言和java广受好评。
