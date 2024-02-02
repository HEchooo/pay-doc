# 跳转收银台

**URL**

POST： https://api.echooo.xyz/service-pay/sellerApi/cashier​



**HEADER**

​[Open API](../open-api-authentication-method/)



**Request Field**

| Parameter            | Type   | Mandatory | Remark                                                                                                                                           |
| -------------------- | ------ | --------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| outerOrderId         | string | Yes       | <p>External order number. Limited to 32 characters, including letters and numbers, case-sensitive.</p><p>Special characters are not allowed.</p> |
| originCurrency       | string | Yes       | Original fiat currency                                                                                                                           |
| originCurrencyAmount | string | Yes       | Original fiat amount                                                                                                                             |
| commodityName        | string | Yes       | Commodity name                                                                                                                                   |

​**Response Example**

| Parameter  | Type   | Remark          |
| ---------- | ------ | --------------- |
| cashierUrl | string | Cashier address |

​**CURL Example**

curl --location 'https://api.valleysound.xyz/service-pay/sellerApi/cashier' \\--header 'Content-Type: application/json' \\--header 'appKey: secret\_key123' \\--header 'timestamp: 1704643200000' \\--header 'signToken: sign123' \\--data '{"outerOrderId": "2050322162971135583","originCurrency": "usd","originCurrencyAmount": "1000","commodityName": "phone"}'​

**Response**

{"code": "0","message": "success","data": {"cashierUrl": "https://pay.echooo.xyz/en-us/v1/?oid=20240122999867758636301\&hash=4e85b9422820461aa252c4ebf353d9a0"\}}​
