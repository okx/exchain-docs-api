## Query all codes

Query all contract codes

#### Rate Limit: 6 requests per second

#### HTTP Request

`GET okexchain/v1/wasm/code`

> Request Example

```wiki
https://exchainrpc.okex.org/okexchain/v1/wasm/code
```

#### Request Parameters

None
> Example Response

```json
[
  {
    "id": 1,
    "creator": "ex1h0j8x0v9hs4eq6ppgamemfyu4vuvp2sl0q9p3v",
    "data_hash": "13A1FC994CC6D1C81B746EE0C0FF6F90043875E0BF1D9BE6B7D779FC978DC2A5",
    "instantiate_permission": {
      "permission": "Everybody"
    }
  },
  {
    "id": 2,
    "creator": "ex1h0j8x0v9hs4eq6ppgamemfyu4vuvp2sl0q9p3v",
    "data_hash": "DCE5CE229B1FE766ABD20AA0F0126D3FA9CB63F9C18C78192E14BAE51634304E",
    "instantiate_permission": {
      "permission": "Everybody"
    }
  }
]
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  id             | int64    | 				| 
|  creator               | String    | 				| 
|  data_hash        | String    | 				| 
|  instantiate_permission| Object    | 				| 
|  delegator_address    | String    | 				| 
|  shares               | String    | 				| 
