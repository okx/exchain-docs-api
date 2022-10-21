### personal_newAccount

Generates a new private key and stores it in the key store directory. The key file is encrypted with the given passphrase. Returns the address of the new account.

#### POST Request

`POST https://exchaintestrpc.okex.org`

> Request Example

```json
curl -X POST --data '{"jsonrpc":"2.0","method":"personal_newAccount","params":["This is the passphrase"],"id":1}' -H "Content-Type: application/json" https://exchaintestrpc.okex.org

```

#### Request Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Passphrase     | String   |  |


> Example Response

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"result": "0xf0e4086ad1c6aab5d42161d5baaae2f9ad0571c0"
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  jsonrpc              | String    | 				| 
|  id                   | String    | 				| 
|  result               | String    | 				|