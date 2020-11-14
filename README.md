# open-falcon_install
open-falcon docker-compose快速安装记录

1. 安装mysql（此处不记录。设置用户密码即可），初始化数据库表结构。db_schema目录下为建库表语句。
2. 安装redis（此处不记录。所有配置默认）。
3. 将docker-compose文件和两个Dockerfile文件放在同一目录下，执行以下命令部署：
```
docker-compose up -d
```

# 几点说明
1. Dockerfile使用github最新官方源码编译。
2. docker-compose默认链接docker容器版mysql和redis，mysql帐号密码默认使用root和123456。如直接在宿主机安装数据库，docker-compose文件需要做相关修改。
