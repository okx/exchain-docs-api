## Get amount in community pool

Query the amount of coins in the community pool

#### Rate Limit: 6 requests per second

#### HTTP Request

`GET okexchain/v1/distribution/community_pool`

> Request Example

```wiki
https://exchainrpc.okex.org/okexchain/v1/distribution/community_pool
```

#### Request Parameters

None
> Example Response

```json
[
    {
        "denom": "okt",
        "amount": "2.471826444531520986"
    }
]
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  denom             | String    | 	community pool denom			| 
|  amount               | String    | 	community pool amount			| 