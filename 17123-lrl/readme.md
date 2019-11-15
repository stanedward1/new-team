# **[niuniu-YOYO]( https://github.com/niuniu-YOYO )**

## 本周的课外学习计划

学习git知识、英语知识，Java跟进学习。

------

## 本学期的课外学习计划

过软考，争取过四级，以及完成好老师布置的任务以外，能做一个项目。

------

## git学习

### 一、Git简介

由于Linus痛恨CVS以及SVN的集中式的版本控制系统，后面又受到BitMover公司的威胁，所以才有了现在的Git分布式版本控制系统。

### 二、安装Git

Linux、macOS、Solaris、Windows、Raspberry Pi都可以安装Git。

三、安装版本库

版本库又名仓库，英文名为repository。可以简单理解为一个目录，目录内的文件都可被Git管理起来（包括文件的修改、删除、还可在未来某个时刻将其“还原”）。

首先，创建一个新目录

![image-20191112204151437](imgs\1-1)

通过git init命令将其目录变成Git可以管理的仓库

![image-20191112204426424](imgs\1-2)

.git目录是跟踪管理版本库的。（不要轻易改动）

### 三、创建.txt文件以及修改

#### 3-1在learngit目录下创建文件readme.txt文件

在readme.txt文件里面输入

![image-20191112210856318](imgs\1-3)

命令如下

![image-20191112210942951](imgs\1-4)

再将文件提交到仓库中

![image-20191112211032347](imgs\1-5)

此命令中-m后面输入的是本次提交的说明，可以输入任何内容。

git commit命令执行后会告诉你，1 file change，2 insertions：插入两行内容（readme.txt有两行内容）。

#### 3-2修改readme.txt文件

![image-20191112213300807](imgs\3-2-1)

然后使用 `git status`  查看状态

![image-20191112213437605](imgs\3-2-2)

 上面的命令输出告诉我们，`readme.txt`被修改过了，但还没有准备提交的修改。 

若记不清楚上次怎么修改了我们可以使用 `git diff`这个命令 。

![image-20191112213608925](imgs\3-2-3)

再使用 `git status`  查看状态

![image-20191112213843152](imgs\3-2-4)

### 四、版本回退

若修改文本太多次，我们可以用 `git log`命令查看 

![image-20191112214544926](imgs\4-1)

简化输出信息加上`--pretty=oneline`参数 

![image-20191112214700188](imgs\4-2)

需要友情提示的是，你看到的一大串类似`73b05...`的是`commit id`（版本号），和SVN不一样，Git的`commit id`不是1，2，3……递增的数字，而是一个SHA1计算出来的一个非常大的数字，用十六进制表示，而且你看到的`commit id`和我的肯定不一样，以你自己的为准。为什么`commit id`需要用这么一大串数字表示呢？因为Git是分布式的版本控制系统。

 现在我们启动时光穿梭机，准备把`readme.txt`回退到上一个版本，也就是`add distributed`的那个版本，怎么做呢？ 

首先，Git必须知道当前版本是哪个版本，在Git中，用`HEAD`表示当前版本，也就是最新的提交`73b05...`（注意我的提交ID和你的肯定不一样），上一个版本就是`HEAD^`，上上一个版本就是`HEAD^^`，当然往上100个版本写100个`^`比较容易数不过来，所以写成`HEAD~100`。

现在，我们要把当前版本`append GPL`回退到上一个版本`add distributed`，就可以使用`git reset`命令。

![image-20191112215335047](imgs\4-3)

查看状态

![image-20191112215535433](imgs\4-4)

### 五、管理修改

 什么是修改？比如你新增了一行，这就是一个修改，删除了一行，也是一个修改，更改了某些字符，也是一个修改，删了一些又加了一些，也是一个修改，甚至创建一个新文件，也算一个修改。 

第一步，对readme.txt进行修改

![image-20191113192405426](imgs\5-1-1)

第二步 再次修改

![image-20191113192512051](imgs\5-1-2)

第三步 提交： 

![image-20191113192644242](imgs\5-3)

第四步查看状态

git status

第五步 Git管理的是修改，当你用`git add`命令后，在工作区的第一次修改被放入暂存区，准备提交，但是，在工作区的第二次修改并没有放入暂存区，所以，`git commit`只负责把暂存区的修改提交了，也就是第一次的修改被提交了，第二次的修改不会被提交。

提交后，用`git diff HEAD -- readme.txt`命令可以查看工作区和版本库里面最新版本的区别：

![image-20191113193030122](C:\Users\Administrator\Desktop\1700130123-刘仁利-创客基地任务\one\imgs\5-4)

