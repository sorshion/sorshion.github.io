---
title: vagrant安装与使用
date: 2018-05-29 22:22:29
tags: vagrant
category: 环境配置
---

网上充斥着vagrant安装教程，个人感觉比较简陋，在使用过程中，我把产生的问题，梳理一遍。
 > 注：以下操作都是在windows下，其他系统不做参考
 
### 1. *安装virtualbox*
> 安装完毕后，`最好`修改虚拟电脑位置,vagrant 默认安装在C盘，一般来说C盘都比较小，放在更大空间的盘符里比较合适
> 操作：打开管理器 => 管理 => 全局设定 =>常规 => 默认虚拟电脑位置(假设D:\virtualbox_vms)

### 2. *安装vagrant*
> 正常来说，vagrant命令会自动加载到环境变量里面，若没有，则重新安装，或者参考网上系统变量加载方式

### 3. 配置vagrant
> 1. 项目主路径  D:\vagrant_project
> 2. 虚拟电脑路径 D:\virtualbox_vms
> 3. 从http://www.vagrantbox.es/下载合适的box,这里以centos7为例,放在D:\vagrant_project下

###### 3.1 快捷键`win+R`,输入`cmd`后切换到 **D:\vagrant_project\test01**下
> test01是项目名
###### 3.2 vagrant box add test01 D:\vagrant_project\centos-7.0-x86_64.box
###### 3.3 vagrant init  **// 初始化**
> 此时产生Vagrantfile，这里面可以修改参数，比如改变内存大小，通过ip访问等等
###### 3.4 vagrant up **// 启动**
###### 3.5 vagrant ssh
> 或者3.3步之后修改Vagrantfile,配置ip，就可以通过第三方ssh软件登陆
###### 3.6 vagrant halt   **// 关机**

###### 3.7 `其他命令，自行查找`,eg:vagrant reload,vagrant box list 等

### 4. *扩容box*
一般下载的box空间都不大，这个时候需要扩容
>参考:
>https://gist.github.com/christopher-hopper/9755310
>http://blog.csdn.net/zxjxingkong/article/details/62419379 (main)

### 5. *打包*
###### 5.1 如果网络模式是 private_network 的话，在打包之前需要清除一下private_network的设置，避免不必要的错误
   rm -f /etc/udev/rule.d/70-persistent-net.rules
###### 5.2 vagrant package --output `mycentos.box` --base `centos`
>centos根据具体名称
