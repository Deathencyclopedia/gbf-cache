# gbf-cache
GBF local cache
碧蓝幻想本地缓存.使用本程序还需要配合Nginx和Chrome插件SwitchyOmega

### 原理
Gbf中静态资源均在http://game-a.granbluefantasy.jp域名下,因此可以通过SwitchyOmega将所有静态资源指向本机
再由Nginx将请求转发给gbf-cache,gbf-cache判断本地是否已缓存该资源,未缓存则从服务器下载到本机

### 安装
####GBF
1. 安装Nginx后,将项目中的nginx/nginx.conf覆盖nginx的conf/nginx.conf后启动
2. 配置SwitchyOmega:<br>
*game-a.granbluefantasy.jp->HTTP 127.0.0.1 80<br>
*game-a*.granbluefantasy.jp->HTTP 127.0.0.1 80<br>
3. 启动gbf-cache,在application.properties中可配置缓存路径
####HTTPS
1. 安装fiddle并启动HTTPS
2. 在FiddleScript-OnBeforeRequest增加内容(fiddle/FiddleScript.js)
3. 配置SwitchyOmega:<br>
   tonofura-r-cdn-*.deepone-online.com->HTTP 127.0.0.1 8888<br>