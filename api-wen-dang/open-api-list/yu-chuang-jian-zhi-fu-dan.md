# 预创建支付单

**URL**

/service-pay/sellerApi/preCreateOrder

**字段说明**

<table><thead><tr><th width="100">参数名称</th><th>参数类型</th><th>是否必须</th><th>示例</th><th>备注</th></tr></thead><tbody><tr><td>outerOrderId</td><td><em>T</em>文本</td><td>是</td><td></td><td>外部订单号。限制长度32位，含字母数字，区分大小写，不允许特殊字符</td></tr><tr><td>originCurrency</td><td><em>T</em>文本</td><td>是</td><td></td><td>原始法币</td></tr><tr><td>originCurrencyAmount</td><td><em>T</em>文本</td><td>是</td><td></td><td>原始法币数量</td></tr><tr><td>commodityName</td><td><em>T</em>文本</td><td>是</td><td></td><td>商品名称</td></tr></tbody></table>

**响应预览**

```
{
  "code": "0",
  "message": "success",
  "data": {
    "cashierUrl": "http://aaa.com",
    "payOrderId": "2023010131412"
  }
}
```
