### web3_sha3

Returns the current network id.

#### POST Request

`POST https://exchaintestrpc.okex.org`

> Request Example

```json
curl --location --request POST 'https://exchaintestrpc.okex.org/' \
--header 'Content-Type: application/json' \
--data-raw '{
	"jsonrpc": "2.0",
	"method": "net_version",
	"params": [],
	"id": 1
}'

```

#### Request Parameters
| **Parameter** | **Type** | **Description**                                                                                                                                                                          |
| :------------ | :------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| params        | Array   |                                                                                                                                                                                          |

> Example Response

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"result": "8"
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| jsonrpc      | String   |                                                                                                                                                                                                                                                      |
| id           | String   |                                                                                                                                                                                                                                                       |
| result       | String   |                                                                                                                                                                                                                                                     | |
