<p align="center">
    <img width="100" src="https://github.com/codePlaceOfficial/Resources/blob/master/logo.png?raw=true" alt="codeplace logo" style="border-radius:20px"/>
</p>

<p align="center"><b>codeplace</b> 一款完全开源的WebIDE</p>

### 技术简介
> 采用前后端分离开发，前端采用React，后端采用nodejs。
> **前端**
> 完全采用函数式组件及React hooks开发，集成了MonacoEditor及Xtermjs，前后端使用websocket交互，使用socketIO基于事件驱动运行。
> **后端**
> 采用nodejs + chokidar + dockerode + docker
> 自动创建并管理docker容器，自动管理并暴露docker流，在前端将xterm接入该流中模拟终端

### 各仓库介绍
> [codeplace-client](https://github.com/codePlaceOfficial/codeplace-client) : 前端，基于React开发，使用create-react-app创建管理
> [codeplace-server](https://github.com/codePlaceOfficial/codeplace-server) : 后端，由express框架构建

_virtualFile_:
> 用于实现前后端文件双向同步,前端文件修改会同步到后端，通过终端手动修改后端文件时也会自动推送到前端，并且支持按需获得文件内容节省流量
[virtualFileClient](https://github.com/codePlaceOfficial/virtualFileClient): 运行在前端用于管理文件系统，接收后端传来的文件操作事件，进行虚拟文件操作，并生成相应的obj格式的虚拟文件
[virtualFileServer](https://github.com/codePlaceOfficial/virtualFileServer)：运行在服务器端接受前端发来的文件操作事件进行相应，并且会监控本地文件的改动自动将文件变动生成事件推送给前端
[virtualFileEvent](https://github.com/codePlaceOfficial/virtualFileEvent)：生成并推送文件操作事件，在virtualFileClient和virtualFileServer中均有使用。

> [sandbox](https://github.com/codePlaceOfficial/sandbox)：用于维护并管理docker容器实例，并使用class包装，使用codeplaceofficial/compiler:0.2镜像，可以直接运行代码和得到tty流
> [compiler](https://github.com/codePlaceOfficial/compiler):存储dockerfile文件，用于构建codeplaceofficial/compiler镜像，基于ubuntu:20.04修改,集成了c/c++,ruby,python,go,nodejs,java,rust……等运行环境，使用zsh作为默认终端环境

### 视频演示


### 快速开始
``` bash
# 拉取代码
git clone https://github.com/codePlaceOfficial/codeplace.git
git submodule update --init --recursive

# 拉取docker镜像
docker pull codeplaceofficial/compiler:0.2

# 使用npm或者yarn安装依赖
git submodule foreach --recursive yarn # or
git submodule foreach --recursive npm

# 开启服务器
cd codeplace-server && yarn dev
# 开启react
cd codeplace-client && yarn start
```
