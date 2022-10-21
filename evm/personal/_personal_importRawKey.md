### personal_importRawKey

Imports the given unencrypted private key (hex string) into the key store, encrypting it with the passphrase.

Returns the address of the new account.

`:::warning Currently, this is not implemented since the feature is not supported by the keys :::`

#### POST Request

`POST https://exchaintestrpc.okex.org`

> Request Example

```json
curl -X POST --data '{"jsonrpc":"2.0","method":"personal_importRawKey","params":["c5bd76cd0cd948de17a31261567d219576e992d9066fe1a6bca97496dec634e2c8e06f8949773b300b9f73fabbbc7710d5d6691e96bcf3c9145e15daf6fe07b9", "the key is this"],"id":1}' -H "Content-Type: application/json" https://exchaintestrpc.okex.org/
```

#### Request Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Hex encoded ECDSA key     | String   |  |
| Passphrase     | String   |  |

> Example Response

```json
{
	"jsonrpc": "2.0",
	"result": "",
	"id": 1
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  jsonrpc              | String    | 				| 
|  id                   | String    | 				| 
|  result               | String    | 				|