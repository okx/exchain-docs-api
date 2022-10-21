## Get tally by proposalId

Get proposer by ID

#### Rate Limit: 6 requests per second

#### HTTP Request

`GET okexchain/v1/gov/proposals/{ProposalID}/tally`

> Request Example

```wiki
https://www.okex.com/okexchain/v1/gov/proposals/17/tally
```

#### Request Parameters

None
> Example Response

```json
{
  "total_power": "165837653241301.605382606344753055",
  "total_voted_power": "116130784063951.268597087599105663",
  "yes": "116130784063951.268597087599105663",
  "abstain": "0.000000000000000000",
  "no": "0.000000000000000000",
  "no_with_veto": "0.000000000000000000"
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| total_power        | String    | 				| 
| total_voted_power  | String    | 				|
| yes                | String    | 				|
| abstain            | String    | 				|
| no                 | String    | 				|
| no_with_veto       | String    | 				|
