## Get accountNumber and sequence

The API endpoints of get user's account_number and sequence


#### Rate Limit: 6 requests per second

#### HTTP Request

`GET okexchain/v1/auth/accounts/{address}`

> Request Example

```wiki
https://www.okex.com/okexchain/v1/auth/accounts/ex1xkl5agjzqnjnptyat2dng2asmx8g5kll7evelk
```

#### Request Parameters

| **Parameter** | **Type** | **Required** | **Description**                                                                                                                                                                                                     |
| :------------ | :------- | :----------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| address      | String   | Yes           | |

> Example Response

```json
{
	"type": "okexchain/EthAccount",
	"value": {
		"address": "ex1xkl5agjzqnjnptyat2dng2asmx8g5kll7evelk",
		"eth_address": "0x35bf4EA24204E530AC9d5a9b342bB0D98e8a5bfF",
		"coins": [{
			"denom": "okt",
			"amount": "52741.300000000000000000"
		}],
		"public_key": "expub17weu6qepqw9q0u6snmd40a7d6jqc5ey4z0se30ev09jw44pnz29lf36p0euv26pqjvf",
		"account_number": 49,
		"sequence": 15,
		"code_hash": "c5d2460186f7233c927e7db2dcc703c0e500b653ca82273b7bfad8045d85a470"
	}
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| address       | String   |   Address of OKExChain                                                                                                                                                                                                                                                  |
| eth_address   | String   |  Address of Etherscan                                                                                                                                                                                                                                                |
| public_key    | String   |                                                                                                                                                                                                                                                  |
| account_number| String   |                                                                                                                                                                                                                                                  |
| sequence      | String   |                                                                                                                                                                                                                                                  |
| code_hash     | String   |                                                                                                                                                                                                                                                  |
| coins         | Array    |                                                                                                                                                                                                                                                  |
| > denom       | String   |                                                                                                                                                                                                                                                       |
| > amount      | String   |                                                                                                                                                                                                                                                      |
