# open-falcon_install
open-falcon docker-compose快速安装记录

1.安装mysql（此处不记录。设置用户密码即可），初始化数据库表结构。db_schema目录下为建库表语句。
2.安装redis（此处不记录。所有配置默认）。
3.将docker-compose文件和两个Dockerfile文件放在同一目录下，执行以下命令部署：
```
docker-compose up -d
```

