# 支付单详情

**URL**

/service-pay/sellerApi/orderDetail

**字段说明**

<table><thead><tr><th width="154">参数名称</th><th width="100">参数类型</th><th>是否必须</th><th>描述</th></tr></thead><tbody><tr><td>outerOrderId</td><td><em>T</em>文本</td><td>外部订单号和支付单号二选一</td><td>外部订单号。限制长度32位，含字母数字，区分大小写，不允许特殊字符</td></tr><tr><td>payOrderId</td><td><em>T</em>文本</td><td>外部订单号和支付单号二选一</td><td>EchoooPay返回的支付订单号</td></tr></tbody></table>

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
