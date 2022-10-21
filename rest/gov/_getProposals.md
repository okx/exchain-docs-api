## Get proposals

Get the all proposals


#### Rate Limit: 6 requests per second

#### HTTP Request

`GET okexchain/v1/gov/proposals`

> Request Example

```wiki
https://www.okex.com/okexchain/v1/gov/proposals

```

#### Request Parameters

None
> Example Response

```json
[{
 	"content": {
 		"type": "okexchain/params/ParameterChangeProposal",
 		"value": {
 			"ParameterChangeProposal": {
 				"title": "open farm",
 				"description": "open farm",
 				"changes": [{
 					"subspace": "farm",
 					"key": "YieldNativeToken",
 					"value": "true"
 				}]
 			},
 			"height": "600"
 		}
 	},
 	"id": "1",
 	"proposal_status": "Passed",
 	"final_tally_result": {
 		"total_power": "484267077339.546817829366687657",
 		"total_voted_power": "352194238067.852231148630318296",
 		"yes": "352194238067.852231148630318296",
 		"abstain": "0.000000000000000000",
 		"no": "0.000000000000000000",
 		"no_with_veto": "0.000000000000000000"
 	},
 	"submit_time": "2021-01-15T12:10:20.683558322Z",
 	"deposit_end_time": "2021-01-15T12:10:20.683558322Z",
 	"total_deposit": [{
 		"denom": "okt",
 		"amount": "100.000000000000000000"
 	}],
 	"voting_start_time": "2021-01-15T12:10:20.683558322Z",
 	"voting_end_time": "2021-01-15T13:00:21.369507718Z"
 }]
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  content              | Object    | 				| 
| > type                | String    | 				| 
| > value               | Object    | 				| 
| >> ParameterChangeProposal| Object    | 				| 
| >>> changes           | Array     | 				| 
| >>>> subspace         | String    | 				| 
| >>>> value            | String    | 				| 
| >>>> key              | String    | 				| 
| >>> description       | String    | 				| 
| >>> title             | String    | 				| 
| >> height             | String    | 				| 
|  voting_start_time    | String    | 				| 
|  id                   | String    | 				| 
|  deposit_end_time     | String    | 				| 
|  submit_time          | String    | 				| 
|  total_deposit        | Array     | 				| 
| > amount              | String    | 				| 
| > denom               | String    | 				| 
|  final_tally_result   | Object    | 				| 
| > total_voted_power   | String    | 				| 
| > no                  | String    | 				| 
| > no_with_veto        | String    | 				| 
| > total_power         | String    | 				| 
| > yes                 | String    | 				| 
| > abstain             | String    | 				| 
|  proposal_status      | String    | 				| 
|  voting_end_time      | String    | 				| 
