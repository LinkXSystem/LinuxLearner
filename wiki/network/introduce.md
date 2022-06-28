## Linux 网络

- RingBuffer 到底是什么，RingBuffer 为什么会丢包？

- 网络相关的硬中断、软中断都是什么？

- Linux里的ksoftirqd内核线程是干什么的？

- 为什么网卡开启多队列能提升网络性能？

- tcpdump 是如何工作的？

- iptable/netfilter 是在哪一层实现的?

- tcpdump 能否抓到被 iptable 封禁的包？

- 网络接收过程中的CPU开销如何查看？

- DPDK 是什么神器？

- 阻塞到底是怎么一回事？

- 同步阻塞 IO 都需要哪些开销？

- 多路复用 epoll 为什么就能提高网络性能？

- epoll 也是阻塞的？

- 为什么 Redis 的网络性能很突出？

- 在查看内核发送数据消耗的 CPU 时，应该看 sy 还是 si ?

- 在服务器上查看 /proc/softirqs ，为什么 NET_RX 要比 NET_TX 大得多的多?

- 发送网络数据的时候都涉及哪些内存拷贝操作？

- 零拷贝到底是怎么回事？

- 为什么 Kafka 的网络性能很突出？

- 127.0.0.1 本机网络 IO 需要经过网卡吗？

- 数据包在内核中是什么走向，和外网发送相比流程上有什么差别？

- 访问本机服务时，使用 127.0.0.1 能比使用本机 IP（例如192.168.x.x）更快吗？

- 为什么服务端程序都需要先 Listen 一下？

- 半连接队列和全连接队列长度如何确定？

- “Cannot assign requested address” 这个报错你知道是怎么回事吗？该如何解决?

- 一个客户端端口可以同时用在两条连接上吗？

- 服务端半／全连接队列满了会怎么样?

- 新连接的 socket 内核对象是什么时候建立的？

- 建立一条 TCP 连接需要消耗多长时间？

- 把服务器部署在北京，给纽约的用户访问可行吗？

- 服务器负载很正常，但是 CPU 被打到底了是怎么回事？

- 内核是如何管理内存的？

- 如何查看内核使用的内存信息？

- 服务器上一条 ESTABLISH 状态的空连接需要消耗多少内存？

- 我的机器上出现了 3 万多个 TIME_WAIT ，内存开销会不会很大？

- “Too many open files” 报错是怎么回事，该如何解决？

- 一台服务端机器最大究竟能支持多少条连接？

- 一台客户端机器最大能发起多少条网络连接？

- 做一个长连接推送产品，支持1亿用户需要多少台机器？


## 容器虚拟网络

- 容器中的 eth0 和母机上的 eth0 是一个东西吗？

- veth 设备是什么，它是如何工作的？

```
ip link add veth0 type veth peer name veth1

ip link show

ip addr add 192.168.1.1/24 dev veth0
ip addr add 192.168.1.2/24 dev veth1

ip link set veth0 up
ip link set veth1 up

ifconfig

echo 0 > /proc/sys/net/ipv4/conf/all/rp_filter

echo 0 > /proc/sys/net/ipv4/conf/veth0/rp_filter
echo 0 > /proc/sys/net/ipv4/conf/veth1/rp_filter

echo 0 > /proc/sys/net/ipv4/conf/veth0/accept_local
echo 0 > /proc/sys/net/ipv4/conf/veth1/accept_local

ping 192.168.1.2 -I veth0

tcpdump -i veth0
```

- Linux 是如何实现虚拟网络环境的？

- Linux 如何保证同宿主机上多个虚拟网络环境中的路由表等可以独立工作？

- 同一宿主机上多个容器之间是如何通信的？

- Linux 上的容器如何和外部机器通信？
