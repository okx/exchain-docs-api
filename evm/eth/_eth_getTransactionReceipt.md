### eth_getTransactionByBlockHashAndIndex

Returns the receipt of a transaction by transaction hash.



#### POST Request

`POST https://exchaintestrpc.okex.org`

> Request Example

```json
curl --location --request POST 'https://exchaintestrpc.okex.org/' \
--header 'Content-Type: application/json' \
--data-raw '{
	"jsonrpc": "2.0",
	"method": "eth_getTransactionReceipt",
	"params": ["0xae64961cb206a9773a6e5efeb337773a6fd0a2085ce480a174135a029afea614"],
	"id": 1
}'

```

#### Request Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Hash of a transaction     | String   |                                                                                                                                                                                                                                                      |

> Example Response

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"result": {
		"blockHash": "0x1b9911f57c13e5160d567ea6cf5b545413f96b95e43ec6e02787043351fb2cc4",
		"blockNumber": "0xc",
		"contractAddress": "0x0000000000000000000000000000000000000000",
		"cumulativeGasUsed": null,
		"from": "0xddd64b4712f7c8f1ace3c145c950339eddaf221d",
		"gasUsed": "0x5289",
		"logs": [{
			"address": "0x439c697e0742a0ddb124a376efd62a72a94ac35a",
			"topics": ["0x64a55044d1f2eddebe1b90e8e2853e8e96931cefadbfa0b2ceb34bee36061941"],
			"data": "0x0000000000000000000000000000000000000000000000000000000000000002",
			"blockNumber": "0xc",
			"transactionHash": "0xae64961cb206a9773a6e5efeb337773a6fd0a2085ce480a174135a029afea615",
			"transactionIndex": "0x0",
			"blockHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
			"logIndex": "0x0",
			"removed": false
		}, {
			"address": "0x439c697e0742a0ddb124a376efd62a72a94ac35a",
			"topics": ["0x938d2ee5be9cfb0f7270ee2eff90507e94b37625d9d2b3a61c97d30a4560b829"],
			"data": "0x0000000000000000000000000000000000000000000000000000000000000002",
			"blockNumber": "0xc",
			"transactionHash": "0xae64961cb206a9773a6e5efeb337773a6fd0a2085ce480a174135a029afea615",
			"transactionIndex": "0x0",
			"blockHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
			"logIndex": "0x1",
			"removed": false
		}],
		"logsBloom": "0x00000000100000000000000000000000000000000000000000000000000000000000020000000000000000000000000000000000000000000000000000000000000040000000000000000000000000200000000000000000000000000000000000000000000000000000000000000000100000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000002000000000000000000000000000000000000000004000000000000000000000000000000000000000000000000000000000000000000000010000000000000000000000000000000000000000000000000000000000000000000000000000",
		"status": "0x1",
		"to": "0x439c697e0742a0ddb124a376efd62a72a94ac35a",
		"transactionHash": "0xae64961cb206a9773a6e5efeb337773a6fd0a2085ce480a174135a029afea615",
		"transactionIndex": "0x0"
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
| > logsBloom           | String    | 				| 
| > gasUsed             | String    | 				| 
| > blockNumber         | String    | 				| 
| > contractAddress     | String    | 				| 
| > cumulativeGasUsed   | String    | 				| 
| > from                | String    | 				| 
| > transactionIndex    | String    | 				| 
| > to                  | String    | 				| 
| > logs                | Array     | 				| 
| >> blockHash          | String    | 				| 
| >> address            | String    | 				| 
| >> logIndex           | String    | 				| 
| >> data               | String    | 				| 
| >> removed            | String    | 				| 
| >> topics             | Array     | 				| 
| >> blockNumber        | String    | 				| 
| >> transactionIndex   | String    | 				| 
| >> transactionHash    | String    | 				| 
| > transactionHash     | String    | 				| 
| > status              | String    | 				|