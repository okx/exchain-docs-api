### eth_getStorageAt

Returns the storage address for a given account address.


#### POST Request

`POST https://exchaintestrpc.okex.org`

> Request Example

```json
curl --location --request POST 'https://exchaintestrpc.okex.org/' \
--header 'Content-Type: application/json' \
--data-raw '{
	"jsonrpc": "2.0",
	"method": "eth_getStorageAt",
	"params": ["0x0f54f47bf9b8e317b214ccd6a7c3e38b893cd7f0", "0", "latest"],
	"id": 1
}'

```

#### Request Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Account Address      | String   |                                                                                                                                                                                                                                                      |
| Integer of the position in the storage           | String   |                                                                                                                                                                                                                                                       |
| Block Number       | String   |                                                                                                                                                                                                                                                     | |


> Example Response

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"result": "0x0000000000000000000000000000000000000000000000000000000000000000"
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| jsonrpc      | String   |                                                                                                                                                                                                                                                      |
| id           | String   |                                                                                                                                                                                                                                                       |
| result       | String   |                                                                                                                                                                                                                                                     | |
