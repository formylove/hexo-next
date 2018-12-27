### 第一步：从官方镜像库里拉取镜像 <kbd>ansyxz/hexo-next</kbd>
```
docker pull ansyxz/hexo-next
```

### 第二步：将挂载点所需的配置以及资源文件从github版本库下载至本机并解压到同一目录下，比如/app/hexo/目录下，[点击下载hexo-next配置以及资源文件](https://github.com/formylove/hexo-next/archive/master.zip)。
#### 各个文件以及目录作用
* <kbd>conf/hexo.yml</kbd>：包含hexo的相关配置
* <kbd>conf/next.yml</kbd>：包含nexT主题的相关配置
* <kbd>next/source/images/</kbd>：放置网站图片资源，主要包括收款码，logo，头像等
* <kbd>source/</kbd>：保存文章，about/categories/tags的页面以及文章用到的图片

### 第三步：修改 <kbd>conf/hexo.yml</kbd>配置文件
> 其中<kbd>conf/next.yml</kbd>是hexo框架的配置文件，其中需要设置网站名称（<kbd>title</kbd>），网站作者（<kbd>author</kbd>），网站描述（<kbd>description</kbd>），网站关键词（<kbd>keywords</kbd>），网站网址（<kbd>url</kbd>）。


### 第四步：修改 <kbd>conf/next.yml</kbd>配置文件
1. 首先祭出nexT官网详细的配置说明：[nexT](https://theme-next.iissnan.com/getting-started.html)，里面详细介绍了配置文件配置的配置细节

2. 必须要提前配置的配置项目我已经放在了<kbd>conf/next.yml</kbd>文件的开头部分，其中包括菜单以及菜单图标（<kbd>menu</kbd>），页脚（<kbd>footer</kbd>），联系方式以及社交账号（<kbd>social</kbd>），备案（<kbd>beian</kbd>）

3. 配置网站图标（<kbd>favicon</kbd>），网站抬头的logo（<kbd>custom_logo</kbd>），侧边栏个人头像（<kbd>avatar</kbd>），打赏收款码（<kbd>reward</kbd>），具体操作方法（以网站图标为例）：
3.1 将想要的网站图标图片放置于本地<kbd>next/source/images/</kbd>目录下
3.2 将<kbd>conf/next.yml</kbd>的<kbd>favicon</kbd>属性修改为图片的文件名，其中的<kbd>small</kbd>属性对应16×16大小的图片，<kbd>medium</kbd>属性对应32×32大小图片
4. 配置第三方文章评论系统Valine，教程 ☞ [Valine](https://www.jianshu.com/p/dda25ffcfd43)

### 第五步：挂载配置以及资源文件并启动（需要将命令中的 /your/path替换为你本地path）
```
docker run --name next -ti -p 80:4000 
-v /your/path/conf:/var/app/moshuier/conf/ \
-v /your/path/source:/var/app/moshuier/source/ \
-v /your/path/next/source/images/:/var/app/moshuier/themes/next/source/images/  \
ansyxz/hexo-next
```
### 第六步：启动成功后，配置后台管理Admin的登陆用户名以及密码

#### 其中需要Admin插件为博客后台编辑插件，具体操作如下：
1.  启动 Hexo 后在浏览器中输入后台地址：yoursite.com/admin（此处yoursite.com为你的域名或者ip），此时的后台还没有登陆用户密码验证

2. 在Admin页面上接着打开<kbd>Settings</kbd> > <kbd>Setup authentification</kbd>

3. 填写用户名密码加密字符的信息
![image.png](https://upload-images.jianshu.io/upload_images/2062562-2481597e2c14080c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


5. 将生成的信息复制到<kbd>conf/hexo.yml</kbd>文件的<kbd>admin</kbd>属性下的对应字段中。
![image.png](https://upload-images.jianshu.io/upload_images/2062562-54d5da1c93897716.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



6. 重启docker

#### 以上是所有部署操作
如果你觉得我的docker对你有所帮助，请star一下我的github哦
