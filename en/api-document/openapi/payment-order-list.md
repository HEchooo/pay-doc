# Payment Order List

**URL**

GET： https://api.echooo.xyz/service-pay/sellerApi/orderPage​



**HEADER**

​[Open API](../open-api-authentication-method/)



**Request Field**

| Parameter | Type   | Mandatory | Remark                    |
| --------- | ------ | --------- | ------------------------- |
| pageNo    | string | Yes       | Page number, start from 1 |
| pageSize  | string | Yes       | Page size                 |

**Response Example**

| Parameter                                           | Type                                                   | Remark                                                           |
| --------------------------------------------------- | ------------------------------------------------------ | ---------------------------------------------------------------- |
| code                                                | number                                                 | Error code                                                       |
| message                                             | string                                                 | Error message                                                    |
| pageSize                                            | number                                                 | Page                                                             |
| pageNo                                              | number                                                 | Page number                                                      |
| total                                               | number                                                 | Total                                                            |
| dataList                                            | object                                                 | Data list                                                        |
| payOrderId                                          | string                                                 | Payment Order ID                                                 |
| outerOrderId                                        | string                                                 | Merchant Order ID                                                |
| chain                                               | object                                                 | Chain                                                            |
| <ul><li>name</li><li>chainId</li><li>icon</li></ul> | <ul><li>string</li><li>number</li><li>string</li></ul> | <ul><li>Chain name</li><li>Chain ID</li><li>Chain icon</li></ul> |
| payStatus                                           | string                                                 | Payment status                                                   |
| gmtPayFinish                                        | date                                                   | Payment end time                                                 |
| originCurrency                                      | string                                                 | Fiat currency                                                    |
| originCurrencyAmount                                | string                                                 | Fiat currency amount                                             |
| payCurrency                                         | string                                                 | Payment currency                                                 |
| payCurrencyAmount                                   | string                                                 | Payment currency amount                                          |

​**CURL Example**

```
curl --location 'https://api.echooo.xyz/service-pay/sellerApi/orderPage?pageNo=1&pageSize=10' \
--header 'appKey: secret_key123' \
--header 'timestamp: 1704643200000' \
--header 'signToken: sign123'
```



**Response Example**

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
