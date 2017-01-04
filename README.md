# CONFIG DOCKER AUTOMATED BUILD WITH GITHUB
## 前提：
   有些镜像可能因为墙的问题，不能访问，那我们需要，但是又下载不了，这时候就很坑爹了。针对这种情况，我们有如下两种方案解决：
####   1.通过代理下载，我们可以安装`squid`代理（不熟悉，不研究）
####   2.借助`github`下载
   下面我们详细说下第二种的实现方法

#### 注：首先你得有`github`和`docker hub`的ID

## 实现：
### 1.登陆到`github`上面，新建一个项目，如下图操作：
![image](https://raw.githubusercontent.com/Leno730/docker-lib/master/images/1.png)


### 2.建好项目后，我们就要开始新建`Dockerfile`(不知道`Dockerfile`作用的，请查阅`docker`的基础知识)

建`Dockerfile`的目的，就是为了使用`dockerfile`里面的from语法的作用，来借用`github`服务器新建我需要的镜像
![image](https://raw.githubusercontent.com/Leno730/docker-lib/master/images/2.png)

上图，先建立文件夹再建立文件，是为了方便我们后面区分镜像包
`Dockerfile`的内容如下：
![image](https://raw.githubusercontent.com/Leno730/docker-lib/master/images/3.png)

### 3.到这里，我们`github`这边就都准备好了，接下来，就要登陆到`docker hub`，然后选择![image](https://raw.githubusercontent.com/Leno730/docker-lib/master/images/4.png)，具体如下：
![image](https://raw.githubusercontent.com/Leno730/docker-lib/master/images/5.png) 

   在第一次新建时，他会要求你关联`github`（上图显示的是我已经关联`github`帐号的页面），你直接输入`github`帐号密码关联即可。
   在你选择了![image](https://raw.githubusercontent.com/Leno730/docker-lib/master/images/6.png)后，就会进入如下页面，要求你选择你在github里面刚新建的项目：

![image](https://raw.githubusercontent.com/Leno730/docker-lib/master/images/7.png)
     
### 4.接下来就要配置你的镜像仓库了
![image](https://raw.githubusercontent.com/Leno730/docker-lib/master/images/8.png)
     建好后如下图
![image](https://raw.githubusercontent.com/Leno730/docker-lib/master/images/9.png)

### 5.镜像库配置好后，我么就要选择进行编译了（因为此时我们的Dockerfile还没有执行，此时，你点击上图中的![image](https://raw.githubusercontent.com/Leno730/docker-lib/master/images/10.png),你会发现并没有镜像文件）
![image](https://raw.githubusercontent.com/Leno730/docker-lib/master/images/11.png) 

### 6.按上述操作，你就编译完成了，你可以在![image](https://raw.githubusercontent.com/Leno730/docker-lib/master/images/12.png)查看当前的一个编译状态，并且可以在![image](https://raw.githubusercontent.com/Leno730/docker-lib/master/images/10.png)中查看编译后的镜像版本
![image](https://raw.githubusercontent.com/Leno730/docker-lib/master/images/13.png)
![image](https://raw.githubusercontent.com/Leno730/docker-lib/master/images/14.png)
     
### 7.执行完上面所有的动作，你就可以去docker服务器里面下载这个镜像了
 ![image](https://raw.githubusercontent.com/Leno730/docker-lib/master/images/15.png)    
     只是下载会比较慢，但是比直接timeout要好很多呀。

#### PS：据说DAOCloud会3小时同步一次docker hub的镜像文件到他自己的镜像库，不知道会不会同步我上传的这个，如果会，那下载就更快了（因为DAOCloud镜像库服务器在国内），这个有待验证。
     


