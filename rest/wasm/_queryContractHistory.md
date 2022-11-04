##  Query contract history information

Query contract history information

#### Rate Limit: 6 requests per second

#### HTTP Request

`GET okexchain/v1/wasm/contract/{contractAddr}/history`

> Request Example

```wiki
https://exchainrpc.okex.org/okexchain/v1/wasm/contract/ex1ufs3tlq4umljk0qfe8k5ya0x6hpavn897u2cnf9k0en9jr7qarqqy2pl6c/history?page=1&count_total=true&reverse=true&limit=2
```

#### Request Parameters
| **Parameter**     | **Type** | **Required** | **Description**                                                                                                                                                                                                                                |
|:------------------|:---------|:-------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| contractAddr      | String   | Yes          |                                                                                                                                                                                                                                                |
| page              | Uint64   | No           |                                                                                                                                                                                                                                                |
| page_key          | String   | No           | `page_key` is a value returned in `PageResponse.next_key` to begin querying the next page most efficiently. Only one of `offset` or `page_key` should be set.                                                                                  |
| offset            | Uint64   | No           | `offset` is a numeric offset that can be used when `page_key` is unavailable. It is less efficient than using key. Only one of `offset` or `page_key` should be set.                                                                           |
| limit             | Uint64   | No           | `limit` is the total number of results to be returned in the result page. If left empty it will default to a value to be set by each app.                                                                                                      |
| count_total       | Bool     | No           | `count_total` is set to true to indicate that the result set should include a count of the total number of items available for pagination in UIs. `count_total` is only respected when `offset` is used. It is ignored when `page_key` is set. |
| reverse           | Bool     | No           | `reverse` is set to true if results are to be returned in the descending order.                                                                                                                                                                |
**Once page is set, page_key or offset cannot be set.**

> Example Response

```json
{
  "entries": [
    {
      "operation": 1,
      "code_id": "5",
      "msg": {
        "decimals": 10,
        "initial_balances": [
          {
            "address": "ex1h0j8x0v9hs4eq6ppgamemfyu4vuvp2sl0q9p3v",
            "amount": "100000000"
          }
        ],
        "name": "my test token",
        "symbol": "MTT"
      }
    }
  ],
  "pagination": {
    "total": "1"
  }
}
```

#### Response Parameters

| **Parameter**                       | **Type**      | **Description**                |
|:------------------------------------|:--------------|:-------------------------------|
| entries                             | Array Object  | 	the history info of contract	 |
| entry.operation                     | Int64         | 	contract operate type			      |
| entry.code_id                       | String        | 		code id		                    |
| entry.msg                           | Object        | 				                           |
| entry.msg.decimals                  | Int64         | 				                           |
| entry.msg.initial_balances          | Array Object  | 			                            |
| entries.msg.initial_balance.address | String        | 				                           |
| entries.msg.initial_balance.address | String        | 				                           |
| entries.msg.name                    | String        | 	contract name			              |
| entries.msg.symbol                  | String        | 		contract symbol		            |
| pagination                          | Object        | 	page response	parameters		    | 
| pagination.next_key                 | String        | 		the next page start key		    |  
| pagination.total                    | String        | 	it's a number format			       | 
