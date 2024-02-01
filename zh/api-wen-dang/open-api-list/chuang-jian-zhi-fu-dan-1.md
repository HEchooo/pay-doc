# 支付单详情

**URL**

GET： https://api.echooo.xyz/service-pay/sellerApi/orderDetail



**HEADER说明**

[开放API鉴权方式](../kai-fang-api-jian-quan-fang-shi/)



**入参说明**

<table><thead><tr><th width="242">参数名称</th><th width="104">参数类型</th><th width="76">必填</th><th>备注</th></tr></thead><tbody><tr><td>outerOrderId</td><td>string</td><td>是</td><td>外部订单号。限制长度32位，含字母数字，区分大小写，不允许特殊字符</td></tr></tbody></table>



**响应说明**

<table><thead><tr><th width="266.66666666666663">参数名称</th><th>参数类型</th><th>备注</th></tr></thead><tbody><tr><td>chain</td><td>object</td><td>链</td></tr><tr><td>name</td><td>string</td><td>链名称</td></tr><tr><td>chainId</td><td>string</td><td>链ID</td></tr><tr><td>icon</td><td>string</td><td>链图标</td></tr><tr><td>orderId</td><td>string</td><td>订单号</td></tr><tr><td>outerOrderId</td><td>string</td><td>商户订单号</td></tr><tr><td>originCurrency</td><td>string</td><td>原始法币</td></tr><tr><td>originCurrencyAmount</td><td>string</td><td>原始法币金额</td></tr><tr><td>payCurrency</td><td>string</td><td>支付法币</td></tr><tr><td>payCurrencyAmount</td><td>string</td><td>支付法币数量</td></tr><tr><td>payStatus</td><td>string</td><td>订单状态</td></tr><tr><td>gmtPayStart</td><td>string</td><td>支付开始时间</td></tr><tr><td>gmtPayFinish</td><td>string</td><td>支付完成时间</td></tr><tr><td>incomeToken</td><td>object</td><td>收入代币</td></tr><tr><td>totalIncomeTokenAmount</td><td>string</td><td>总收入代币金额</td></tr><tr><td>actualIncomeTokenAmount</td><td>string</td><td>实际收入代币金额</td></tr><tr><td>incomeFeeTokenAmount</td><td>string</td><td>收入手续费代币金额</td></tr></tbody></table>



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
