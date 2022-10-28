## Get UnBondingToken of delegator

Query the unbonding token information of the specified delegator

#### Rate Limit: 6 requests per second

#### HTTP Request

`GET okexchain/v1/staking/delegators/{address}/unbonding_delegations`

> Request Example

```wiki
https://exchainrpc.okex.org/okexchain/v1/staking/delegators/ex17se79kf0c9t5sw0yg0jjdm6et79sy8aradphtg/unbonding_delegations
```

#### Request Parameters

None
> Example Response

```json
{
  "delegator_address": "ex10q0rk5qnyag7wfvvt7rtphlw589m7frs3hvqmf",
  "quantity": "1.02400000",
  "completion_time": "2020-05-25T09:44:55.736074648Z"
}

```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  delegator_address             | String    | 				| 
|  quantity               | String    | 				| 
|  completion_time        | String    | 				| 
