# Verify Callback Interface

The merchant will receive an order status callback from the platform within 30 minutes after initiating the transaction. Here are the returned fields. How to initiate a transaction:

{% content-ref url="../integration-guide/initial-transaction.md" %}
[initial-transaction.md](../integration-guide/initial-transaction.md)
{% endcontent-ref %}



Order Status:

{% content-ref url="../others/order-status.md" %}
[order-status.md](../others/order-status.md)
{% endcontent-ref %}



### Merchant Callback Order

### Callback Information: POST

| Parameter           |                          | Remark                                      |
| ------------------- | ------------------------ | ------------------------------------------- |
| outerOrderId        | Merchant Transaction ID  |                                             |
| orderId             | EchoooPay Transaction ID |                                             |
| receiptAddress      | Merchant wallet address  |                                             |
| payCurrency         | Order fiat currency      |                                             |
| payCurrencyAmount   | Order fiat amount        |                                             |
| payStatus           | Payment Status           |                                             |
| chainId             | Payment network ID       | chain ID, example：Ethereum                  |
| payTokenCoingeckoId | Payment currency         | Link\[[链接](https://www.coingecko.com/)][^1] |
| payTokenAmount      | Payment amount           |                                             |
| incomeTokenAddress  | Receive address          |                                             |
| finishTime          | Complete time            |                                             |
| signature           | Signature                |                                             |

### Process

platform maintains a pair of RSA key, the private key is managed by the platform and not disclosed, while the public key is publicly available.

Public Key:

```
MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAhLrV9mzKGU2ntzXAt/AUn+JaA8T6WAUtBiT+EQjRjEi6gYXlxOEsmkh2a0lmlaYdIewUmmsyHYvpD5pB1r6GmWUomIzOqB15sdVCmvydMwF3cKqYmrUH45R3ap/mqqP+3C+2Ed/FiMRMkfxvAMMCy3ow4xD/P72LLoWtQwq/ULx41Y3Ps3Ckf+8kFRsNigCm5nkgs6S+hOTc40j+GaoiLc4ORb9CivV3BcnQ2CVsp48VIH3DBRa1gGPAQ0dbB08IlGf6zzKNgzHiagx8u0G78x9DkG8kujCy5L+eWV2QcrRSEQM8MSDDnlqmjdRZw3vJ07RH+8rxwignccq68w2E0QIDAQAB
```

The platform signs the callback request using the private key and writes the signature into the 'signature' field of the callback information. The merchant, on their own implemented callback interface, verifies the signature using the public key. Only if the signature is validated, the merchant processes the callback information; otherwise, it is discarded.

### Signature and Verification Rules

In the callback parameter list, all parameters returned in the callback, excluding the 'signature' parameter, are the ones to be signed. Each value in the array is sorted alphabetically from 'a' to 'z'. In case of the same initial letter, the second letter is considered, and so on. After sorting, all array values are connected with 'key="value"' and "&" characters, forming the string to be verified. The signature algorithm is the same as the open interface authentication section.

**Note:**

* **Parameters with no values need not be included in the data to be signed.**
* **When converting characters to byte streams during signature, the specified character set is UTF-8.**
* **Example code to verify signature:**

```
// Merchants use the public key to verify the signature, where 'data' is the 'string to be verified' and 'signature' is the signature returned in the callback.
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

[^1]: 
