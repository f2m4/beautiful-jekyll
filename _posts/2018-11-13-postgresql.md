---
layout: post
title: Postgresql
subtitle: 数据库的世界
bigimg: /img/path.jpg
tags: [postgresql,数据库]
---
# postgresql数据库自学总结
## 安装
> 方法不外乎包直接装和源码安装.  
> 对于初学就直接包安装即可,各平台都有.Android也有啊.良心啦.  
> 源码安装更倾向于定制和运维.具体用的时候在看参数来吧.  
> 万能的docker当然也有.这种最简单.哈哈.我选这个.即便是初学.顺便复习一下docker.  
## 安装之后的解惑
安装好之后是不是可以直接使用了呢?当然不.尤其是对于源码安装的方式.  
1. 用户--专属一个用户  
    这种设计是为了避免postgresql潜在的漏洞会威胁到系统.  
    使用专门的一个用户来管理数据库.(有道理啊)  
    默认用户名postgres,所属组也是postgres.  
    它的home在 /var/lib/pgsql  
    按理说,它拥有的权限越小越好.继续往往看.  
2. 数据库目录--数据簇  
    简单理解是:数据库存放的位置.另外还有一些其他相关的文件,如配置,日志等.
    如何建立呢?  
    ```bash
    mkdir -p ./pgdata/11/{data, backups, scripts, archive_wals}  
    #修改权限700 用户所属组。700可以不用设置initdb的时候会自动收回其它权限
    chown -R postgres.postgres ./pgdata/11 
    chmod 0700 ./pgdata/11/data 
    ``` 
3. 初始化数据库并启动
    ```bash
    initdb -D /pgdata/11/data -W
    pg_ctl init -D /pgdata/11/data -o "-W"
    #上面两条是一样的.设置数据库存放目录，此目录必须为空。并设置密码。
    #启动数据库
    pg_ctl -D /pgdata/11/data -l logfile start
    ```
    以上两块是自定义的建立。默认使用postgres的时候，切换到该用户下直接用就可以。都在该用户的home目录下进行。/var/lib/pgsql/11目录和它的两个子目录：data目录和backups目录。通过service postgresql-11 init命令会初始化/var/lib/pgsql/11/data目录作为数据目录。这样很方便，但是可定制性并不好，建议自己始化数据目录。  
4. 这才是开始  
    ```bash
    #创建数据库
    createdb mydb
    #创建用户
    createuser myname
    psql mydb myname
    #第一个是数据库名，第二个是用户名
    ```

未完......