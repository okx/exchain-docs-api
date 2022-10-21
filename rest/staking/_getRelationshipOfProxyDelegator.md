## Get relationship of proxy delegator

Query the proxy relationship on a proxy delegator

#### Rate Limit: 6 requests per second

#### HTTP Request

`GET okexchain/v1/staking/delegators/{address}/proxy
`

> Request Example

```wiki
https://www.okex.com/okexchain/v1/staking/delegators/ex1pt7xrmxul7sx54ml44lvv403r06clrdk0s8rxy/proxy
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
