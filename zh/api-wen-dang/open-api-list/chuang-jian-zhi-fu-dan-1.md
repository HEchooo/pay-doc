# 支付单详情

**URL**

GET： https://api.echooo.xyz/service-pay/sellerApi/orderDetail



**HEADER说明**

[开放API鉴权方式](../kai-fang-api-jian-quan-fang-shi/)



**BODY说明**

<table><thead><tr><th width="242">参数名称</th><th width="104">参数类型</th><th width="76">必填</th><th>备注</th></tr></thead><tbody><tr><td>outerOrderId</td><td><em>T</em>文本</td><td>是</td><td>外部订单号。限制长度32位，含字母数字，区分大小写，不允许特殊字符</td></tr></tbody></table>



**CURL示例**

```
curl --location 'https://api.echooo.xyz/service-pay/sellerApi/orderDetail?outerOrder=2024013099986729480675' \
--header 'appKey: secret_key123' \
--header 'timestamp: 1704643200000' \
--header 'signToken: sign123'
```



**响应预览**

```

{
  "code": "0",
  "message": "success",
  "data": {
    "chain": {
      "name": "cillum proident",
      "chainId": "1",
      "icon": "http://123.com"
    },
    "orderId": "2023010131231",
    "outerOrderId": "23415329",
    "originCurrencyAmount": "1",
    "originCurrency": "1",
    "payCurrencyAmount": "1",
    "payCurrency": "1",
    "payStatus": "1",
    "gmtPayFinish": "1",
    "gmtPayStart": "1",
    "totalIncomeTokenAmount": "1",
    "incomeToken": {
      "name": "L",
      "icon": "http://123.com",
      "code": "1",
      "address": "0x1231akjfkashk123",
      "coingeckoId": "usdc"
    },
    "actualIncomeTokenAmount": "1000000",
    "incomeFeeTokenAmount": "1000"
  }
}
```
