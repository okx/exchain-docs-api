## Get proposer by proposalId

Get proposer by ID

#### Rate Limit: 6 requests per second

#### HTTP Request

`GET okexchain/v1/gov/proposals/{ProposalID}/proposer`

> Request Example

```wiki
https://exchainrpc.okex.org/okexchain/v1/gov/proposals/17/proposer
```

#### Request Parameters

None
> Example Response

```json
{
  "proposal_id": "17",
  "proposer": "ex18au05qx485u2qcw2gvqsrfh29evq77lmnmqk2e"
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| proposal_id             | String    | 				| 
| proposer                | String    | 				|
