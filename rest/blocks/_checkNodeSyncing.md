## Check node syncing

GET if the node is currently syning with other nodes

#### Rate Limit: 6 requests per second

#### HTTP Request

`GET okexchain/v1/syncing`

> Request Example

```wiki
https://www.okex.com/okexchain/v1/syncing
```

#### Request Parameters

None
> Example Response

```json
{
  "syncing": false
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  syncing  | Object    | 				|
