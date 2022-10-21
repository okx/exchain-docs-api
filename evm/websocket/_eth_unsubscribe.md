### eth_subscribe

Unsubscribe from an event using the subscription id

#### POST Request

`POST https://exchaintestrpc.okex.org`

> Request Example

```json
curl --location --request POST 'https://exchaintestrpc.okex.org/' \
--header 'Content-Type: application/json' \
--data-raw '{"id": 1, "method": "eth_unsubscribe", "params": ["0x34da6f29e3e953af4d0c7c58658fd525"]}'

```

#### Request Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Subscription ID     | String   |  |
> Example Response

```json
{
	"jsonrpc": "2.0",
	"result": true,
	"id": 1
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  jsonrpc              | String    | 				| 
|  id                   | String    | 				| 
|  result               | Boolean    | 				|