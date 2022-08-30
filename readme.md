# 云备份项目 Cloud-Backup-Project



### 项目功能

---

搭建云备份服务器与客户端，客户端程序运行在客户机上自动将指定目录下的文件备份到服务器，并且能支持浏览器查看与下载，其中下载支持断点续传功能，并且服务器端对备份的文件进行热点管理，将长时间无访问的文件进行压缩存储



### 开发环境

---

- Centos7.6
- vim、g++、gdb、makefile
- Windows10 / VisualStudio 2019



### 项目模块

---

- ##### 服务端

  - 数据管理模块：内存中使用 hash 表存储提高访问效率，持久化使用文件存储管理备份数据
  - 业务处理模块：搭建 http 服务器与客户端进行通信处理客户端的上传、下载、查看请求，并支持断点续传
  - 热点管理模块：对备份的文件进行热点管理，将长时间未访问的文件进行压缩存储，以节省磁盘空间

- ##### 客户端

  - 数据管理模块：内存中使用 hash 表存储提高访问效率，持久化使用文件存储管理备份数据
  - 文件检索模块：基于 C++17 文件系统库，遍历获取指定文件夹下的所有文件
  - 文件备份模块：搭建 http 客户端上传备份文件



### 使用说明

---

项目的源码已全部上传，使用 make 命令调用目录下的 makefile 文件进行生成即可，备份上传的文件将存放在 backup_dir 文件夹下，成为非热点文件后将被压缩转移到 pack_dir 文件夹下；同时目录中的 http 文件夹中存放了可供测试的 html 相关文件，后续可进行进一步的美化