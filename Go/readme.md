#使用

##服务使用(centos 7 ubuntu 16.04)
1. 普通用户设置

```
 $ systemctl enable docker
 $ cd /etc/systemd/system/multi-user.target.wants
 $ vi docker.service //前提是该目录下有docker.service文件
 $ 在`ExecStart`这一行末尾添加 `--insecure-registry=101.200.132.112` (其中`101.200.132.112`即为Harbor仓库的IP地址)
 $ sudo systemctl daemon-reload
 $ sudo systemctl restart docker
 $ docker login 101.200.132.112
 $ 输入用户名和密码
```

2. pull/push镜像

```
 # testproject对应Harbor上的一个项目
 $ docker tag ubuntu:14.04 101.200.132.112/testproject/ubuntu:14.04
 $ docker push 101.200.132.112/testproject/ubuntu:14.04 
``` 


##镜像仓库操作
1. 安装: install_harbor.sh
2. 重启: 

```
在harbor目录下，即有`docker-compose.ymal`的目录下：

 $ docker-compose down
 $ ./prepare
 $ docker-compose up -d
 $ docker ps //查看状态，会启动6个容器

```