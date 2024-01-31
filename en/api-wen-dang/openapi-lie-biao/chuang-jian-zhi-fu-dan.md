# 创建支付单

**URL**

/service-pay/sellerApi/create

**字段说明**

| 参数名称                 | 参数类型    | 是否必须 | 示例 |                                   |
| -------------------- | ------- | ---- | -- | --------------------------------- |
| outerOrderId         | \_T\_文本 | 是    |    | 外部订单号。限制长度32位，含字母数字，区分大小写，不允许特殊字符 |
| originCurrency       | \_T\_文本 | 是    |    | 原始法币                              |
| originCurrencyAmount | \_T\_文本 | 是    |    | 原始法币数量                            |
| chainId              | \_T\_文本 | 是    |    | 支付链ID                             |
| payTokenAddress      | \_T\_文本 | 是    |    | 支付代币符号                            |
| commodityName        | \_T\_文本 | 是    |    | 商品名称                              |

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
