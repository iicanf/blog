---
title: k8s stand alone 1 base environment
tags:
  - k8s
  - docker
  - hyper-v
  - win 10
categories:
  - architect
date: 2019-07-25 21:23:44
---

## 单机K8S集群1：基础环境

### 背景

近半年本人大部分时间在写业务代码，难度不大，浑浑噩噩，近期觉得有必要折腾下K8S，作为基础，为后续的微服务搭建实验，做个基础。

### 基本环境

1、个人PC

2、4C16G

### 目的

启动两个虚拟机（`192.168.1.101`,`192.168.1.102`），搭配宿主机，模拟3台物理机的场景。

### shell

安装ubuntu 18.04 wsl.

安装mobaXterm，新建wsl session

### 虚拟机

1、启用hyper-v

2、下载ubuntu18.04 server版镜像文件

3、新建hyper-v交换机命名为 `虚拟机专用`  外部网络

4、创建虚拟机，内存默认即可，网络选择新建的 `虚拟机专用`，镜像选择ubuntu的镜像文件，注意选择 `第一代虚拟机`

5、启动虚拟机，注意切换为`国内的源地址`

6、启动成功后，`ssh-copy-id` 部署公钥

7、固定ip

    network:
    ethernets:
        eth0:
             #dhcp4: true
                addresses:
                        - 192.168.1.101/24
                gateway4: 192.168.1.1
                nameservers:
                        addresses:
                                - 175.188.160.254
                                - 175.188.160.154
    version: 2

8、重启虚拟机，重复以上1-8，安装另一台虚拟机，ip固定为`192.168.1.102`

### docker demaon

1、安装docker desktop，成功后暴露daemon的tcp端口，注意使用国内镜像仓库

2、进去ubuntu wsl，安装docker-ce-cli，安装官网教程[ubuntu linux install](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

3、声明环境变量：`export DOCKER_HOST="tcp://0.0.0.0:2375"`

4、检查，执行 `docker ps`，成功列表所有镜像。