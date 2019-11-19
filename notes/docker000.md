# 安装 docker-ce

[查看官方提供的全面的安装文档](https://docs.docker.com/install)

# 设置 docker 镜像加速器

国内的网络状况连接国外的站点让人揪心，阿里云提供了免费的docker镜像加速器

申请路径：产品与服务 > 弹性计算 > 容器镜像服务 > 镜像加速器。点击[免费申请阿里云 docker 镜像加速器](https://cr.console.aliyun.com/?spm=5176.8351553.aliyun_sidebar.3.76b71991n6i5lD#/accelerator)

docker配置镜像加速器的方法，请自己查看阿里云镜像加速器页面的操作文档

# 设置 docker 开机自动启动

    sudo systemctl start docker
    sudo systemctl enable docker

# 拉取 docker 镜像

    拉取最新版本的镜像
    command: docker pull [IMAGE_NAME]
    e.g. 
        docker pull redis

    拉取指定版本的镜像 https://hub.docker.com/r/library/[IMAGE_NAME]/tags/
    command: docker pull [IMAGE_NAME]:[TAG]
    e.g.
        docker pull redis:3.2

# 运行镜像实例（已 redis 为例）

    command: docker run [OPTIONS] IMAGE [COMMAND] [ARG...]
    docker官方文档 https://docs.docker.com/engine/reference/commandline/run/

    启动一个持久化开机重启的 redis 实例
    docker run --restart always --name myredis -p 6379:6379 -d redis redis-server --appendonly yes

    --restart   容器重启策略 always 总是重启
    https://docs.docker.com/engine/reference/commandline/run/#restart-policies---restart
        
    --name      redis实例友好名称 myredis

    -p          主机端口映射到redis实例暴露的端口 将 linux:6379 映射到 redis实例:6379

    redis-server --appendonly yes 在最后执行的命令