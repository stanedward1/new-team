## 前言
- 我的GitHub名称：weillfrog1
- 主页地址：  
https://github.com/wellfrog1/working

## 本周的课外学习计划

1.连续完成日常晚上带初中小崽生活（好吧，带孩子真的不容易，算是体验生活了一次，hahah）  
2.学习API接口调用的原理与方法，完成阿里云认证（貌似这段时间0元，搞一下，搞一下）  
3.复习java图形界面设计  
4.学习Github的使用  
5.学习git，markdown的基础使用方法  

------

## 本学期的课外学习计划

1.带崽生活（完成进度5/6；再带崽我是🐕，我是🐕）  
2.学习教师资格证的考试内容  
3.学习软考相关考试内容（已完成，我尽力了QAQ）  
4.学习c#语法，与unity3D的使用  
5.复习数据结构与算法与大学数学  
6.攒钱，旅行，增加见闻  

------

## git学习
- 理解  
  git对于我来说属于一个全新接触的东西，我说一下暂时我对于git的理解：git是一个分布式项目版本控制系统，它是由c语言开发完成的（永远万能的C），对于一个发布人即将发布的项目可以实现存档功能，例子：**进度类游戏通关时的存档，手机系统版本的回溯等**，暂时对于git的理解，不是很成熟
- 实践操作中遇到的一些问题    
  1.git add 文件名:添加或修改的文件到缓存区  
    ps：此命令添加内存为0的文件是会出现 **fatal: pathspec '文件名' did not match any files**，说明在本地目录里没有这个文件。
解决办法 1.手动创建一个文件 2.通过git命令创建touch readme.txt  
  2.git commit -m "内容描述" ：缓存区的内容提交码云 （"存档")
  Linux系统下此命令为单引号‘ ’，windows系统下次命令为双引号“ ”，虽然windows下的Git Bash的编写很像Linux，但如果搞混用单引号‘  ’则会出现**did not match any file known to git**这样的提示，值得注意。  
  3.**warning: LF will be replaced by CRLF in read.txt.
The file will have its original line endings in your working directory**  
   这个问题解释起来有一点点复杂，但正常在windows系统下出现这样的提示时，**啥也别做，啥也别做！！**虽然这是一个警告，但这个警告能够保证项目团队正常**跨系统**git操作代码，使用者不必进行任何修改。  
   以上是本周我在学习git操作时所遇到的小问题，在今后的学习发现问题我会陆续更新，但大部分原因或是在命令的使用上存在失误，或是不理解命令的原理而进行的错误使用，所以在git的学习上要认真，不过好在git可以进行“存档”来保存版本，所以不会出现因为一个错误命令而影响整体的情况。任重而道远，继续加油吧。   
   git status 查看文件是否被更改  
   git diff 文件名   显示详细更改情况  
   git log   查看历史更迭  
   git reset --hard 版本号   进行版本跳跃  
   [常用的git命令](https://blog.csdn.net/qq_33061377/article/details/80713140)
------

## markdown
-理解  
Markdown 是一种轻量级标记语言，好吧，对于我来讲也只能总结出这样的一句话，因为Markdown的功能确实强大，Markdown的语法简洁明了、学习容易，而且功能比纯文本更强，因此有很多人用它写博客。Markdown 编写的文档可以导出 HTML 、Word、图像、PDF、Epub 等多种格式的文档。编写的文档后缀为 .md, .markdown。*PS：千万不要使用Windows自带的记事本编辑任何文本文件。原因是Microsoft开发记事本的团队使用了一个非常弱智的行为来保存UTF-8编码的文件，他们自作聪明地在每个文件开头添加了0xefbbbf（十六进制）的字符，你会遇到很多不可思议的问题，比如，网页第一行可能会显示一个“?”，明明正确的程序一编译就报语法错误，等等，都是由记事本的弱智行为带来的。*ps部分选自廖雪峰的官方网站。。  虽然markdown所能实现的功能众多，但目前我的理解确实还是处于这样的初级阶段。  
-Markdown命令    
 关于Markdown命令的总结，简书高鸿祥的总结比较详细，命令不熟的同学可以时常翻阅，[Markdown语法](https://www.jianshu.com/p/191d1e21f7ed)  
-VSCODE    
做为Markdown的几种常用的编译器中的一个，强烈安利**VSCODE**，谁用谁知道。


------

## 资源推荐  
### git与github的学习  
1.[廖雪峰的官方网站](https://www.liaoxuefeng.com/wiki/896043488029600)简单易懂，可边学边操作，安利一波  
2.[腾讯课堂](https://ke.qq.com/course/list/git)质量可以，讲解比较清晰，但部分付费，不是非常推荐,部分免费资源可在b站搜索到  
### Markdown的学习  
1.[Markdown使用教程（1小时从小白到精通）](https://www.bilibili.com/video/av68984507?from=search&seid=11721757716234169065)  
### 数据结构
**有关复习数据结构同学可以选择《大话数据结构》比较通俗易懂，容易上手**
