# open-falcon_install
open-falcon docker-compose快速安装记录

1. 安装mysql（此处不记录。设置用户密码即可），初始化数据库表结构。db_schema目录下为建库表语句。
2. 安装redis（此处不记录。所有配置默认）。
3. 将docker-compose文件和两个Dockerfile文件放在同一目录下，执行以下命令部署：
```
docker-compose up -d
```
4. docker exec进入容器内，执行以下命令启动相关服务:
```
./ctrl.sh start all
```
执行后可使用 ./open-falcon.sh check 命令查看服务是否正常启动，如存在服务未成功启动，可在./logs目录下查看日志。
5. 服务正常启动后，此时输入 ip:8081 应该可正常打开网页，注册帐号成功登录，过一会应该就会有机器出现。

# 几点说明
1. Dockerfile使用github最新官方源码编译。
2. docker-compose默认链接docker容器版mysql和redis，mysql帐号密码默认使用root和123456。如直接在宿主机安装数据库，docker-compose文件需要做相关修改。
3. 前端容器默认未开放8081端口，我使用了docker版nginx直接链接了open-falcon容器，反向代理了8081端口。如不实用反向代理，请修改docker-compose文件，映射出8081端口。
4. 监控多台机器主要在机器上启动agent服务，修改agent配置文件，位置在 ./agent/config/cfg.json ，将transfer和heartbeat模块的地址改成管理机地址。
5. 要注意，默认开放注册功能，所有人均可注册，用户配置完成后需要关闭注册功能。修改 ./api/config/cfg.json 文件，将 signup_disable 改成 true，重启服务即可关闭注册。
6. 默认安装邮件网关，配置后即可使用。
