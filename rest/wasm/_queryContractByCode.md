## Query all corresponding contracts of specified codeid

Query all corresponding contracts of specified codeid

#### Rate Limit: 6 requests per second

#### HTTP Request

`GET okexchain/v1/wasm/code/{codeID}/contracts`

> Request Example

```wiki
https://exchainrpc.okex.org/okexchain/v1/wasm/code/3/contracts?page=1&count_total=true&reverse=true&limit=1
```

#### Request Parameters
| **Parameter** | **Type** | **Required** | **Description**                                                                                                                                                                                                                   |
|:--------------|:---------|:-------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| codeID       | String   | Yes           |                                                                                                                                                                                                                                   |
| page          | Uint64   | No           |                                                                                                                                                                                                                                   |
| page_key      | String   | No           | page_key is a value returned in PageResponse.next_key to begin querying the next page most efficiently. Only one of offset or key should be set.                                                                                  |
| offset        | Uint64   | No           | offset is a numeric offset that can be used when page_key is unavailable. It is less efficient than using key. Only one of offset or key should be set.                                                                           |
| limit         | Uint64   | No           | limit is the total number of results to be returned in the result page. If left empty it will default to a value to be set by each app.                                                                                           |
| count_total   | Bool     | No           | count_total is set to true to indicate that the result set should include a count of the total number of items available for pagination in UIs. count_total is only respected when offset is used. It is ignored when key is set. |
| reverse       | Bool     | No           | reverse is set to true if results are to be returned in the descending order.                                                                                                                                                     |
**Once page is set, page_key or offset cannot be set.**

> Example Response

```json
{
  "contracts": [
    "ex1qg5ega6dykkxc307y25pecuufrjkxkaggkkxh7nad0vhyhtuhw3s4zjvwg"
  ],
  "pagination": {
    "total": "1"
  }
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  contracts             | Array    | 		contract Address Array		| 
|  pagination               | Object    | 	page response	parameters		| 
|  pagination.next_key      | String    | 		the next page start key		|  
|  pagination.total               | String    | 	it's a number format			|  
