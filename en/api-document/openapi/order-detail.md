# Order Detail

**URL**

/service-pay/sellerApi/orderDetail



**Field Description**

<table><thead><tr><th width="154">Parameter</th><th width="100">Type</th><th>Mandatory</th><th>Remark</th></tr></thead><tbody><tr><td>outerOrderId</td><td><em>T Text</em></td><td>External order number or payment order number</td><td><p>External order number. Limited to 32 characters, including letters and numbers, case-sensitive.</p><p>Special characters are not allowed.</p></td></tr><tr><td>payOrderId</td><td><em>T Text</em></td><td>External order number or payment order number</td><td>Transaction ID returned by EchoooPay</td></tr></tbody></table>



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
