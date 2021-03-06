---
layout: post
title: "使用 Docker hub 及其他镜像站点加速下载"
tagline: ""
description: ""
category: 经验总结
tags: [docker, google, cloud, images]
last_updated: 
---

有很多网站可以托管 Docker 镜像， Docker 官方站点 hub.docker.com 速度在国内访问不是很快，不过幸好国内有公司做了 hub.docker.com 的镜像，通过 CDN 优化了下载。Docker Hub 为用户提供无限数量的公开镜像托管服务，但是仅提供一个私有镜像托管。Docker Hub 上镜像分为两类，一类为官方镜像，ubuntu，redis 等等由权威三方开发和维护通过 Docker 官方认证，另一类就是普通用户镜像。

## 使用 registry mirrors
手动修改 Docker 配置 `/etc/docker/daemon.json` 文件

    {
        "registry-mirrors": [
            "加速地址"
        ],
        "insecure-registries": []
    } 

修改其中的 `加速地址`，不同的服务提供的镜像加速地址不一样。记得修改配置之后 `sudo /etc/init.d/docker restart` 重启 docker。下面就总结一下国内的Docker镜像站点。

### DaoCloud
DaoCloud [提供](https://www.daocloud.io/mirror#accelerator-doc)的加速地址:

    http://6ce28dce.m.daocloud.io

这个地址不同用户看起开不一样，可以使用我的，也可以自己注册。

这个地址不知道是不是长久地址，不过失效，可以到他的官方[网站](http://6ce28dce.m.daocloud.io)查看。

### Docker cn
也可以使用 Docker 官方提供的镜像

    https://registry.docker-cn.com

官网[地址](https://www.docker-cn.com/registry-mirror)

### 个人维护的镜像

[mritd](https://mritd.me/2017/03/21/private-maintenance-docker-mirror-registry/)反向代理了主流的三大仓库（Docker Hub，gcr.io，quay.io）。

## docker registries
不得不说的 hub.docker.com，官方提供

### daocloud hub
这是国内 DaoCloud 公司提供的

- https://hub.daocloud.io/

### gcr.io
可以通过下面的链接查看 gcr.io 中存在镜像，类似于直接在 <https://hub.docker.com/> 中搜索查看。

- <https://console.cloud.google.com/gcr/images/google-containers/GLOBAL?location=GLOBAL&project=google-containers>

### 阿里云
这里是阿里云提供的镜像托管服务

- <https://dev.aliyun.com/search.html>

然后[有人](http://dockone.io/question/1216)把 `gcr.io/google-containers` 下所有的 Docker 镜像都同步到了中央库

- <https://hub.docker.com/u/googlecontainer/>

更多的 registry 可以参考[这里](https://github.com/veggiemonk/awesome-docker#registry)

