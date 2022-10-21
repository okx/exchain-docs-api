### eth_getFilterChanges

Polling method for a filter, which returns an array of logs which occurred since last poll.


#### POST Request

`POST https://exchaintestrpc.okex.org`

> Request Example

```json
curl --location --request POST 'https://exchaintestrpc.okex.org/' \
--header 'Content-Type: application/json' \
--data-raw '{
	"jsonrpc": "2.0",
	"method": "eth_getFilterChanges",
	"params": ["0x127e9eca4f7751fb4e5cb5291ad8b455"],
	"id": 1
}'

```

#### Request Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| The filter id     | String   |                                                                                                                                                                                                                                                      |

> Example Response

```json
{
	"jsonrpc": "2.0",
	"id": 1,
	"result": ["0xc6f08d183a81e149896fc5317c872f9092068e88e956ca1864e9bd4c81c09b44", "0x3ca6dfb5be15549d721d1b3d10c1bec50ed6217c9ac7b61df361fac9692a27e5", "0x776fffac134171acb1ebf2e59856625501ad5ccc5c4c8fe0359e0d4dff8919f2", "0x84123103704dbd738c089276ab2b04b5936330b24f6e78453c4ba8bf4848aaf9", "0xffddbe5bd8e8aa41e44002daa9ea89ade9e6980a0d83f51d104cf16498827eca", "0x53430e49963e8ae32605d8f22dec2e757a691e6436d593854ca4d9383eeab86a", "0x975948058c9351a91fbec332ca00dda39d1a919f5f16b996a4c7e30c38ba423b", "0x619e37e32024c8efef7f7220e6caff4ee1d682ea78b2ac91e0a6b30850dc0677", "0x31a5d985a40d08303ac68000ce008df512bcd1a911c497415c97f0624b4a271a", "0x91dcf1fce4503a8dbb3e6fb61073f25cd31d69c766ecba639fefde4436e59d07", "0x606d9e0143cfdb410a6812c590a8135b5c6b5c59eec26d760d5cd930aa47257d", "0xd3c00b859b29b20ba654415eef648ef58251389c73a138580db87675b0d5465f", "0x954391f0eb50888be90489898016ebb54f750f612f3adec2a00854955d5e52d8", "0x698905f06aff921a9e9fcef39b8b0d107747c3e6204d2ea79cf4c12debf8d253", "0x9fcafec5721938a06eb8e2951ede4b6ef8fae54a8c8f85f3166ec9782a0032b5", "0xaec6d3364e47a5716ba69e4705f3c705d017f81298859589591183bfea87be7a", "0x91bf2ee13319b6eaca96ed89c126437b66c4df1b13560c6a9bb18556ee3b7e1f", "0x4f426dc1fc0ea8149052033065b237892d2d34927b2d558ab50c5a7fb98d6e79", "0xdd809fb07e5aab638fef5311371b4e2b27c9c9a6183fde0cdd2b7724f6d2a89b", "0x7e12fc92ab953e233a304959a2a8474d96195e71efd9388fdceb1326a577811a", "0x30618ef6b490c3cc9979c47163459db37c1a1e0aa5793c56accd417f9d89973b", "0x614609f06ee24bae7408e45895b1a25e6b19a8159aeea7a95c9d1339d9ba286f", "0x115ddc6d533620040791d241f01f1c5ae3d9d1a8f64b15af5e9793e4d9096e22", "0xb7458c9323beeca2cd54f32a6af5671f3cd5a7a251aed9d82bdd6ebe5f56305b", "0x573dd48a5ba7bf4cc3d49597cd7419f75ecc9897258f1ebadebd670446d0d358", "0xcb6670918439f9698413b53f3b5336d82ca4be152fdefaacf45e052fff6262fc", "0xf3fe2a8945abafd269ab97bfdc80b3dbff2202ffdce59a227f952874b966b230", "0x989980707007533cc0840a079f77f261a2e818abae1a1ffd3af02f3fff1d35fd", "0x886b6ae365fec996be8a9a2c31cf4cda97ff8352908be2c83f17abd66ef1591e", "0xfd90df68706ef95a62b317de93d6899a9bd6c80416e42d007f5c30fcdedfce24", "0x7af8491fbb0373886d9032bb74e0ef52ed9e100f260b79bd15f46126b38cbede", "0x91d1e2cd55533cf7dd5de86c9aa73295e811b1279be193d429bbd6ba83810e16", "0x6b65b3128c2104005a04923288fe2aa33a2477a4962bef70532f94cab582f2a7"]
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  jsonrpc              | String    | 				| 
|  id                   | String    | 				| 
|  result               | Array    | 				|