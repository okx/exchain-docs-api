## Get balance

The API endpoints of Get Balance of all currencies for a single Address .
By default, just show currencies partially, you can use parameter of `show=all` to see all; you can use the parameter of `symbol=btc` to see just one.



#### Rate Limit: 6 requests per second

#### HTTP Request

`GET okexchain/v1/accounts/{address}`

> Request Example

```wiki
https://exchainrpc.okex.org/okexchain/v1/accounts/ex1508d7eq592kg2lh9d46xvv3r4sm7gm8we5fakv
https://exchainrpc.okex.org/okexchain/v1/accounts/ex1508d7eq592kg2lh9d46xvv3r4sm7gm8we5fakv?show=partial
https://exchainrpc.okex.org/okexchain/v1/accounts/ex1508d7eq592kg2lh9d46xvv3r4sm7gm8we5fakv?show=all
https://exchainrpc.okex.org/okexchain/v1/accounts/ex1508d7eq592kg2lh9d46xvv3r4sm7gm8we5fakv?symbol=btc

```

#### Request Parameters

| **Parameter** | **Type** | **Required** | **Description**                                                                                                                                                                                                     |
| :------------ | :------- | :----------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| address      | String   | Yes           | |
| show         | String   | No            | Type: <br> `all`: show all <br> `partial`: show part <br> |
| symbol       | String   | No            | for example `btc`|

> Example Response

```json
{
	"code": 0,
	"msg": "",
	"detail_msg": "",
	"data": {
		"address": "ex1508d7eq592kg2lh9d46xvv3r4sm7gm8we5fakv",
		"currencies": [{
			"symbol": "okt",
			"available": "51123.350000000000000000",
			"locked": "0"
		}]
	}
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| address      | String   |                                                                                                                                                                                                                                                      |
| currencies   | String   |                                                                                                                                                                                                                                                       |
| > symbol     | String   | Currency symbol                                                                                                                                                                                                                                                      |
| > available  | String   | The amount can use                                                                                                                                                                                                                                                     |
| > locked     | String   | The amount locked                                                                                                                                                                                                                                            |
