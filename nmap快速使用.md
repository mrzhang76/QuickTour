# Nmap快速使用（基于7.90）
## 安装
+ window:前往nmap.org下载安装包安装  
+ kali:系统预安装  
+ linux：
```
git clone https://github.com/nmap/nmap.git
cd nmap
./configure
make
make install
```
## 常用选项
使用命令结构：  
```nmap [<扫描类型>][<选项>][<扫描目标说明>]```  
常用选项说明：
  
+ 目标：
```
可以直接使用主机名，IP地址，网段等（例如：scanme.nmap.org, microsoft.com/24, 192.168.0.1; 10.0.0-255.1-254），或读取文件中的目标列表  

-iL <要输入的文件名> //从文件中输入一列目标  
--exclude <host1[,host2][,host3],...> //从想扫描的IP段中排除某些IP
--excludefile <exclude_file>  //从文件列表中读取扫描的IP段中想要排除的某些IP
```
  
+ 主机发现：
```
-sL:只是列出目标主机，不进行数据包发送
-sn:Ping扫描，只探测主机存活，不扫描端口  
-Pn:禁用主机检测，无论主机是否可以Ping，都进行扫描，用于一些禁止Ping的主机  
-PS:TCP SYN 扫描，发送一个设置了SYN标志位的空TCP报文，尝试建立连接，成功返回报文以及运行信息  
-PA:TCP ACK 扫描，发送一个设置了ACK标志位的空TCP报文，尝试建立连接，成功返回报文以及运行信息  
-PU:UDP 扫描，发送一个空的UDP报文，成功返回响应报文及运行信息  
-PO[protocol list]:使用IP协议扫描  
-n/-R:不进行DNS解析/进行反向解析 [缺省值: sometimes]  
--dns-servers <serv1[,serv2],...>:更换DNS服务器获得不同扫描结果  
--system-dns:使用系统DNS服务  
--traceroute:进行路由追踪  
```
  
+ 端口发现：
```
-sS/sT/sA/sW/sM: 基于TCP SYN（半开放扫描，具有一定的隐蔽性）/Connect()/ACK/Window/Maimon的扫描  
-sU: 基于UDP协议的扫描  
-sN/sF/sX: 基于TCP Null/FIN/Xmas的扫描  
--scanflags <flags>:自定义TCP flags标志位的扫描  
```
  
+ 指定端口和扫描菜单
```
-p:扫描特定类型端口/范围
--exclude-ports:排除不想扫描的端口  
-F:快速扫描  
-r:按顺序扫描  
--top-ports<number>:扫描top n的常用端口   
```
  
+ 服务/版本探测
```
-sV:进行特征库对比  
--version-intensity <level>:设置扫描强度（0-9）  
--version-trace:跟踪扫描过程  
```
  
+ 操作系统探测
```
-o:启用操作系统探测  
--osscan-limit:限制操作系统的检测范围  
--osscan-guess:更加积极的进行操作系统猜测  
```
  
+ 欺骗防火墙/IDS
```
-f --mtu <val>:设置MTU值  
-D <decoy1,decoy2[,ME],...>:使用诱饵进行源地址伪造  
-S <IP_Address>:虚假源地址  
-e <iface>:使用指定网络接口  
-g/--source-port <portnum>:使用指定端口  
--proxies <url1,[url2],...>:通过HTTP/SOCKS4代理建立连接  
--data <hex string>:在数据包中加入自定义payload  
--data-string <string>:在数据包中加入自定义的ASCII字符串  
--data-length <num>:在数据包中加入长度为n的随机数据  
--ip-options <options>:发送具有指定IP选项的数据包  
--ttl <val>:设置存活时间  
--spoof-mac <mac address/prefix/vendor name>:伪造源MAC地址  
--badsum:发送带有虚假TCP/UDP/SCTP checksum的数据包  
```
  
+ 结果输出
```
-oN <file>:将标准输出直接写入指定的文件  
-oX <file>:输出XML格式到文件  
-oA <basename>:输出到所有格式  
-v:提高输出信息的详细度，使用-vv获取更加详细的信息  
-d:调试模式输出，使用-dd获取更加详细的调试信息  
--packet-trace:输出每个发送和接收的报文  
--iflist:列举接口和路由  
--resume <filename>:继续中断的扫描  
--append-output:在已有输出文件中添加  
```