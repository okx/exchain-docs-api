## Get latest blocks

Get the latest information on blocks


#### Rate Limit: 6 requests per second

#### HTTP Request

`GET okexchain/v1/blocks/latest`

> Request Example

```wiki
https://www.okex.com/okexchain/v1/blocks/latest

```

#### Request Parameters

None
> Example Response

```json
{
  "block_id": {
    "hash": "318A4D6BCBBF646BFB85803D4A4DFBB30BFBC42DC424D4B26ADE34C43E6FA135",
    "parts": {
      "total": "1",
      "hash": "E9FCD3B437149AFE48986DB4D990F9413C0D29F29E066CD753D949FAF86C746E"
    }
  },
  "block": {
    "header": {
      "version": {
        "block": "10",
        "app": "0"
      },
      "chain_id": "exchain-66",
      "height": "2603621",
      "time": "2021-05-07T08:01:26.35548598Z",
      "last_block_id": {
        "hash": "7FE82A494E32E54CB1BAB23B9742101B26347B5AA08C08F4F146C8B1E3FE7635",
        "parts": {
          "total": "1",
          "hash": "4DD2803A3C906A1D8CCD9F05B09C46EE91A0F4C19E49EB60F36E4D49D1DDB639"
        }
      },
      "last_commit_hash": "0464FACC42944898C4B58AF4B9AACB5640889AD1CC2BB9F4667A12400513C679",
      "data_hash": "16AA2C550F7B7734F1BD0453DC5641C31AFD6DC12D59A4657D745792D1A2C0F5",
      "validators_hash": "FFAA79D077B93BBE1568A2773B7770D261D749A3D1F1DF7FB5DCF08EFE29521D",
      "next_validators_hash": "FFAA79D077B93BBE1568A2773B7770D261D749A3D1F1DF7FB5DCF08EFE29521D",
      "consensus_hash": "048091BC7DDC283F77BFBF91D73C44DA58C3DF8A9CBC867405D8B7F3DAADA22F",
      "app_hash": "EB98972779BE109B820676CCAFBE26D1AE191B4895D5D3B60385A133F708611B",
      "last_results_hash": "",
      "evidence_hash": "",
      "proposer_address": "C12BA4719F0F124D44CD1C820F7A7DE5AA2724EF"
    },
    "data": {
      "txs": [
        "mwolpr5UCpQKCJ4WEgoxMDAwMDAwMDAwGODsDSIUMbgg2ke0662B9lP98ylS0bwbxGkqATAyxAjIFSi4AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAEAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAC4AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAACAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAEAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABYAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAEAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAYJTzvAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAADAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAADP2X7cAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABnByaWNlcwAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAANCVEMAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAEAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAYJTzRAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAADAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAADP8z/ggAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABnByaWNlcwAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAANCVEMAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAACAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAEAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAwAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABguzqbTA0FJlOQczVDQz4kCirKtcW+789YroCK2MVd0KNxcJuTnNaWnfV4287csYS36Q3NZ0kdV0QzBDjf31wK1wAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAcAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAGCt0M/dRE+bEKGIiydvN/Q1NKWMOuCK98/4ZG6wc91hjttMyfgBLC8+OboF9XdBf2805VoD6UauSIxrpkAQO8QJAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABs6AjI3QkwyNzY1NDA5OTU1MzQ4NzcxMTkxMzU1MDQxNTE1NDQwNTYyNTg4OTc3MDM2NTU3ODM3NzczMTc3NTA3MDI5MTc5MDczNDE1MzI4NTI5Sk0zNTQwMzY5Mzg5OTU3NDY0MDQ0MzQxNDk0MTk1NjgzMDc1MTE2OTY2ODE0MDk3NTI0NDY0NzQ0MzM0NzQ5MzM4MjE1MjU3OTI4MjMyOA=="
      ]
    },
    "evidence": {
      "evidence": null
    },
    "last_commit": {
      "height": "2603620",
      "round": "0",
      "block_id": {
        "hash": "7FE82A494E32E54CB1BAB23B9742101B26347B5AA08C08F4F146C8B1E3FE7635",
        "parts": {
          "total": "1",
          "hash": "4DD2803A3C906A1D8CCD9F05B09C46EE91A0F4C19E49EB60F36E4D49D1DDB639"
        }
      },
      "signatures": [
        {
          "block_id_flag": 2,
          "validator_address": "0FE9CF2FFAC38F7BCC50818B9B431FF9934C9597",
          "timestamp": "2021-05-07T08:01:26.482302807Z",
          "signature": "Hs9xfPWcGvUMTtaEBFDdbPxrjqlQf0FPvC+syFkFKaXowfkI3rLxRBJTRRUrjtVpN83mK3Uge4IfDc/trrjjCQ=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "1C2BB905E9B6F7D6B8625077CD955C0F1A3BA026",
          "timestamp": "2021-05-07T08:01:26.32079867Z",
          "signature": "nC99f5Kkprn/zZAk+jlU2Vgqo/foHb+PP2eorRZQQuVKhNIQV+hF+3g5EKMaNgYGlGw1ufaYss9r4IGZq9ETDA=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "206BC60D6024CCFE4062CE1D358C5BA18CDCA284",
          "timestamp": "2021-05-07T08:01:26.350357993Z",
          "signature": "WWdf79WVBVwCZWY7owpSGfDqnPOX40v15kFQyUSK5I2OeOXvFEY3O1uwhrWAnHXTPWsf7eNdBMCgafNTAwnNCA=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "2DA545954A696F8F09AEF25AEDE2B0DDE1A67B60",
          "timestamp": "2021-05-07T08:01:26.350464826Z",
          "signature": "aaLobtLpl/NwKm+vxT5SCcDTguApIO294TX8vNSVWTnxJ61Qx+IbkhMNF8kPcyHuF2+deoMjLhBQZ2vAhLFuBA=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "32409E2BBF7F551EC182769BD142B2F262B261F0",
          "timestamp": "2021-05-07T08:01:26.357054729Z",
          "signature": "wk2+WYIMQ5kQTUfHC6KV0pdeK91P7ZWqvgGhoVBKlKRd6R8/MBSOfrnS+mhSVRyCGDBla2Vubcgk9gQD1MNiCg=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "33FAA80AA17F6412E8594ED447BAD09454A557AC",
          "timestamp": "2021-05-07T08:01:26.35548598Z",
          "signature": "Ma0UNpyyKs89ZakVNa7ZYNyIAVfdmirYCocyaU36K1i/HHNrNNc4ikdLvNzJSA9YGOcKU7NvguW9ZIRZphg8Cg=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "456D70DDD05B7AF40369FABFFDFACC2135AA5232",
          "timestamp": "2021-05-07T08:01:26.354770468Z",
          "signature": "cNWX9Z3/lYgy455QfH6Os+M8IWPXp4a+3X4o92Bhc9Il8mi0/a9cX9kL5fNQDh2Tg4GrDr9mM1nUmIezPl9CCQ=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "5304C540AD76FD12BF228C30DC889AD2F80A65FC",
          "timestamp": "2021-05-07T08:01:26.442362032Z",
          "signature": "6CRIdv7yp52/iWH+/WmLmY+h+Pg1JsrvEHCzHtuDX03O+50bQDns+fn1RpswdvrnKCghrRQzjmzfvyANATueBw=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "697C3DBA5A7E7326B560E496D6F7B9924A26ED1B",
          "timestamp": "2021-05-07T08:01:26.383749463Z",
          "signature": "DHV4ndTjz1zTwCgm6aZArZugg01AHgeyhx4LU6u//boMpBM92WAP6Urh1vewZqHypm9GQHKMUhOGLHycZA9YBw=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "6BE29CEF63D91013E5DE84064BAC7B2DE2B8B949",
          "timestamp": "2021-05-07T08:01:26.379679477Z",
          "signature": "Z24TLSMlC7ONPhWDzCNEeiwsbfzB7IClfe1lpmyeTt0+MFMvIZdKIfVYSPaBylfSXW8NSAyDRKoXofRJQqKtBw=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "7AE14A0113E95291CB37E5773A699A01D5071C1D",
          "timestamp": "2021-05-07T08:01:26.353737588Z",
          "signature": "EbwqvKVO49a8wLySrTIeckRLWSV4WLEPvM/nOfUKIdQOK/t9cGf7r2xBbchR67EKimLzg47GOtrMYPXXrTYzBA=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "B08F1E9CD9BDAD3EB8AEEC37E0662ABCC70BFB3E",
          "timestamp": "2021-05-07T08:01:26.376131036Z",
          "signature": "Ei+ju2r1sk+7HyOMlgY0gLBKWsheepdzamZtud5BrlsCPmDuT8TpDToN5U0W1LamLerGE+0QhqDtC0dSOdFLCw=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "B527086523C2B0B093BECFE42D45729B6775F56D",
          "timestamp": "2021-05-07T08:01:26.344440065Z",
          "signature": "P1l6GhSDpiYrnmrGgqDKbt95hPBm5sMq+p1A3tdEx31EOU+To9vk+f4BMZfJw/eXbPH2OuvqbPtWizFhfM/mDA=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "B8586789B5681169A6CDC670775AC83FF560AA2F",
          "timestamp": "2021-05-07T08:01:26.380683036Z",
          "signature": "U/X4zMSBchYNikSnsX1297kWMp5hnI1jBaw4fxNLCv8tLjNFQqhunlQ65eypl1qlFGaAAhTzghZgq9vbLOQ7Bw=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "C12BA4719F0F124D44CD1C820F7A7DE5AA2724EF",
          "timestamp": "2021-05-07T08:01:26.383968357Z",
          "signature": "0vDSh0IaRBRfGluifumJpAbbW90SKVaM8gFN8pu7/eb0NL7U3n1YPpPxrBiL5jpOhvy/VZyuIVjjcSEH/F6cDA=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "C1D32DDFC3C0C06F44BEE90593D5ED7539D5BA12",
          "timestamp": "2021-05-07T08:01:26.354564603Z",
          "signature": "CCexLtzVEtujUQVcjjOC8uN+AOAQvmgvA/cKLmcFIvDyRJUgwTy1cFRZVA38S/adcB6DE70xaV8YG/mwxeETDw=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "C624AEA0BAF4BB7D65B204B6D50D26D0D0AF5DA0",
          "timestamp": "2021-05-07T08:01:26.345453216Z",
          "signature": "1IsSxY4D1epNXoP1GTZ9dxkuq9MhQBdA/nLVSN+XjhffDHxquJwMuklRPJC9L59v99y3EUEbDtQzq3eGgJ9gAA=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "D67B9BA8B93D16A80B3F228D9DDCEFBEC0463D10",
          "timestamp": "2021-05-07T08:01:26.373584005Z",
          "signature": "1cWu3c5WhU7qmvmQLa928MPTRTphEYIyVtDJ46KpnBDUOLwyg1cuNMJzx7V5+YrCNbiZdVqjXp1hcsZPYPzqCQ=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "D7958E043A8FCFF9405F043E1F8EFFB9C1147F60",
          "timestamp": "2021-05-07T08:01:26.354144567Z",
          "signature": "dtW1xcZbfNdXyd2xhI2VNoOaJgjnGxTcovlZN9SMzHc+9HrneFo87b5cGjxxiOeil/EQDxykw2E60M2Lm056Dw=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "E3F8C6177337DC894631E702D8154BBEC9A931D5",
          "timestamp": "2021-05-07T08:01:26.354528064Z",
          "signature": "r5jcMKtINAQrMFMWBz2Z6c7DlKnjLfMQ4Ao4IzLsCoe+FSw72kUchlmXIibDohw5XrZItdlRk8TRug4e1+aHAg=="
        },
        {
          "block_id_flag": 2,
          "validator_address": "E42368D36DEB5E5D6682858E730E63014B1CA2C5",
          "timestamp": "2021-05-07T08:01:26.389600911Z",
          "signature": "cJfHaM+u8ubzhW+ixtyqekBUBjQM5ObEX9/QiymGNJ66Tbf/PQGV6vdt5NDlCs7XtP94THOT/gP643ttY6x8Dg=="
        }
      ]
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
| >> signatures         | Array     | 				|
| >>> signature         | String    | 				|
| >>> validator_address | String    | 				|
| >>> block_id_flag     | String    | 				|
| >>> timestamp         | String    | 				|
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
