## Get validators

Query information on all validators

#### Rate Limit: 6 requests per second

#### HTTP Request

`GET okexchain/v1/staking/validators?status=all`

> Request Example

```wiki
https://www.okex.win/okexchain/v1/staking/validators?status=all
```

#### Request Parameters

None
> Example Response

```json
[{
	"operator_address": "exvaloper1q9nct2gska2yutx24starv6s63xz022fdwdgzv",
	"consensus_pubkey": "exvalconspub1zcjduepqks93pmhg3aqak0unyx28vgwhnh9vhtapddm75uax4ls2z2frfunsd9mnrx",
	"jailed": false,
	"status": 2,
	"tokens": "0",
	"delegator_shares": "8927161232181.244799749706439149",
	"description": {
		"moniker": "Collector",
		"identity": "",
		"website": "",
		"details": ""
	}
}]
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  block_height         | String    | 				|
|  validators           | Array     | 				|
| > address             | String    | 				|
| > proposer_priority   | String    | 				|
| > pub_key             | String    | 				|
| > voting_power        | String    | 				|