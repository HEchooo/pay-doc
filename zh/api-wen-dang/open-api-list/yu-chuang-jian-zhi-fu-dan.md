# 跳转收银台

**URL**

POST： https://api.echooo.xyz/service-pay/sellerApi/cashier



**HEADER说明**

[开放API鉴权方式](../kai-fang-api-jian-quan-fang-shi/)



**入参说明**

<table><thead><tr><th width="242">参数名称</th><th width="104">参数类型</th><th width="76">必填</th><th>备注</th></tr></thead><tbody><tr><td>outerOrderId</td><td><em>T</em>文本</td><td>是</td><td>外部订单号。限制长度32位，含字母数字，区分大小写，不允许特殊字符</td></tr><tr><td>originCurrency</td><td><em>T</em>文本</td><td>是</td><td>订单法币类型。见附录 - 支持币种</td></tr><tr><td>originCurrencyAmount</td><td><em>T</em>文本</td><td>是</td><td>订单法币数量，单位分</td></tr><tr><td>commodityName</td><td><em>T</em>文本</td><td>是</td><td>商品名称</td></tr></tbody></table>



**响应说明**

<table><thead><tr><th width="242">参数名称</th><th width="104">参数类型</th><th>备注</th></tr></thead><tbody><tr><td>cashierUrl</td><td><em>T</em>文本</td><td>收银台跳转地址</td></tr></tbody></table>



**CURL示例**

```
curl --location 'https://api.valleysound.xyz/service-pay/sellerApi/cashier' \
--header 'Content-Type: application/json' \
--header 'appKey: secret_key123' \
--header 'timestamp: 1704643200000' \
--header 'signToken: sign123' \
--data '{
    "outerOrderId": "2050322162971135583",
    "originCurrency": "usd",
    "originCurrencyAmount": "1000",
    "commodityName": "phone"
}'
```



**响应预览**

```
{
  "code": "0",
  "message": "success",
  "data": {
    "cashierUrl": "https://pay.echooo.xyz/en-us/v1/?oid=20240122999867758636301"
  }
}
```

