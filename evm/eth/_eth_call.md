### eth_call
Executes a new message call immediately without creating a transaction on the block chain.


#### POST Request

`POST https://exchaintestrpc.okex.org`

> Request Example

```json
curl --location --request POST 'https://exchaintestrpc.okex.org/' \
--header 'Content-Type: application/json' \
--data-raw '{
	"jsonrpc": "2.0",
	"method": "eth_call",
	"params": [{
		"from": "0x3b7252d007059ffc82d16d022da3cbf9992d2f70",
		"to": "0xddd64b4712f7c8f1ace3c145c950339eddaf221d",
		"gas": "0x5208",
		"gasPrice": "0x55ae82600",
		"value": "0x16345785d8a0000",
		"data": "0xd46e8dd67c5d32be8d46e8dd67c5d32be8058bb8eb970870f072445675058bb8eb970870f072445675"
	}, "0x0"],
	"id": 1
}'

```

#### Request Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| from | String   |  DATA, 20 Bytes - (optional) The address the transaction is sent from. |
| to | String   |  DATA, 20 Bytes - The address the transaction is directed to.|
| gas | String   |  QUANTITY - gas provided for the transaction execution. eth_call consumes zero gas, but this parameter may be needed by some executions.|
| gasPrice | String   |  QUANTITY - gasPrice used for each paid gas |
| value | String   | QUANTITY - value sent with this transaction |
| data | String   | DATA - (optional) Hash of the method signature and encoded parameters. For details see Ethereum Contract ABI in the Solidity documentation|
| Block number | String   |  |

> Example Response

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"result": "0x"
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| jsonrpc      | String   |                                                                                                                                                                                                                                                      |
| id           | String   |                                                                                                                                                                                                                                                       |
| result       | String   |                                                                                                                                                                                                                                                     | |
 