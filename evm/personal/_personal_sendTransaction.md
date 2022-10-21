### personal_sendTransaction

Validate the given passphrase and submit transaction.

The transaction is the same argument as for eth_sendTransaction and contains the from address. If the passphrase can be used to decrypt the private key belogging to tx.from the transaction is verified, signed and send onto the network.

`:::warning The account is not unlocked globally in the node and cannot be used in other RPC calls. :::`

#### POST Request

`POST https://exchaintestrpc.okex.org`

> Request Example

```json
curl -X POST --data '{"jsonrpc":"2.0","method":"personal_sendTransaction","params":[{"from":"0x3b7252d007059ffc82d16d022da3cbf9992d2f70","to":"0xddd64b4712f7c8f1ace3c145c950339eddaf221d", "value":"0x16345785d8a0000"}, "passphrase"],"id":1}' -H "Content-Type: application/json" https://exchaintestrpc.okex.org

```

#### Request Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| from     | String   | DATA, 20 Bytes - The address the transaction is send from.|
| to    | String   |  DATA, 20 Bytes - (optional when creating new contract) The address the transaction is directed to|
| value     | String   |  QUANTITY - value sent with this transaction|
| Passphrase     | String   | |


> Example Response

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"result": "0xd2a31ec1b89615c8d1f4d08fe4e4182efa4a9c0d5758ace6676f485ea60e154c"
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  jsonrpc              | String    | 				| 
|  id                   | String    | 				| 
|  result               | String    | 				|