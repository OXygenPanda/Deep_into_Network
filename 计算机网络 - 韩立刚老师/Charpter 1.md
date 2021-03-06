<p align='center'>
<a href="https://oxygenpanda.github.io/" target="_blank"><img alt="Website" src="https://img.shields.io/badge/博客-劳振煜的知識倉儲-faf2f2.svg?style=flat-square&logo=Blogger"></a>
<a href="https://www.github.com/OXygenPanda" target="_blank"><img src="https://img.shields.io/badge/Github-@劳振煜-f3e1e1.svg?style=flat-square&logo=GitHub"></a>
<a href="https://i.loli.net/2020/11/11/SBZ2mFJGKLjUtTO.jpg" target="_blank"><img src="https://img.shields.io/badge/微信-@OXygen-f1d1d1.svg?style=flat-square&logo=WeChat"></a>


# 计算机网络 第一章

>   计算机网络第一章的主要内容是 : 概述

## 课程安排

第一章 : 概述

第二章 : 物理层

第三章 : 数据链路层

第四章 : 网络层

第五章 : 运输层

第六章 : 应用层

第七章 : 网络安全

第八章 : 因特网上的音频,视频服务

第九章 : 无线网络

第十章 : 下一代因特网

## 计算机网络在信息时代的作用

21世纪的特征 : 数字化, 网络化, 信息化

网络化 : 三网(电信网络, 计算机网络, 有线电视网络)

计算机网络 : 因特网, 其他网络(政府网络, 军用网络)

### 计算机网络的重要功能

连通性 : 彼此联通, 交换信息

共享 : 信息共享, 软硬件共享(软 : ssh ; 硬 : 打印机等设备)

## 因特网概述

终端到网络(路由器)的距离大约是100米, 路由器与路由器的连接扩展了网络的距离和接入网设备的数量.

### 概念

网络 : 许多计算机连接在一起

互联网 : 许多网络连接在一起 (internet)

因特网 : 全球最大的一个互联网 (Internet, 使用 TCP/IP 协议)

### 因特网发展的三个阶段

1st : ARPANET向互联网发展 (上世纪60年代 - 80 年代中期)

-   1969年 分组交换网
-   1975年 互联网
-   1983年 TCP/IP (因特网起源)

2nd : 三级结构的因特网 (上世纪80年代中期 - 90 年代初期)

-   分层次, 比如 : 学校网 - 区域网 - 主干网(带宽 : 45 M)

3rd : 多层次ISP结构的因特网

-   ISP : Internet Service Provider 因特网服务提供商
-   第一层ISP - 第二层ISP - 第三层ISP(提供接入) - 校园网等
-   如果服务器需要提供的客户范围较小, 应该接入越低层的ISP

### 因特网的标准化工作

因特网协会 : ISOC

因特网体系结构委员会 IAB :

-   因特网研究部 IRTF :
    -   因特网研究指导小组 IRSG
-   因特网工程部 IETF :
    -   因特网工程指导小组 IESG

### 因特网的组成

**因特网的核心部分**

**因特网的边缘部分**

主机之间的通信方式 :

-   客户端服务器方式 (Client / Server 方式)
-   对等方式 (Peer-to-Peer 方式)

数据交换方式 :

-   电路交换 (Circuit Switching)
    -   交换机同时只能提供网络中的两个终端通信
    -   过程 : 申请占用通信资源, 一直占用通信资源, 释放通信资源
    -   适用于 : 实时性通信, 核心路由器之间可以使用电路交换
-   报文交换 (Message Switching)
    -   报文一般比分组长的多
    -   报文交换的时延较长
-   分组交换 (Packet Switching)
    -   完整的一个数据包称为报文, 需要分为多个组进行发送
    -   每一个分组带上一个首部
    -   分组的优势在于, 通信时路径可以复用
    -   接收端去电首部后, 拼接分组成报文
    -   路由器有存储转发功能
    -   优点 : 高效, 灵活, 迅速, 可靠
    -   问题 : 时延, 开销

## 计算机在我国的发展

中国在1994年4月20日正式接入互联网.

