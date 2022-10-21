### eth_estimateGas
Returns an estimate value of the gas required to send the transaction.



#### POST Request

`POST https://exchaintestrpc.okex.org`

> Request Example

```json
curl --location --request POST 'https://exchaintestrpc.okex.org/' \
--header 'Content-Type: application/json' \
--data-raw '{
	"jsonrpc": "2.0",
	"method": "eth_estimateGas",
	"params": [{
		"from": "0x0f54f47bf9b8e317b214ccd6a7c3e38b893cd7f0",
		"to": "0x3b7252d007059ffc82d16d022da3cbf9992d2f70",
		"value": "0x16345785d8a00000"
	}],
	"id": 1
}'

```

#### Request Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| from | String   |  DATA, 20 Bytes - The address the transaction is send from. |
| to | String   |  DATA, 20 Bytes - (optional when creating new contract) The address the transaction is directed to.|
| value | String   | QUANTITY - value sent with this transaction|

> Example Response

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"result": "0x1199b"
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| jsonrpc      | String   |                                                                                                                                                                                                                                                      |
| id           | String   |                                                                                                                                                                                                                                                       |
| result       | String   |                                                                                                                                                                                                                                                     | |
 