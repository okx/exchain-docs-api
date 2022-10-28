## Get validator commission

Query distribution validator commission

#### Rate Limit: 6 requests per second

#### HTTP Request

`GET okexchain/v1/distribution/validators/{validatorAddr}/validator_commission`

> Request Example

```wiki
https://exchainrpc.okex.org/okexchain/v1/distribution/validators/exvaloper1q9nct2gska2yutx24starv6s63xz022fdwdgzv/validator_commission
```

#### Request Parameters

None
> Example Response

```json
[
    {
        "denom": "okt",
        "amount": "2.038175975947119947"
    }
]
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  denom             | String    | validator commission	denom		| 
|  amount               | String    | validator commission amount			| 