## Query contract information

Query contract information by contract address

#### Rate Limit: 6 requests per second

#### HTTP Request

`GET okexchain/v1/wasm/contract/{contractAddr}`

> Request Example

```wiki
https://exchainrpc.okex.org/okexchain/v1/wasm/contract/ex14hj2tavq8fpesdwxxcu44rty3hh90vhujrvcmstl4zr3txmfvw9s6fqu27
```

#### Request Parameters

| **Parameter** | **Type** | **Required** | **Description**                                                                                                                                                                                                     |
| :------------ | :------- | :----------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| contractAddr      | String   | Yes           | |

> Example Response

```json
{
  "address": "ex14hj2tavq8fpesdwxxcu44rty3hh90vhujrvcmstl4zr3txmfvw9s6fqu27",
  "code_id": 2,
  "creator": "ex1h0j8x0v9hs4eq6ppgamemfyu4vuvp2sl0q9p3v",
  "label": "local0.1.0"
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  address             | String    | 	contract address 			| 
|  code_id               | int64    | 		code id		| 
|  creator        | String    | 		the creator of  contract 		| 
|  label| String    | 		contract label		|
