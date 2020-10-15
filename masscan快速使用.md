# masscan快速使用（基于7.90）
## 安装
+ window:参考此项目github，快速使用不进行说明  
+ kali:系统预安装  
+ linux：
```
sudo apt-get install git gcc make libpcap-dev  
git clone https://github.com/robertdavidgraham/masscan  
cd masscan  
make  
```

## 快速使用
masscan的使用类似于nmap  
+ 常用选项：
```
-p:指定要扫描的端口,多个端口号中用逗号隔开  
--rate:指定发包速率  
--open-only:仅显示开放的端口
--banners:获取banners
-c :使用自定义的扫描配置文件
--ping:扫之前是否要先ping下目标
-oL:把扫描结果存到指定文件中
--excludefile:排除不扫描的ip段
``` 
+ 配置文件格式：
```
rate =1000.00            # 指定发包速率  
output-format=list       # 指定扫描结果保存的文件格式,支持XML格式  
output-filename=         # 指定结果文件保存位置  
output-status=open       # 只保留开放的端口信息
ports=80,443,8080,U:53   # 指定要扫描的端口,默认tcp,当然,你也可以指定UDP的端口,U即udp
range=                   # 指定要扫描的ip段,可以连续指定多个,中间使用逗号隔开
ping=false               # 扫描的前是否进行ping
banners=true             # 获取端口指纹信息
excludefile=blacklist.conf    # 指定不扫描的ip段,可以把不想扫描的一些ip段都加到这个文件中,如:内网ip段是不需要扫的
```