---
title: ue4_vs2017_install
tags:
  - ue4
  - vs2017
  - c++
categories:
  - game
date: 2019-05-22 22:05:12
---
## UE4安装相关

### 版本

1、Unreal Engine : 4.22.0-5660361+++UE4+Release-4.22

2、Visual Studio Community 2017 : 15.9.11

### 问题

1、Universal CRT 

    ERROR: Visual Studio 2017 requires the Universal CRT to be installed.

  解决：修改vs2017的安装组件，单个组件中寻找`用于 CMake 的 Visual C++ 工具`,安装即可。

2、vs 2017 30天授权

  vs 2017 仅有30天评估时间，超过这个时间后，需要注册微软账号。注册登录即可