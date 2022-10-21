### eth_getCode


Returns the code for a given account address and Block Number.


#### POST Request

`POST https://exchaintestrpc.okex.org`

> Request Example

```json
curl --location --request POST 'https://exchaintestrpc.okex.org/' \
--header 'Content-Type: application/json' \
--data-raw '{
	"jsonrpc": "2.0",
	"method": "eth_getBlockTransactionCountByNumber",
	"params": ["0x8101cc04aea3341a6d4b3ced715e3f38de1e72867d6c0db5f5247d1a42fbb085", "0x0"],
	"id": 1
}'

```

#### Request Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Account Address    | String   |                                                                                                                                                                                                                                                       |
| Block Number    | String   |                                                                                                                                                                                                                                                       |

> Example Response

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"result": "0xef616c92f3cfc9e92dc270d6acff9cea213cecc7020a76ee4395af09bdceb4837a1ebdb5735e11e7d3adb6104e0c3ac55180b4ddf5e54d022cc5e8837f6a4f971b"
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| jsonrpc      | String   |                                                                                                                                                                                                                                                      |
| id           | String   |                                                                                                                                                                                                                                                       |
| result       | String   |                                                                                                                                                                                                                                                     | |
 