### 六、撤销修改

若你不小心在readme.txt中添加了一行错误

![image-20191113210141808](C:\Users\Administrator\Desktop\1700130123-刘仁利-创客基地任务\one\imgs\6-1)

若再不小心打了个盹，将其放到了暂存区，那么就可以运行 用命令`git reset HEAD `可以把暂存区的修改撤销掉（unstage），重新放回工作区。

### 七、删除文件

创建文件test.txt。再运用rm命令将其删除

![image-20191113211344827](C:\Users\Administrator\Desktop\1700130123-刘仁利-创客基地任务\one\imgs\7-1)

使用 `git status`命令会立刻告诉你哪些文件被删除了： 

![image-20191113211509425](C:\Users\Administrator\Desktop\1700130123-刘仁利-创客基地任务\one\imgs\7-2)

 现在你有两个选择，一是确实要从版本库中删除该文件，那就用命令`git rm`删掉，并且`git commit`： 

![image-20191113211634456](C:\Users\Administrator\Desktop\1700130123-刘仁利-创客基地任务\one\imgs\7-3)

### 八、远程仓库

 第1步：创建SSH Key。在用户主目录下，看看有没有.ssh目录，如果有，再看看这个目录下有没有`id_rsa`和`id_rsa.pub`这两个文件，如果已经有了，可直接跳到下一步。如果没有，打开Shell（Windows下打开Git Bash），创建SSH Key： 

![image-20191114202013635](C:\Users\Administrator\Desktop\1700130123-刘仁利-创客基地任务\one\imgs\8-1)

![image-20191114202104723](C:\Users\Administrator\Desktop\1700130123-刘仁利-创客基地任务\one\imgs\8-2)

第2步：登陆GitHub，打开“Account settings”，“SSH Keys”页面：

然后，点“Add SSH Key”，填上任意Title，在Key文本框里粘贴`id_rsa.pub`文件的内容：

![image-20191114202140666](C:\Users\Administrator\Desktop\1700130123-刘仁利-创客基地任务\one\imgs\8-3)

