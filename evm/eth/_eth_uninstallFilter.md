### eth_uninstallFilter¶

Removes the filter with the given filter id. Returns true if the filter was successfully uninstalled, otherwise false.



#### POST Request

`POST https://exchaintestrpc.okex.org`

> Request Example

```json
curl --location --request POST 'https://exchaintestrpc.okex.org/' \
--header 'Content-Type: application/json' \
--data-raw '{
	"jsonrpc": "2.0",
	"method": "eth_uninstallFilter",
	"params": ["0xb91b6608b61bf56288a661a1bd5eb34a"],
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
	"result": true
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  jsonrpc              | String    | 				| 
|  id                   | String    | 				| 
|  result               | Boolean    | 				|