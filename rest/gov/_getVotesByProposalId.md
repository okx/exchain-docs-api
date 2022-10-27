## Get votes by proposalId

Get votes by proposalId

#### Rate Limit: 6 requests per second

#### HTTP Request

`GET okexchain/v1/gov/proposals/{ProposalID}/votes`

> Request Example

```wiki
https://exchainrpc.okex.org/okexchain/v1/gov/proposals/17/votes
```

#### Request Parameters

None
> Example Response

```json
[
  {
    "proposal_id": "17",
    "voter": "ex18au05qx485u2qcw2gvqsrfh29evq77lmnmqk2e",
    "option": "Yes"
  },
  {
    "proposal_id": "17",
    "voter": "ex1s6nfs7mlj7ewsskkrmekqhpq2w234fczzm23lw",
    "option": "Yes"
  },
  {
    "proposal_id": "17",
    "voter": "ex1zxthrcdcecfe5ss4tal0tq30hzel2lksvx6cnp",
    "option": "Yes"
  },
  {
    "proposal_id": "17",
    "voter": "ex1q9nct2gska2yutx24starv6s63xz022fmf8vxk",
    "option": "Yes"
  },
  {
    "proposal_id": "17",
    "voter": "ex195ez67wmhprwrru34gvttyd8ttpl7edx8xvrc8",
    "option": "Yes"
  },
  {
    "proposal_id": "17",
    "voter": "ex19wln93k3faq7vkqzlc9gljr3ey5fljt984rz57",
    "option": "Yes"
  },
  {
    "proposal_id": "17",
    "voter": "ex1qva0ejf0t943x6rt824gwmvtjgec9cjr2v72ha",
    "option": "Yes"
  },
  {
    "proposal_id": "17",
    "voter": "ex1ka92ujcwh6hyyeu4tymzy3dedgxplt4dahf6zd",
    "option": "Yes"
  },
  {
    "proposal_id": "17",
    "voter": "ex1zza3jrylyecrtuh0p9ts2xauzsefuvwarc0d5u",
    "option": "Yes"
  },
  {
    "proposal_id": "17",
    "voter": "ex1ygcvtcqxl82xvzrq25dymam434k3nnc8qfx8jp",
    "option": "Yes"
  },
  {
    "proposal_id": "17",
    "voter": "ex1ja9xngm4zh0t442mse73ll30p7dczd49xqdhwu",
    "option": "Yes"
  },
  {
    "proposal_id": "17",
    "voter": "ex1c34s7lc7ec8gs9xrtxeh0j2wjaam25c37gsz9t",
    "option": "Yes"
  },
  {
    "proposal_id": "17",
    "voter": "ex1m569cfenudxemegcf4mmykhugnslhdv0ssxukq",
    "option": "Yes"
  }
]
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| proposal_id        | String    | 				| 
| voter              | String    | 				|
| option             | String    | 				|
