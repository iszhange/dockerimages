# dockerimages
dockerfile、docker-compose文件，快速使用docker搭建开发环境

### 索引
- PHP  
PHP镜像，包含composer
直接执行build.(sh|ps1)，即可构建docker image并进入容器
默认安装的是最新的composer，可以通过以下命令切换composer版本:
```
## 切换到v1版本
composer self-update --1

## 切换到v2版本
composer self-update --2
```

- typecho  
web环境是LNMP，各目录如下:
```$xslt
typecho
  |-data // MySQL数据目录，保证数据不会随容器的删除而丢失
  |-html // 网站程序目录
  |-nginx
    |-default.conf // 网站配置文件
    |-Dockerfile
    |-fastcgi.conf
  |-php
    |-Dockerfile
    |-php.ini // PHP配置文件
    |-php-fpm.conf // 以fpm方式运行PHP的配置文件
  |-.env // docker compose环境变量文件
  |-docker-compose.yml
```
  
如何使用？
```$xslt
在typecho目录下
1、编译配置 docker-compose config
2、构建 docker-compose build
3、启动 docker-compose up -d (如果有容器启动失败，执行 docker-compose logs 查看失败原因)
```
至此，访问 127.0.0.1 即可进入安装页面
  
如何自定义域名？
修改`nginx/default.conf`中`server_name`，改成你想要的域名  
停止容器 `docker-compose stop`  
删除容器 `docker-compose rm`  
重新执行 1、2、3 步骤  
  
数据库有问题？  
typecho是不会创建数据库的，需要进入MySQL容器手动创建

数据会不会丢失?  
这个是不会的，MySQL数据目录与网站目录都是将本地目录挂载到容器内的，所有的操作都会保存到本地磁盘
