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