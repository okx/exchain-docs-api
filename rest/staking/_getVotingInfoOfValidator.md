## Get votingInfo of validator

Query all voting information on a validator

#### Rate Limit: 6 requests per second

#### HTTP Request

`GET okexchain/v1/staking/validators/{address}/shares
`

> Request Example

```wiki
https://www.okex.com/okexchain/v1/staking/validators/exvaloper1q9nct2gska2yutx24starv6s63xz022fdwdgzv/shares
```

#### Request Parameters

None
> Example Response

```json
[
  {
    "voter_address": "ex12mek8h0mjs9m4hrh5q4zyhx04pqltyrnrtarud",
    "votes": "1424779953353.73000000"
  },
  {
    "voter_address": "ex12mek8h0mjs9m4hrh5q4zyhx04pqltyrnrtarud",
    "votes": "1424779953353.73000000"
  },
  {
    "voter_address": "ex12mek8h0mjs9m4hrh5q4zyhx04pqltyrnrtarud",
    "votes": "1424779953353.73000000"
  }
]

```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  voter_address     | String    | 				| 
|  votes             | String    | 				| 
