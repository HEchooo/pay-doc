# Create Payment Order

**URL**

/service-pay/sellerApi/create



**Field Description**

| Parameter            | Type     | Mandatory | Example | Remark                                                                                                                                           |
| -------------------- | -------- | --------- | ------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| outerOrderId         | _T Text_ | Yes       |         | <p>External order number. Limited to 32 characters, including letters and numbers, case-sensitive.</p><p>Special characters are not allowed.</p> |
| originCurrency       | _T Text_ | Yes       |         | Fiat currency                                                                                                                                    |
| originCurrencyAmount | _T Text_ | Yes       |         | Fiat currency amount                                                                                                                             |
| chainId              | _T Text_ | Yes       |         | Payment Chain ID                                                                                                                                 |
| payTokenAddress      | _T Text_ | Yes       |         | Payment Token symbol                                                                                                                             |
| commodityName        | _T Text_ | Yes       |         | Commodity name                                                                                                                                   |



**Response Example**

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
