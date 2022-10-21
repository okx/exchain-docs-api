### eth_getBlockByHash

Returns transaction details given the ethereum tx something.


#### POST Request

`POST https://exchaintestrpc.okex.org`

> Request Example

```json
curl --location --request POST 'https://exchaintestrpc.okex.org/' \
--header 'Content-Type: application/json' \
--data-raw '{
	"jsonrpc": "2.0",
	"method": "eth_getTransactionByHash",
	"params": ["0xec5fa15e1368d6ac314f9f64118c5794f076f63c02e66f97ea5fe1de761a8973"],
	"id": 1
}'

```

#### Request Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| hash of a transaction      | String   |                                                                                                                                                                                                                                                      |

> Example Response

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"result": {
		"blockHash": "0x7a7398cc11d9c4c8e6f53e0c73824297aceafdab62db9e4b867a0da694384864",
		"blockNumber": "0x188",
		"from": "0x3b7252d007059ffc82d16d022da3cbf9992d2f70",
		"gas": "0x147ee",
		"gasPrice": "0x3b9aca00",
		"hash": "0xec5fa15e1368d6ac314f9f64118c5794f076f63c02e66f97ea5fe1de761a8973",
		"input": "0x6dba746c",
		"nonce": "0x18",
		"to": "0xa655256f589060437e5ffe2246dec385d040f148",
		"transactionIndex": "0x0",
		"value": "0x0",
		"v": "0xa96",
		"r": "0x6db399d694a452fb4106419140a6e5dbbe6817743a0f6f695a651e6576e59a5e",
		"s": "0x25dd6ab1f936d0280d2fed0caeb0ebe5b9a46de6d8cb08ad8fd2c88deb55fc31"
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