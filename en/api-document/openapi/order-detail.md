# Order Detail

**URL**

GET： https://api.echooo.xyz/service-pay/sellerApi/orderDetail



**HEADER**

​[Open API](../open-api-authentication-method/)



**Request Field**

<table><thead><tr><th width="154">Parameter</th><th width="100">Type</th><th>Mandatory</th><th>Remark</th></tr></thead><tbody><tr><td>outerOrderId</td><td>String</td><td>Yes</td><td><p>External order number. Limited 8~32 characters, including letters and numbers, case-sensitive.</p><p>Special characters are not allowed.</p></td></tr></tbody></table>



**Response Example**

<table><thead><tr><th width="266.66666666666663">Parameter</th><th>Type</th><th>Remark</th></tr></thead><tbody><tr><td>chain</td><td>object</td><td>Chain</td></tr><tr><td>name</td><td>string</td><td>Chain Name</td></tr><tr><td>chainId</td><td>string</td><td>Chain ID</td></tr><tr><td>icon</td><td>string</td><td>Chain Icon</td></tr><tr><td>orderId</td><td>string</td><td>Order ID</td></tr><tr><td>outerOrderId</td><td>string</td><td>Merchant Order ID</td></tr><tr><td>originCurrency</td><td>string</td><td>Fiat currency</td></tr><tr><td>originCurrencyAmount</td><td>string</td><td>Fiat currency amount</td></tr><tr><td>payCurrency</td><td>string</td><td>Payment currency</td></tr><tr><td>payCurrencyAmount</td><td>string</td><td>Payment currency amount</td></tr><tr><td>payStatus</td><td>string</td><td>Order Status</td></tr><tr><td>gmtPayStart</td><td>string</td><td>Payment start time</td></tr><tr><td>gmtPayFinish</td><td>string</td><td>Payment end time</td></tr><tr><td>incomeToken</td><td>object</td><td>Income token</td></tr><tr><td>totalIncomeTokenAmount</td><td>string</td><td>Total income token amount</td></tr><tr><td>actualIncomeTokenAmount</td><td>string</td><td>Actual income token amount</td></tr><tr><td>incomeFeeTokenAmount</td><td>string</td><td>Income Tx fee token amount</td></tr></tbody></table>

​

**CURL Example**

```
curl --location 'https://api.echooo.xyz/service-pay/sellerApi/orderDetail?outerOrder=2024013099986729480675' \
--header 'appKey: secret_key123' \
--header 'timestamp: 1704643200000' \
--header 'signToken: sign123'
```

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
