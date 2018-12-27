# hexo-next
ansyxz/hexo-next docker volume挂载,里面包含了next和hexo的配置文件以及资源文件


### 第一步：从官方镜像库里拉取镜像ansyxz/hexo-next


### 第二步：将挂载点所需的配置以及资源文件从github版本库下载至本机同一目录下，比如/app/hexo/目录下

### 第三步：在本机修改<kbd>conf/hexo.yml</kbd>配置文件
> 其中<kbd>conf/next.yml</kbd>是hexo框架的配置文件，其中需要设置网站名称（title），网站作者（author），网站描述（description），网站关键词（keywords），网站网址（url）。


### 第四步：配置下载好的配置文件--<kbd>conf/next.yml</kbd>
1. 首先祭出next官网详细的配置说明：[nexT](https://theme-next.iissnan.com/getting-started.html)，里面详细介绍了配置文件配置的具体细节

2. 必须要提前配置的配置项目我已经放在了<kbd>conf/next.yml</kbd>文件的开头部分，其中包括

3. 配置网站图标（favicon），网站抬头的logo（custom_logo），侧边栏个人头像（avatar），具体操作方法（以网站图标为例）：
3.1 将想要的网站图标图片放置于本地<kbd>next/source/images/</kbd>目录下
3.2 将<kbd>conf/next.yml</kbd>的<kbd>favicon</kbd>属性修改为图片的文件名，其中的<kbd>small</kbd>属性对应16×16大小的图片，<kbd>medium</kbd>对应32×32大小图片


### 第五步：挂载启动

### 第六步：配置后台管理Admin

#### 其中需要admin插件为博客后台编辑插件，具体操作如下：
1.  启动 Hexo 后在浏览器中输入后台地址：http://yoursite.com/admin（此处yoursite为你的域名或者ip），此时的后台还没有登陆用户密码验证

2. Once that's in place, start up your hexo server and going to /admin/ will require you to enter your password.

5. Custom post metadata
To add and edit your own post metadata with the admin interface, add the metadata variable and your custom variables to your hexo _config.yml:

metadata:
  author_id: defaultAuthorId
  language:
You can provide default values that will be used to initialize the metadata of a new post. These can be either primitives or arrays.

6. Contribute!
