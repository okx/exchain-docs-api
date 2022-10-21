### eth_sendTransaction

Sends transaction from given account to a given account.


#### POST Request

`POST https://exchaintestrpc.okex.org`

> Request Example

```json
curl --location --request POST 'https://exchaintestrpc.okex.org/' \
--header 'Content-Type: application/json' \
--data-raw '{
	"jsonrpc": "2.0",
	"method": "eth_sendTransaction",
	"params": [{
		"from": "0x3b7252d007059ffc82d16d022da3cbf9992d2f70",
		"to": "0x0f54f47bf9b8e317b214ccd6a7c3e38b893cd7f0",
		"value": "0x16345785d8a0000",
		"gasLimit": "0x5208",
		"gasPrice": "0x55ae82600"
	}],
	"id": 1
}'

```

#### Request Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| from    | String   |   DATA, 20 Bytes - The address the transaction is send from.                                                                                                                                                                                                                                                    |
| to    | String   |   DATA, 20 Bytes - (optional when creating new contract) The address the transaction is directed to.                                                                                                                                                                                                                                                    |
| gas    | String   |   QUANTITY - (optional, default: 90000) Integer of the gas provided for the transaction execution. It will return unused gas.|
| gasPrice    | String   |   QUANTITY - (optional, default: To-Be-Determined) Integer of the gasPrice used for each paid gas|
| value    | String   |   QUANTITY - value sent with this transaction|
| data    | String   |   DATA - The compiled code of a contract OR the hash of the invoked method signature and encoded parameters. For details see Ethereum Contract ABI|
| nonce    | String   |   QUANTITY - (optional) Integer of a nonce. This allows to overwrite your own pending transactions that use the same nonce.|

> Example Response

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"result": "0x33653249db68ebe5c7ae36d93c9b2abc10745c80a72f591e296f598e2d4709f6"
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| jsonrpc      | String   |                                                                                                                                                                                                                                                      |
| id           | String   |                                                                                                                                                                                                                                                       |
| result       | String   |                                                                                                                                                                                                                                                     | |
 