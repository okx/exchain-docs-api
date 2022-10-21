### web3_clientVersion

Get the web3 client version.

#### POST Request

`POST https://exchaintestrpc.okex.org`

> Request Example

```json
curl --location --request POST 'https://exchaintestrpc.okex.org/' \
--header 'Content-Type: application/json' \
--data-raw '{
	"jsonrpc": "2.0",
	"method": "web3_clientVersion",
	"params": [],
	"id": 67
}'

```

#### Request Parameters

None

> Example Response

```json
{
	"jsonrpc": "2.0",
	"id": 67,
	"result": "exchain-v0.18.4"
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| jsonrpc      | String   |                                                                                                                                                                                                                                                      |
| id           | String   |                                                                                                                                                                                                                                                       |
| result       | String   |                                                                                                                                                                                                                                                     | |
