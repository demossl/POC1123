# 成都信通网易医疗科技发展有限公司PACS(医学影像信息管理系统)dabh存在SQL注入漏洞

# 一、漏洞简介
成都信通网易医疗科技发展有限公司总部位于四川成都高新区天府软件园，在国内医疗软件行业中率先采用Java技术，融入国际国内标准，整体设计，持续研发，先后形成了“智慧云医院信息平台”、“医共体信息平台”、“互联网医院平台”、“医养融合信息平台”等新一代一系列自主知识产权产品，全面覆盖了单体医院业务、区域医疗、医共体、“互联网+健康”等信息化建设领域。成都信通网易医疗科技发展有限公司PACS(医学影像信息管理系统)dabh存在SQL注入漏洞，攻击者可通过该漏洞获取数据库敏感信息。

# 二、影响版本
+ 成都信通网易医疗科技发展有限公司PACS(医学影像信息管理系统)

# 三、特征
![1700650941861-e1d2149c-0043-4e5b-8d5a-a051c63982a6.png](./img/SVgl4MzaEBYH3VYX/1700650941861-e1d2149c-0043-4e5b-8d5a-a051c63982a6-874139.png)

# 四、漏洞复现
```plain
/XtWebPacsASp/XTWebPacsGetJcbgByDabh.asp?dabh=1
```

![1700651304147-bb52a220-c2d7-4841-af18-c0e7aec6ef2a.png](./img/SVgl4MzaEBYH3VYX/1700651304147-bb52a220-c2d7-4841-af18-c0e7aec6ef2a-114819.png)



> 更新: 2024-02-29 23:55:28  
> 原文: <https://www.yuque.com/xiaokp7/ocvun2/oq3n3kbupmwuhibq>