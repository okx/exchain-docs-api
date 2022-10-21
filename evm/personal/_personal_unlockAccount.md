### personal_unlockAccount

Decrypts the key with the given address from the key store.

Both passphrase and unlock duration are optional when using the JavaScript console. The unencrypted key will be held in memory until the unlock duration expires. If the unlock duration defaults to 300 seconds. An explicit duration of zero seconds unlocks the key until geth exits.

The account can be used with eth_sign and eth_sendTransaction while it is unlocked.


#### POST Request

`POST https://exchaintestrpc.okex.org`

> Request Example

```json
curl -X POST --data '{"jsonrpc":"2.0","method":"personal_unlockAccount","params":["0x0f54f47bf9b8e317b214ccd6a7c3e38b893cd7f0", "secret passphrase", 30],"id":1}' -H "Content-Type: application/json" https://exchaintestrpc.okex.org

```

#### Request Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Account Address     | String   |  |
| Passphrase    | String   |  |
| Duration     | String   |  |


> Example Response

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"result": true
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  jsonrpc              | String    | 				| 
|  id                   | String    | 				| 
|  result               | Boolean    | 				|