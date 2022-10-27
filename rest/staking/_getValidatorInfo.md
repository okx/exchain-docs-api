## Get validator Info

Query current staking pool assets

#### Rate Limit: 6 requests per second

#### HTTP Request

`GET okexchain/v1/staking/pool`

> Request Example

```wiki
https://exchainrpc.okex.org/okexchain/v1/staking/pool
```

#### Request Parameters

None
> Example Response

```json
{
  "not_bonded_tokens": "46658.862345999999959778",
  "bonded_tokens": "4561558.000338499999741215"
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  not_bonded_tokens     | String    | 				|
|  bonded_tokens         | String    | 				|
