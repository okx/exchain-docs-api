## Get validatorsets

Get the latest validator set

#### Rate Limit: 6 requests per second

#### HTTP Request

`GET okexchain/v1/validatorsets/{height}`

> Request Example

```wiki
https://www.okex.win/okexchain/v1/validatorsets/2697221
```

#### Request Parameters

None
> Example Response

```json
{
  "block_height": "2697221",
  "validators": [
    {
      "address": "exvalcons1pl5u7tl6cw8hhnzssx9ekscllxf5e9vhu73l6w",
      "pub_key": "exvalconspub1zcjduepqu6473zvyzy3zwhmdhd38z7cdkw7wf50hdztngrndhxgr8xrqhrrq0m3nhf",
      "proposer_priority": "47638082485597",
      "voting_power": "8928485820324"
    },
    {
      "address": "exvalcons1rs4mjp0fkmmadwrz2pmum92upudrhgpx2cwjrk",
      "pub_key": "exvalconspub1zcjduepqllecydfvumn0swfx7mvyjtxepnsaqwm6qu4n0294st82qrc4zd8qtmeftd",
      "proposer_priority": "-11717811164568",
      "voting_power": "8924447091464"
    },
    {
      "address": "exvalcons1yp4uvrtqynx0usrzecwntrzm5xxdeg5ycgw6zq",
      "pub_key": "exvalconspub1zcjduepqgczr87k588khjz87z0fagqyqz4ua6alevq2hcfdldv5wmx4293xsuhhmk3",
      "proposer_priority": "-66887003646092",
      "voting_power": "8941020162109"
    },
    {
      "address": "exvalcons19kj5t922d9hc7zdw7fdwmc4smhs6v7mqxv09ny",
      "pub_key": "exvalconspub1zcjduepqk93rdqd8lkknq7rhr5pfnzj7px0knpqw85jycsqdj7xvc950q5vqdqu4rx",
      "proposer_priority": "-53429103469247",
      "voting_power": "8945483192825"
    },
    {
      "address": "exvalcons1xfqfu2al0a23asvzw6dazs4j7f3tyc0stgxe7w",
      "pub_key": "exvalconspub1zcjduepqgw849shr86xu0zqgfur0wqsws3xer5ckfy0k5ga969wxqfmllz0q39yrch",
      "proposer_priority": "-59773971759003",
      "voting_power": "8944137851687"
    },
    {
      "address": "exvalcons1x0a2sz4p0ajp96zefm2y0wksj32224avzy2g4z",
      "pub_key": "exvalconspub1zcjduepqp7ul8pfremls80jvqdnqe3cy56avzgj25jjqz0luz3cjzlp8a3ssur08mt",
      "proposer_priority": "-27281552372722",
      "voting_power": "1816470879930"
    },
    {
      "address": "exvalcons1g4khphwstda0gqmfl2llm7kvyy66553jn5x7jq",
      "pub_key": "exvalconspub1zcjduepqv6anlah0pedc6wpdmphlhnzh85yxalpwgwf9zk6enjxh5pg0swfs9e5nj3",
      "proposer_priority": "34328204085167",
      "voting_power": "8929778377427"
    },
    {
      "address": "exvalcons12vzv2s9dwm7390ez3scdezy66tuq5e0ussvzsn",
      "pub_key": "exvalconspub1zcjduepqk7wrtvrx0wwm8a3jyvfth2gl37g7ldal8sn0ydvjv2vxawyflw4s49xuv2",
      "proposer_priority": "-47582304935826",
      "voting_power": "1580739072371"
    },
    {
      "address": "exvalcons1d97rmwj60eejddtqujtddaaejf9zdmgmuglxef",
      "pub_key": "exvalconspub1zcjduepqqfwzk69r2nt7xcqjzmjvwuxaelevsdjftgqk8wafmdqr9ac9gd0ssukkrn",
      "proposer_priority": "24286871104272",
      "voting_power": "8942591311372"
    },
    {
      "address": "exvalcons1d03femmrmygp8ew7ssryhtrm9h3t3w2fc9mkdd",
      "pub_key": "exvalconspub1zcjduepqrtlw4twnhr5ckjzuzh3t0wkfvzqv67mnk4pkz645gaqclevzn7lqaf37v9",
      "proposer_priority": "4209895378605",
      "voting_power": "8940766457823"
    },
    {
      "address": "exvalcons10ts55qgna9ffrjehu4mn56v6q82sw8qaxzdlap",
      "pub_key": "exvalconspub1zcjduepq2qcpnzz98rtn5afqqlymdmd2ywkyt3pqwyduskdyayt248znu2rq7dmrmx",
      "proposer_priority": "-98906929598155",
      "voting_power": "1651296571160"
    },
    {
      "address": "exvalcons1kz83a8xehkknaw9wasm7qe32hnrsh7e78xmaz7",
      "pub_key": "exvalconspub1zcjduepqw2ey0qhr9tq6m5nvrsu00ww4gtwa56gm4w49rksfgpngsgqz9rwsvq4s86",
      "proposer_priority": "33136674257290",
      "voting_power": "8922248352089"
    },
    {
      "address": "exvalcons1k5nssefrc2ctpya7eljz63tjndnhtatd9ytk3p",
      "pub_key": "exvalconspub1zcjduepqy5067ef9j9rlk6keue8pejycu6vlr85q5a9x4kkpwa0wg56ngp4q6h0cr7",
      "proposer_priority": "67158700502611",
      "voting_power": "8938720467195"
    },
    {
      "address": "exvalcons1hpvx0zd4dqgknfkdcec8wkkg8l6kp230fx7sds",
      "pub_key": "exvalconspub1zcjduepqks93pmhg3aqak0unyx28vgwhnh9vhtapddm75uax4ls2z2frfunsd9mnrx",
      "proposer_priority": "48959031615518",
      "voting_power": "8927161232181"
    },
    {
      "address": "exvalcons1cy46guvlpufy63xdrjpq77nauk4zwf80e62pvy",
      "pub_key": "exvalconspub1zcjduepqg97q5h96s3tqnsyhs4ls94zyx7t6xkd6hrg9cmzzm0fvclstghvq3qlc6j",
      "proposer_priority": "6970694512149",
      "voting_power": "8936789255579"
    },
    {
      "address": "exvalcons1c8fjmh7rcrqx7397ayze840dw5uatwsj8ly48h",
      "pub_key": "exvalconspub1zcjduepqyzlcq82epx9sm3udg322xsurg2fuad9gdf4f87zclm6yap2qrppsu8lmdq",
      "proposer_priority": "31805356122365",
      "voting_power": "8931100101565"
    },
    {
      "address": "exvalcons1ccj2ag967jah6edjqjmd2rfx6rg27hdqg9xdsz",
      "pub_key": "exvalconspub1zcjduepqkx07ggrk37tu3jcks0rsx04ztpwxdk6ykffs39t3dpn38nqfqxtq7ahgzz",
      "proposer_priority": "6690328744154",
      "voting_power": "8936345849761"
    },
    {
      "address": "exvalcons16eaeh29e85t2szely2xemh80hmqyv0gsxnggy8",
      "pub_key": "exvalconspub1zcjduepqm608y3qu6vkrahlralhy0km4gz0299nqk2uutftg00svr73q7e5ssytssw",
      "proposer_priority": "-94450872539121",
      "voting_power": "8932533633426"
    },
    {
      "address": "exvalcons1672cupp63l8ljszlqslplrhlh8q3glmqvq5sd0",
      "pub_key": "exvalconspub1zcjduepq4p7mgjsyszl74agwv4swpl23klvtl0gn7vmfy3cz36yh87qusuesek95hn",
      "proposer_priority": "37677632023734",
      "voting_power": "8920932531050"
    },
    {
      "address": "exvalcons1u0uvv9mnxlwgj333uupds92thmy6jvw4c78d8v",
      "pub_key": "exvalconspub1zcjduepqpmdpu2gwxe5x3hpcl66ehek4fjdqa23aunsj8gs3ug94yvrx8adsa8tqhk",
      "proposer_priority": "68803590178606",
      "voting_power": "8933855135698"
    },
    {
      "address": "exvalcons1us3k35mdad096e5zsk88xrnrq993egk90f6k5r",
      "pub_key": "exvalconspub1zcjduepqnlmt2qhdn2hghculh34gxukx4gac7q7pl24knglc0lqpsrrph6ps6e7pwh",
      "proposer_priority": "48364488474677",
      "voting_power": "8925831512679"
    }
  ]
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  block_height         | String    | 				|
|  validators           | Array     | 				|
| > address             | String    | 				|
| > proposer_priority   | String    | 				|
| > pub_key             | String    | 				|
| > voting_power        | String    | 				|