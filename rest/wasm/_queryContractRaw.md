## Query contract data through key

Query contract data by key

#### Rate Limit: 6 requests per second

#### HTTP Request

`GET okexchain/v1/wasm/contract/{contractAddr}/raw/{key}?encoding=hex`

> Request Example

```wiki
https://exchainrpc.okex.org/okexchain/v1/wasm/contract/ex1qg5ega6dykkxc307y25pecuufrjkxkaggkkxh7nad0vhyhtuhw3s4zjvwg/raw/0006636F6E666967636F6E7374616E7473?encoding=hex
```

#### Request Parameters

| **Parameter** | **Type** | **Required** | **Description**                   |
|:--------------|:---------|:-------------|:----------------------------------|
| contractAddr  | String   | Yes          | contract address required         |
| key           | String   | Yes          | queried key value required        |
| encoding      | string   | Yes          | Must use hex because `key` is hex | 

> Example Response

Response is Base64
```shell
"eyJuYW1lIjoibXkgdGVzdCB0b2tlbiIsInN5bWJvbCI6Ik1UVCIsImRlY2ltYWxzIjoxMH0="
# base64Code represent{"name":"my test token","symbol":"MTT","decimals":10}
```

#### Response Parameters

None
