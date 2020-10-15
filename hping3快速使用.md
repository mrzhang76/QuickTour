# hping快速使用
## 安装
+ window:参考此项目github，快速使用不进行说明  
+ kali:系统预安装  
+ linux:参考此项目github，快速使用不进行说明
  
## 快速使用
+ 常规选项：  
```
  -h  --help      帮助
  -v  --version   版本信息
  -c  --count     发送数据包的次数 
  -i  --interval  包发送间隔时间 (uX为X微秒, 例如 -i u1000)
      --fast      相当于 -i u10000 (一秒发送十个数据包)
      --faster    相当于 -i u1000 (一秒发送100个数据包)
      --flood      尽可能快的发送数据包，不显示结果  
  -n  --numeric   数字输出，象征性的输出主机地址  
  -q  --quiet     退出
  -I  --interface 接口名 (默认为路由接口)
  -V  --verbose   详细显示模式  
  -D  --debug     显示debug信息
  -z  --bind      绑定ctrl+z到ttl           (默认为dst端口)
  -Z  --unbind    取消绑定ctrl+z
      --beep      每收到一个匹配的数据包就发出哔声
```
+ 发送数据包的类型：  
```
  默认     TCP
  -0  --rawip      RAW IP模式，发送带数据的IP头
  -1  --icmp       ICMP模式
  -2  --udp        UDP模式
  -8  --scan       SCAN模式
                   例如：hping --scan 1-30,70-90 -S www.target.host
  -9  --listen     监听模式
```
+ 数据包自定义：  
+ IP:
```
  -a  --spoof      伪造源IP地址
  --rand-dest      随机目的地址模式，详情使用man查询
  --rand-source    随机源地址模式，详情使用man查询
  -t  --ttl        数据包存活时间(默认为64)
  -N  --id         id (默认随机)
  -W  --winid      使用win*系统的ID回应  
  -r  --rel        使ID值顺序输出 (用于估计目标主机流量)  
  -f  --frag       更改包的FRAG，这可以测试对方对于包碎片的处理能力，通过有缺陷的acl  
  -x  --morefrag   此功能可以发送碎片使主机忙于恢复碎片而造成主机的拒绝服务  
  -y  --dontfrag   发送不可恢复的IP碎片，这可以让你了解更多的MTU PATH DISCOVERY  
  -g  --fragoff    设置片段偏移量
  -m  --mtu        设置虚拟mtu,如果数据包比mtu更大，使用--frag选项 
  -o  --tos        服务类型 (默认 0x00), 使用 --tos 获得帮助  
  -G  --rroute     启用RECORD_ROUTE选项并显示路由缓存  
  --lsrr           loose source routing and record route
  --ssrr           strict source routing and record route
  -H  --ipproto    设置IP协议字段，仅在RAW IP模式下适用
```
- ICMP:

```
  -C  --icmptype   icmp类型 (默认为 echo request)
  -K  --icmpcode   icmp代码 (默认为 0)
      --force-icmp 发送全部类型的ICMP (默认只发送被支持的类型)
      --icmp-gw    为ICMP重定向指定网关(默认为 0.0.0.0)
      --icmp-ts    相当于 --icmp --icmptype 13 (ICMP timestamp)
      --icmp-addr  相当于 --icmp --icmptype 17 (ICMP address subnet mask)
      --icmp-help  显示其他选项的帮助  
```

- UDP/TCP:
```
  -s  --baseport   源端口             (默认随机)
  -p  --destport   [+][+]<port> 设置目标端口，缺省为0，一个加号设置为:每发送一个请求包到达后，端口加1，两个加号为：每发一个包，端口数加1
  -k  --keep       保持源端口
  -w  --win        发送win系统规格的数据包 (大小为 64)
  -O  --tcpoff     设置虚假的tcp offset     (代替了tcphdrlen / 4)
  -Q  --seqnum     只展示tcp序列
  -b  --badcksum   尝试发送有错误的checksum的数据包
                   大多数系统在发送数据包使会填补IP checksum
                   你可以使用一个有错误UDP/TCP checksum的数据包代替
  -M  --setseq     设置TCP序列数
  -L  --setack     设置TCP ack
  -F  --fin        设置FIN flag
  -S  --syn        设置SYN flag
  -R  --rst        设置RST flag
  -P  --push       设置PUSH flag
  -A  --ack        设置ACK flag
  -U  --urg        设置URG flag
  -X  --xmas       设置X unused flag (0x40)
  -Y  --ymas       设置Y unused flag (0x80)
  --tcpexitcode    use last tcp->th_flags as exit code
  --tcp-mss        enable the TCP MSS option with the given value
  --tcp-timestamp  enable the TCP timestamp option to guess the HZ/uptime

```  
- 常用参数  
```
  -d  --data       数据长度                   (默认为0)
  -E  --file       从文件读取数据
  -e  --sign       添加'签名'
  -j  --dump       将数据包以hex格式转储
  -J  --print      转储数据包为可打印的字符
  -B  --safe       启用'safe'协议
  -u  --end        当文件达到EOF时告知，防止倒带
  -T  --traceroute 跟踪路由            (使用此参数时--bind和--ttl 1也将被启动)
  --tr-stop        在跟踪路由模式下收到第一个非ICMP包时退出
  --tr-keep-ttl    保持源TTL固定，这对监控单跳很有用
  --tr-no-rtt      在跟踪路由模式下不计算/显示RTT信息
```

## 官方文档：
https://github.com/antirez/hping