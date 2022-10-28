## Get delegator Info

Query information of a delegator

#### Rate Limit: 6 requests per second

#### HTTP Request

`GET okexchain/v1/staking/delegators/{delegatorAddr}`

> Request Example

```wiki
https://exchainrpc.okex.org/okexchain/v1/staking/delegators/ex17se79kf0c9t5sw0yg0jjdm6et79sy8aradphtg
```

#### Request Parameters

None
> Example Response

```json
{
  "delegator_address": "ex17se79kf0c9t5sw0yg0jjdm6et79sy8aradphtg",
  "validator_address": [
    "exvaloper19e6edpu97d6w2t5dlp7lph2fkdja0lvlj8ngk0",
    "exvaloper18v23ln9ycrtg0mrwsm004sh4tdknudtdapcfcq",
    "exvaloper1ucmx6vvtrwam9pg20fnwmy9z80uhchyxqn67wq",
    "exvaloper1tat4lam8wjqmeax9mv4s584vu2mp7c0cgvlajl",
    "exvaloper1rz7frqz9ky52qqjwlpawfe5hz6plcrmmpha0px",
    "exvaloper1w3ptfgekjgdvwkqmdepdeyvuxqmcplfszlz3jm",
    "exvaloper104y8sy0r6fke4a9qr8u05j6v5y68gkh4v3ud9t",
    "exvaloper1qva0ejf0t943x6rt824gwmvtjgec9cjrut5wn8"
  ],
  "shares": "72053.451006669074462727",
  "tokens": "0.024951000000000000",
  "is_proxy": false,
  "total_delegated_tokens": "0.000000000000000000",
  "proxy_address": ""
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  is_proxy             | String    | 				| 
|  tokens               | String    | 				| 
|  proxy_address        | String    | 				| 
|  validator_address    | Array    | 				| 
|  total_delegated_tokens| String    | 				| 
|  delegator_address    | String    | 				| 
|  shares               | String    | 				| 
