### eth_getTransactionByBlockHashAndIndex

Returns transaction details given the block hash and the transaction index.



#### POST Request

`POST https://exchaintestrpc.okex.org`

> Request Example

```json
curl --location --request POST 'https://exchaintestrpc.okex.org/' \
--header 'Content-Type: application/json' \
--data-raw '{
	"jsonrpc": "2.0",
	"method": "eth_getTransactionByBlockHashAndIndex",
	"params": ["0x1b9911f57c13e5160d567ea6cf5b545413f96b95e43ec6e02787043351fb2cc4", "0x0"],
	"id": 1
}'

```

#### Request Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Hash of a block.      | String   |                                                                                                                                                                                                                                                      |
| Transaction index position.      | String   |                                                                                                                                                                                                                                                      |

> Example Response

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"result": {
		"blockHash": "0x1b9911f57c13e5160d567ea6cf5b545413f96b95e43ec6e02787043351fb2cc4",
		"blockNumber": "0xc",
		"from": "0xddd64b4712f7c8f1ace3c145c950339eddaf221d",
		"gas": "0x4c4b40",
		"gasPrice": "0x3b9aca00",
		"hash": "0xae64961cb206a9773a6e5efeb337773a6fd0a2085ce480a174135a029afea615",
		"input": "0x4f2be91f",
		"nonce": "0x0",
		"to": "0x439c697e0742a0ddb124a376efd62a72a94ac35a",
		"transactionIndex": "0x0",
		"value": "0x0",
		"v": "0xa96",
		"r": "0xced57d973e58b0f634f776d57daf41d3d3387ceb347a3a72ca0746e5ec2b709e",
		"s": "0x384e89e209a5eb147a2bac3a4e399507400ac7b29cd155531f9d6203a89db3f2"
	}
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  jsonrpc              | String    | 				| 
|  id                   | String    | 				| 
|  result               | Object    | 				| 
| > blockHash           | String    | 				| 
| > transactionIndex    | String    | 				| 
| > nonce               | String    | 				| 
| > input               | String    | 				| 
| > r                   | String    | 				| 
| > s                   | String    | 				| 
| > v                   | String    | 				| 
| > blockNumber         | String    | 				| 
| > gas                 | String    | 				| 
| > from                | String    | 				| 
| > to                  | String    | 				| 
| > value               | String    | 				| 
| > hash                | String    | 				| 
| > gasPrice            | String    | 				| 