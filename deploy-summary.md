# 1.【建站网站】技术

## 1.1 软件技术

* 前端
  * bootstrap
  * sass
  * jQuery 
  * gulp
  * jquery-plugins
  * vue 
* 后端
  * springmvc
  * mybaits

## 1.2架构图

![](/assets/a.png)

# 2. 静态文件目录结构

![](/assets/tree.png)

* **gallery\_init**

  图库需要同步到平台的图片目录，总共25个分类，有25个文件夹，编号1～25。每个文件夹有对应分类的图片，图片名称为图片标签（关键字）`，`多个关键字用，隔开，比如“`美女 范冰冰.jpg`”。  
  点击[http://etmode.com/web/2/gallery](http://etmode.com/web/2/gallery)的按钮`同步图库`后，将会执行同步操作，图库更新完成，tpl-&gt;init-&gt;gallyer会生成相应的图片，

* **site**  
  `新建站点`后，**该**网站产生的相关文件都会存在此目录下。比如发布后的静态页面，快照，全文索引。

* **tpl**

  * **footer**

    7种页脚的9种风格8种配色的截图

  * **header**

    10种页眉9种风格8种配色的截图

  * **style**

    9种风格8种配色7种页脚10种页眉的截图

  * **init**

    `14x5`表示 比例是14:5的默认图片  
    gallyery:图库文件

# 3. 依赖工具（软件）

* nginx

  > Nginx \(engine x\) 是一个高性能的HTTP和反向代理服务器，做端口转发。  
  > 下载地址：[http://nginx.org/en/download.html](http://nginx.org/en/download.html)

* tomcat

  > Tomcat是由Apache软件基金会下属的Jakarta项目开发的一个Servlet容器，按照Sun Microsystems提供的技术规范，实现了对Servlet和JavaServer Page（JSP）的支持，并提供了作为Web服务器的一些特有功能，如Tomcat管理和控制平台、安全域管理和Tomcat阀等。由于Tomcat本身也内含了一个HTTP服务器，它也可以被视作一个单独的Web服务器。但是，不能将Tomcat和Apache HTTP服务器混淆，Apache HTTP服务器是一个用C语言实现的HTTPWeb服务器；这两个HTTP web server不是捆绑在一起的。Apache Tomcat包含了一个配置管理工具，也可以通过编辑XML格式的配置文件来进行配置。  
  > 下载地址：[http://tomcat.apache.org/](http://tomcat.apache.org/)

* mysql

  > MySQL（官方发音为/maɪ ˌɛskjuːˈɛl/“My S-Q-L”\[1\]，但也经常读作/maɪ ˈsiːkwəl/“My Sequel”）原本是一个开放源代码的关系数据库管理系统，MySQL在过去由于性能高、成本低、可靠性好，已经成为最流行的开源数据库，因此被广泛地应用在Internet上的中小型网站中。  
  > 下载地址： [https://www.mysql.com/cn/downloads/](https://www.mysql.com/cn/downloads/)



