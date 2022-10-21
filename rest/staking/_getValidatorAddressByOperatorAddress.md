## Get validator address

Query corresponding account_address through operator_address

#### Rate Limit: 6 requests per second

#### HTTP Request

`GET okexchain/v1/v1/staking/address/{operator_addr}/account_address`

> Request Example

```wiki
https://www.okex.com/okexchain/v1/staking/address/exvaloper1q9nct2gska2yutx24starv6s63xz022fdwdgzv/account_address
```

#### Request Parameters

None
> Example Response

```json
"ex1q9nct2gska2yutx24starv6s63xz022fmf8vxk"
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  address         | String    | 				|
