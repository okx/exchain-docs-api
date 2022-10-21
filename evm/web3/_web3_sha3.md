### web3_sha3

Returns Keccak-256 (not the standardized SHA3-256) of the given data.

#### POST Request

`POST https://exchaintestrpc.okex.org`

> Request Example

```json
curl --location --request POST 'https://exchaintestrpc.okex.org/' \
--header 'Content-Type: application/json' \
--data-raw '{
	"jsonrpc": "2.0",
	"method": "web3_sha3",
	"params": ["0x67656c6c6f20776f726c64"],
	"id": 1
}'

```

#### Request Parameters
| **Parameter** | **Type** | **Description**                                                                                                                                                                          |
| :------------ | :------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| params        | String   |                                                                                                                                                                                          |

> Example Response

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"result": "0x1b84adea42d5b7d192fd8a61a85b25abe0757e9a65cab1da470258914053823f"
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| jsonrpc      | String   |                                                                                                                                                                                                                                                      |
| id           | String   |                                                                                                                                                                                                                                                       |
| result       | String   |                                                                                                                                                                                                                                                     | |
