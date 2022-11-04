## Smart query of contract data

Smart query of contract data

#### Rate Limit: 6 requests per second

#### HTTP Request

`GET okexchain/v1/wasm/contract/{contractAddr}/smart/{query}?encoding=base64`

> Request Example

```wiki
https://exchainrpc.okex.org/okexchain/v1/wasm/contract/ex1qg5ega6dykkxc307y25pecuufrjkxkaggkkxh7nad0vhyhtuhw3s4zjvwg/smart/eyJiYWxhbmNlIjp7ImFkZHJlc3MiOiJleDFoMGo4eDB2OWhzNGVxNnBwZ2FtZW1meXU0dnV2cDJzbDBxOXAzdiJ9fQ==?encoding=base64
```

#### Request Parameters

| **Parameter** | **Type** | **Required** | **Description**                                                                                                                                                                                                     |
| :------------ | :------- | :----------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| contractAddr      | String   | Yes           |  contract address required|
| query      | String   | Yes           | request data required base64 code |
| encoding | string | Yes | Must use base64| 

> Example Response

```shell
{"smart":"eyJiYWxhbmNlIjoiOTk5OTk5MDAifQ=="} 
//eyJiYWxhbmNlIjoiOTk5OTk5MDAifQ== represent {"balance":"99999900"}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  smart             | string    | Base64 Code				|
