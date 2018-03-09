1. 下载`tomcat` [http://tomcat.apache.org/](http://tomcat.apache.org/)
2. 解压`tomcat`
3. 部署war

   修改`ROOT.war`中的配置文件`sitemgt.properties`

```
jdbc.url=jdbc:mysql://114.55.173.102:47801/portal?useUnicode=true&characterEncoding=UTF-8
jdbc.username=root
jdbc.password=jkxyx205


#静态文件路径
upload=/Users/rick/jkxyx205/tmp

#图库待同步的文件
gallery_init=/Users/rick/jkxyx205/tmp/gallery_init

#文件服务器 nginx静态文件服务器
fileServer=http://localhost:3000

#截图脚本路径
phantomjs=/Users/rick/jkxyx205/phantomjs-2.1.1-macosx

#建站平台域名
domain=devyean.com:8000
```

4.启动

```bash
/bin/startup.bat
```





