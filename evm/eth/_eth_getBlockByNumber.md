### eth_getBlockByNumber
Returns information about a block by block number.



#### POST Request

`POST https://exchaintestrpc.okex.org`

> Request Example

```json
curl --location --request POST 'https://exchaintestrpc.okex.org/' \
--header 'Content-Type: application/json' \
--data-raw '{
	"jsonrpc": "2.0",
	"method": "eth_getBlockByNumber",
	"params": ["0x1", false],
	"id": 1
}'

```

#### Request Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Block Number | String   | |
| If true it returns the full transaction objects, if false only the hashes of the transactions. | Boolean   |  |

> Example Response

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"result": {
		"difficulty": null,
		"extraData": "0x0",
		"gasLimit": "0xffffffff",
		"gasUsed": null,
		"hash": "0xabac6416f737a0eb54f47495b60246d405d138a6a64946458cf6cbeae0d48465",
		"logsBloom": "0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
		"miner": "0x0000000000000000000000000000000000000000",
		"nonce": null,
		"number": "0x1",
		"parentHash": "0x",
		"sha3Uncles": null,
		"size": "0x9b",
		"stateRoot": "0x",
		"timestamp": "0x5f5bd3e5",
		"totalDifficulty": null,
		"transactions": [],
		"transactionsRoot": "0x",
		"uncles": []
	}
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  jsonrpc              | String    | 				| 
|  id                   | String    | 				| 
|  result               | Object    | 				| 
| > logsBloom           | String    | 				| 
| > totalDifficulty     | String    | 				| 
| > extraData           | String    | 				| 
| > transactions        | Array    | 				| 
| > nonce               | String    | 				| 
| > miner               | String    | 				| 
| > difficulty          | String    | 				| 
| > gasLimit            | String    | 				| 
| > number              | String    | 				| 
| > gasUsed             | String    | 				| 
| > uncles              | Array    | 				| 
| > sha3Uncles          | String    | 				| 
| > size                | String    | 				| 
| > transactionsRoot    | String    | 				| 
| > stateRoot           | String    | 				| 
| > parentHash          | String    | 				| 
| > hash                | String    | 				| 
| > timestamp           | String    | 				|                                                                                                                                                                                                                                                    | |
 