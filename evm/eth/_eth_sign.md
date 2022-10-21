### eth_sign


The sign method calculates an Ethereum specific signature with: sign(keccak256(”\x19Ethereum Signed Message:\n” + len(message) + message))).

By adding a prefix to the message makes the calculated signature recognisable as an Ethereum specific signature. This prevents misuse where a malicious DApp can sign arbitrary data (e.g. transaction) and use the signature to impersonate the victim.

`warning the address to sign with must be unlocked.`

#### POST Request

`POST https://exchaintestrpc.okex.org`

> Request Example

```json
curl --location --request POST 'https://exchaintestrpc.okex.org/' \
--header 'Content-Type: application/json' \
--data-raw '{
	"jsonrpc": "2.0",
	"method": "eth_sign",
	"params": ["0x3b7252d007059ffc82d16d022da3cbf9992d2f70", "0xdeadbeaf"],
	"id": 1
}'

```

#### Request Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Account Address    | String   |                                                                                                                                                                                                                                                       |
| Message to sign    | String   |                                                                                                                                                                                                                                                       |

> Example Response

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"result": "0x909809c76ed2a5d38733de39207d0f411222b9b49c64a192bf649cb13f63f37b45acb4f6939facb4f1c277bc70fb00407564140c0f18600ac44388f2c1dfd1dc1b"
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| jsonrpc      | String   |                                                                                                                                                                                                                                                      |
| id           | String   |                                                                                                                                                                                                                                                       |
| result       | String   |                                                                                                                                                                                                                                                     | |
 