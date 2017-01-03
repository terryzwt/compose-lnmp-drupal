本项目用来基于docker技术快速建立Drupal的开发环境
###前置条件
* 安装好docker和docker-compose
* 安装[Dnsmasq](http://www.thekelleys.org.uk/dnsmasq/doc.html)
或者在/etc/host里面，将.dev的域名，都强制指向到127.0.0.1

###安装
```bash
git clone git@github.com:terryzwt/compose-lnmp-drupal.git
cd compose-lnmp-drupal
docker-compose up -d
```

###代码目录说明
* 代码目录都存放在app/web，如果该文件夹不存在，则手工创建。
* 例如，需要访问的地址是example.dev,则app/web/example是该drupal网站的根目录。
* 如果有app/web/test这个目录，则可以通过test.dev可以访问。

###数据库文件目录说明
* 数据库文件目录是mysql-data。你可以将已经存在的mysql数据库文件，软连接过来，命令如下
```bash
ln -s /var/lib/mysql mysql-data
```
* 如果不介意，则可以直接使用该文件夹存储mysql的数据库文件。

###参考
最终的目录结构如下
<pre>
├── README.md
├── app
│   └── web -> /Users/terry/www
├── docker-compose.yml
├── etc
│   ├── mysql
│   │   └── mysql.cnf
│   ├── nginx
│   │   ├── fastcgi.conf
│   │   ├── fastcgi.conf.default
│   │   ├── fastcgi_params
│   │   ├── fastcgi_params.default
│   │   ├── koi-utf
│   │   ├── koi-win
│   │   ├── mime.types
│   │   ├── mime.types.default
│   │   ├── nginx.conf
│   │   ├── nginx.conf.default
│   │   ├── scgi_params
│   │   ├── scgi_params.default
│   │   ├── servers
│   │   │   ├── drupal8.conf
│   │   │   └── wild-dev.conf
│   │   ├── uwsgi_params
│   │   ├── uwsgi_params.default
│   │   └── win-utf
│   └── php
|___ mysql-data -> /Users/terry/docker/storage/mysql-data

</pre>