## 计算机网络的类别

计算机网络最简单的定义 : 一些互相连接的, 自治的计算机的集合

作用范围(使用的技术) :

广域网 : WAN (花钱买服务, 花钱买带宽

城域网 : MAN

局域网 : LAN (自己购买设备, 带宽固定, 自己维护, 距离100米之内)

使用者 : 公用网, 专用网

拓扑结构 : 总线型, 环型, 星型, 树型, 网状

交换方式 : 电路交换, 报文交换, 分组交换

工作方式 : 资源子网, 通信子网, 接入网

## 计算机网络的性能

以下5点是性能指标 :

### 速率

速率是指连接在计算机网络上的主机在**数字信道**上传送数据位数的速率, 也称为 data rate 或者 bit rate. 单位是 b/s kb/s Mb/s Gb/s

一般来说, 运营商告诉的100M是指100Mbps, 转换成下行速率是 100 / 8 = 12.5 Mbit / s

### 带宽

带宽是指数据通信领域中, **数字信道**所能传送的最高速率

### 吞吐量

吞吐量是指在单位时间内通过**某个网络**的数据量

### 时延

时延 = 发送时延 + 传播时延 + 处理时延 + 排队时延

发送时延 = 数据块长度(比特) / 信道带宽(比特/秒)

传播时延 = 信道长度(米) / 信号在信道上的传播速率(米/秒)

处理时延 = 网络节点存储转发处理时间

排队时延 = 网络节点缓存队列排队时间

### 利用率

信道利用率 = 有数据通过时间 / (有 + 无) 数据通过时间

网络利用率 = 信道利用率加权平均值

D = D0 / (1 - U) [D0 : 网络空闲时延 D : 网络当前时延 U : 信道利用率]

以下7点是非性能指标 : 费用, 质量, 标准化, 可靠性, 可扩展性, 可升级性, 管理与维护

## 计算机网络的体系机构

### 概念

ISO : 国际标准化组织

OSI/RM : 互联网法律上的国际标准

TCP/IP Suite : 因特网事实上的国际标准

Network Protocols : 数据交换遵守的规则, 标准或约定

网络体系结构 : 计算机网络各层及协议的集合

### OSI 参考模型

**OSI 是七层模型 :**

​	应用层 - 能够产生网络流量, 能够和用户交互的应用程序

​	表示层 - 加密, 压缩, 编解码 (开发人员考虑)

​	会话层 - 服务和客户端建立的会话 查木马 netstat -nb | more

​	传输层 - 可靠传输建立会话, 不可靠传输不建立会话(QQ发消息, DNS解析), 流量控制

​	网络层 - IP地址编址 选择最佳路径 动态路由

​	链路层 - 数据如何封装 为数据包添加物理层地址(MAC地址)

​	物理层 - 电压 接口标准

**分层的作用 :** 1.标准化 ; 2.降低耦合度

开发者考虑应用层到会话层, 网络工程师考虑传输层到链路层

**网络排错 :** 从底层往上检查(比如 : 先看网线, IP, 浏览器检查)

**网络安全和OSI参考模型 :**

​	物理层安全 - 给别人提供了接入网络的机会

​	链路层安全 - ADSL密码, 无线网卡密码

​	网络层安全 - 网关设置内网中某些网段可以访问外网, 某一些不可以

​	应用层安全 - SQL注入漏洞, 上传漏洞(文件类型检查)

### TCP/IP模型

**TCP/IP 是五层模型 :**

​	应用层

​	传输层

​	网络层

​	链路层

​	物理层

**开放系统信息交换涉及的概念 :**

实体 : 交换信息的硬件和软件的进程

协议 : 控制两个对等实体通信的规则

服务 : 下层向上层提供服务, 上层需要使用下层提供的服务来实现本层的功能

服务访问点 : 相邻两层实体间交换信息的地方

**TCP/IP 模型的数据单元 :**

​	应用层 - 传输数据单元 PDU

​	运输层 - 运输层报文

​	网络层 - IP数据报(IP分组)

​	数据链路层 - 数据帧

​	物理层 - bits
