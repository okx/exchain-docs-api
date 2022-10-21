### personal_lockAccount

Removes the private key with given address from memory. The account can no longer be used to send transactions.


#### POST Request

`POST https://exchaintestrpc.okex.org`

> Request Example

```json
curl -X POST --data '{"jsonrpc":"2.0","method":"personal_lockAccount","params":["0x0f54f47bf9b8e317b214ccd6a7c3e38b893cd7f0"],"id":1}' -H "Content-Type: application/json" https://exchaintestrpc.okex.org

```

#### Request Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Account Address     | String   |  |


> Example Response

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"result": true]
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  jsonrpc              | String    | 				| 
|  id                   | String    | 				| 
|  result               | Boolean    | 				|