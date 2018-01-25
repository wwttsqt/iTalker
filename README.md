使用MD设计的高效IM APP，http://coding.imooc.com/class/100.html

## 非常重要的事
- **群文件/代码文件夹/TXT文件有重要内容，请提前查看！！！**
- [常见问题解决方案](https://github.com/qiujuer/iTalker/issues)


## 盗版
> 我非常热衷开源，但是我希望大家都能尊重最初的作者，以上的技术全部都在我的实战课程中，欢迎购买课程支持我继续产出高质量内容。

最新发现很多人拿着课程的原版代码贴到自己项目中，贴进去无所谓，文件中有著名出处就好，但是我非常反感贴进去后还说是自己做的朋友；这就不厚道了哈。

我想大家都是圈子里的人，要知道圈子不大，很容易我就看到了；虽然看到了也不能怎么你。但是我想要是我推动一下这些事情，你以后的职业生涯还是会有污点的。


## 如何学好课程？
我应该如何学好课程？

我想你应该问问你自己这句话，课程买了不是用来装B，因为单凭一个课程你还没法装B，我也没达到那么高的境界。

## 心态

言归正传，学习这门课程，你首先应该摆正你的心态，对于哪些一来就说这里不会哪里不好的同学，其实老师真的很难伺候。

什么样的心态才算正确？

这在课程第一节中就讲过了，你不需要畏难，你不需要懂全部的技术，你只需要放空心态，然后跟我的步骤走就好。

对于那些只学过Android的朋友学习服务器开发其实不必担心，最难的就是环境搭建和项目建立，这个步骤很繁琐容易出错，老师也没那么多时间规划去讲，但是你Android开发都能完成，又怎么不能完成服务器的环境搭建呢？相信你自己！

而对于只会Java的朋友，我想这才是比较困难的，因为Android说简单却需要学习很多，如果你属于这类，你联系我，我有入门教程。

OK，环境心态准备好了后，就跟着我一起开发吧。

## debug

在开发过程中你会遇到软件的重重崩溃，或者接口不是预期等情况，其实只要代码在你手中，不是环境问题，那么99%可以通过debug调试解决。

这个部分我想是你们的弱点所在，后续抽时间我完成一篇文章给你们讲讲，现在你们只要记住遇到问题加断点调试，调试是程序员开发软件的基础必备技能，越早学好，你的优势越大。


## 常见问题
### 服务器运行没有看见欢迎界面

对于这个问题只可能出在3个地方：

1. 环境没有搭建好。
  > 对于这个情况你需要反复确定你的tomcat服务器已经可以在本地跑起来；idea不是社区版本，社区版本不提供web支持。
  > 对于部分用户电脑tomcat安装在系统目录需要给tomcat目录设置所有用户可读写权限，win用户在文件夹属性-安全里边，Mac用命令解决。

2. 代码没有写对，这个部分出在build文件中的依赖项目写错的情况，和群里代码对比即可。

3. gradle依赖未完成，服务器的运行依赖于很多框架的支持，这些都是通过gradle来完成的，所以确保gradle版本正确，你的网络正常，目前电信没问题，出问题的大部分是网通，长城等同学。

### 数据库没有生成表

> 对于这个问题其实你把课程好好的看看，看清楚，看完整了，那么自然解决了。

那么问题在哪儿？问题一般来说是因为你没有完成初始化代码调用，没有调用初始化，数据库自然不会去做初始化操作。


### 图片画廊无权限崩溃

对于这个，你想说你已经添加了权限为什么还是崩溃？很简单:

- Android6.0 以上设备需要动态授权，遇到这样的问题，要么去设置-APP-设置所有权限为允许；要么你往后接着看，后面章节有权限授权讲解。
- Android7.0 以上需要使用Provider进行文件夹目录操作，百度一下你就知道怎么办了；So Easy～

### XXX_Table 类未找到

> 该问题出现在手机端，出现的情况无法编译。


1. 首先你需要明白客户端我们使用的是DBflow作为我们的数据库框架，这个框架不同于其他运行时数据库框架，运行时或多或少有一定的延迟，该框架是编译时数据库框架，什么意思呢？就是说数据库所需的东西在编译时自动生成，但是前提是能够编译成功。

2. 既然有这样的条件那么出现XX_Table无法找到时请尝试rebuild操作，如果操作后失败，此时请看错误信息，错误信息或许很多，你可以略过找不到的错误然后看其他，当你看见一个不是找不到XX_Table的错误时，看看详细信息，然后去代码解决他，然后再次rebuild操作即可。

这样做的目的是解决自己的错误，然后通过rebuild让其自动生成对应文件，然后就OK了。

当然或许你看见的全部都是找不到，那么此时你需要检查你的DBflow框架依赖是否正确，同时检查找不到的类包名时候正确。

最正确的做法是：**添加model-rebuild-再写逻辑**


### 基础封装后Loading一直存在不进入主界面

对于该问题检查流程逻辑时候正确，如果都OK，那么看看是否由于个推未正确返回pushid导致的等待。

如果是那么可以确定是个推的问题，个推的SDK有一定可能在部分手机上出现该问题，建议的做法是，在获取pushid的方法上默认返回某一伪造的字符串，该字符串自然无法用于正常使用，只是用于通过第一步让你们可以学习后面的课程，毕竟后面还有很多很多。

对于这个SDK的问题，后面会有另外一篇文章讲解如何升级到最新SDK来解决。

### 学到推送部分，后台发送了消息手机未收到

这个问题分如下步骤检查：

1. 服务器添加断点检查是否真的调用了个推的发送逻辑，如果没有从入口开始断点看看走过的路径来确定问题
2. 第一步没有问题，那么检查手机端是否正确获取到pushid并请求接口进行绑定
3. 检查手机端使用的个推key等参数时候和服务器为一整套，课程所个的无法正常调试
4. 如果全部走过无法解决联系我吧
