### personal_listAccounts

Returns a list of addresses for accounts this node manages.


#### POST Request

`POST https://exchaintestrpc.okex.org`

> Request Example

```json
curl -X POST --data '{"jsonrpc":"2.0","method":"personal_listAccounts","params":[],"id":1}' -H "Content-Type: application/json" https://exchaintestrpc.okex.org

```

#### Request Parameters

None

> Example Response

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"result": ["0x3b7252d007059ffc82d16d022da3cbf9992d2f70", "0xddd64b4712f7c8f1ace3c145c950339eddaf221d", "0x0f54f47bf9b8e317b214ccd6a7c3e38b893cd7f0"]
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  jsonrpc              | String    | 				| 
|  id                   | String    | 				| 
|  result               | Array    | 				|