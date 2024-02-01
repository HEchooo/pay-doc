# 回调接口验证方式

商户在发起交易订单后30分钟内会收到平台的订单状态回调, 返回如下字段。

如何发起交易：

{% content-ref url="../dui-jie-zhi-yin/fa-qi-jiao-yi.md" %}
[fa-qi-jiao-yi.md](../dui-jie-zhi-yin/fa-qi-jiao-yi.md)
{% endcontent-ref %}

订单状态枚举:

{% content-ref url="../fu-lu/ding-dan-zhuang-tai.md" %}
[ding-dan-zhuang-tai.md](../fu-lu/ding-dan-zhuang-tai.md)
{% endcontent-ref %}



## 商户订单回调

### 回调信息：POST&#x20;

传参方式: Content-Type: application/json

**字段说明:**&#x20;

| 字段                  | 含义           |                                                                                            |
| ------------------- | ------------ | ------------------------------------------------------------------------------------------ |
| outerOrderId        | 商户订单号        |                                                                                            |
| orderId             | EchoooPay订单号 |                                                                                            |
| receiptAddress      | 商户入网钱包地址     |                                                                                            |
| payCurrency         | 订单法币币种       | \[[支持币种](../fu-lu/inviting-members.md)], 例：usd                                             |
| payCurrencyAmount   | 订单法币金额       |                                                                                            |
| payStatus           | 订单状态         |                                                                                            |
| chainId             | 付款网络ID       | 链ID, 例：Ethereum                                                                            |
| payTokenCoingeckoId | 付款币种         | 获取方式\[[链接](https://www.coingecko.com/)]                                                    |
| payTokenAmount      | 付款数量         |                                                                                            |
| incomeTokenAddress  | 订单收款地址       |                                                                                            |
| finishTime          | 完成时间         | 时间戳(ms),例：1706167219110                                                                    |
| signature           | 签名           | [#qian-ming-he-yan-qian-gui-ze](seller-callback.md#qian-ming-he-yan-qian-gui-ze "mention") |

**例:**

```
curl 'https://api.youraddress.com/order/status/callback' \
 -X POST \ 
 -H 'Accept: */*' \ 
 -H 'Timestamp: 1706167219110' \ 
 -H 'Accept-Language: en_us' \ 
 -H 'SignToken: F09QgHxuxRNnwkVoPmnS+QX94RSImA1/2i0UkMeMSGGMUhVO98EJ7YYYZ61LtJ5A' \ 
 -H 'Connection: keep-alive' \ 
 -H 'Content-Type: application/json' \ 
 --data-raw '{
  "outerOrderId": "100000000000000998",
  "orderId": "202401292468613637",
  "receiptAddress": "0xdac17f958d2ee523a2206206994597c13d831ec7",
  "payCurrency": "usd",
  "payCurrencyAmount": "1000",
  "payStatus": "PAY_SUCCESS",
  "chainId": "5",
  "payTokenCoingeckoId": "usdd",
  "payTokenAmount": "1000",
  "incomeTokenAddress": "0xdac17f958d2ee523a2206206994597c13d831ec7",
  "finishTime": "1706167219110",
  "signature": "DErfFug4ShiXjojFBZ0FpN3IObc4ZSMQ74g/DbnyQ/DGl5nY4ZNyZyagGBeziwAWNQED2IO/ts1f8v7lbcrTIf77PFgQn4Vsc1NlgAtazbf7NGCYzDdr202exUi6l0f24lAh9AiPkYvldEgUObSAxVJV07VlPGTijmuOo5H4sj9x1H/EveLwpkFc7Nu/mBE06hOwvIvgze2BzoHralkGaX3PlVuz/u+dzNIeKqGuProndwWdZMVf2e+1j94g7OCg/FD6teTQvEvFT1pTk0rn5M3GYeUjXbDBOoYCvrGIXFBhdJw7I8QjPe6zS0/bO+TWm8nw7nFC0roePWallc1Omw=="
}'
```

**返回格式(商户实现):**

平台在接收到http响应200并且返回code=0时, 判定为回调成功, 如:&#x20;

```
{
  "code": 0,
  "message": "success",
  "data": {
  }
}
```

### 流程:

平台维护一对RSA秘钥对，私钥由平台管理不公开，公钥公开。

公钥:

```
MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAhLrV9mzKGU2ntzXAt/AUn+JaA8T6WAUtBiT+EQjRjEi6gYXlxOEsmkh2a0lmlaYdIewUmmsyHYvpD5pB1r6GmWUomIzOqB15sdVCmvydMwF3cKqYmrUH45R3ap/mqqP+3C+2Ed/FiMRMkfxvAMMCy3ow4xD/P72LLoWtQwq/ULx41Y3Ps3Ckf+8kFRsNigCm5nkgs6S+hOTc40j+GaoiLc4ORb9CivV3BcnQ2CVsp48VIH3DBRa1gGPAQ0dbB08IlGf6zzKNgzHiagx8u0G78x9DkG8kujCy5L+eWV2QcrRSEQM8MSDDnlqmjdRZw3vJ07RH+8rxwignccq68w2E0QIDAQAB
```

平台使用私钥签名回调请求, 写入回调信息的 signature 字段, 商户在自己实现的回调接口使用公钥验证签名，签名通过后才处理回调信息逻辑, 否则丢弃。

### 签名和验签规则:

在回调返回参数列表中，除去signature参数外，回调返回的参数都是要签名的参数。

对数组里的每一个值从a到z的顺序排序，若遇到相同首字母，则看第二个字母，以此类推。

排序完成之后，再把所有数组值以key="value"和“&"字符连接起来，这串字符串便是待验签名字符串。签名算法同[开放接口鉴权](kai-fang-api-jian-quan-fang-shi/)部分。

_**Note:**_

_**没有值的参数，无需包含到待签名数据中；**_

_**签名时将字符转化成字节流时指定的字符集为 UTF-8；**_

**商户验签代码示例:**

```
// 商户使用公钥验证签名,其中data为 '待验签名字符串', signature为回调返回签名
public static boolean publicKeyVerify(String data, String publicKey, String signData, Charset charset) throws Exception {
    byte[] publicBytes = Base64.decodeBase64(publicKey);
    X509EncodedKeySpec keySpec = new X509EncodedKeySpec(publicBytes);
    KeyFactory keyFactory = KeyFactory.getInstance("RSA");
    PublicKey pubKey = keyFactory.generatePublic(keySpec);
    Signature signature = Signature.getInstance("SHA256withRSA");
    signature.initVerify(pubKey);
    byte[] dataBytes = data.getBytes(charset);
    signature.update(dataBytes);
    return signature.verify(Base64.decodeBase64(signData));
}
```
