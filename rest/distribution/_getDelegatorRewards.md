## Get delegator rewards

Query rewards from all validators

#### Rate Limit: 6 requests per second

#### HTTP Request

`GET okexchain/v1/distribution/delegators/{delegatorAddr}/rewards`

> Request Example

```wiki
https://exchainrpc.okex.org/okexchain/v1/distribution/delegators/ex17se79kf0c9t5sw0yg0jjdm6et79sy8aradphtg/rewards
```

#### Request Parameters

None
> Example Response

```json
{
    "rewards": [
        {
            "validator_address": "exvaloper1q6ls3h64gkxq0r73u2eqwwr7d5mp583fm325zu",
            "reward": [
                {
                    "denom": "okt",
                    "amount": "2.081385971734814468"
                }
            ]
        },
        {
            "validator_address": "exvaloper1pt7xrmxul7sx54ml44lvv403r06clrdkehd8z7",
            "reward": [
                {
                    "denom": "okt",
                    "amount": "2.081385971734814468"
                }
            ]
        },
        {
            "validator_address": "exvaloper1gd6avvrg0jp5wxpfyfa4c84fygtl6cn9dage6d",
            "reward": [
                {
                    "denom": "okt",
                    "amount": "2.081385971734814468"
                }
            ]
        },
        {
            "validator_address": "exvaloper1ve4mwgq9967gk338yptsg2fheur4ke322gzynt",
            "reward": [
                {
                    "denom": "okt",
                    "amount": "2.081385971734814468"
                }
            ]
        }
    ],
    "total": [
        {
            "denom": "okt",
            "amount": "8.325543886939257872"
        }
    ]
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  rewards             | Array    | 	reward array			| 
|  validator_address      | String    | 		validator address		| 
|  reward        | String    | 	reward from validator address			| 	| 
|  total | Array    | 		Collection of all rewards		| 
