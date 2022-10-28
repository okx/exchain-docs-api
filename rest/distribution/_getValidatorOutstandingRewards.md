## Get outstanding for a validator

Query distribution outstanding (un-withdrawn) rewards for a validator and all their delegations

#### Rate Limit: 6 requests per second

#### HTTP Request

`GET okexchain/v1/distribution/validators/{{validatorAddr}}/outstanding_rewards`

> Request Example

```wiki
https://exchainrpc.okex.org/okexchain/v1/distribution/validators/exvaloper1q9nct2gska2yutx24starv6s63xz022fdwdgzv/outstanding_rewards
```

#### Request Parameters

None
> Example Response

```json
[
    {
        "denom": "okt",
        "amount": "3.150937542414329105"
    }
]
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  denom             | String    | 				| 
|  amount               | String    | 				| 