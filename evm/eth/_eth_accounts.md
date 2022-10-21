### eth_gasPrice

Returns array of all eth accounts.


#### POST Request

`POST https://exchaintestrpc.okex.org`

> Request Example

```json
curl --location --request POST 'https://exchaintestrpc.okex.org/' \
--header 'Content-Type: application/json' \
--data-raw '{
	"jsonrpc": "2.0",
	"method": "eth_accounts",
	"params": [],
	"id": 1
}'

```

#### Request Parameters

None

> Example Response

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"result": ["0x3b7252d007059ffc82d16d022da3cbf9992d2f70", "0xddd64b4712f7c8f1ace3c145c950339eddaf221d", "0x0f54f47bf9b8e317b214ccd6a7c3e38b893cd7f0"]
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| jsonrpc      | String   |                                                                                                                                                                                                                                                      |
| id           | String   |                                                                                                                                                                                                                                                       |
| result       | Array    |                                                                                                                                                                                                                                                     | |
