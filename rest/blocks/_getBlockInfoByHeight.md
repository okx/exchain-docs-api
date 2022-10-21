## Get block info

Get information on by block height


#### Rate Limit: 6 requests per second

#### HTTP Request

`GET okexchain/v1/blocks/{height}`

> Request Example

```wiki
https://www.okex.com/okexchain/v1/blocks/2322601
```

#### Request Parameters

None
> Example Response

```json
{
  "block_id": {
    "hash": "AEF267A96586B10F8911B4B13934C31887DBEF03757A44B538C88DB87A5EEE83",
    "parts": {
      "total": "1",
      "hash": "9A119B06F376BB6080FE80516130FEA25498EB59A60A04E7CE4CA09AE5A1DA32"
    }
  },
  "block": {
    "header": {
      "version": {
        "block": "10",
        "app": "0"
      },
      "chain_id": "exchain-66",
      "height": "2322601",
      "time": "2021-01-15T12:00:00Z",
      "last_block_id": {
        "hash": "",
        "parts": {
          "total": "0",
          "hash": ""
        }
      },
      "last_commit_hash": "",
      "data_hash": "",
      "validators_hash": "106BA08C88D75667552A7726EDD3ABF65A3B183935D9BACB40128939EC2B3E30",
      "next_validators_hash": "106BA08C88D75667552A7726EDD3ABF65A3B183935D9BACB40128939EC2B3E30",
      "consensus_hash": "048091BC7DDC283F77BFBF91D73C44DA58C3DF8A9CBC867405D8B7F3DAADA22F",
      "app_hash": "",
      "last_results_hash": "",
      "evidence_hash": "",
      "proposer_address": "32409E2BBF7F551EC182769BD142B2F262B261F0"
    },
    "data": {
      "txs": null
    },
    "evidence": {
      "evidence": null
    },
    "last_commit": {
      "height": "0",
      "round": "0",
      "block_id": {
        "hash": "",
        "parts": {
          "total": "0",
          "hash": ""
        }
      },
      "signatures": null
    }
  }
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  block_id             | Object    | 				|
| > parts               | Object    | 				|
| >> total              | String    | 				|
| >> hash               | String    | 				|
| > hash                | String    | 				|
|  block                | Object    | 				|
| > data                | Object    | 				|
| >> txs                | String    | 				|
| > evidence            | Object    | 				|
| >> evidence           | String    | 				|
| > last_commit         | Object    | 				|
| >> round              | String    | 				|
| >> block_id           | Object    | 				|
| >>> parts             | Object    | 				|
| >>>> total            | String    | 				|
| >>>> hash             | String    | 				|
| >>> hash              | String    | 				|
| >> signatures         | String    | 				|
| >> height             | String    | 				|
| > header              | Object    | 				|
| >> validators_hash    | String    | 				|
| >> chain_id           | String    | 				|
| >> consensus_hash     | String    | 				|
| >> proposer_address   | String    | 				|
| >> next_validators_hash| String    | 				|
| >> version            | Object    | 				|
| >>> app               | String    | 				|
| >>> block             | String    | 				|
| >> data_hash          | String    | 				|
| >> last_results_hash  | String    | 				|
| >> last_block_id      | Object    | 				|
| >>> parts             | Object    | 				|
| >>>> total            | String    | 				|
| >>>> hash             | String    | 				|
| >>> hash              | String    | 				|
| >> evidence_hash      | String    | 				|
| >> app_hash           | String    | 				|
| >> time               | String    | 				|
| >> height             | String    | 				|
| >> last_commit_hash   | String    | 				|
