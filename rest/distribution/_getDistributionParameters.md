## Query distribution params

Query distribution params onchain

#### Rate Limit: 6 requests per second

#### HTTP Request

`GET okexchain/v1/distribution/parameters`

> Request Example

```wiki
https://exchainrpc.okex.org/okexchain/v1/distribution/parameters
```

#### Request Parameters

None
> Example Response

```json
{
    "community_tax": "0.020000000000000000",
    "withdraw_addr_enabled": true,
    "distribution_type": 1,
    "withdraw_reward_enabled": true,
    "reward_truncate_precision": "0"
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  community_tax             | String    | 		community tax		| 
|  withdraw_addr_enabled               | bool    | 	enable use	withdraw address 		| 
|  distribution_type        | int    | 		distribution model,0 offchain; 1 onchain		| 
|  withdraw_reward_enabled    | bool    | 	enable withdraw reward			| 
|  reward_truncate_precision| String    | 	Dividend precision truncated. 0 means to keep 0 decimal points, such as 1.2345 truncated dividend is 1; 2 means to keep two decimal points. For example, the dividend after 1.2345 truncated is 1.23			| 