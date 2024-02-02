# Open API Authentication Method

## OpenAPI

**The following is a list of supported Open APIs:**

{% content-ref url="../openapi/" %}
[openapi](../openapi/)
{% endcontent-ref %}

All Open APIs mentioned in this document must go through the signature process,  Send below parameters in HTTP Header

| appKey    | appkey from Merchant                        |
| --------- | ------------------------------------------- |
| appKey    | appKey generate from merchant backup system |
| timestamp | Time(milliseconds)                          |
| signToken | Signature                                   |



## Process

1. Key management generates app\_key and app\_secret, which are stored in the pay\_merchant\_secret table on the server and exposed to the merchant.&#x20;
2. Merchants use appKey:secret\_key123 in the request header for querying interface calls.&#x20;
3. For create, update, and delete operations, in addition to appKey, the merchant needs to sign with their private key and include a timestamp in the header (such as signToken:sign123, timestamp=1704643200000(ms)).

{% content-ref url="use-openssl-to-generate-rsa-keys.md" %}
[use-openssl-to-generate-rsa-keys.md](use-openssl-to-generate-rsa-keys.md)
{% endcontent-ref %}

## signToken Generation Rule

1. The merchant concatenates the pending signature string with the content: timestamp (in ms)\_URI\_param.&#x20;
2. Use the private key to sign the above pending signature string (private key generation method) to generate the signToken.

### Concatenation Explanation

1. The URI is the Path part, for example, /service-pay/sellerApi/getMerchantByUsername
2.  Concatenate the parameters and their values into a string, with parameter names and values connected by '=' (sorted in ascending order of ASCII code, comparing the next letter if the first letters are the same).

    * &#x20;**Get**&#x20;

    ?aparam=2\&aaparam=3\&username=4802097272\&abparam=1&#x20;

    **Process result**: aaparam=3\&abparam=1\&aparam=2\&username=4802097272

    * **Post**

    {"username":"4802097272","aparam":"2","abparam":"1","aaparam":"3"}

    **Process result:** aaparam=3\&abparam=1\&aparam=2\&username=4802097272

Note: The parameter concatenation process should occur before the caller encodes the parameters in the URL. The concatenated parameters do not need to go through URL encoding; symbols such as "&", ":", or Chinese characters should remain as they are. The concatenation process is independent of the encoding process that occurs during the transmission of the request.

3. All parts are connected with underscores "\_" to form a complete concatenated string.

## Full Example

Example of Parameters for Signing:&#x20;

Example Interface:   `/service-pay/sellerApi/getMerchantByUsername`

### Merchant Public Key

```
MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDWm7/UV5l23A9akyNM06oUX7Hn
umKOzp31wiNDTXnlCTAKs9LcLutLkyPzwye9BQO/rWfvQCWYb+vXToHTt2k8GCVa
FmHJnL49y6uMNymS+HWvVvM8ms2ByWZ9ISLP6WxDcwU/CYK51YMsDLhMNTDAYkkq
vx6UsO35Vpa/R65vSwIDAQAB
```

### Merchant Secret Key

```
MIICdgIBADANBgkqhkiG9w0BAQEFAASCAmAwggJcAgEAAoGBANabv9RXmXbcD1qT
I0zTqhRfsee6Yo7OnfXCI0NNeeUJMAqz0twu60uTI/PDJ70FA7+tZ+9AJZhv69dO
gdO3aTwYJVoWYcmcvj3Lq4w3KZL4da9W8zyazYHJZn0hIs/pbENzBT8JgrnVgywM
uEw1MMBiSSq/HpSw7flWlr9Hrm9LAgMBAAECgYAe4S5LCYfFeIilCcLsjRBN+i8J
HuKLleNYt2SHjKBbemT1RUaz8/RbXYKw0oXnRs9xRyxLWrmOI5yV0HAR3LRBc+va
DzaeE03fMavlHhnUV50M+FWLDplia7R/CvIVLLSO8nnuSCe8M2RDaNPtZNGkSfnf
I87xEFGL1NIf9oQoQQJBAOqsXA/bBz5623aQOZmS9Dv3PBgSQafO8T2AqqOoS51N
9M9ODPQntE5nhmA3+sCpnYi41XjJUhdjbkfU9VhfWPsCQQDqHJVDC/a15X6vzcSw
ZyeFITXM9FNkPcpXQtz79HWrrzq9UaTOVmWZVqTUbQmaV96clhzDNXlZWSF/oxdJ
mRHxAkEA6TrwLFn08yXLZCSm+njQ/6ASO6I5WnwTyppL/WdP70EBI99ghG/JhXri
VFKOhliM1stMbkU3r0ME4aNHS9NHbQJAavkokvxSfQcifj5t05UvD7v/E2nI+RLq
9DiPNWmcoxhspLk7rzT3M7vNkWtJagcgpzhIaEJ08oixr9rb9ztEYQJAY8t4Z/3A
DQLETh3GZ5XPPCpEFElAXJg1ksNU/HAlF6+DCwv4E5ainVAlR3+ZeXcvw0a/KTpg
vOntaIf9dsS4Fw==
```

### Timestamp:

`124124`

### URL:

`/service-pay/sellerApi/getMerchantByUsername`

### HTTP Body:

`null`

### Sorted and Concatenated String for Signing

`124124_/service-pay/sellerApi/getMerchantByUsername_aaparam=3&abparam=1&aparam=2&username=4802097272`

### Signature Generation

Generate a SHA256withRSA digest using the 'Sorted and Concatenated String for Signing' result with the 'Merchant Private Key', and encode it in Base64.

_Note: When passing the result from step 3 to SHA256withRSA for calculation, ensure that the string is UTF-8 encoded. Below is a Java code example._

```java
    // 
    private static String sign(String privateKeyStr, String data) throws Exception {
        byte[] keyBytes = Base64.getDecoder().decode(privateKeyStr);
        PKCS8EncodedKeySpec keySpec = new PKCS8EncodedKeySpec(keyBytes);
        KeyFactory keyFactory = KeyFactory.getInstance("RSA");
        PrivateKey privateKey = keyFactory.generatePrivate(keySpec);

        Signature signature = Signature.getInstance("SHA256withRSA");
        signature.initSign(privateKey);
        signature.update(data.getBytes("UTF-8"));

        byte[] signBytes = signature.sign();
        return Base64.getEncoder().encodeToString(signBytes);
    }
```

The signature generated using the merchant's private key mentioned above is:

```
V3pfPN1F3RX9Slak0EOhBmWI79iwmsQTECOLs5HOnLa3AOiYx7pZHMAroA3wJ6ksik1bORwhNVdhIf0jexzisD/SZHMRniZmSd7l6+PLT/iE/sguxyhqyz68tvXGSj5+Bv33cH5JMqIHH6ey4R+ojDgY4/zHKMnsdIkbdyQAk/o=
```
