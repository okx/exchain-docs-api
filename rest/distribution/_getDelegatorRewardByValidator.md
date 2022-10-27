## Get delegator rewards from a validator

Query delegator rewards from a particular validator

#### Rate Limit: 6 requests per second

#### HTTP Request

`GET okexchain/v1/distribution/delegators/{delegatorAddr}/rewards/{validatorAddr}`

> Request Example

```wiki
https://exchainrpc.okex.org/okexchain/v1/distribution/delegators/ex17se79kf0c9t5sw0yg0jjdm6et79sy8aradphtg/rewards/exvaloper1q9nct2gska2yutx24starv6s63xz022fdwdgzv
```

#### Request Parameters

None
> Example Response

```json
[
    {
        "denom": "okt",
        "amount": "2.694422051593216614"
    }
]
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  denom             | String    | 				| 
|  amount               | String    | 				| 