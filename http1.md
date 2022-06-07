# http入门
* protocol-协议
* http全称Hyper Text Transfer Protocol
* dns全称Domain Name Server

### ip
* 只要在互联网-就至少有一个独特的ip

### hosts 文件在哪？

* 答： 在 Windows 系统中，hosts 位于 C:\Windows\System32\drivers\etc\hosts 。在 macOS / Linux系统中，hosts 位于 /etc/hosts



### 路由器的功能
* 现在路由器有两个ip,一个外网ip一个内网ip
* 内网中的设备可以相互访问,但是不能直接访问外网
* 内网设备想要访问外网,就必须经过路由器中转
* 外网中的设备可以相互访问,但是无法访问你的内网 
* 外网设备  想要把内容送到内网  ,也必须经过路由器
* 也就是说内网和外网就像两个隔绝的空间,无法互通,唯一的联通点就是路由器
* 所以路由器也叫做网关

### 几个特殊ip
* 127.0.0.1表示自己
* localhost通过hosts指定自己
* 0.0.0.0不表示任何设备

### 端口
* 一台机器可以提供不同服务
1. 提供HTTP服务最好使用80端口
2. 提供HTTPs服务最好使用443端口
3. 提供ftp服务最好使用21端口
4. 一共65535个端口

* 端口使用规则
1. 0到1023号端口是留给系统的
2. 只有拥有管理员权限,才能使用这1024个端口
3. 其他端口是给普通用户使用
4. 比如http-server默认使用8080端口
5. 一个端口被占用,只能换一个端口

* ip和端口缺一不可

### 域名
* 一个域名对应不同ip
* 这个叫做均衡负载  防止一个机器扛不住
* 一个ip可以对应不用域名
* 这个叫做共享主机,穷开发者这么做

### 把域名和ip对应起来的---通过dns
1. 当你输入一个网址
2. 你的浏览器会向电信/联通提供dns服务器,询问网址对应什么ip
3. 电信//联通会回答一个ip
4. 然后浏览器才会向对应的端口80/443端口发送请求
5. 请求内容查看网址首页

* 为什么是80/443端口 
* 服务器默认用80端口提供http服务
* 默认使用443端口提供https服务
* 可以在开发者工具看到具体端口

### www.xxx.com和xxx.com不是同一个域名
* 她们之间是什么关系
* com是顶级域名
* xxx.com是二级域名(俗称一级域名)
* www.xxx.com是三级域名(俗称二级域名)
* 他们是父子关系
* GitHub.io把子域名xxx.GitHub.io免费给你使用
* 所以www.xx.com和xx.com可以是同一公司也可以不是
* www是多余的
### 如何请求不同的页面
* 路径可以做到
1. https://developer.mozilla.org/zh-CN/docs/Web/HTML
2. https://developer.mozilla.org/zh-CN/docs/Web/css
* 使用开发者工具network面板可以看看区别

### 同一个页面不同内容
* 查询参数可做到
* http://www.baidu.com/s?wd=hi
* http://www.baidu.com/s?wd=hello
* 查询参数为wd=hi

### 查同一页面不同位置
* 锚点可以做到
* https://developer.mozilla.org/zh-CN/docs/Web/CSS#参考书
* https://developer.mozilla.org/zh-CN/docs/Web/CSS#教材
* 注意
* 锚点看起来有中文实际不支持中文
* #参考书会变成乱码
* 锚点是无法在network面板看到的
* 因为锚点不会传给服务器

### url -统一资源定位服务
* 协议+域名或ip+端口号+路径+查询字符串+锚点(锚点是不会发送到服务器的)
* ![图](images/77.jpg)

### curl命令
* 用curl可以发出请求
* curl -v http://baidu.com
* curl -s -v --https://www.baidu.com
* 理解概念
* url会被curl工具重写(会在网址后加/),会先请求dns获得ip
* 先进行tcp链接,tcp连接成功后,开始发送http请求
* 请求内容看一下
* 响应内容看一下
* 响应结束后,关闭tcp链接
* 真正结束
* http
* 规定请求格式是什么,响应格式是什么

### ![1](images/屏幕截图%202022-06-06%20094235.jpg)

### nslookup作用:用于查询dns的记录,查询域名解析是否正常