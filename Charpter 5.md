<p align='center'>
<a href="https://oxygenpanda.github.io/" target="_blank"><img alt="Website" src="https://img.shields.io/badge/博客-劳振煜的知識倉儲-faf2f2.svg?style=flat-square&logo=Blogger"></a>
<a href="https://www.github.com/OXygenPanda" target="_blank"><img src="https://img.shields.io/badge/Github-@劳振煜-f3e1e1.svg?style=flat-square&logo=GitHub"></a>
<a href="https://i.loli.net/2020/11/11/SBZ2mFJGKLjUtTO.jpg" target="_blank"><img src="https://img.shields.io/badge/微信-@OXygen-f1d1d1.svg?style=flat-square&logo=WeChat"></a>


# 计算机网络 第五章

>   第五章的主要内容是 : 传输层

传输层涉及到的协议有 : TCP / UDP

## 传输层两个协议应用场景

### TCP

分段 编号 流量控制 建立会话 netstat -n

### UDP

一个数据包就能完成数据通信 不建立会话 多播

## 传输层和应用层之间的关系

http = TCP + 80

https = TCP + 443

ftp = TCP + 21

SMTP = TCP + 25

POP3 = TCP + 110

RDP = TCP + 3389

共享文件夹 = TCP + 445

SQL = TCP + 1433

DNS = UDP + 53 or TCP + 53

## 应用层协议和服务之间的关系

服务运行后使用 TCP 或 UDP 的某个端口侦听客户端请求

## UDP

UDP 是无连接的, 即发送数据之前不需要建立连接.

UDP 使用尽最大努力交付, 即不保证可靠交付, 同时也不使用拥塞控制.

UDP 是面向报文的. UDP没有拥塞控制, 很适合多媒体通信的要求.

UDP 支持一对一, 一对多, 多对一盒多对多的交互通信.

UDP 首部8字节.

UDP 首部格式 :

| 源端口{2} | 目的端口{2} | 长度{2} | 检验和{2} |

长度 : 2个字节, 指的是头部+应用层数据的长度和.

检验和 : 2个字节, 在计算检验和的时候, 会使用一个伪首部{12}, 包括IP首部的部分字段.

## TCP

TCP 是面向连接的传输层协议.

每一条 TCP 连接只能有两个端点, 每一条TCP连接只能是点对点的(一对一).

TCP 提供可靠交付的服务.

TCP 提供全双工通信.

面向字节流.

## TCP协议特点

### TCP首部格式

首部 : 固定{20} | 可变长 | :

| 源端口{2} | 目的{2} |

| 序号{4} |

| 确认号{4} |

| 数据偏移{4b} | 保留{6b} | URG | ACK | PSH | RST | SYN | FIN | 窗口{2} |

| 检验和{2} | 紧急指针{2} |

变长部分 : | 选项{可变} | 填充至4字节的整数倍 |

序号 : 4字节, 值为当前数据包中第一个字节是整个数据中的第几个字节.

确认号 : 4字节, 接收方告诉发送方下一次应该发送第几个字节的数据包.

数据偏移 : 4位, 表示TCP首部的长度(每一个值代表4个字节, 最大为60字节)

保留 : 6位, 没有用.

URG(urgent) : 紧急位, 1代表不排队, 告诉对方数据停止发送

ACK(acknowledgment) : 确认位, 0代表确认号无效, 1代表确认号有效.

PSH(push) : 1代表接收方需要把当前包直接提交给应用程序.

RST(reset) : 1代表需要重新建立连接.

SYN : 同步位, 1代表建立会话

SYN攻击利用建立连接使计算机处理不过来.

LAND攻击伪造目标主机和目标主机建立连接请求.

FIN(finish) : 1代表要释放连接

... 三次握手的时候, 标记位的变化 :

1.  发送方第一次握手, 由于确认号还没有清零, 所以ACK=0, SYN=1, 序号为0
2.  接收方第二次握手, 序号为0, 确认号为1, ACK=1, SYN=1.
3.  发送方第三次握手, 序号为1, 确认号为1, ACK=1, SYN=0.
4.  发送数据, ACK=1, SYN=0.

窗口 : 2字节, 发送滑动窗口的大小.

检验和 : 2字节, 12字节伪首部和TCP首部和数据的校验.

紧急指针 : 2字节, URG=1时有效, 数值指明紧急数据结束的位置.

选项 : 可选功能 : 告诉数据的大小, 是否允许选择确认.

### TCP如何实现可靠传输

**停止等待协议**

发送端超时重传. 可以在不可靠的传输网络上实现可靠的通信.

这种可靠传输协议常称为自动重传请求ARQ(Automatic Repeat reQuest).

ARQ表明重传的请求是自动进行的, 接收方不需要请求发送方重传某个出错的分组.

停止等待协议优点是简单, 缺点是信道利用率太低.

**超时重传时间的选择**

TCP 每发送一个报文段, 就对这个报文段设置一个计时器. 超过计时器设置的时间, 就重传.

新的RTTs = (1-a) x (旧的RTTs) + a x (新的RTT样本) RFC2988推荐的a值为1/8.

超时重传时间应该略大于上面得到的加权平均往返时间RTTs.

**流水线传输√**

发送方不间断传输, 提高信道利用率.

可靠传输的保障, 发送方维持一个滑动窗口(比如5), 确定了最前方的若干个, 才能往前移动进行发送.

**累计确认√**

接收方确认连续的最大的数据包.

**总结**

以字节为单位的滑动窗口技术

### TCP如何实现流量控制

流量控制往往指在给定的发送端和接收端之间的点对点通信量的控制, 它所要做的就是抑制发送端发送数据的速率, 以便使接收端来得及接收.

### TCP如何避免网络拥塞

出现资源拥塞的条件: 对资源需求的总和 > 可用资源

**慢开始和拥塞窗口**

拥塞控制是一个全局性的过程, 涉及到所有的主机, 所有的路由器, 以及与降低网络传输性能有关的所有因素.

慢开始, 开始以指数增长, 达到慢开始门限.

达到慢开始门限后, 进入拥塞避免阶段, 线性增加.

丢包后, 计算新的慢开始门限, 数据包数量从1开始. 重复.

**快速重传**

接收方知道丢包后, 连续发送3次确认的回应, 发送方重传丢包的数据包.

**快恢复**

因为能够收到三个确认数据包, 所以判定当前网络并不是特别拥堵. 所以, 拥塞窗口不从1开始, 而是从新的慢开始门限开始.

## TCP传输连接管理

传输连接有三个阶段, 即 : 连接建立, 数据传送和连接释放.

TCP连接的建立都是采用客户服务器方式.

三次握手:

1.  SYN = 1, ACK = 0, seq = x
2.  SYN = 1, ACK = 1, seq = y, ack = x + 1
3.  SYN = 0, ACK = 1, seq = x + 1, ack = y + 1

四次挥手:

1.  FIN = 1, seq = u
2.  ACK = 1, seq = v, ack = u + 1
3.  FIN = 1, ACK = 1, seq = w, ack = u + 1
4.  ACK = 1, seq = u + 1, ack = w + 1

<img src="https://i.loli.net/2020/12/04/S8JXm2VILDlCxu5.png"/>

TIME-WAIT 等待 2MSL(防止发给服务器的数据包它没有收到, 服务器再次请求断开连接一直无响应)