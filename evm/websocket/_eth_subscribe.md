### eth_subscribe

subscribe using JSON-RPC notifications. This allows clients to wait for events instead of polling for them.

It works by subscribing to particular events. The node will return a subscription id. For each event that matches the subscription a notification with relevant data is send together with the subscription id.

#### POST Request

`POST https://exchaintestrpc.okex.org`

> Request Example

```json
curl --location --request POST 'https://exchaintestrpc.okex.org/' \
--header 'Content-Type: application/json' \
--data-raw '{"id": 1, "method": "eth_subscribe", "params": ["newHeads", {"includeTransactions": true}]}'

```

#### Request Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Subscription Name     | String   |  |
| Optional Arguments     | String   |  |

> Example Response

```json
{
	"jsonrpc": "2.0",
	"result": "0x34da6f29e3e953af4d0c7c58658fd525",
	"id": 1
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  jsonrpc              | String    | 				| 
|  id                   | String    | 				| 
|  result               | String    | 				|