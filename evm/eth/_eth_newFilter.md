### eth_getTransactionByBlockHashAndIndex

Create new filter using topics of some kind.



#### POST Request

`POST https://exchaintestrpc.okex.org`

> Request Example

```json
curl --location --request POST 'https://exchaintestrpc.okex.org/' \
--header 'Content-Type: application/json' \
--data-raw '{
	"jsonrpc": "2.0",
	"method": "eth_newFilter",
	"params": [{
		"topics": ["0x0000000000000000000000000000000000000000000000000000000012341234"]
	}],
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
	"result": "0xdc714a4a2e3c39dc0b0b84d66a3ccb00"
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  jsonrpc              | String    | 				| 
|  id                   | String    | 				| 
|  result               | String    | 				|