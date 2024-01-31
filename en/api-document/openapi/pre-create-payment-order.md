# Pre-create Payment Order

**URL**

/service-pay/sellerApi/preCreateOrder



**Field Description**

<table><thead><tr><th width="100">Parameter</th><th>Type</th><th>Mandatory</th><th>Example</th><th>Remark</th></tr></thead><tbody><tr><td>outerOrderId</td><td><em>T Text</em></td><td>Yes</td><td></td><td><p>External order number. Limited to 32 characters, including letters and numbers, case-sensitive.</p><p>Special characters are not allowed.</p></td></tr><tr><td>originCurrency</td><td><em>T Text</em></td><td>Yes</td><td></td><td>Original fiat currency</td></tr><tr><td>originCurrencyAmount</td><td><em>T Text</em></td><td>Yes</td><td></td><td>Original fiat amount</td></tr><tr><td>commodityName</td><td><em>T Text</em></td><td>Yes</td><td></td><td>Commodity name</td></tr></tbody></table>

**Response Example**

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
