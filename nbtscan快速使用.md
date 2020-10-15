# nbscan快速使用  
此工具用于内网扫描  
## 安装  
+ window:前往 http://unixwiz.net/tools/nbtscan.html 下载安装包安装  
+ kali:系统预安装  
+ linux：前往 http://unixwiz.net/tools/nbtscan.html 下载安装包安装  

## 快速使用  
+ 常用选项
```
-V/--version显示版本信息  
-f:显示每一次扫描的完整NBT记录，可以用于对某个目标的详细研究，面对大量目标时会有些困难  
-O <outfile>:将扫描结果写入外部文件中  
-H:生成一个HTTP头，有时会在远程IIS WEB服务器上安装nbtscan并使用unicode漏洞运行，添加http头避免输出被web服务器混淆  
-P:生成Perl hashref输出，该输出可以加载到现有的程序中处理  
-v:展示调试信息  
-n:关闭反向查找  
-p <port>:指定发出数据包的端口  
-m:在响应中包括MAC地址，使用-f参数时将默认启用此选项  
-T:设置响应超时，默认为2秒   
-w:设置发送等待（暂停）时间，默认为10毫秒  
-t:每个地址的尝试次数，默认为1  
-n:不在完整列表中进行反向DNS查找（显示IP地址）  
-1:强制使用Winsock版本1(仅适用于Windows)，而不是默认的版本2  
```