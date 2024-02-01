# 支付单分页

**URL**

GET： https://api.echooo.xyz/service-pay/sellerApi/orderPage



**HEADER说明**

[开放API鉴权方式](../kai-fang-api-jian-quan-fang-shi/)



**BODY说明**

<table><thead><tr><th width="242">参数名称</th><th width="104">参数类型</th><th width="76">必填</th><th>备注</th></tr></thead><tbody><tr><td>pageNo</td><td><em>T</em>文本</td><td>是</td><td>页面，从1开始</td></tr><tr><td>pageSize</td><td><em>T</em>文本</td><td>是</td><td>单页数量</td></tr></tbody></table>



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
