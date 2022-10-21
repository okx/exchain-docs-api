### eth_syncing

The sync status object may need to be different depending on the details of Tendermint’s sync protocol. However, the ‘synced’ result is simply a boolean, and can easily be derived from Tendermint’s internal sync state.


#### POST Request

`POST https://exchaintestrpc.okex.org`

> Request Example

```json
curl --location --request POST 'https://exchaintestrpc.okex.org/' \
--header 'Content-Type: application/json' \
--data-raw '{
	"jsonrpc": "2.0",
	"method": "eth_syncing",
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
	"result": false
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| jsonrpc      | String   |                                                                                                                                                                                                                                                      |
| id           | String   |                                                                                                                                                                                                                                                       |
| result       | Boolean   |                                                                                                                                                                                                                                                     | |
