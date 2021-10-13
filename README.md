# development-env
使用 docker-compose 快速构建开发环境。 

### 快速上手

Sail 的大部分操作都是通过可执行文件 ./vendor/sail/bin/sail 来执行。

首先需要设置快捷命令：
```
alias sail='bash vendor/sail/bin/sail'
```

或使用软链`ln -s /vendor/sail/bin/sail sail`

重启终端，即可直接 sail up 而不是 ./vendor/sail/bin/sail up。
```
$ sail up
```

是启动容器的命令，对应的关闭容器：
```
$ sail down
```

使用参数 -d 来启动 Sail 容器，让其在后台运行：
```
$ sail up -d
```
查看当前正在运行的容器情况：
```
$ sail
```
进入容器内部：
```
$ sail shell
```

### PHP服务启动

修改 `/vendor/sail/runtimes/[php-8.0/php-7.4]/supervisord.conf` 启动服务
```
command=/usr/bin/php -d variables_order=EGPCS -t /var/www/html/code/YourProjPath -S 0.0.0.0:80
```

### 数据库配置、端口转发
通过修改 .env 文件来实现。

MySQL:
```
FORWARD_DB_PORT=3306
DB_DATABASE=dev
DB_USERNAME=sail
DB_PASSWORD=password
```

Redis
```
REDIS_PASSWORD=null
REDIS_PORT=6379
FORWARD_REDIS_PORT=6379
```

>> 基于 Laravel/Sail 修改自用。 [搭建 Laravel Sail 开发环境](https://learnku.com/docs/laravel-development-environment/8.x/what-is-laravel-sail/10329)