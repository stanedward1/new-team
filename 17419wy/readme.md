[Alarnzearn](https://github.com/Alarnearn) ：https://github.com/Alarnearn/
# 17419wy
* 本周的学习计划：
   * 1、完成专业相关作业
   * 2、学习Linux搭载环境相关知识
   * 3、学习H5进一步的应用开发
 
# 关于git的概念和基本使用的一些学习
 * 简介:Git(读音为/gɪt/。)是一个开源的分布式版本控制系统，可以有效、高速地处理从很小到非常大的项目版本管理。 Git 是 Linus Torvalds 为了帮助管理 Linux 内核开发而开发的一个开放源码的版本控制软件。Torvalds 开始着手开发 Git 是为了作为一种过渡方案来替代 BitKe<br> 
 **Github** --- 一个平台（网站）。
 `Github官方网站`：https://github.com/  <br>提供给用户创建git仓储空间，保存（托管）用户的一些数据文档或者代码等。         
 * 功能特点：<br>
1. git是一个开源的分布式版本控制系统，从服务器上克隆完整的Git仓库（包括代码和版本信息）到单机上。可以用以有效、高速的处理从很小到非常大的项目版本管理。<br>
2. git是个工具，在linux里面也就类似gcc这样的工具一样，是一个shell命令。<br>
3. 可以在自己的机器上根据不同的开发目的，创建分支，修改代码。在单机上自己创建的分支上提交代码。<br>
4. 可以在单机上合并分支，也可以把服务器上最新版的代码fetch下来，然后跟自己的主分支合并。<br>
5. 生成补丁（patch），把补丁发送给主开发者。<br>
6. 看主开发者的反馈，如果主开发者发现两个一般开发者之间有冲突（他们之间可以合作解决的冲突），就会要求他们先解决冲突，然后再由其中一个人提交。如果主开发者可以自己解决，或者没有冲突，就通过。一般开发者之间解决冲突的方法，开发者之间可以使用pull 命令解决冲突，解决完冲突之后再向主开发者提交补丁。
 * 一些学习：<br>
 1. 创建一个版本库：git init <br>
( kwydwuf注: 新版 git 中应该用 git init ，不要再用 init-db 命令，具体可以通过命令 git help init 查看)
可以了。现在我们来为本文的写作创建一个版本库：
```
$mkdir gittutorcn
$cd gittutorcn
$git init
```
git 将会作出以下的回应<br>
**Initialized empty Git repository in/[yourpath]/.git** 或
**(Initialized empty Git repository in /Users/1a/gittutorcn/.git/
)** <br>
这样，一个空的版本库就创建好了，并在当前目录中创建一个叫 .git 的子目录。你可以用 ls -a 查看一下，并请注意其中的三项内容：<br>
* 一个叫 HEAD 的文件，我们现在来查看一下它的内容：
`$cat.git/HEAD` 
现在 *HEAD* 的内容应该是这样：`ref:refs/heads/master` <br>
我们可以看到，HEAD 文件中的内容其实只是包含了一个索引信息，并且，这个索引将总是指向你的项目中的当前开发分支。<br>
* 一个叫 *objects* 的子目录，它包含了你的项目中的所有对象，我们不必直接地了解到这些对象内容，我们应该关心是存放在这些对象中的项目的数据。
* 请注意：master 是默认的分支，这也是为什么 .git/HEAD 创建的时候就指向 master 的原因，尽管目前它其实并不存在。 git 将假设你会在 master 上开始并展开你以后的工作，除非你自己创建你自己的分支。<br>
另外，这只是一个约定俗成的习惯而已，实际上你可以将你的工作分支叫任何名字，而不必在版本库中一定要有一个叫 master 的分支，尽管很多 git 工具都认为 master 分支是存在的。
2. 增加内容
增加内容跟踪信息：git add  <br>
通过创建两个文件举例作为练习：
``
$echo"Helloworld">hello
$echo"SnakeZero">snake
``
我们再用 git add 命令将这两个文件加入到版本库文件索引当中：
`$git add hello snake`
git add 实际上是个脚本命令，它是对 git 内核命令 **git update-index** 的调用。因此上面的命令和下面的命令其实是等价的：<br>
`$git update-index --add hello snake`
如果你要将某个文件从 git 的目录跟踪系统中清除出去，同样可以用 **git update-index** 命令。例如：`$git update-index --force-remove foo.c`
3. 提交内容到版本库：`git commit`
既然我们刷新了 Git 的跟踪信息，现在我们看看版本库的状态：<br>
`$git status`
我们能看到 git 的状态提示：
```
#
#Initial commit
#
#
#Updated but not checkedin:
#(willcommit)
#
#newfile:example
#newfile:hello
#
```
提示信息告诉我们版本库中加入了两个新的文件，并且 git 提示我们提交这些文件，我们可以通过 **git commit** 命令来提交：<br>
`$git commit -m "Initial commit of git tutor reposistory"`
查看当前的工作：`git diff`
git diff 命令将比较当前的工作目录和版本库数据库中的差异。现在我们编辑一些文件来体验一下 git 的跟踪功能。<br>
`$echo'这段是后来加的'>snake`
我们再来比较一下，当前的工作目录和版本库中的数据的差别。<br>
`$gitdiff`<br>
差异将以典型的 *patch* 方式表示出来：
```
diff--gita/snakeb/snake
index3b85043..d79f20a100644
---a/snake
+++b/snake
@@-1+1@@
-snakezero
```
+这段是后来加的,此时，我们可以再次使用组合命令**git add** 和 **git commit** 将我们的工作提交到版本库中。
``
$git add snake
$git commit -m "new day for git"
``
实际上，如果要提交的文件都是已经纳入 git 版本库的文件，那么不必为这些文件都应用 git add 命令之后再进行提交，下面的命令更简捷并且和上面的命令是等价的。<br>
`$git commit -a -m"new day for git"`

# 个人学习的markdown的一些语法 
### < --Headers (标题部分) -->
#   ``#这是h1``  
  ##   ``##这是h2``  
   ######  ``######这是h6``

### <-- Emphasis (字体部分) -->
* 语法 
 ```
 *这样写出来的是斜体字*                   
_这样写出来的也是斜体字_              
**这样写出来的是加粗的字**                   
__这样写出来的也是加粗的字__         
_你也**可以** 组合使用他们_            
这是一个 ~~删除线~~                 
**~~斜粗体删除线1~~***	        	  
~~***斜粗体删除线2***~~    
```
* 示例效果 <br>
 *这样写出来的是斜体字*                   
_这样写出来的也是斜体字_              
**这样写出来的是加粗的字**                   
__这样写出来的也是加粗的字__         
_你也**可以** 组合使用他们_            
这是一个 ~~删除线~~                 
**~~斜粗体删除线1~~***	        	  
~~***斜粗体删除线2***~~   

### <--- Unordered (列表) -->
##### （1）无序列表语法和效果：<br>
使用 * ，+ ，- 表示无序列表。 <br>
注意：符号后面一定要有一个空格，起到缩进的作用。<br>
举例：
```
- 无序列表1  
+ 无序列表2
* 无序列表3
```
- 无序列表1
+ 无序列表2
* 无序列表3
##### （2）有序列表语法和效果：<br>
使用数字和一个英文句点表示有序列表。 <br>
注意：英文句点后面一定要有一个空格，起到缩进的作用。<br>
举例：
```
1. first
2. second
3. third
```
1. first
2. second
3. third
##### （3）有序列表 + 无序列表语法和效果：<br>
 ```
 * Item 1 <br>
 * Item 2 <br>
   * Item 2a <br>
   * Item 2b <br>
 ```
* 呈现效果:
* Item 1
* Item 2
  * Item 2a
  * Item 2b

ATTENTION注意事项：在使用列表时，只要是数字后面加上英文的点，容易无意产生列表，比如2019.11.13 这时候想表达的是日期，可能就把它被误认为是列表。<br>解决方式：在每个点前面加上\就可以了。 

### <-- picture (图片) -->
基本格式：![alt](URL title)
<br>URL即图片的url地址，如果引用本仓库中的图片，直接使用相对路径就可了，如果引用其他github仓库中的图片要注意格式，即：仓库地址/raw/分支名/图片路径

### <-- link (链接) -->
* 链接外部URL  http://github.com - automatic!   
   eg：```[GitHub](http://github.com)```  <br>效果：[GitHub](http://github.com)
* 链接本仓库里的URL  [照片](./照片)

### <-- anchor (锚点) -->
锚点其实就是页内超链接。比如我这里写下一个锚点，点击回到目录，就能跳转到目录。 在目录中点击这一节，就能跳过来。<br>
注意：在简书中使用锚点时，点击会打开一个新的当前页面，虽然锚点用的不是很舒服，但是可以用注脚实现这个功能。 <br>
语法：`[回到顶部](#readme)`(语法说明：在你准备跳转到的指定标题后插入锚点{#标记}，然后在文档的其它地方写上连接到锚点的链接.)   
效果：[回到顶部](#readme)	

### <--常用技巧-->
#### (1)换行
* 方法1: 连续两个以上空格+回车 
* 方法2：使用html语言换行标签：
#### (2)emoji表情使用
:EMOJICODE:的格式，详细列表可见: https://www.webfx.com/tools/emoji-cheat-sheet/
<br>但是现在很多markdown工具或者网站都不支持，已知的仅有GitHub是支持的。<br>
* 举例：
``
:smile:
:smirk:
``
* 效果：
:smile:
:smirk:
#### (3)特殊符号
1. 对于 Markdown 中的语法符号，前面加反斜线\即可显示符号本身。
2. 其他特殊字符，需要参考这个网站：https://unicode-table.com/cn/
#### (4)分割线
你可以在一行中用三个以上的星号( * )、减号( - )、底线( _ )来建立一个分隔线，行内不能有其他东西，可以在星号或是减号中间插入空格。<br>
* 举例：
```
--------------
**************
______________
```
* 效果：
--------------
**************
______________
### 最后强推的  _学习圣地[（完结）（小甲鱼）数据结构和算法_哔哩哔哩 (゜-゜)つロ 干杯~-bilibili  ](https://www.bilibili.com/video/av2975983)
