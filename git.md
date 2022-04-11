### git知识点

#### 准备工作

##### 1、卸载git：

检查git的环境变量，清理环境变量。然后再正常卸载程序。

环境变量是用于在任何地方可以使用全局的git。安装成功后可以不用配置

##### 2、下载：

官网下载（速度慢）： https://git-scm.com

镜像下载（解决官网下载速度慢发问题）: http://npm.taobao.org/mirrors/git-for-windows/ 

##### 3、安装

一直next就可以。安装成功后会有三个可选择的程序。如下：

**git Bash**: Unix与Linux风格的命令行，使用最多，推荐最多,

**git CMD**: windows风格的命令行

**git GUI**：图形界面的Git

#### 基本linux命令，配合git命令的使用

**cd**			改变目录，例如cd project ;进入到名字为project的文件夹下

**cd..**		 退回上一级目录，直接cd进入默认目录

**pwd** 		显示当前目录路径

**ls** 			列出当前目录中的所有文件，两个II列出的内容更为详细



**touch** 在当前目录下，新建一个文件

**mkdir**   在当前目录下，新建一个文件夹



**rm**     删除一个文件

**rm-r**     删除一个文件夹

**rm -rf /**  		递归删除根目录下的所有的文件，切勿尝试，相当于格式化



**mv** 移动文件，mv test.txt project。 test.txt是移动的文件，project是目标文件夹。这两者在同一目录下。

**reset**  重新初始化终端/清屏

**clear** 清屏

**history**  查看历史命令

**help**  帮助

**exit**   退出

#**表示注释**



#### git配置

git config --list --global =  查看配置   ->简写： git config -l -g

![image-20220410163033844](C:\Users\songj\AppData\Roaming\Typora\typora-user-images\image-20220410163033844.png)

需要先把用户的配置的user.name和user.email配置一下，如上图





#### git基本理论

 **git的四个工作区域**

**工作目录**（working directory）

平时存放项目代码的地方

**暂存区（stage/index）**

用于存放你的改动，事实上塔只是一个文件，保存即将提交到的文件列表信息

**资源库(repository)**

本地仓库、就是安全存放数据的位置，这里有提交的所有版本的数据，其中hear指向最新存放入仓库的版本

**远程git仓库(remote directory)**

远程仓库、托管代码的服务器、可以简单认为是你项目组中的一台电脑，用于远程数据交换



#### git 文件操作

文件的状态

```
git status [filename]   //可以看到以下四种文件的状态
```

1、untracked： 未跟踪，此文件在文件夹中，但是没有加入到git库，不参与版本控制，通过**git add**状态变为staged。

2、unmodify： 文件已入库、未修改。即版本库中的文件快照内容与文件夹中完全一致，这种类型文件有两种去处、如果被修改、则变为modified。如果使用**git rm**移出版本库，则变成untracked状态文件

3、modified： 文件已修改。通过**git add**可进入暂存staged 状态，使用git checkout则丢弃修改过，返回到unmodify未修改状态。

4、staged: 暂存状态。执行**git commit** 则将修改同步到库中、这时库中的文件和本地文件一致。本地文件又变为unmodify状态。执行git reset HEAD filename取消暂存，文件状态为modified。



#### git项目搭建

创建本地仓库的方法

1、创建全新的仓库

```cmd
git init
```

2、克隆远程的仓库

```
git clone [github地址]
```



#### git 基本命令

**git init**    =>  初始化git项目（这时会产生一个.git的隐藏文件）

**git add .**   =>  将工作目录的改动添加到暂存区。

**git commit**  => 将暂存区中的内容提交到本地仓库中

**git push**    =>   将本地的仓库提交到远程的仓库某个分支下



**git clone**    =>  将远程仓库克隆到本地仓库

**git pull**     => 将远程仓库拉到工作目录下

**git fetch**

**git checkout**  



#### git 分支操作命令

```
git brance  //列出所有本地分支

git brance -r   //列出所有远程分支

git brance [brance-name]	//新建一个分支，但依然停留在当前分支

git checkout -b [brance]  //新建一个分支并且切换到该分支

git merge [brance]  //合并指定分支到当前分支

git brance -d [brance-name]   //删除分支

git push origin --delete [brance-name]  //删除远程分支
git brance -dr [remote/brance]	//删除远程分支
```

​         





#### 如何忽略不需要提交的文件

创建一个.gitignore文件，里面的写法规则如下

1、忽略文件中的空行或以#号开始的行将会被忽略

2、可以使用linux通配符，例如：*号代表多个字符，?代表一个字符，[abc]代表可选字符范围。{string1,string2}代表可选的字符串等

3、!lib.text             表示例外规则，将不被忽略

4、/temp     表示要忽略的文件，在此目录下，而子目录中的文件不忽略

5、 doc/test.txt    表示要忽略的是此目录下该名称的子目录，而非文件（默认文件或目录都忽略）



#### 远程管理仓库

github/gitee(码云)/公司内部自己搭建的git服务



**本地与远程建立联系，可以免登录将本地的仓库Push到远程的仓库。进行管理。**

1、通过cmd命令行，如下,在电脑上生成.ssh文件，

`ssh-keygen -t rsa`

2、然后在c盘下的用户目录下找到刚刚生成的.ssh文件夹下的id_rsa.pub，以文本方式打开，复制里面的内容。

3、然后打开git网址，找到添加ssh公钥菜单，然后把刚刚复制的内容粘贴下来。   

