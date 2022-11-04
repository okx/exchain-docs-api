## Query contract status

Query contract all state data

#### Rate Limit: 6 requests per second

#### HTTP Request

`GET okexchain/v1/wasm/contract/{contractAddr}/state`

> Request Example

```wiki
https://exchainrpc.okex.org/okexchain/v1/wasm/contract/ex1ufs3tlq4umljk0qfe8k5ya0x6hpavn897u2cnf9k0en9jr7qarqqy2pl6c/state?page=1&count_total=true&reverse=true&limit=2
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

**Once page is set, page_key or offset cannot be set.* 
> Example Response

```json
{
  "models": [
    {
      "key": "0006636F6E666967746F74616C5F737570706C79",
      "value": "AAAAAAAAAAAAAAAABfXhAA=="
    },
    {
      "key": "0006636F6E666967636F6E7374616E7473",
      "value": "eyJuYW1lIjoibXkgdGVzdCB0b2tlbiIsInN5bWJvbCI6Ik1UVCIsImRlY2ltYWxzIjoxMH0="
    }
  ],
  "pagination": {
    "next_key": "AAhiYWxhbmNlc2V4MWV1dHl1cXFhc2UzZXl2d2U5MmNhdzhkY3g1bHk4czU0NHEzaG1x",
    "total": "4"
  }
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  models             | Array Object    | 				|
|  model.key             | String    | 		data key which is hex code		| 
|  model.value               | String    | 		data value which is base64		| 
|  pagination               | Object    | 	page response	parameters		| 
|  pagination.next_key      | String    | 		the next page start key		|  
|  pagination.total               | String    | 	it's a number format			| 

