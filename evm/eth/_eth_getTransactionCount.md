### eth_getTransactionCount

Returns the total transaction for a given account address and Block Number.


#### POST Request

`POST https://exchaintestrpc.okex.org`

> Request Example

```json
curl --location --request POST 'https://exchaintestrpc.okex.org/' \
--header 'Content-Type: application/json' \
--data-raw '{
	"jsonrpc": "2.0",
	"method": "eth_getTransactionCount",
	"params": ["0x7bf7b17da59880d9bcca24915679668db75f9397", "0x0"],
	"id": 1
}'

```

#### Request Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Account Address      | String   |                                                                                                                                                                                                                                                      |
| Block Number           | String   |                                                                                                                                                                                                                                                       |

> Example Response

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"result": "0x8"
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| jsonrpc      | String   |                                                                                                                                                                                                                                                      |
| id           | String   |                                                                                                                                                                                                                                                       |
| result       | String    |                                                                                                                                                                                                                                                     | |
