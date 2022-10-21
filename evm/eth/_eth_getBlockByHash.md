### eth_getBlockByHash

Returns the block info given the hash found in the command above and a bool.


#### POST Request

`POST https://exchaintestrpc.okex.org`

> Request Example

```json
curl --location --request POST 'https://exchaintestrpc.okex.org/' \
--header 'Content-Type: application/json' \
--data-raw '{
	"jsonrpc": "2.0",
	"method": "eth_getBlockByHash",
	"params": ["0x1b9911f57c13e5160d567ea6cf5b545413f96b95e43ec6e02787043351fb2cc4", false],
	"id": 1
}'

```

#### Request Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Hash of a block.      | String   |                                                                                                                                                                                                                                                      |
| If true it returns the full transaction objects, if false only the hashes of the transactions.           | String   |                                                                                                                                                                                                                                                       |

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
		"hash": "0x1b9911f57c13e5160d567ea6cf5b545413f96b95e43ec6e02787043351fb2cc4",
		"logsBloom": "0x00000000100000000000000000000000000000000000000000000000000000000000020000000000000000000000000000000000000000000000000000000000000040000000000000000000000000200000000000000000000000000000000000000000000000000000000000000000100000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000002000000000000000000000000000000000000000004000000000000000000000000000000000000000000000000000000000000000000000010000000000000000000000000000000000000000000000000000000000000000000000000000",
		"miner": "0x0000000000000000000000000000000000000000",
		"nonce": null,
		"number": "0xc",
		"parentHash": "0x404e58f31a9ede1b614b98701d6b0fbf1450f186842dbcf6426dd16811a5ca0d",
		"sha3Uncles": null,
		"size": "0x307",
		"stateRoot": "0x599ccdb111fc62c6398dc39be957df8e97bf8ab72ce6c06ff10641a92b754627",
		"timestamp": "0x5f5fdbbd",
		"totalDifficulty": null,
		"transactions": ["0xae64961cb206a9773a6e5efeb337773a6fd0a2085ce480a174135a029afea615"],
		"transactionsRoot": "0x4764dba431128836fa919b83d314ba9cc000e75f38e1c31a60484409acea777b",
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
| > timestamp           | String    | 				| 