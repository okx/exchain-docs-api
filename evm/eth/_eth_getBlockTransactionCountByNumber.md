### eth_getBlockTransactionCountByNumber¶


Returns the total transaction count for a given block number.


#### POST Request

`POST https://exchaintestrpc.okex.org`

> Request Example

```json
curl --location --request POST 'https://exchaintestrpc.okex.org/' \
--header 'Content-Type: application/json' \
--data-raw '{
	"jsonrpc": "2.0",
	"method": "eth_getBlockTransactionCountByNumber",
	"params": ["0x1"],
	"id": 1
}'

```

#### Request Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Block Number           | String   |                                                                                                                                                                                                                                                       |

> Example Response

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"result": {
		"difficulty": null,
		"extraData": "0x0",
		"gasLimit": "0xffffffff",
		"gasUsed": "0x0",
		"hash": "0x8101cc04aea3341a6d4b3ced715e3f38de1e72867d6c0db5f5247d1a42fbb085",
		"logsBloom": "0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
		"miner": "0x0000000000000000000000000000000000000000",
		"nonce": null,
		"number": "0x17d",
		"parentHash": "0x70445488069d2584fea7d18c829e179322e2b2185b25430850deced481ca2e77",
		"sha3Uncles": null,
		"size": "0x1df",
		"stateRoot": "0x269bb17fe7adb8dd5f15f57b717979f82078d6b7a675c1ba1b0da2d27e415fcc",
		"timestamp": "0x5f5ba97c",
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
| > timestamp           | String    | 				| 