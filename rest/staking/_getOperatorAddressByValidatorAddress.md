## Get operator address

Query corresponding operator_address through validator_address

#### Rate Limit: 6 requests per second

#### HTTP Request

`GET okexchain/v1/v1/staking/address/{operator_addr}/validator_address`

> Request Example

```wiki
https://www.okex.com/okexchain/v1/staking/address/B8586789B5681169A6CDC670775AC83FF560AA2F/validator_address
```

#### Request Parameters

None
> Example Response

```json
"exvaloper1q9nct2gska2yutx24starv6s63xz022fdwdgzv"
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  address         | String    | 				|
