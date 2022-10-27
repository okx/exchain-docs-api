## Get withdraw address

Query delegator's withdraw address

#### Rate Limit: 6 requests per second

#### HTTP Request

`GET okexchain/v1/distribution/delegators/{{delegatorAddr}}/withdraw_address`

> Request Example

```wiki
https://exchainrpc.okex.org/okexchain/v1/distribution/delegators/ex17se79kf0c9t5sw0yg0jjdm6et79sy8aradphtg/withdraw_address
```

#### Request Parameters

None
> Example Response

```json
"ex1h0j8x0v9hs4eq6ppgamemfyu4vuvp2sl0q9p3v"
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  String             | String    | 	withdraw address			| 