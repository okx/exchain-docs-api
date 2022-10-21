### eth_getFilterChanges

Returns an array of all logs matching a given filter object.


#### POST Request

`POST https://exchaintestrpc.okex.org`

> Request Example

```json
curl --location --request POST 'https://exchaintestrpc.okex.org/' \
--header 'Content-Type: application/json' \
--data-raw '{"jsonrpc":"2.0","method":"eth_getLogs","params":[{"topics":["0x775a94827b8fd9b519d36cd827093c664f93347070a554f65e4a6f56cd738898","0x0000000000000000000000000000000000000000000000000000000000000011"],"fromBlock":"latest"}],"id":1}'

```

#### Request Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| fromBlock     | String   |   QUANTITY TAG - (optional, default: “latest”) Integer block number, or “latest” for the last mined block or “pending”, “earliest” for not yet mined transactions.|
| toBlock     | String   |   QUANTITY TAG - (optional, default: “latest”) Integer block number, or “latest” for the last mined block or “pending”, “earliest” for not yet mined transactions.|
| address     | String   |    DATA Array, 20 Bytes - (optional) Contract address or a list of addresses from which logs should originate.|
| topics     | Array   |     Array of DATA, - (optional) Array of 32 Bytes DATA topics. Topics are order-dependent. Each topic can also be an array of DATA with “or” options.                                                                                                                                                                                                                                                 |
| blockhash     | String   |  (optional, future) With the addition of EIP-234, blockHash will be a new filter option which restricts the logs returned to the single block with the 32-byte hash blockHash. Using blockHash is equivalent to fromBlock = toBlock = the block number with hash blockHash. If blockHash is present in in the filter criteria, then neither fromBlock nor toBlock are allowed.                                                                                                                                                                                                                                                    |

> Example Response

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"result": []
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  jsonrpc              | String    | 				| 
|  id                   | String    | 				| 
|  result               | Array    | 				|