##  Query contract history information

Query contract history information

#### Rate Limit: 6 requests per second

#### HTTP Request

`GET okexchain/v1/wasm/contract/{contractAddr}/history`

> Request Example

```wiki
https://exchainrpc.okex.org/okexchain/v1/wasm/code
```
coderID
#### Request Parameters
| **Parameter** | **Type** | **Required** | **Description**                                                                                                                                                                                                                   |
|:--------------|:---------|:-------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| contractAddr       | String   | Yes           |                                                                                                                                                                                                                                   |
| page          | Uint64   | No           |                                                                                                                                                                                                                                   |
| page_key      | String   | No           | page_key is a value returned in PageResponse.next_key to begin querying the next page most efficiently. Only one of offset or key should be set.                                                                                  |
| offset        | Uint64   | No           | offset is a numeric offset that can be used when page_key is unavailable. It is less efficient than using key. Only one of offset or key should be set.                                                                           |
| limit         | Uint64   | No           | limit is the total number of results to be returned in the result page. If left empty it will default to a value to be set by each app.                                                                                           |
| count_total   | Bool     | No           | count_total is set to true to indicate that the result set should include a count of the total number of items available for pagination in UIs. count_total is only respected when offset is used. It is ignored when key is set. |
| reverse       | Bool     | No           | reverse is set to true if results are to be returned in the descending order.                                                                                                                                                     |
> Example Response

```json
{
  "code_infos": [
    {
      "id": "1",
      "creator": "ex1h0j8x0v9hs4eq6ppgamemfyu4vuvp2sl0q9p3v",
      "data_hash": "13A1FC994CC6D1C81B746EE0C0FF6F90043875E0BF1D9BE6B7D779FC978DC2A5",
      "instantiate_permission": {
        "permission": "Everybody"
      }
    }
  ],
  "pagination": {
    "next_key": "AAAAAAAAAAI=",
    "total": "2"
  }
}
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