#### 添加远程库

 首先，登陆GitHub，然后，在右上角找到“Create a new repo”按钮，创建一个新的仓库： 

 ![github-create-repo-1](https://www.liaoxuefeng.com/files/attachments/919021631860000/0) 

 在Repository name填入`learngit`，其他保持默认设置，点击“Create repository”按钮，就成功地创建了一个新的Git仓库： 

![image-20191114203255536](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20191114203255536.png)

目前，在GitHub上的这个`learngit`仓库还是空的，GitHub告诉我们，可以从这个仓库克隆出新的仓库，也可以把一个已有的本地仓库与之关联，然后，把本地仓库的内容推送到GitHub仓库。

现在，我们根据GitHub的提示，在本地的`learngit`仓库下运行命令：

![image-20191114204313977](C:\Users\Administrator\Desktop\1700130123-刘仁利-创客基地任务\one\imgs\8-4)

 下一步，就可以把本地库的所有内容推送到远程库上： 

![image-20191114204950281](C:\Users\Administrator\Desktop\1700130123-刘仁利-创客基地任务\one\imgs\8-5)

 推送成功后，可以立刻在GitHub页面中看到远程库的内容已经和本地一模一样： 

![image-20191114205038402](C:\Users\Administrator\Desktop\1700130123-刘仁利-创客基地任务\one\imgs\8-6)

 从现在起， 只要本地作了提交，就可以通过命令： 

![image-20191114205241971](C:\Users\Administrator\Desktop\1700130123-刘仁利-创客基地任务\one\imgs\8-7)

 把本地`master`分支的最新修改推送至GitHub，现在，你就拥有了真正的分布式版本库！ 

#### 从远程库克隆

再次创建一个新的仓库（gitskills），这次不一样的是 勾选`Initialize this repository with a README`，这样GitHub会自动为我们创建一个`README.md`文件。创建完毕后，可以看到`README.md`文件： 

![image-20191114205516607](C:\Users\Administrator\Desktop\1700130123-刘仁利-创客基地任务\one\imgs\8-8)

![image-20191114205825191](C:\Users\Administrator\Desktop\1700130123-刘仁利-创客基地任务\one\imgs\8-9)

克隆一个本地库

![image-20191114210114668](C:\Users\Administrator\Desktop\1700130123-刘仁利-创客基地任务\one\imgs\8-10)

### 九、分支管理

分支就是科幻电影里面的平行宇宙，当你正在电脑前努力学习Git的时候，另一个你正在另一个平行宇宙里努力学习SVN。

如果两个平行宇宙互不干扰，那对现在的你也没啥影响。不过，在某个时间点，两个平行宇宙合并了，结果，你既学会了Git又学会了SVN！

![learn-branches](https://www.liaoxuefeng.com/files/attachments/919021987875136/0)

分支在实际中有什么用呢？假设你准备开发一个新功能，但是需要两周才能完成，第一周你写了50%的代码，如果立刻提交，由于代码还没写完，不完整的代码库会导致别人不能干活了。如果等代码全部写完再一次提交，又存在丢失每天进度的巨大风险。

现在有了分支，就不用怕了。你创建了一个属于你自己的分支，别人看不到，还继续在原来的分支上正常工作，而你在自己的分支上干活，想提交就提交，直到开发完毕后，再一次性合并到原来的分支上，这样，既安全，又不影响别人工作。

其他版本控制系统如SVN等都有分支管理，但是用过之后你会发现，这些版本控制系统创建和切换分支比蜗牛还慢，简直让人无法忍受，结果分支功能成了摆设，大家都不去用。

但Git的分支是与众不同的，无论创建、切换和删除分支，Git在1秒钟之内就能完成！无论你的版本库是1个文件还是1万个文件。

#### 9.1创建与合并分支

创建dev分支，并且切换到dev分支：

![image-20191114211607632](C:\Users\Administrator\Desktop\1700130123-刘仁利-创客基地任务\one\imgs\9.1-1)

 然后，用`git branch`命令查看当前分支： 

![image-20191114211646800](C:\Users\Administrator\Desktop\1700130123-刘仁利-创客基地任务\one\imgs\9.1-2)

 `git branch`命令会列出所有分支，当前分支前面会标一个`*`号。 

 对readme.txt文档进行修改。然后提交： 

![image-20191114211743036](C:\Users\Administrator\Desktop\1700130123-刘仁利-创客基地任务\one\imgs\9.1-3)

 现在，`dev`分支的工作完成，我们就可以切换回`master`分支： 

![image-20191114211847601](C:\Users\Administrator\Desktop\1700130123-刘仁利-创客基地任务\one\imgs\9.1-4)

 现在，我们把`dev`分支的工作成果合并到`master`分支上，然后查看readme.txt。 

![image-20191114212041485](C:\Users\Administrator\Desktop\1700130123-刘仁利-创客基地任务\one\imgs\9.1-5)

 合并完成后，就可以放心地删除`dev`分支了。 查看`branch`，就只剩下`master`分支了： 

![image-20191114212203928](C:\Users\Administrator\Desktop\1700130123-刘仁利-创客基地任务\one\imgs\9.1-6)

#### 9.2解决冲突

准备新的分支featurel分支，修改readme.txt的最后一行为Creating a new branch is quick AND simple.，将分支featurel提交，切换到master分支上，在master分支上将readme.txt文档的最后一行更改为Creating a new branch is quick & simple.并提交。

![image-20191114215329733](C:\Users\Administrator\Desktop\1700130123-刘仁利-创客基地任务\one\imgs\9.2-1)

 现在，`master`分支和`feature1`分支各自都分别有新的提交，变成了这样： 

 ![git-br-feature1](https://www.liaoxuefeng.com/files/attachments/919023000423040/0) 



 这种情况下，Git无法执行“快速合并”，只能试图把各自的修改合并起来，但这种合并就可能会有冲突， `git status`可以告诉我们冲突的文件： 

![image-20191114215852064](C:\Users\Administrator\Desktop\1700130123-刘仁利-创客基地任务\one\imgs\9.2-2)

 我们可以直接查看readme.txt的内容： 

![image-20191114215945467](C:\Users\Administrator\Desktop\1700130123-刘仁利-创客基地任务\one\imgs\9.2-3)

 用带参数的`git log`也可以看到分支的合并情况： 

![image-20191115174813783](C:\Users\Administrator\Desktop\1700130123-刘仁利-创客基地任务\one\imgs\9.2-4)

 最后，删除`feature1`分支： 

![image-20191115174831986](C:\Users\Administrator\Desktop\1700130123-刘仁利-创客基地任务\one\imgs\9.2-5)

### 9.3分支管理策略

通常，合并分支时，如果可能，Git会用`Fast forward`模式，但这种模式下，删除分支后，会丢掉分支信息。

如果要强制禁用`Fast forward`模式，Git就会在merge时生成一个新的commit，这样，从分支历史上就可以看出分支信息。



### 未完待续……





------

## markdown

用的typora软件，用起来就像word一样，还可以直接导出为各种格式，包括github的readme.md也是用的这个martkdown。

------

## 资源推荐

菜鸟教程
