# 支付单分页

**URL**

GET： https://api.echooo.xyz/service-pay/sellerApi/orderPage



**HEADER说明**

[开放API鉴权方式](../kai-fang-api-jian-quan-fang-shi/)



**入参说明**

<table><thead><tr><th width="242">参数名称</th><th width="104">参数类型</th><th width="76">必填</th><th>备注</th></tr></thead><tbody><tr><td>pageNo</td><td>string</td><td>是</td><td>页面，从1开始</td></tr><tr><td>pageSize</td><td>string</td><td>是</td><td>单页数量</td></tr><tr><td>gmtPayFinishStart</td><td>number</td><td>否</td><td>订单支付完成时间起始时间戳，毫秒级</td></tr><tr><td>gmtPayFinishEnd</td><td>number</td><td>否</td><td>订单支付完成时间结束时间戳，毫秒级</td></tr><tr><td>payStatus</td><td>string</td><td>否</td><td><a href="../../fu-lu/ding-dan-zhuang-tai.md">支付状态</a></td></tr><tr><td>chainId</td><td>number</td><td>否</td><td><a href="../../fu-lu/inviting-members.md">链ID</a></td></tr></tbody></table>



**响应说明**

| 参数名称                                                | 类型                                                     | 备注                                            |
| --------------------------------------------------- | ------------------------------------------------------ | --------------------------------------------- |
| code                                                | number                                                 | 错误码                                           |
| message                                             | string                                                 | 错误详情                                          |
| pageSize                                            | number                                                 | 页码                                            |
| pageNo                                              | number                                                 | 分页大小                                          |
| total                                               | number                                                 | 数据总数                                          |
| dataList                                            | object \[]                                             | 结果列表                                          |
| payOrderId                                          | string                                                 | 支付单号                                          |
| outerOrderId                                        | string                                                 | 商家订单号                                         |
| chain                                               | object                                                 | 链                                             |
| <ul><li>name</li><li>chainId</li><li>icon</li></ul> | <ul><li>string</li><li>number</li><li>string</li></ul> | <ul><li>链名称</li><li>链ID</li><li>链图标</li></ul> |
| payStatus                                           | string                                                 | 支付状态                                          |
| gmtPayFinish                                        | date                                                   | 支付完成时间                                        |
| originCurrency                                      | string                                                 | 订单原始法币                                        |
| originCurrencyAmount                                | string                                                 | 订单原始法币金额                                      |
| payCurrency                                         | string                                                 | 订单应付法币                                        |
| payCurrencyAmount                                   | string                                                 | 订单应付法币金额                                      |

\




**CURL示例**

```
curl --location 'https://api.echooo.xyz/service-pay/sellerApi/orderPage?pageNo=1&pageSize=10' \
--header 'appKey: secret_key123' \
--header 'timestamp: 1704643200000' \
--header 'signToken: sign123'
```



**响应预览**

```
{
    "code": 0,
    "message": "操作成功",
    "data": {
        "code": 0,
        "message": "操作成功",
        "dataList": [
            {
                "payOrderId": "2024013099986745616265",
                "outerOrderId": "100000000000000006",
                "chain": {
                    "name": "Ethereum",
                    "chainId": 1,
                    "icon": "https://cdn.echooo.xyz/images/financing/chain_tiny_gray/Ethereum.png",
                    "alreadyIsContact": null
                },
                "payStatus": "PAY_FAIL",
                "gmtPayFinish": null,
                "originCurrency": "JPY",
                "originCurrencyAmount": "0.1",
                "payCurrency": "USD",
                "payCurrencyAmount": "0.000675"
            },
            {
                "payOrderId": "2024012599986789491262",
                "outerOrderId": "100000000000000005",
                "chain": {
                    "name": "Ethereum",
                    "chainId": 1,
                    "icon": "https://cdn.echooo.xyz/images/financing/chain_tiny_gray/Ethereum.png",
                    "alreadyIsContact": null
                },
                "payStatus": "PAY_FAIL",
                "gmtPayFinish": null,
                "originCurrency": "JPY",
                "originCurrencyAmount": "0.1",
                "payCurrency": "USD",
                "payCurrencyAmount": "0.000679"
            },
            {
                "payOrderId": "2024012499986741241892",
                "outerOrderId": "lilin111",
                "chain": {
                    "name": "Ethereum",
                    "chainId": 1,
                    "icon": "https://cdn.echooo.xyz/images/financing/chain_tiny_gray/Ethereum.png",
                    "alreadyIsContact": null
                },
                "payStatus": "PAY_FAIL",
                "gmtPayFinish": null,
                "originCurrency": "JPY",
                "originCurrencyAmount": "0.1",
                "payCurrency": "USD",
                "payCurrencyAmount": "0.000674"
            },
            {
                "payOrderId": "2024012299986710259073",
                "outerOrderId": "100000000000000002",
                "chain": {
                    "name": "Ethereum",
                    "chainId": 1,
                    "icon": "https://cdn.echooo.xyz/images/financing/chain_tiny_gray/Ethereum.png",
                    "alreadyIsContact": null
                },
                "payStatus": "PAY_FAIL",
                "gmtPayFinish": null,
                "originCurrency": "JPY",
                "originCurrencyAmount": "0.1",
                "payCurrency": "USD",
                "payCurrencyAmount": "0.000675"
            },
            {
                "payOrderId": "2024011899986738564743",
                "outerOrderId": "224",
                "chain": {
                    "name": "Ethereum",
                    "chainId": 1,
                    "icon": "https://cdn.echooo.xyz/images/financing/chain_tiny_gray/Ethereum.png",
                    "alreadyIsContact": null
                },
                "payStatus": "WAIT_PAY",
                "gmtPayFinish": null,
                "originCurrency": "JPY",
                "originCurrencyAmount": "0.1",
                "payCurrency": "USD",
                "payCurrencyAmount": "0.000675"
            }
        ],
        "pageSize": 10,
        "pageNo": 1,
        "total": 5,
        "traceId": null
    },
    "placeholder": null,
    "traceId": ""
}
```
