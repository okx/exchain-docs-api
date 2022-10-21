## Get govParameters

Get gov parameters by type, `deposit / voting / tallying`


#### Rate Limit: 6 requests per second

#### HTTP Request

`GET okexchain/v1/gov/parameters/{ParamsType}`

> Request Example

```wiki
https://www.okex.com/okexchain/v1/gov/parameters/deposit
```

#### Request Parameters

None
> Example Response

```json
{
  "min_deposit": [
    {
      "denom": "okt",
      "amount": "10.000000000000000000"
    }
  ],
  "max_deposit_period": "86400000000000"
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  min_deposit          | Array     | 				| 
| > amount              | String    | 				| 
| > denom               | String    | 				| 
|  max_deposit_period   | String    | 				| 

> Request Example

```wiki
https://www.okex.com/okexchain/v1/gov/parameters/voting
```

#### Request Parameters

None
> Example Response

```json
{
  "voting_period": "259200000000000"
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  voting_period          | String     | 				| 


#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  min_deposit          | Array     | 				| 
| > amount              | String    | 				| 
| > denom               | String    | 				| 
|  max_deposit_period   | String    | 				| 

> Request Example

```wiki
https://www.okex.com/okexchain/v1/gov/parameters/tallying
```

#### Request Parameters

None
> Example Response

```json
{
  "quorum": "0.334000000000000000",
  "threshold": "0.500000000000000000",
  "veto": "0.334000000000000000",
  "yes_in_vote_period": "0.667000000000000000"
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  quorum          | String     | 				| 
|  threshold          | String     | 				| 
|  veto          | String     | 				| 
|  yes_in_vote_period          | String     | 				| 
