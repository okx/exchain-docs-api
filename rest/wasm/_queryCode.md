## Get contract code

Get contract code by codeID

#### Rate Limit: 6 requests per second

#### HTTP Request

`GET okexchain/v1/wasm/code/{codeID}`

> Request Example



```wiki
https://exchainrpc.okex.org/okexchain/v1/wasm/code/1
```

#### Request Parameters

| **Parameter** | **Type** | **Required** | **Description**                                                                                                                                                                                                     |
| :------------ | :------- | :----------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| coderID      | String   | Yes           | |

> Example Response

```json
{
  "id": 1,
  "creator": "ex1h0j8x0v9hs4eq6ppgamemfyu4vuvp2sl0q9p3v",
  "data_hash": "13A1FC994CC6D1C81B746EE0C0FF6F90043875E0BF1D9BE6B7D779FC978DC2A5",
  "instantiate_permission": {
    "permission": "Everybody"
  },
  "data": "contract bytescode"
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  id             | int64    | 				| 
|  creator               | String    | 				| 
|  data_hash        | String    | 				| 
|  instantiate_permission| Object    | 				| 
|  data    | String    | 				| 
|  Object.permission               | String    | 				| 
