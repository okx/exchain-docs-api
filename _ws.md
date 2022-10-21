# WebSocket API

## Overview

WebSocket is a new HTML5 protocol that achieves full-duplex data transmission between the client and server, allowing data to be transferred effectively in both directions. A connection between the client and server can be established with just one handshake. The server will then be able to push data to the client according to preset rules. Its advantages include:

- The WebSocket request header size for data transmission between client and server is only 2 bytes.
- Either the client or server can initiate data transmission.
- There's no need to repeatedly create and delete TCP connections, saving resources on bandwidth and server.

<aside class="notice">
We recommend developers use WebSocket API to retrieve market data and order book depth.
</aside>

## Connect

<!-- **Public service address**: *wss://real.okexchain.com:8443/ws/public/v5* -->

<!-- **Private service address**: *wss://real.okexchain.com:8443/ws/private/v5* -->

**Connection instructions**:

**Connection limit**: 1 time per second

When subscribing to a public channel, use the address of the public service. When subscribing to a private channel, use the address of the private service

**Subscription limit**: 240 times per hour

<aside class="notice">
<p>If there’s a network problem, the system will automatically disable the connection.
<p>The connection will break automatically if the subscription is not established or data has not been pushed for more than 30 seconds.
<p>To keep the connection stable: 
<p>1. Set a timer of N seconds whenever a response message is received, where N is less than 30. 
<p>2. If the timer is triggered, which means that no new message is received within N seconds, send the String 'ping'.
<p>3. Expect a 'pong' as a response. If the response message is not received within N seconds, please raise an error or reconnect.
</aside>

## Login

> Request format description

```json
{
  "op": "login",
  "args": [
    {
      "apiKey": "<api_key>",
      "passphrase": "<passphrase>",
      "timestamp": "<timestamp>",
      "sign": "<sign>"
    }
  ]
}
```

> Request Example

```json
{
  "op": "login",
  "args": [
    {
      "apiKey": "985d5b66-57ce-40fb-b714-afc0b9787083",
      "passphrase": "123456",
      "timestamp": "1538054050",
      "sign": "7L+zFQ+CEgGu5rzCj4+BdV2/uUHGqddA9pI6ztsRRPs="
    }
  ]
}
```

> Successful Response Example

```json
{
  "event": "login",
  "code": "0",
  "msg": ""
}
```

> Failure Response Example

```json
{
  "event": "error",
  "code": "60008",
  "msg": "Login is not supported for public channels."
}
```

**api_key**: Unique identification for invoking API. Requires user to apply one manually.

**passphrase**: API Key password

**timestamp**: the Unix Epoch time, the unit is seconds

**sign**: signature string, the signature algorithm is as follows:

First concatenate `timestamp`, `method`, `requestPath`, and `body` strings, then use HMAC SHA256 method to encrypt the concatenated string with SecretKey, and then perform Base64 encoding.

**secretKey**: The security key generated when the user applies for APIKey, e.g. : 22582BD0CFF14C41EDBF1AB98506286D

**Example of timestamp**: const timestamp ='' + Date.now() / 1000

**Among sign example**: sign=CryptoJS.enc.Base64.Stringify(CryptoJS.HmacSHA256(timestamp +'GET'+'/users/self/verify', secretKey))

**method**: always 'GET'.

**requestPath** : always '/users/self/verify'

<aside class="notice">
The request will expire 30 seconds after the timestamp. If your server time differs from the API server time, we recommended using the REST API to query the API server time and then set the timestamp.
</aside>

## Subscribe

**Subscription Instructions**

> Request format description

```json
{
  "op": "subscribe",
  "args": ["<SubscriptionTopic>"]
}
```

WebSocket channels are divided into two categories: `public` and `private` channels.

`Public channels` -- include tickers channel, K-Line channel, limit price channel, order book channel, and mark price channel, etc -- do not require log in.

`Private channels` -- including account channel, order channel, and position channel, etc -- require log in.

Users can choose to subscribe to one or more channels, and the total length of multiple channels cannot exceed 4096 bytes.

> Request Example

```json
{
  "op": "subscribe",
  "args": [
    {
      "channel": "tickers",
      "instId": "LTC-USD-200327"
    },
    {
      "channel": "candle1m",
      "instId": "LTC-USD-200327"
    }
  ]
}
```

**Request parameters**

| Parameter  | Type   | Required | Description                                                                                     |
| :--------- | :----- | :------- | ----------------------------------------------------------------------------------------------- |
| op         | String | Yes      | Operation, `subscribe`                                                                          |
| `args`     | Array  | Yes      | List of subscribed channels                                                                     |
| > channel  | String | Yes      | Channel name                                                                                    |
| > instType | String | No       | Instrument type<br />`SPOT`<br />`MARGIN`<br />` SWAP`<br />`FUTURES`<br />`OPTION `<br />`ANY` |
| > uly      | String | No       | Underlying                                                                                      |
| > instId   | String | No       | Instrument ID                                                                                   |

> Example response

```json
{
  "event": "subscribe",
  "arg": {
    "channel": "tickers",
    "instId": "LTC-USD-200327"
  }
}
```

**Return parameters**

| Parameter  | Type   | Required | Description                                                                                     |
| :--------- | :----- | :------- | ----------------------------------------------------------------------------------------------- |
| event      | String | Yes      | Event, `subscribe` `error`                                                                      |
| `arg`      | Object | No       | Subscribed channel                                                                              |
| > channel  | String | Yes      | Channel name                                                                                    |
| > instType | String | No       | Instrument type<br />`SPOT`<br />`MARGIN`<br />` SWAP`<br />`FUTURES`<br />`OPTION` <br />`ANY` |
| > uly      | String | No       | Underlying                                                                                      |
| > instId   | String | No       | Instrument ID                                                                                   |
| code       | String | No       | Error code                                                                                      |
| msg        | String | No       | Error message                                                                                   |

## Unsubscribe

Unsubscribe from one or more channels.

> Request format description

```json
{
  "op": "unsubscribe",
  "args": ["< SubscriptionTopic> "]
}
```

> Request Example

```json
{
  "op": "unsubscribe",
  "args": [
    {
      "channel": "tickers",
      "instId": "LTC-USD-200327"
    },
    {
      "channel": "candle1m",
      "instId": "LTC-USD-200327"
    }
  ]
}
```

**Request parameters**

| Parameter  | Type   | Required | Description                                                                                     |
| :--------- | :----- | :------- | ----------------------------------------------------------------------------------------------- |
| op         | String | Yes      | Operation, `unsubscribe`                                                                        |
| `args`     | Array  | Yes      | List of channels to unsubscribe from                                                            |
| > channel  | String | Yes      | Channel name                                                                                    |
| > instType | String | No       | Instrument type<br />`SPOT`<br />`MARGIN`<br />` SWAP`<br />`FUTURES`<br />`OPTION `<br />`ANY` |
| > uly      | String | No       | Underlying                                                                                      |
| > instId   | String | No       | Instrument ID                                                                                   |

> Example response

```json
{
  "event": "unsubscribe",
  "arg": {
    "channel": "tickers",
    "instId": "LTC-USD-200327"
  }
}
```

**Return parameters**

| Parameter  | Type   | Required | Description                                                                          |
| :--------- | :----- | :------- | ------------------------------------------------------------------------------------ |
| event      | String | Yes      | Event, `unsubscribe` `error`                                                         |
| `arg`      | Object | No       | Unsubscribed channel                                                                 |
| > channel  | String | Yes      | Channel name                                                                         |
| > instType | String | No       | Instrument type<br />`SPOT`<br />`MARGIN`<br />` SWAP`<br />`FUTURES`<br />`OPTION ` |
| > uly      | String | No       | Underlying                                                                           |
| > instId   | String | No       | Instrument ID                                                                        |
| code       | String | No       | Error code                                                                           |
| msg        | String | No       | Error message                                                                        |

## Checksum

This mechanism can help users verify the accuracy of depth data.

`Calculation description`

The checksum is a signed integer (32-bit) crc32 value, which is formed by converting a string concatenate the price and quantity in ask and bid with a colon

`Verification Instructions`

Data pushed from the order book channel includes a timestamp and checksum. Users can compare the received checksum against the one computed from the string aggregated, and resubscribe to the channel if they do not match.


`Order Book Aggregation Rule`

After successfully subscribing to order book channel, user will first receive a full-snapshot data on all depth levels and then receive incremental data afterwards. Then traverse the first entry from the bids and asks list of the incremental data, and compare them with the first entry from the bids and asks list of full snapshot data.

1. If the price is the same, compare the quantity. If the quantity is different and is not 0, update the buy one or sell one in the total data. Otherwise, delete the buy one or sell one.

2. If the prices are not the same, sort them in order and insert buy one or sell one into the full data.

> Example 1

```json
{
 "arg": {
       "channel": "books",
       "instId":"BTC-USD-191227"
     },
 "action":"snapshot",
 "data": [
      {
        "asks": [[3366.8, 9, 10, 3],[ 3368,8,3,4 ]],
        "bids": [[3366.1, 7, 0, 3],[ 3366,6,3,4 ]],
        "ts": "1597026383085",
        "checksum": -855196043
      }
  ]
}
```

Example 1: When bid and ask are aligned, the string to be verified is:<br>`bid[price:size]`:`ask[price:size]`:`bid[price:size]`:`ask[price:size]`...

The checksum string corresponding to this example is: <br>`3366.1`:`7`:`3366.8`:`9`:`3366`:`6`:`3368`:`8`

> Example 2

```json
{
  "arg": {
    "channel": "books",
    "instId": "BTC-USD-191227"
  },
  "action": "update",
  "data": [
    {
      "asks": [
        [3366.8, 9, 10, 3],
        [3368, 8, 3, 4],
        [3372, 8, 3, 4]
      ],
      "bids": [[3366.1, 7, 0, 3]],
      "ts": "1597026383085",
      "checksum": -855196043
    }
  ]
}
```

Example 2: When bid and ask are not aligned, the string to be verified is:<br>
`bid[price:size]`:`ask[price:size]`:`ask[price:size]`:`ask[price:size]`:...

The checksum string corresponding to this example is: <br>`3366.1`:`7`:`3366.8`:`9`:`3368`:`8`:`3372`:`8`

## Public Channel

### Instruments Channel

The full instrument list will be pushed for the first time after subscription. Subsequently, the instruments will be pushed if there's any change to the instrument’s state (such as delivery of FUTURES, exercise of OPTION, listing of new contracts / trading pairs, trading suspension, etc.).

> Request Example

```json
{
  "op": "subscribe",
  "args": [
    {
      "channel": "instruments",
      "instType": "FUTURES"
    }
  ]
}
```

#### Request parameters

| Parameter  | Type   | Required | Description                                                            |
| ---------- | ------ | -------- | ---------------------------------------------------------------------- |
| op         | String | Yes      | Operation, `subscribe` `unsubscribe`                                   |
| args       | Array  | Yes      | List of subscribed channels                                            |
| > channel  | String | Yes      | Channel name, `instruments`                                            |
| > instType | String | Yes      | Instrument type<br />`SPOT`<br />`SWAP`<br />`FUTURES` <br />` OPTION` |

> Successful Response Example

```json
{
  "event": "subscribe",
  "arg": {
    "channel": "instruments",
    "instType": "FUTURES"
  }
}
```

> Failure Response Example

```json
{
  "event": "error",
  "code": "60012",
  "msg": "Unrecognized request: {\"op\": \"subscribe\", \"argss\":[{ \"channel\" : \"instruments\", \"instType\" : \"FUTURES\"}]}"
}
```

#### Response parameters

| Parameter  | Type   | Required | Description                                                             |
| :--------- | :----- | :------- | :---------------------------------------------------------------------- |
| event      | String | Yes      | Event, `subscribe` `unsubscribe` `error`                                |
| arg        | Object | No       | Subscribed channel                                                      |
| > channel  | String | Yes      | Channel name                                                            |
| > instType | String | Yes      | Instrument type<br />`SPOT`<br />`SWAP` <br />`FUTURES` <br />` OPTION` |
| code       | String | No       | Error code                                                              |
| msg        | String | No       | Error message                                                           |

> Push Data Example

```json
{
  "arg": {
    "channel": "instruments",
    "instType": "FUTURES"
  },
  "data": [
    {
      "instType": "FUTURES",
      "instId": "BTC-USD-191115",
      "uly": "BTC-USD",
      "category": "1",
      "baseCcy": "",
      "quoteCcy": "",
      "settleCcy": "BTC",
      "ctVal": "10",
      "ctMult": "1",
      "ctValCcy": "USD",
      "optType": "",
      "stk": "",
      "listTime": "",
      "expTime": "",
      "tickSz": "0.01",
      "lotSz": "1",
      "minSz": "1",
      "ctType": "linear",
      "alias": "this_week",
      "state": "live"
    },
    {
      "instType": "FUTURES",
      "instId": "BTC-USD-201115",
      "uly": "BTC-USD",
      "category": "1",
      "baseCcy": "",
      "quoteCcy": "",
      "settleCcy": "BTC",
      "ctVal": "10",
      "ctMult": "1",
      "ctValCcy": "USD",
      "optType": "",
      "stk": "",
      "listTime": "",
      "expTime": "",
      "tickSz": "0.01",
      "lotSz": "1",
      "minSz": "1",
      "ctType": "linear",
      "alias": "this_week",
      "state": "live"
    }
  ]
}
```

#### Push data parameters

| Parameter   | Type   | Description                                                                                                   |
| :---------- | :----- | :------------------------------------------------------------------------------------------------------------ |
| arg         | Object | Subscribed channel                                                                                            |
| > channel   | String | Channel name                                                                                                  |
| > instType  | String | Instrument type                                                                                               |
| data        | Array  | Subscribed data                                                                                               |
| > instType  | String | Instrument type                                                                                               |
| > instId    | String | Instrument ID, e.g. `BTC-USD-SWAP`                                                                            |
| > uly       | String | Underlying, e.g. `BTC-USD`<br />Only applicable to `FUTURES/SWAP/OPTION`                                      |
| > category  | String | Fee Schedule                                                                                                  |
| > baseCcy   | String | Base currency, e.g. `BTC` in `BTC-USDT`<br />Only applicable to `SPOT`                                        |
| > quoteCcy  | String | Quote currency, e.g. `USDT` in `BTC-USDT`<br />Only applicable to `SPOT`                                      |
| > settleCcy | String | Settlement and margin currency, e.g. `BTC`<br />Only applicable to `FUTURES/SWAP/OPTION`                      |
| > ctVal     | String | Contract value                                                                                                |
| > ctMult    | String | Contract multiplier                                                                                           |
| > ctValCcy  | String | Contract value currency                                                                                       |
| > optType   | String | Option type, `C`: Call `P`: Put<br />Only applicable to `OPTION`                                              |
| > stk       | String | Strike price<br />Only applicable to `OPTION`                                                                 |
| > listTime  | String | Listing time<br />Only applicable to `FUTURES/OPTION`                                                         |
| > expTime   | String | Expiry time<br />Only applicable to `FUTURES/OPTION`                                                          |
| > lever     | String | Leverage<br />Not applicable to `SPOT`, used to distinguish between `MARGIN` and `SPOT`.                      |
| > tickSz    | String | Tick size, e.g. `0.0001`                                                                                      |
| > lotSz     | String | Lot size,e.g. BTC-USDT-SWAP: `1`                                                                              |
| > minSz     | String | Minimum order size                                                                                            |
| > ctType    | String | Contract type, `linear`: linear contract `inverse`: inverse contract                                          |
| > alias     | String | Alias<br />`this_week`<br />`next_week`<br />`quarter`<br />`next_quarter`<br /> Only applicable to `FUTURES` |
| > state     | String | Instrument status <br /> `live`<br/>`suspend`<br/>`expired`<br/>`preopen`                                     |

<aside class="notice"> 
Instrument status will trigger pushing of incremental data from instruments channel. When there is system/instrument upgrade or failure, instrument status will be changed to suspend. When trading resumes, the instrument status will be changed to live. When a new contract is going to be listed, the instrument data of the new contract will be available with status preopen. When a product is going to be delisted (e.g. when a FUTURES contract is settled or OPTION contract is exercised), the instrument status will be changed to expired.
</aside>

### Tickers Channel

Retrieve the last traded price, bid price, ask price and 24-hour trading volume of instruments. Data will be pushed every 100 ms.

> Request Example

```json
{
  "op": "subscribe",
  "args": [
    {
      "channel": "tickers",
      "instId": "LTC-USD-200327"
    }
  ]
}
```

#### Request parameters

| Parameter | Type   | Required | Description                          |
| :-------- | :----- | :------- | ------------------------------------ |
| op        | String | Yes      | Operation, `subscribe` `unsubscribe` |
| `args`    | Array  | Yes      | List of subscribed channels          |
| > channel | String | Yes      | Channel name, `tickers`              |
| > instId  | String | Yes      | Instrument ID                        |

> Successful Response Example

```json
{
  "event": "subscribe",
  "arg": {
    "channel": "tickers",
    "instId": "LTC-USD-200327"
  }
}
```

> Failure Response Example

```json
{
  "event": "error",
  "code": "60012",
  "msg": "Unrecognized request: {\"op\": \"subscribe\", \"argss\":[{ \"channel\" : \"tickers\", \"instId\" : \"LTC-USD-200327\"}]}"
}
```

#### Response parameters

| Parameter | Type   | Required | Description                              |
| :-------- | :----- | :------- | ---------------------------------------- |
| event     | String | Yes      | Event, `subscribe` `unsubscribe` `error` |
| `arg`     | Object | No       | Subscribed channel                       |
| > channel | String | Yes      | Channel name                             |
| > instId  | String | Yes      | Instrument ID                            |
| code      | String | No       | Error code                               |
| msg       | String | No       | Error message                            |

> Push Data Example

```json
{
  "arg": {
    "channel": "tickers",
    "instId": "LTC-USD-200327"
  },
  "data": [
    {
      "instType": "SWAP",
      "instId": "LTC-USD-SWAP",
      "last": "9999.99",
      "lastSz": "0.1",
      "askPx": "9999.99",
      "askSz": "11",
      "bidPx": "8888.88",
      "bidSz": "5",
      "open24h": "9000",
      "high24h": "10000",
      "low24h": "8888.88",
      "volCcy24h": "2222",
      "vol24h": "2222",
      "sodUtc0": "2222",
      "sodUtc8": "2222",
      "ts": "1597026383085"
    }
  ]
}
```

#### Push data parameters

| **Parameter** | **Type** | **Description**                                                                          |
| ------------- | -------- | ---------------------------------------------------------------------------------------- |
| `arg`         | Object   | Successfully subscribed channel                                                          |
| > channel     | String   | Channel name                                                                             |
| > instId      | String   | Instrument ID                                                                            |
| `data`        | Array    | Subscribed data                                                                          |
| > instType    | String   | Instrument type                                                                          |
| > instId      | String   | Instrument ID                                                                            |
| > last        | String   | Last traded price                                                                        |
| > lastSz      | String   | Last traded size                                                                         |
| > askPx       | String   | Best ask price                                                                           |
| > askSz       | String   | Best ask size                                                                            |
| > bidPx       | String   | Best bid price                                                                           |
| > bidSz       | String   | Best bid size                                                                            |
| > open24h     | String   | Open price in the past 24 hours                                                          |
| > high24h     | String   | Highest price in the past 24 hours                                                       |
| > low24h      | String   | Lowest price in the past 24 hours                                                        |
| > volCcy24h   | String   | Trading volume in the past 24 hours                                                      |
| > vol24h      | String   | Trading volume in the past 24 hours                                                      |
| >sodUtc0      | String   | Open price in the UTC 0                                                                  |
| >sodUtc8      | String   | Open price in the UTC 8                                                                  |
| > ts          | String   | Ticker data generation time, Unix timestamp format in milliseconds, e.g. `1597026383085` |

### Open interest Channel

Retrieve the open interest. Data will by pushed every 3 seconds.

> Request Example

```json
{
  "op": "subscribe",
  "args": [
    {
      "channel": "open-interest",
      "instId": "LTC-USD-SWAP"
    }
  ]
}
```

#### Request parameters

| Parameter | Type   | Required | Description                          |
| :-------- | :----- | :------- | ------------------------------------ |
| op        | String | Yes      | Operation, `subscribe` `unsubscribe` |
| `args`    | Array  | Yes      | List of subscribed channels          |
| > channel | String | Yes      | Channel name, `open-interest`        |
| > instId  | String | Yes      | Instrument ID                        |

> Successful Response Example

```json
{
  "event": "subscribe",
  "arg": [
    {
      "channel": "open-interest",
      "instId": "LTC-USD-SWAP"
    }
  ]
}
```

> Failure Response Example

```json
{
  "event": "error",
  "code": "60012",
  "msg": "Unrecognized request: {\"op\": \"subscribe\", \"argss\":[{ \"channel\" : \"open-interest\", \"instId\" : \"LTC-USD-SWAP\"}]}"
}
```

#### Response parameters

| Parameter | Type   | Required | Description                               |
| :-------- | :----- | :------- | ----------------------------------------- |
| event     | String | Yes      | Event, `subscribe ` `unsubscribe` `error` |
| `arg`     | Object | No       | Subscribed channel                        |
| > channel | String | Yes      | Channel name                              |
| > instId  | String | Yes      | Instrument ID                             |
| code      | String | No       | Error code                                |
| msg       | String | No       | Error message                             |

> Push Data Example

```json
{
  "arg": {
    "channel": "open-interest",
    "instId": "LTC-USD-SWAP"
  },
  "data": [
    {
      "instType": "SWAP",
      "instId": "LTC-USD-SWAP",
      "oi": "5000",
      "oiCcy": "555.55",
      "ts": "1597026383085"
    }
  ]
}
```

#### Push data parameters

| **Parameter** | **Type** | **Description**                                                                                 |
| ------------- | -------- | ----------------------------------------------------------------------------------------------- |
| `arg`         | Object   | Successfully subscribed channel                                                                 |
| channel       | String   | Channel name                                                                                    |
| instId        | String   | Instrument ID                                                                                   |
| `data`        | Array    | Subscribed data                                                                                 |
| instType      | String   | Instrument type                                                                                 |
| instId        | String   | Instrument ID, e.g. `BTC-USD-18021`                                                             |
| oi            | String   | Open interest, in units of contracts.                                                           |
| oiCcy         | String   | Open interest, in currency units                                                                |
| ts            | String   | The time when the data was updated, Unix timestamp format in milliseconds, e.g. `1597026383085` |

### Candlesticks Channel

Retrieve the candlesticks data of an instrument. Data will be pushed every 500 ms.

> Request Example

```json
{
  "op": "subscribe",
  "args": [
    {
      "channel": "candle1D",
      "instId": "LTC-USD-200327"
    }
  ]
}
```

#### Request parameters

| Parameter | Type   | Required | Description                                                                                                                                                                                                                                                     |
| :-------- | :----- | :------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| op        | String | Yes      | Operation, `subscribe ` `unsubscribe`                                                                                                                                                                                                                           |
| `args`    | Array  | Yes      | List of subscribed channels                                                                                                                                                                                                                                     |
| channel   | String | Yes      | Channel name<br />`candle1Y` <br />`candle6M` `candle3M` `candle1M`<br />`candle1W`<br />`candle1D` `candle2D` `candle3D` `candle5D`<br />`candle12H` `candle6H` `candle4H` `candle2H` `candle1H`<br />`candle30m` `candle15m` `candle5m` `candle3m` `candle1m` |
| instId    | String | Yes      | Instrument ID                                                                                                                                                                                                                                                   |

> Successful Response Example

```json
{
  "event": "subscribe",
  "arg": {
    "channel": "candle1D",
    "instId": "BTC-USD-191227"
  }
}
```

> Failure Response Example

```json
{
  "event": "error",
  "code": "60012",
  "msg": "Unrecognized request: {\"op\": \"subscribe\", \"argss\":[{ \"channel\" : \"candle1D\", \"instId\" : \"BTC-USD-191227\"}]}"
}
```

#### Response parameters

| Parameter | Type   | Required | Description                              |
| :-------- | :----- | :------- | ---------------------------------------- |
| event     | String | Yes      | Event, `subscribe` `unsubscribe` `error` |
| `arg`     | Object | No       | Subscribed channel                       |
| channel   | String | yes      | channel name                             |
| instId    | String | Yes      | Instrument ID                            |
| code      | String | No       | Error code                               |
| msg       | String | No       | Error message                            |

> Push Data Example

```json
{
  "arg": {
    "channel": "candle1D",
    "instId": "BTC-USD-191227"
  },
  "data": [
    [
      "1597026383085",
      "8533.02",
      "8553.74",
      "8527.17",
      "8548.26",
      "45247",
      "529.5858061"
    ]
  ]
}
```

#### Push data parameters

| **Parameter** | **Type** | **Description**                                                                   |
| :------------ | :------- | --------------------------------------------------------------------------------- |
| `arg`         | Object   | Successfully subscribed channel                                                   |
| > channel     | String   | Channel name                                                                      |
| > instId      | String   | Instrument ID                                                                     |
| `data`        | Array    | Subscribed data                                                                   |
| > ts          | String   | Data generation time, Unix timestamp format in milliseconds, e.g. `1597026383085` |
| > o           | String   | Open price                                                                        |
| > h           | String   | Higest price                                                                      |
| > l           | String   | Lowest price                                                                      |
| > c           | String   | Close price                                                                       |
| > vol         | String   | Trading volume (cont)                                                             |
| > volCcy      | String   | Trading volume (coin)                                                             |

### Trades Channel

Retrieve the recent trades data. Data will be pushed whenever there is a trade.

> Request Example

```json
{
  "op": "subscribe",
  "args": [
    {
      "channel": "trades",
      "instId": "BTC-USD-191227"
    }
  ]
}
```

#### Request parameters

| Parameter | Type   | Required | Description                          |
| :-------- | :----- | :------- | ------------------------------------ |
| op        | String | Yes      | Operation, `subscribe` `unsubscribe` |
| `args`    | Array  | Yes      | List of subscribed channels          |
| > channel | String | Yes      | Channel name, `trades`               |
| > instId  | String | Yes      | Instrument ID                        |

> Successful Response Example

```json
{
  "op": "subscribe",
  "args": [
    {
      "channel": "trades",
      "instId": "BTC-USD-191227"
    }
  ]
}
```

> Failure Response Example

```json
{
  "event": "error",
  "code": "60012",
  "msg": "Unrecognized request: {\"op\": \"subscribe\", \"argss\":[{ \"channel\" : \"trades\", \"instId\" : \"BTC-USD-191227\"}]}"
}
```

#### Response parameters

| Parameter | Type   | Required | Description                              |
| :-------- | :----- | :------- | ---------------------------------------- |
| event     | String | Yes      | Event, `subscribe` `unsubscribe` `error` |
| `arg`     | Object | No       | Subscribed channel                       |
| > channel | String | Yes      | Channel name                             |
| > instId  | String | Yes      | Instrument ID                            |
| code      | String | No       | Error code                               |
| msg       | String | No       | Error message                            |

> Push Data Example

```json
{
  "arg": {
    "channel": "trades",
    "instId": "BTC-USD-191227"
  },
  "data": [
    {
      "instId": "BTC-USD-191227",
      "tradeId": "9",
      "px": "0.016",
      "sz": "50",
      "side": "buy",
      "ts": "1597026383085"
    }
  ]
}
```

#### Push data parameters

| **Parameter** | **Type** | **Description**                                                          |
| :------------ | :------- | ------------------------------------------------------------------------ |
| `arg`         | Object   | Successfully subscribed channel                                          |
| > channel     | String   | Channel name                                                             |
| > instId      | String   | Instrument ID                                                            |
| `data`        | Array    | Subscribed data                                                          |
| > instId      | String   | Instrument ID, e.g. `BTC-USD-180216`                                     |
| > tradeId     | String   | Trade ID                                                                 |
| > px          | String   | Trade price                                                              |
| > sz          | String   | Trade size                                                               |
| > side        | String   | Trade direction, `buy`, `sell`                                           |
| > ts          | String   | Filled time, Unix timestamp format in milliseconds, e.g. `1597026383085` |

### Estimated delivery/exercise Price Channel

Retrieve the estimated delivery/exercise price of FUTURES contracts and OPTION.

Only the estimated delivery/exercise price will be pushed an hour before delivery/exercise, and will be pushed if there is any price change.

> Request Example

```json
{
  "op": "subscribe",
  "args": [
    {
      "channel": "estimated-price",
      "instType": "FUTURES",
      "uly": "BTC-USD"
    }
  ]
}
```

#### Request parameters

| Parameter  | Type   | Required | Description                                                |
| :--------- | :----- | :------- | ---------------------------------------------------------- |
| op         | String | Yes      | Operation, `subscribe` `unsubscribe`                       |
| `args`     | Array  | Yes      | List of subscribed channels                                |
| > channel  | String | Yes      | Channel name, `estimated-price`                            |
| > instType | String | Yes      | Instrument type <br />`ANY`<br />` OPTION` <br />`FUTURES` |
| > uly      | String | No       | Underlying                                                 |
| > instId   | String | No       | Instrument ID                                              |

> Successful Response Example

```json
{
  "event": "subscribe",
  "arg": {
    "channel": "estimated-price",
    "instType": "FUTURES",
    "uly": "BTC-USD"
  }
}
```

> Failure Response Example

```json
{
  "event": "error",
  "code": "60012",
  "msg": "Unrecognized request: {\"op\": \"subscribe\", \"argss\":[{ \"channel\" : \"estimated-price\", \"instId\" : \"FUTURES\",\"uly\" :\"BTC-USD\"}]}"
}
```

#### Response parameters

| Parameter  | Type   | Required | Description                                   |
| :--------- | :----- | :------- | --------------------------------------------- |
| event      | String | Yes      | Event, `subscribe ` `unsubscribe` `error`     |
| `arg`      | Object | No       | Subscribed channel                            |
| > channel  | String | Yes      | Channel name                                  |
| > instType | String | Yes      | Instrument type <br />`FUTURES`<br />`OPTION` |
| > uly      | String | No       | Underlying                                    |
| > instId   | String | No       | Instrument ID                                 |
| code       | String | No       | Error code                                    |
| msg        | String | No       | Error message                                 |

> Push Data Example

```json
{
  "arg": {
    "args": "estimated-price",
    "instType": "FUTURES",
    "uly": "BTC-USD"
  },
  "data": [
    {
      "instType": "FUTURES",
      "instId": "BTC-USD-170310",
      "settlePx": "200",
      "ts": "1597026383085"
    }
  ]
}
```

#### Push data parameters

| **Parameter** | **Type** | **Description**                                                               |
| :------------ | :------- | ----------------------------------------------------------------------------- |
| `arg`         | Object   | Successfully subscribed channel                                               |
| > channel     | String   | Channel name                                                                  |
| > instType    | String   | Instrument type<br />`FUTURES`<br />`OPTION`                                  |
| > uly         | String   | Underlying                                                                    |
| > instId      | String   | Instrument ID                                                                 |
| `data`        | Array    | Subscribed data                                                               |
| > instType    | String   | Instrument type                                                               |
| > instId      | String   | Instrument ID, e.g. `BTC-USD-170310`                                          |
| > settlePx    | String   | Estimated delivery/exercise price                                             |
| > ts          | String   | Data update time, Unix timestamp format in milliseconds, e.g. `1597026383085` |

### Mark Price Channel

Retrieve the mark price. Data will be pushed every 200 ms when the mark price changes, and will be pushed every 10 seconds when the mark price does not change.

> Request Example

```json
{
  "op": "subscribe",
  "args": [
    {
      "channel": "mark-price",
      "instId": "LTC-USD-190628"
    }
  ]
}
```

#### Request parameters

| Parameter | Type   | Required | Description                          |
| :-------- | :----- | :------- | ------------------------------------ |
| op        | String | Yes      | Operation, `subscribe` `unsubscribe` |
| `args`    | Array  | Yes      | List of subscribed channels          |
| > channel | String | Yes      | Channel name, `mark-price`           |
| > instId  | String | Yes      | Instrument ID                        |

> Successful Response Example

```json
{
  "event": "subscribe",
  "arg": {
    "channel": "mark-price",
    "instId": "LTC-USD-190628"
  }
}
```

> Failure Response Example

```json
{
  "event": "error",
  "code": "60012",
  "msg": "Unrecognized request: {\"op\": \"subscribe\", \"argss\":[{ \"channel\" : \"mark-price\", \"instId\" : \"LTC-USD-190628\"}]}"
}
```

#### Response parameters

| Parameter | Type   | Required | Description                              |
| :-------- | :----- | :------- | ---------------------------------------- |
| event     | String | Yes      | Event, `subscribe` `unsubscribe` `error` |
| `arg`     | Object | No       | Subscribed channel                       |
| > channel | String | Yes      | Channel name                             |
| > instId  | String | No       | Instrument ID                            |
| code      | String | No       | Error code                               |
| msg       | String | No       | Error message                            |

> Push Data Example

```json
{
  "arg": {
    "channel": "mark-price",
    "instId": "LTC-USD-190628"
  },
  "data": [
    {
      "instType": "FUTURES",
      "instId": "LTC-USD-190628",
      "markPx": "0.1",
      "ts": "1597026383085"
    }
  ]
}
```

#### Push data parameters

| Parameter  | Type   | Description                                                                    |
| :--------- | :----- | ------------------------------------------------------------------------------ |
| `arg`      | Object | Successfully subscribed channel                                                |
| > channel  | String | Channel name                                                                   |
| > instId   | String | Instrument ID                                                                  |
| `data`     | Array  | Subscribed data                                                                |
| > instType | String | Instrument type                                                                |
| > instId   | String | Instrument ID                                                                  |
| > markPx   | String | Mark price                                                                     |
| > ts       | String | Price update time, Unix timestamp format in milliseconds, e.g. `1597026383085` |

### Mark Price Candlesticks Channel

Retrieve the candlesticks data of the mark price. Data will be pushed every 500 ms.

> Request Example

```json
{
  "op": "subscribe",
  "args": [
    {
      "channel": "mark-price-candle1D",
      "instId": "BTC-USD-190628"
    }
  ]
}
```

#### Request parameters

| Parameter | Type   | Required | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| :-------- | :----- | :------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| op        | String | Yes      | Operation, `subscribe ` `unsubscribe`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `args`    | Array  | Yes      | List of subscribed channels                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| > channel | String | Yes      | Channel name<br />`mark-price-candle1Y` <br />`mark-price-candle6M` <br />`mark-price-candle3M` <br />`mark-price-candle1M` <br />`mark-price-candle1W` <br />`mark-price-candle1D`<br />`mark-price-candle2D`<br />`mark-price-candle3D` <br />`mark-price-candle5D`<br />`mark-price-candle12H` <br />`mark-price-candle6H` <br />`mark-price-candle4H`<br />`mark-price-candle2H`<br />`mark-price-candle1H` <br />`mark-price-candle30m`<br />`mark-price-candle15m` <br />`mark-price-candle5m` <br />`mark-price-candle3m` <br />`mark-price-candle1m` |
| > instId  | String | Yes      | Instrument ID                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |

> Successful Response Example

```json
{
  "event": "subscribe",
  "arg": {
    "channel": "mark-price-candle1D",
    "instId": "BTC-USD-190628"
  }
}
```

> Failure Response Example

```json
{
  "event": "error",
  "code": "60012",
  "msg": "Unrecognized request: {\"op\": \"subscribe\", \"argss\":[{ \"channel\" : \"mark-price-candle1D\", \"instId\" : \"BTC-USD-190628\"}]}"
}
```

#### Response parameters

| Parameter | Type   | Required | Description                              |
| :-------- | :----- | :------- | ---------------------------------------- |
| event     | String | Yes      | Event, `subscribe` `unsubscribe` `error` |
| `arg`     | Object | No       | Subscribed channel                       |
| > channel | String | Yes      | Channel name                             |
| > instId  | String | Yes      | Instrument ID                            |
| code      | String | No       | Error code                               |
| msg       | String | No       | Error message                            |

> Push Data Example

```json
{
  "arg": {
    "channel": "mark-price-candle1D",
    "instId": "BTC-USD-190628"
  },
  "data": [
    ["1597026383085", "3.721", "3.743", "3.677", "3.708"],
    ["1597026383085", "3.731", "3.799", "3.494", "3.72"]
  ]
}
```

#### Push data parameters

| Parameter | Type   | Description                                                                       |
| :-------- | :----- | --------------------------------------------------------------------------------- |
| `arg`     | Object | Successfully subscribed channel                                                   |
| > channel | String | Channel name                                                                      |
| > instId  | String | Instrument ID                                                                     |
| `data`    | Array  | Subscribed data                                                                   |
| > ts      | String | Data generation time, Unix timestamp format in milliseconds, e.g. `1597026383085` |
| > o       | String | Open price                                                                        |
| > h       | String | Highest price                                                                     |
| > l       | String | Lowest price                                                                      |
| > c       | String | Close price                                                                       |

### Price Limit Channel

Retrieve the maximum buy price and minimum sell price of the instrument. Data will be pushed every 5 seconds when there are changes in limits, and will not be pushed when there is no changes on limit.

> Request Example

```json
{
  "op": "subscribe",
  "args": [
    {
      "channel": "price-limit",
      "instId": "LTC-USD-190628"
    }
  ]
}
```

#### Request parameters

| Parameter | Type   | Required | Description                          |
| :-------- | :----- | :------- | ------------------------------------ |
| op        | String | Yes      | Operation, `subscribe` `unsubscribe` |
| `args`    | Array  | Yes      | List of subscribed channels          |
| > channel | String | Yes      | Channel name, `price-limit`          |
| > instId  | String | Yes      | Instrument ID                        |

> Successful Response Example

```json
{
  "event": "subscribe",
  "arg": {
    "channel": "price-limit",
    "instId": "LTC-USD-190628"
  }
}
```

> Failure Response Example

```json
{
  "event": "error",
  "code": "60012",
  "msg": "Unrecognized request: {\"op\": \"subscribe\", \"argss\":[{ \"channel\" : \"price-limit\", \"instId\" : \"LTC-USD-190628\"}]}"
}
```

#### Response parameters

| Parameter | Type   | Required | Description                              |
| :-------- | :----- | :------- | ---------------------------------------- |
| event     | String | Yes      | Event, `subscribe` `unsubscribe` `error` |
| `arg`     | Object | No       | Subscribed channel                       |
| > channel | String | Yes      | Channel name                             |
| > instId  | String | Yes      | Instrument ID                            |
| code      | String | No       | Error code                               |
| msg       | String | No       | Error message                            |

> Push Data Example

```json
{
  "arg": {
    "channel": "price-limit",
    "instId": "LTC-USD-190628"
  },
  "data": [
    {
      "instId": "LTC-USD-190628",
      "buyLmt": "200",
      "sellLmt": "300",
      "ts": "1597026383085"
    }
  ]
}
```

#### Push data parameters

| **Parameter** | **Type** | **Description**                                                                |
| :------------ | :------- | ------------------------------------------------------------------------------ |
| `arg`         | Object   | Successfully subscribed channel                                                |
| > channel     | String   | Channel name                                                                   |
| > instId      | String   | Instrument ID                                                                  |
| `data`        | Array    | Subscribed data                                                                |
| > instType    | String   | Instrument type                                                                |
| > instId      | String   | Instrument ID, e.g. `BTC-USD-SWAP`                                             |
| > buyLmt      | String   | Maximum buy price                                                              |
| > sellLmt     | String   | Minimum sell price                                                             |
| > ts          | String   | Price update time, Unix timestamp format in milliseconds, e.g. `1597026383085` |

### Order Book Channel

Retrieve order book data.<br>

Use `books` for 400 depth levels, `book5` for 5 depth levels, and `books-l2-tbt` for tick-by-tick 400 depth levels.<br />

`books`: 400 depth levels will be pushed in the initial full snapshot. Incremental data will be pushed every 100 ms when there is change in order book.<br />
`books5`: 5 depth levels will be pushed every time. Data will be pushed every 100 ms when there is change in order book.<br/>
`books-l2-tbt`: 400 depth levels will be pushed in the initial full snapshot. Incremental data will be pushed tick by tick, i.e. whenever there is change in order book.

> Request Example

```json
{
  "op": "subscribe",
  "args": [
    {
      "channel": "books",
      "instId": "BTC-USD-191227"
    }
  ]
}
```

#### Request parameters

| Parameter | Type   | Required | Description                                   |
| :-------- | :----- | :------- | --------------------------------------------- |
| op        | String | Yes      | Operation, `subscribe` `unsubscribe`          |
| `args`    | Array  | Yes      | List of subscribed channels                   |
| > channel | String | Yes      | Channel name, `books` `books5` `books-l2-tbt` |
| > instId  | String | Yes      | Instrument ID                                 |

> Example Response

```json
{
  "event": "subscribe",
  "arg": {
    "channel": "books",
    "instId": "BTC-USD-191227"
  }
}
```

> Failure example

```json
{
  "event": "error",
  "code": "60012",
  "msg": "Unrecognized request: {\"op\": \"subscribe\", \"argss\":[{ \"channel\" : \"books\", \"instId\" : \"BTC-USD-191227\"}]}"
}
```

#### Response parameters

| Parameter | Type   | Required | Description                              |
| :-------- | :----- | :------- | ---------------------------------------- |
| event     | String | Yes      | Event, `subscribe` `unsubscribe` `error` |
| `arg`     | Object | No       | Subscribed channel                       |
| > channel | String | Yes      | Channel name                             |
| > instId  | String | Yes      | Instrument ID                            |
| msg       | String | No       | Error message                            |
| code      | String | No       | Error code                               |

> Push Data Example: Full Snapshot

```json
{
  "arg": {
    "channel": "books",
    "instId": "BTC-USD-191227"
  },
  "action": "snapshot",
  "data": [
    {
      "asks": [
        ["8476.98", "415", "0", "13"],
        ["8477", "7", "0", "2"],
        ["8477.34", "85", "0", "1"],
        ["8477.56", "1", "0", "1"],
        ["8505.84", "8", "0", "1"],
        ["8506.37", "85", "0", "1"],
        ["8506.49", "2", "0", "1"],
        ["8506.96", "100", "0", "2"]
      ],
      "bids": [
        ["8476.97", "256", "0", "12"],
        ["8475.55", "101", "0", "1"],
        ["8475.54", "100", "0", "1"],
        ["8475.3", "1", "0", "1"],
        ["8447.32", "6", "0", "1"],
        ["8447.02", "246", "0", "1"],
        ["8446.83", "24", "0", "1"],
        ["8446", "95", "0", "3"]
      ],
      "ts": "1597026383085",
      "checksum": -855196043
    }
  ]
}
```

> Push Data Example: Incremental Data

```json
{
  "arg": {
    "channel": "books",
    "instId": "BTC-USD-191227"
  },
  "action": "update",
  "data": [
    {
      "asks": [
        ["8476.98", "415", "0", "13"],
        ["8477", "7", "0", "2"],
        ["8477.34", "85", "0", "1"],
        ["8477.56", "1", "0", "1"],
        ["8505.84", "8", "0", "1"],
        ["8506.37", "85", "0", "1"],
        ["8506.49", "2", "0", "1"],
        ["8506.96", "100", "0", "2"]
      ],
      "bids": [
        ["8476.97", "256", "0", "12"],
        ["8475.55", "101", "0", "1"],
        ["8475.54", "100", "0", "1"],
        ["8475.3", "1", "0", "1"],
        ["8447.32", "6", "0", "1"],
        ["8447.02", "246", "0", "1"],
        ["8446.83", "24", "0", "1"],
        ["8446", "95", "0", "3"]
      ],
      "ts": "1597026383085",
      "checksum": -855196043
    }
  ]
}
```

#### Push data parameters

| **Parameter** | **Type** | **Description**                                                                                         |
| :------------ | :------- | ------------------------------------------------------------------------------------------------------- |
| `arg`         | Object   | Successfully subscribed channel                                                                         |
| > channel     | String   | Channel name                                                                                            |
| > instId      | String   | Instrument ID                                                                                           |
| `data`        | Array    | Subscribed data                                                                                         |
| > asks        | Array    | Order book on sell side                                                                                 |
| > bids        | Array    | Order book on buy side                                                                                  |
| > action      | String   | Push data action, incremental data or full snapshot.<br />`snapshot`: full <br />` update`: incremental |
| > ts          | String   | Order book generation time, Unix timestamp format in milliseconds, e.g. `1597026383085`                 |
| > checksum    | Integer  | Checksum                                                                                                |

<aside class="notice">
An example of the array of asks and bids values: ["411.8", "10", "1", "4"]<br />
"411.8" is the depth price, "10" is the size at the price, "1" is the number of liquidated orders at the price, and "4" is the number of orders at the price.
</aside>

### OPTION Summary Channel

Retrieve detailed pricing information of all OPTION contracts. Data will be pushed at once.

> Request Example

```json
{
  "op": "subscribe",
  "args": [
    {
      "channel": "opt-summary",
      "uly": "BTC-USD"
    }
  ]
}
```

#### Request parameters

| Parameter | Type   | Required | Description                          |
| :-------- | :----- | :------- | ------------------------------------ |
| op        | String | Yes      | Operation, `subscribe` `unsubscribe` |
| `args`    | Array  | Yes      | List of subscribed channels          |
| > channel | String | Yes      | Channel name, `opt-summary`          |
| > uly     | String | Yes      | Underlying                           |

> Example Response

```json
{
  "event": "subscribe",
  "arg": {
    "channel": "opt-summary",
    "uly": "BTC-USD"
  }
}
```

> Failure example

```json
{
  "event": "error",
  "code": "60012",
  "msg": "Unrecognized request: {\"op\": \"subscribe\", \"argss\":[{ \"channel\" : \"opt-summary\", \"uly\" : \"BTC-USD\"}]}"
}
```

#### Response parameters

| Parameter | Type   | Required | Description                              |
| :-------- | :----- | :------- | ---------------------------------------- |
| event     | String | Yes      | Event, `subscribe` `unsubscribe` `error` |
| `arg`     | Object | No       | Subscribed channel                       |
| > channel | String | Yes      | Channel name                             |
| > uly     | String | Yes      | Underlying                               |
| code      | String | No       | Error code                               |
| msg       | String | No       | Error message                            |

> Push Data Example

```json
{
  "arg": {
    "channel": "opt-summary",
    "uly": "BTC-USD"
  },
  "data": [
    {
      "instType": "OPTION",
      "instId": "BTC-USD-200103-5500-C",
      "uly": "BTC-USD",
      "delta": "0.7494223636",
      "gamma": "-0.6765419039",
      "theta": "-0.0000809873",
      "vega": "0.0000077307",
      "deltaBS": "0.7494223636",
      "gammaBS": "-0.6765419039",
      "thetaBS": "-0.0000809873",
      "vegaBS": "0.0000077307",
      "realVol": "0",
      "bidVol": "",
      "askVol": "1.5625",
      "markVol": "0.9987",
      "lever": "4.0342",
      "ts": "1597026383085"
    }
  ]
}
```

#### Push data parameters

| **Parameter** | **Type** | **Description**                                                                |
| :------------ | :------- | ------------------------------------------------------------------------------ | --- |
| `arg`         | Object   | Successfully subscribed channel                                                |
| > channel     | String   | Channel name                                                                   |
| > uly         | String   | Underlying                                                                     |     |
| `data`        | Array    | Subscribed data                                                                |
| > instType    | String   | Instrument type, `OPTION`                                                      |
| > instId      | String   | Instrument ID                                                                  |
| > uly         | String   | Underlying                                                                     |
| > delta       | String   | Sensitivity of option price to `uly` price                                     |
| > gamma       | String   | The delta's sensitivity to `uly` price                                         |
| > vega        | String   | Sensitivity of option price to implied volatility                              |
| > theta       | String   | Sensitivity of option priceo remaining maturity                                |
| > deltaBS     | String   | Sensitivity of option price to `uly` price in BS mode                          |
| > gammaBS     | String   | The delta's sensitivity to `uly ` price in BS mode                             |
| > vegaBS      | String   | Sensitivity of option price to implied volatility in BS mode                   |
| > thetaBS     | String   | Sensitivity of option price to remaining maturity in BS mode                   |
| > lever       | String   | Leverage                                                                       |
| > markVol     | String   | Mark volatility                                                                |
| > bidVol      | String   | Bid volatility                                                                 |
| > askVol      | String   | Ask Volatility                                                                 |
| > realVol     | String   | Realized volatility (not currently used)                                       |
| > ts          | String   | Price update time, Unix timestamp format in milliseconds, e.g. `1597026383085` |

### Funding Rate Channel

Retrieve funding rate. Data will be pushed every minute.

> Request Example

```json
{
  "op": "subscribe",
  "args": [
    {
      "channel": "funding-rate",
      "instId": "BTC-USD-SWAP"
    }
  ]
}
```

#### Request parameters

| Parameter | Type   | Required | Description                          |
| :-------- | :----- | :------- | ------------------------------------ |
| op        | String | Yes      | Operation, `subscribe` `unsubscribe` |
| `args`    | Array  | Yes      | List of subscribed channels          |
| > channel | String | Yes      | Channel name, `funding-rate`         |
| > instId  | String | Yes      | Instrument ID                        |

> Successful Response Example

```json
{
  "event": "subscribe",
  "arg": {
    "channel": "funding-rate",
    "instId": "BTC-USD-SWAP"
  }
}
```

> Failure Response Example

```json
{
  "event": "error",
  "code": "60012",
  "msg": "Unrecognized request: {\"op\": \"subscribe\", \"argss\":[{ \"channel\" : \"funding-rate\", \"instId\" : \"BTC-USD-SWAP\"}]}"
}
```

#### Response parameters

| Parameter | Type   | Required | Description                              |
| :-------- | :----- | :------- | ---------------------------------------- |
| event     | String | Yes      | Event, `subscribe` `unsubscribe` `error` |
| `arg`     | Object | No       | Subscribed channel                       |
| > channel | String | yes      | Channel name                             |
| > instId  | String | No       | Instrument ID                            |
| code      | String | No       | Error code                               |
| msg       | String | No       | Error message                            |

> Push Data Example

```json
{
  "arg": {
    "channel": "funding-rate",
    "instId": "BTC-USD-SWAP"
  },
  "data": [
    {
      "instType": "SWAP",
      "instId": "BTC-USD-SWAP",
      "fundingRate": "0.018",
      "nextFundingRate": "",
      "fundingTime": "1597026383085"
    }
  ]
}
```

#### Push data parameters

| **Parameter**     | **Type** | **Description**                                                                                     |
| :---------------- | :------- | --------------------------------------------------------------------------------------------------- |
| `arg`             | Object   | Successfully subscribed channel                                                                     |
| > channel         | String   | Channel name                                                                                        |
| > instId          | String   | Instrument ID                                                                                       |
| `data`            | Array    | Subscribed data                                                                                     |
| > instType        | String   | Instrument type, `SWAP`                                                                             |
| > instId          | String   | Instrument ID, e.g. `BTC-USD-SWAP`                                                                  |
| > fundingRate     | String   | Current funding rate                                                                                |
| > nextFundingRate | String   | Forecasted funding rate for the next period                                                         |
| fundingTime       | String   | Funding time of the latest settlement, Unix timestamp format in milliseconds, e.g. `1597026383085`. |

### Index Candlesticks Channel

Retrieve the candlesticks data of the index. Data will be pushed every 500 ms.

> Request Example

```json
{
  "op": "subscribe",
  "args": [
    {
      "channel": "index-candle30m",
      "instId": "BTC-USD"
    }
  ]
}
```

#### Request parameters

| Parameter | Type   | Required | Description                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| :-------- | :----- | :------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| op        | String | Yes      | Operation, `subscribe` `unsubscribe`                                                                                                                                                                                                                                                                                                                                                                                                               |
| `args`    | Array  | Yes      | List of subscribed channels                                                                                                                                                                                                                                                                                                                                                                                                                        |
| > channel | String | Yes      | Channel name<br />`index-candle1Y`<br />`index-candle6M`<br />`index-candle3M`<br />`index-candle1M`<br />`index-candle1W`<br />`index-candle1D`<br />`index-candle2D`<br />`index-candle3D`<br />`index-candle5D`<br />`index-candle12H`<br />`index-candle6H`<br />`index-candle4H`<br />`index -candle2H`<br />`index-candle1H`<br />`index-candle30m`<br />`index-candle15m`<br />`index-candle5m`<br />`index-candle3m`<br />`index-candle1m` |
| > instId  | String | Yes      | Instrument ID                                                                                                                                                                                                                                                                                                                                                                                                                                      |

> Successful Response Example

```json
{
  "event": "subscribe",
  "arg": {
    "channel": "index-candle30m",
    "instId": "BTC-USD"
  }
}
```

> Failure Response Example

```json
{
  "event": "error",
  "code": "60012",
  "msg": "Unrecognized request: {\"op\": \"subscribe\", \"argss\":[{ \"channel\" : \"index-candle30m\", \"instId\" : \"BTC-USD\"}]}"
}
```

#### Response parameters

| Parameter | Type   | Required | Description               |
| :-------- | :----- | :------- | ------------------------- |
| event     | String | Yes      | `subscribe` `unsubscribe` |
| `arg`     | Object | No       | Subscribed channel        |
| > channel | String | Yes      | Channel name              |
| > instId  | String | No       | Instrument ID             |
| code      | String | No       | Error code                |
| msg       | String | No       | Error message             |

> Push Data Example

```json
{
  "arg": {
    "channel": "index-candle30m",
    "instId": "BTC-USD"
  },
  "data": [["1597026383085", "3811.31", "3811.31", "3811.31", "3811.31"]]
}
```

#### Push data parameters

| Parameter | Type   | Description                                                                       |
| :-------- | :----- | --------------------------------------------------------------------------------- |
| `arg`     | Object | Successfully subscribed channel                                                   |
| > channel | String | Channel name                                                                      |
| > instId  | String | Instrument ID                                                                     |
| `data`    | Array  | Subscribed data                                                                   |
| > ts      | String | Data generation time, Unix timestamp format in milliseconds, e.g. `1597026383085` |
| > o       | String | Open price                                                                        |
| > h       | String | Highest price                                                                     |
| > l       | String | Lowest price                                                                      |
| > c       | String | Close price                                                                       |

<aside class="notice">
The order of the returned values is: [ts,o,h,l,c]
</aside>

### Index Tickers Channel

Retrieve index tickers data

> Request Example

```json
{
  "op": "subscribe",
  "args": [
    {
      "channel": "index-tickers",
      "instId": "BTC-USDT"
    }
  ]
}
```

#### Request parameters

| Parameter | Type   | Required | Description                                                      |
| :-------- | :----- | :------- | ---------------------------------------------------------------- |
| op        | String | Yes      | `subscribe` `unsubscribe`                                        |
| `args`    | Array  | Yes      | List of subscribed channels                                      |
| > channel | String | Yes      | Channel name, `index-tickers`                                    |
| > instId  | String | Yes      | Index with USD, USDT, BTC as the quote currency, e.g. `BTC-USDT` |

> Successful Response Example

```json
{
  "event": "subscribe",
  "arg": {
    "channel": "index-tickers",
    "instId": "BTC-USDT"
  }
}
```

> Failure Response Example

```json
{
  "event": "error",
  "code": "60012",
  "msg": "Unrecognized request: {\"op\": \"subscribe\", \"argss\":[{ \"channel\" : \"index-tickers\", \"instId\" : \"BTC-USDT\"}]}"
}
```

#### Response parameters

| Parameter | Type   | Required | Description                       |
| :-------- | :----- | :------- | --------------------------------- |
| event     | String | Yes      | `subscribe` `unsubscribe` `error` |
| `arg`     | Object | No       | Subscribed channel                |
| > channel | String | Yes      | Channel name, `index-tickers`     |
| > instId  | String | No       | Instrument ID                     |
| code      | String | No       | Error code                        |
| msg       | String | No       | Error message                     |

> Push Data Example

```json
{
  "arg": {
    "channel": "index-tickers",
    "instId": "BTC-USDT"
  },
  "data": [
    {
      "instId": "BTC-USDT",
      "idxPx": "0.1",
      "high24h": "0.5",
      "low24h": "0.1",
      "open24h": "0.1",
      "sodUtc0": "0.1",
      "sodUtc8": "0.1",
      "ts": "1597026383085"
    }
  ]
}
```

#### Push data parameters

| Parameter | Type   | Description                                                              |
| :-------- | :----- | ------------------------------------------------------------------------ |
| `arg`     | Object | Successfully subscribed channel                                          |
| > channel | String | Channel name                                                             |
| > instId  | String | Index with USD, USDT, or BTC as quote currency, e.g. `BTC-USDT`.         |
| `data`    | Array  | Subscribed data                                                          |
| > instId  | String | Index                                                                    |
| > idxPx   | String | Latest Index Price                                                       |
| > open24h | String | Open price in the past 24 hours                                          |
| > high24h | String | Highest price in the past 24 hours                                       |
| > low24h  | String | Lowest price in the past 24 hours                                        |
| > sodUtc0 | String | Open price in the UTC 0                                                  |
| > sodUtc8 | String | Open price in the UTC 8                                                  |
| > ts      | String | Update time, Unix timestamp format in milliseconds, e.g. `1597026383085` |


### Status Channel

Get the status of system maintenance and push when the system maintenance status changes. First subscription: "Push the latest change data"; every time there is a state change, push the changed content

> Request Example

```json
{
  "op": "subscribe",
  "args": [
    {
      "channel": "status"
    }
  ]
}
```

#### Request parameters

| Parameter | Type   | Required | Description                                                      |
| :-------- | :----- | :------- | ---------------------------------------------------------------- |
| op        | String | Yes      | `subscribe` `unsubscribe`                                        |
| `args`    | Array  | Yes      | List of subscribed channels                                      |
| > channel | String | Yes      | Channel name, `status`                                    |

> Successful Response Example

```json
{
  "event": "subscribe",
  "arg": {
    "channel": "status"
  }
}
```

> Failure Response Example

```json
{
  "event": "error",
  "code": "60012",
  "msg": "Unrecognized request: {\"op\": \"subscribe\", \"argss\":[{ \"channel\" : \"statuss\"}]}"
}
```

#### Response parameters

| Parameter | Type   | Required | Description                       |
| :-------- | :----- | :------- | --------------------------------- |
| event     | String | Yes      | `subscribe` `unsubscribe` `error` |
| `arg`     | Object | No       | Subscribed channel                |
| > channel | String | Yes      | Channel name, `status`            |
| code      | String | No       | Error code                        |
| msg       | String | No       | Error message                     |

> Push Data Example

```json
{
	"arg": {
		"channel": "status"
	},
	"data": [{
		"title": "Spot System Upgrade",
		"state": "scheduled",
		"begin": "1610019546",
        "href": "",
		"end": "1610019546",
		"serviceType": "1",
        "system": "classic",
        "scheDesc": "",
		"ts": "1597026383085"
	}]
}
```

#### Push data parameters

| Parameter | Type   | Description                                                              |
| :-------- | :----- | ------------------------------------------------------------------------ |
| `arg`     | Object | Successfully subscribed channel                                          |
| > channel | String | Channel name                                                             |
| `data`    | Array  | Subscribed data                                                          |
| > title  | String | The title of system maintenance instructions                              |
| > state   | String | System maintenance status, `scheduled`: waiting; `ongoing`: processing; `completed`: completed; `canceled`: canceled   |
| > begin | String | Start time of system maintenance, Unix timestamp format in milliseconds, e.g. `1617788463867` |
| > end | String | End time of system maintenance, Unix timestamp format in milliseconds, e.g. `1617788463867`     |
| > href  | String | Hyperlink for system maintenance details, if there is no return value, the default value will be empty. e.g. “”  |
| > serviceType | String | Service type, `0`：WebSocket ; `1`：Spot/Margin ; `2`：Futures ; `3`：Perpetual ; `4`：Options ; 5：Trading service |
| > system | String | System， `classic`：Classic account， `unified`：Unified account                                                   |
| > scheDesc | String | Rescheduled description，e.g. `Rescheduled from 2021-01-26T16:30:00.000Z to 2021-01-28T16:30:00.000Z`                                                |
| > ts      | String | Push time, Unix timestamp format in milliseconds, e.g. `1617788463867` |

## Private Channel

### Account Channel

Retrieve account information. Data will be pushed when triggered by events such as placing/canceling order, and will also be pushed in regular interval according to subscription granularity.

> Request Example : single

```json
{
  "op": "subscribe",
  "args": [
    {
      "channel": "account",
      "ccy": "BTC"
    }
  ]
}
```

> Request Example

```json
{
  "op": "subscribe",
  "args": [
    {
      "channel": "account"
    }
  ]
}
```

#### Request parameters

| Parameter | Type   | Required | Description                          |
| :-------- | :----- | :------- | ------------------------------------ |
| op        | String | Yes      | Operation, `subscribe` `unsubscribe` |
| `args`    | Array  | Yes      | List of subscribed channels          |
| > channel | String | Yes      | Channel name, `account`              |
| > ccy     | String | No       | Currency                             |

> Successful Response Example : single

```json
{
  "event": "subscribe",
  "arg": {
    "channel": "account",
    "ccy": "BTC"
  }
}
```

> Successful Response Example

```json
{
  "event": "subscribe",
  "arg": {
    "channel": "account"
  }
}
```

> Failure Response Example

```json
{
  "event": "error",
  "code": "60012",
  "msg": "Unrecognized request: {\"op\": \"subscribe\", \"argss\":[{ \"channel\" : \"account\", \"ccy\" : \"BTC\"}]}"
}
```

#### Response parameters

| Parameter | Type   | Required | Description                                  |
| :-------- | :----- | :------- | -------------------------------------------- |
| event     | String | Yes      | Operation, `subscribe` `unsubscribe` `error` |
| `arg`     | Object | No       | Subscribed channel                           |
| > channel | String | Yes      | Channel name, `account`                      |
| > ccy     | String | No       | Currency                                     |
| code      | String | No       | Error code                                   |
| msg       | String | No       | Error message                                |

> Push Data Example: single

```json
{
  "arg": {
    "channel": "account",
    "ccy": "BTC"
  },
  "data": [
    {
      "uTime": "1597026383085",
      "totalEq": "41624.32",
      "isoEq": "3624.32",
      "adjEq": "41624.32",
      "ordFroz": "0",
      "imr": "4162.33",
      "mmr": "4",
      "mgnRatio": "41624.32",
      "details": [
        {
          "availBal": "",
          "availEq": "1",
          "ccy": "BTC",
          "cashBal": "1",
          "disEq": "50559.01",
          "eq": "1",
          "frozenBal": "0",
          "interest": "0",
          "isoEq": "0",
          "liab": "0",
          "mgnRatio": "",
          "ordFrozen": "0",
          "upl": "0",
          "uplLiab": "0",
          "crossLiab": "0",
          "isoLiab": "0",
          "uTime": "1597026383085"
        }
      ]
    }
  ]
}
```

> Push Data Example

```json
{
  "arg": {
    "channel": "account"
  },
  "data": [
    {
      "uTime": "1614846244194",
      "totalEq": "91884.8502560037982063",
      "adjEq": "91884.8502560037982063",
      "isoEq": "0",
      "ordFroz": "0",
      "imr": "0",
      "mmr": "0",
      "mgnRatio": "100000",
      "details": [{
          "availBal": "",
          "availEq": "1",
          "ccy": "BTC",
          "cashBal": "1",
          "disEq": "50559.01",
          "eq": "1",
          "frozenBal": "0",
          "interest": "0",
          "isoEq": "0",
          "liab": "0",
          "mgnRatio": "",
          "ordFrozen": "0",
          "upl": "0",
          "uplLiab": "0",
          "crossLiab": "0",
          "isoLiab": "0",
          "uTime": "1614846244194"
        },
        {
          "availBal": "",
          "availEq": "41307.251992607125",
          "ccy": "USDT",
          "cashBal": "41307.251992607125",
          "disEq": "41325.8402560037982063",
          "eq": "41307.251992607125",
          "frozenBal": "0",
          "interest": "0",
          "isoEq": "0",
          "liab": "0",
          "mgnRatio": "",
          "ordFrozen": "0",
          "upl": "0",
          "uplLiab": "0",
          "crossLiab": "0",
          "isoLiab": "0",
          "uTime": "1614846244194"
        }
      ]
    }
  ]
}
```

#### Push data parameters

| **Parameters** | **Types** | **Description**                                                                                                   |
| -------------- | --------- | ----------------------------------------------------------------------------------------------------------------- |
| uTime          | String    | The latest time to get account information, millisecond format of Unix timestamp, e.g. `1597026383085`            |
| totalEq        | String    | Total equity in USD level                                                                                         |
| isoEq          | String    | Isolated margin equity in USD level<br/>Applicable to `Single-currency margin` and `Multi-currency margin`        |
| adjEq          | String    | Adjusted/Effective equity in USD level<br/>Applicable to `Multi-currency margin`                                  |
| ordFroz     | String   |  Margin frozen for pending orders in USD level<br />Applicable to `Multi-currency margin`          |
| imr            | String    | Initial margin requirement in USD level<br/>Applicable to `Multi-currency margin`                                 |
| mmr            | String    | Maintenance margin requirement in USD level <br/>Applicable to `Multi-currency margin`                            |
| mgnRatio       | String    | Margin ratio in USD level <br/>Applicable to `Multi-currency margin`                                              |
| details        | Array     | Detailed asset information in all currencies                                                                      |
| > ccy          | String    | Currency                                                                                                          |
| > eq           | String    | Equity of the currency                                                                                            |
| > cashBal      | String    | Cash Balance                                                    |
| > uTime        | String    | Update time, Unix timestamp format in milliseconds, e.g. `1597026383085`   |
| > isoEq        | String    | Isolated margin equity of the currency<br/>Applicable to `Single-currency margin` and `Multi-currency margin`     |
| > availEq      | String    | Available equity of the currency<br/>Applicable to `Single-currency margin` and `Multi-currency margin`           |
| > disEq      | String    | discount equity of the currency in USD level         |
| > availBal     | String    | Available balance of the currency<br/>Applicable to `Simple`                                                      |
| > frozenBal    | String    | Frozen balance of the currency                                                                                    |
| > ordFrozen    | String    | Margin frozen for open orders                                                                                     |
| > liab         | String    | Liabilities of the currency<br/>Applicable to `Multi-currency margin`                                             |
| > upl          | String    | Unrealized profit and loss of the currency<br/>Applicable to `Single-currency margin` and `Multi-currency margin` |
| > uplLib       | String    | Liabilities due to Unrealized loss of the currency<br/>Applicable to `Multi-currency margin` |
| > crossLiab    | String    | Cross Liabilities of the currency<br/>Applicable to `Multi-currency margin` |
| > isoLiab      | String    | Isolated Liabilities of the currency<br/>Applicable to `Multi-currency margin` |
| > mgnRatio     | String    | Margin ratio of the currency<br/>Applicable to `Single-currency margin`                                           |
| > interest     | String    | Interest of the currency<br>Applicable to `Multi-currency margin`                                                 |

<aside class="notice">
"" will be returned for inapplicable fields under the current account level.
</aside>

<aside class="notice"> 
<p> 
  When multiple orders are being executed at the same time, the changes of account data will be aggregated into one as much as possible.
</p> 
</aside>

<aside class="notice"> 
<p> Initial snapshot: Only currencies with non-zero balance will be pushed. Definition of non-zero balance: any value of eq, availEq, availBql parameters is not 0.
</p> 
<p> Data pushed in regular interval: Only currencies with non-zero balance will be pushed. Definition of non-zero balance: any value of eq, availEq, availBql parameters is not 0.
</p> 
<p> For example, when subscribing to account channel without specifying ccy and there are 5 currencies are with non-zero balance, all 5 currencies data will be pushed in initial snapshot and in regular interval. Subsequently when there is change in balance or equity of an token, only the incremental data of that currency will be pushed triggered by this change.
</p> 
</aside>

Distribution of applicable fields under each account level are as follows:

| **Parameters** | Simple | Single-currency margin | Multi-currency margin |
| :------------- | :------------- | :--------------------- | :-------------------- |
| uTime          | Yes            | Yes                    | Yes                   |
| totalEq        | Yes            | Yes                    | Yes                   |
| isoEq          |                | Yes                    | Yes                   |
| adjEq          |                |                        | Yes                   |
| ordFroz	       |                |                        | Yes                    |
| imr            |                |                        | Yes                   |
| mmr            |                |                        | Yes                   |
| mgnRatio       |                |                        | Yes                   |
| details        |                |                        |                       |
| > ccy          | Yes            | Yes                    | Yes                   |
| > eq           | Yes            | Yes                    | Yes                   |
| > cashBal      | Yes            | Yes                    | Yes                   |
| > uTime        | Yes            | Yes                    | Yes                   |
| > isoEq        |                | Yes                    | Yes                   |
| > availEq      |                | Yes                    | Yes                   |
| > disEq        | Yes            | Yes                    | Yes                   |
| > availBal     | Yes            |                        |                       |
| > frozenBal    | Yes            | Yes                    | Yes                   |
| > ordFrozen    | Yes            | Yes                    | Yes                   |
| > liab         |                |                        | Yes                   |
| > upl          |                | Yes                    | Yes                   |
| > uplLib       |                |                        | Yes                   |
| > crossLiab    |                |                        | Yes                   |
| > isoLiab      |                |                        | Yes                   |
| > mgnRatio     |                | Yes                    |                       |
| > interest     |                |                        | Yes                   |

### Positions Channel

Retrieve position information. Initial snapshot will be pushed according to subscription granularity. Data will be pushed when triggered by events such as placing/canceling order, and will also be pushed in regular interval according to subscription granularity.

> Request Example : single

```json
{
  "op": "subscribe",
  "args": [
    {
      "channel": "positions",
      "instType": "FUTURES",
      "uly": "BTC-USD",
      "instId": "BTC-USD-200329"
    }
  ]
}
```

> Request Example

```json
{
  "op": "subscribe",
  "args": [
    {
      "channel": "positions",
      "instType": "ANY"
    }
  ]
}
```

#### Request parameters

| Parameter  | Type   | Required | Description                                                                        |
| :--------- | :----- | -------- | ---------------------------------------------------------------------------------- |
| op         | String | Yes      | Operation, `subscribe` `unsubscribe`                                               |
| `args`     | Array  | Yes      | List of subscribed channels                                                        |
| > channel  | String | Yes      | Channel name, `positions`                                                          |
| > instType | String | Yes      | Instrument type<br />`MARGIN`<br />`SWAP`<br />`FUTURES`<br />`OPTION` <br />`ANY` |
| > uly      | String | No       | Underlying                                                                         |
| > instId   | String | No       | Instrument ID                                                                      |

> Successful Response Example : single

```json
{
  "event": "subscribe",
  "arg": {
    "channel": "positions",
    "instType": "FUTURES",
    "uly": "BTC-USD",
    "instId": "BTC-USD-200329"
  }
}
```

> Successful Response Example

```json
{
  "event": "subscribe",
  "arg": {
    "channel": "positions",
    "instType": "ANY"
  }
}
```

> Failure Response Example

```json
{
  "event": "error",
  "code": "60012",
  "msg": "Unrecognized request: {\"op\": \"subscribe\", \"argss\":[{ \"channel\" : \"positions\", \"instType\" : \"FUTURES\"}]}"
}
```

#### Response parameters

| Parameter  | Type   | Required | Description                                                                         |
| :--------- | :----- | -------- | ----------------------------------------------------------------------------------- |
| event      | String | Yes      | Event, `subscribe` `unsubscribe` `errror`                                           |
| `arg`      | Object | No       | Subscribed channel                                                                  |
| > channel  | String | Yes      | Channel name                                                                        |
| > instType | String | Yes      | Instrument type<br />`OPTION`<br />`FUTURES` <br />`SWAP`<br />`MARGIN` <br />`ANY` |
| > uly      | String | No       | Underlying                                                                          |
| > instId   | String | No       | Instrument ID                                                                       |
| code       | String | No       | Error code                                                                          |
| msg        | String | No       | Error message                                                                       |

> Push Data Example: single

```json
{
  "arg": {
    "channel": "positions",
    "instType": "FUTURES",
    "instId": "BTC-USD-200329"
  },
  "data": [
    {
      "instId": "BTC-USD-200329",
      "instType": "FUTURES",
      "mgnMode": "cross",
      "posSide": "long",
      "pos": "10",
      "ccy": "BTC",
      "posCcy": "",
      "availPos": "10",
      "avgPx": "3320",
      "upl": "0.00020928",
      "uplRatio": "0.00020928",
      "lever": "2",
      "liqPx": "0.00020928",
      "imr": "2",
      "margin": "",
      "mgnRatio": "",
      "mmr": "2",
      "liab": "0.00020928",
      "liabCcy": "USDT",
      "interest": "2",
      "tradeId": "2",
      "optVal": "",
      "adl": "1",
      "last": "13452.1",
      "cTime": "1597026383085",
      "uTime": "1597026383085",
      "pTime": "1597026383085"
    }
  ]
}
```

> Push Data Example

```json
{
  "arg": {
    "channel": "positions",
    "instType": "ANY"
  },
  "data": [
    {
      "instId": "BTC-USD-200329",
      "instType": "FUTURES",
      "mgnMode": "cross",
      "posSide": "long",
      "pos": "10",
      "ccy": "BTC",
      "posCcy": "",
      "availPos": "10",
      "avgPx": "3320",
      "upl": "0.00020928",
      "uplRatio": "0.00020928",
      "lever": "2",
      "liqPx": "0.00020928",
      "imr": "2",
      "margin": "",
      "mgnRatio": "",
      "mmr": "2",
      "liab": "0.00020928",
      "liabCcy": "USDT",
      "interest": "2",
      "tradeId": "2",
      "optVal": "",
      "adl": "1",
      "last": "13452.1",
      "cTime": "1597026383085",
      "uTime": "1597026383085",
      "pTime": "1597026383085"
    },
    {
      "instType": "SWAP",
      "instId": "BTC-USD-SWAP",
      "mgnMode": "cross",
      "posSide": "long",
      "pos": "10",
      "ccy": "BTC",
      "posCcy": "",
      "availPos": "10",
      "avgPx": "3320",
      "upl": "0.00020928",
      "uplRatio": "0.00020928",
      "lever": "2",
      "liqPx": "0.00020928",
      "imr": "2",
      "margin": "",
      "mgnRatio": "",
      "mmr": "2",
      "liab": "0.00020928",
      "liabCcy": "USDT",
      "interest": "2",
      "tradeId": "2",
      "optVal": "",
      "adl": "1",
      "last": "1342.1",
      "cTime": "1597026383085",
      "uTime": "1597026383085",
      "pTime": "1597026383085"
    }
  ]
}
```

#### Push data parameters

| Parameter     | Type   | Description                                                                                                                                                                                                                                                          |
| :------------ | :----- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `arg`         | Object | Successfully subscribed channel                                                                                                                                                                                                                                      |
| > channel     | String | Channel name                                                                                                                                                                                                                                                         |
| > instType    | String | Instrument type                                                                                                                                                                                                                                                      |
| > uly         | String | Underlying                                                                                                                                                                                                                                                           |
| > instId      | String | Instrument ID                                                                                                                                                                                                                                                        |
| `data`        | Array  | Subscribed data                                                                                                                                                                                                                                                      |
| &gt; instType | String | Instrument type                                                                                                                                                                                                                                                      |
| > mgnMode     | String | Margin mode, `cross` `isolated`                                                                                                                                                                                                                                      |
| > posSide     | String | Position side<br>`long`<br />`short`<br />`net` (`FUTURES/SWAP/OPTION`: positive `pos` means long position and negative `pos` means short position. `MARGIN`: `posCcy` being base currency means long position, `posCcy` being quote currency means short position.) |
| > pos         | String | Quantity of positions                                                                                                                                                                                                                                                |
| > posCcy      | String | Position currency, only applicable to `MARGIN` positions                                                                                                                                                                                                             |
| > availPos    | String | Position that can be closed<br />Only applicable to `MARGIN`, `FUTURES/SWAP` in the `long-short` mode, `OPTION` in `Simple` and `isolated` `OPTION` in margin Account.                                                                                               |
| > avgPx       | String | Average open price                                                                                                                                                                                                                                                   |
| > upl         | String | Unrealized profit and loss                                                                                                                                                                                                                                           |
| > uplRatio    | String | Unrealized profit and loss ratio                                                                                                                                                                                                                                     |
| > instId      | String | Instrument ID, e.g. `BTC-USD-180216`                                                                                                                                                                                                                                 |
| > lever       | String | Leverage, not applicable to `OPTION` seller                                                                                                                                                                                                                          |
| > liqPx       | String | Estimated liquidation price<br/>Not applicable to `cross` `FUTURES/SWAP` in `Multi-currency margin`.<br />Not applicable to `OPTION`                                                                                                                                 |
| > imr         | String | Initial margin requirement, only applicable to `cross`                                                                                                                                                                                                               |
| > margin      | String | Margin, can be added or reduced. Only applicable to `isolated` `Margin`.                                                                                                                                                                                             |
| > mgnRatio    | String | Margin ratio                                                                                                                                                                                                                         |
| > mmr         | String | Maintenance margin requirement                                                                                                                                                                                                                                       |
| > liab        | String | Liabilities, only applicable to `MARGIN`.                                                                                                                                                                                                                            |
| > liabCcy     | String | Liabilities currency, only applicable to `MARGIN`.                                                                                                                                                                                                                   |
| > interest    | String | Interest. Interest that has been incurred.                                                                                                                                                                                                                           |
| > tradeId     | String | Last trade ID                                                                                                                                                                                                                                                        |
| > optVal      | String | Option Value, only applicable to `OPTION`.                                                                                                                                                                                                                           |
| > adl         | String | Auto decrease line, signal area<br/>Divided into 5 levels, from 1 to 5, the smaller the number, the weaker the adl intensity.                                                                                                                                        |
| > ccy         | String | Currency used for margin                                                                                                                                                                                                                                             |
| > last        | String | Latest traded price                                                                                                                                                                                                                                                  |
| > cTime       | String | Creation time, Unix timestamp format in milliseconds, e.g. `1597026383085`.                                                                                                                                                                                          |
| > uTime       | String | Latest time position was adjusted, Unix timestamp format in milliseconds, e.g. `1597026383085`.                                                                                                                                                                      |
| > pTime       | String | Push time of positions information, Unix timestamp format in milliseconds, e.g. `1597026383085`.                                                                                                                                                                     |

<aside class="notice"> 
<p> 
When multiple orders are being executed at the same time, the changes of position data will be aggregated into one as much as possible.
</p> 
</aside>

<aside class="notice"> 
<p>
Initial snapshot: Only position with non-zero position quantity will be pushed. Definition of non-zero quantity: value of pos parameter is not 0.
</p> 
<p> Data pushed in regular interval: Only position with non-zero position quantity will be pushed. Definition of non-zero quantity: value of pos parameter is not 0.
</p> 
<p> For example, when subscribing to positions channel specifying an underlying and there are 20 positions are with non-zero quantity, all 20 positions data will be pushed in initial snapshot and in regular interval. Subsequently when there is change in pos of a position, only the data of that position will be pushed triggered by this change.
</p> 
</aside>

### Balance and Position Channel

Retrieve account balance and position information. Data will be pushed when triggered by events such as filled order, funding transfer. 

> Request Example 

```json
{
	"op": "subscribe",
	"args": [{
		"channel": "balance_and_position"
	}]
}
```
#### Request parameters 

| Parameter      | Type   | Required | Description                                                |
| :-------- | :----- | :------- | :-------------------------------------------------- |
| op        | String | Yes       | Operation, `subscribe` `unsubscribe` |
| args      | Array  | Yes       | List of subscribed channels                                  |
| > channel | String | Yes       | Channel name，`balance_and_position`                                   |

> Response Example 

```json
{
	"event": "subscribe",
	"arg": {
		"channel": "balance_and_position"
	}
}
```

> Failure Response Example

```json
{
	"event": "error",
	"code": "60012",
	"msg": "Unrecognized request: {\"op\": \"subscribe\", \"argss\":[{ \"channel\" : \"balance_and_position\"}]}"
}
```
#### Response parameters 

| Parameter       | Type   | Required | Description                                                         |
| :--------- | :----- | :------- | :----------------------------------------------------------- |
| event      | String | Yes      | Operation，`subscribe`      `unsubscribe`    `error` |
| arg        | Object | No       | List of subscribed channels                                                  |
| > channel  | String | Yes      | Channel name，`balance_and_position`                                            |
| code       | String | No       | Error code                                                       |
| msg        | String | No       | Error message                                                     |


> Push Data Example

```json
{
	"arg": {
		"channel": "balance_and_position"
	},
	"data": [{
		"pTime": "1597026383085",
		"eventType": "snapshot",
		"balData": [{
			"ccy": "BTC",
			"cashBal": "1",
      "uTime": "1597026383085"
		}],
		"posData": [{
			"posId": "1111111111",
			"tradeId": "2",
			"instId": "BTC-USD-191018",
			"instType": "FUTURES",
			"mgnMode": "cross",
			"posSide": "long",
			"pos": "10",
			"ccy": "BTC",
			"posCcy": "",
			"avgPx": "3320",
      "uTIme": "1597026383085"
		}]
	}]
}
```

#### Push data parameters

| **Parameter**   | **Type** | **Description**                                                     |
| :----------- | :------- | :----------------------------------------------------------- |
| arg        | Object   | Channel to subscribe to                                               |
| > channel   | String   | Channel name                                                      |
| data       | Array    | Subscribed data                                                   |
| > pTime       | String   | Push time of both balance and position information, millisecond format of Unix timestamp, e.g. `1597026383085` |
| > eventType   | String   | Event Type, `snapshot`、`delivered` 、`exercised`、`transferred`、`filled`, `liquidation`, `claw_back`, `adl`, `funding_fee`,`adjust_margin`, `set_leverage` |
| > balData     | String   | Balance data   |
| >> ccy        | String   | Currency      |
| >> cashBal    | String   | Cash Balance                  |
| >> uTime      | String   | Update time, Unix timestamp format in milliseconds, e.g. `1597026383085`                 |
| > posData     | String   | Position data                  |
| >> posId       | String   | Position ID                      |
| >> tradeId     | String   | Last trade ID                 |
| >> instId      | String   | Instrument ID, e.g `BTC-USD-180213`                |
| >> instType    | String   | Instrument type                 |
| >> mgnMode     | String   | Margin mode,  `isolated`, `cross`                |
| >> avgPx       | String   | Average open price                  |
| >> ccy         | String   | Currency used for margin                |
| >> posSide     | String   | Position side：`long`, `short`, `net`                  |
| >> pos         | String   | Quantity of positions                |
| >> posCcy      | String   | Position currency, only applicable to MARGIN positions.            |
| >> uTime       | String   | Update time, Unix timestamp format in milliseconds, e.g. `1597026383085` |


<aside class="notice"> 
<p> 
  When multiple orders are being executed at the same time, the data changes of both balance and position will be aggregated into one as much as possible
</p> 
</aside> 



<aside class="notice"> 
<p> Initial snapshot: Only either  position with non-zero position quantity or cash balance with non-zero quantity will be pushed.
</p> 



<p> For example, if you subscribe according to all currencies and the user has 5 currency balances that are not 0 and 20 positions, 
all 20 positions data and 5 currency balances data will be pushed in initial snapshot; 
Subsequently when there is change in pos of a position, only the data of that position will be pushed triggered by this change.
</p> 
</aside> 

### Order Channel

Retrieve order information. Data will not be pushed when first subscribed. Data will only be pushed when triggered by events such as placing/canceling order.

> Request Example : single

```json
{
  "op": "subscribe",
  "args": [
    {
      "channel": "orders",
      "instType": "FUTURES",
      "uly": "BTC-USD",
      "instId": "BTC-USD-200329"
    }
  ]
}
```

> Request Example

```json
{
  "op": "subscribe",
  "args": [
    {
      "channel": "orders",
      "instType": "FUTURES",
      "uly": "BTC-USD"
    }
  ]
}
```

#### Request parameters

| Parameter  | Type   | Required | Description                                                                                      |
| :--------- | :----- | -------- | ------------------------------------------------------------------------------------------------ |
| op         | String | Yes      | Operation, `subscribe` `unsubscribe`                                                             |
| `args`     | Array  | Yes      | List of subscribed channels                                                                      |
| > channel  | String | Yes      | Channel name, `orders`                                                                           |
| > instType | String | Yes      | Instrument type<br />`SPOT `<br />`MARGIN`<br />` SWAP`<br />`FUTURES`<br />`OPTION `<br />`ANY` |
| > uly      | String | No       | Underlying                                                                                       |
| > instId   | String | No       | Instrument ID                                                                                    |

> Successful Response Example : single

```json
{
  "event": "subscribe",
  "arg": {
    "channel": "orders",
    "instType": "FUTURES",
    "uly": "BTC-USD"
  }
}
```

> Successful Response Example

```json
{
  "event": "subscribe",
  "arg": {
    "channel": "orders",
    "instType": "FUTURES",
    "uly": "BTC-USD"
  }
}
```

> Failure Response Example

```json
{
  "event": "error",
  "code": "60012",
  "msg": "Unrecognized request: {\"op\": \"subscribe\", \"argss\":[{ \"channel\" : \"orders\", \"instType\" : \"FUTURES\"}]}"
}
```

#### Response parameters

| Parameter  | Type   | Required | Description                                                                                       |
| :--------- | :----- | -------- | ------------------------------------------------------------------------------------------------- |
| event      | String | Yes      | Event, `subscribe` `unsubscribe` `errror`                                                         |
| `arg`      | Object | No       | Subscribed channel                                                                                |
| > channel  | String | Yes      | Channel name                                                                                      |
| > instType | String | Yes      | Instrument type<br />`SPOT `<br />`MARGIN`<br />` SWAP`<br />`FUTURES`<br />`OPTION ` <br />`ANY` |
| > uly      | String | No       | Underlying                                                                                        |
| > instId   | String | No       | Instrument ID                                                                                     |
| code       | String | No       | Error code                                                                                        |
| msg        | String | No       | Error message                                                                                     |

> Push Data Example: single

```json
{
  "arg": {
    "channel": "orders",
    "instType": "FUTURES",
    "instId": "BTC-USD-200329"
  },
  "data": [
    {
      "instType": "FUTURES",
      "instId": "BTC-USD-200329",
      "ccy": "BTC",
      "ordId": "123445",
      "clOrdId": "b1",
      "tag": "",
      "px": "999",
      "sz": "3",
      "ordType": "limit",
      "side": "buy",
      "posSide": "long",
      "tdMode": "cross",
      "fillSz": "0",
      "fillPx": "long",
      "tradeId": "0",
      "accFillSz": "323",
      "fillTime": "0",
      "state": "canceled",
      "avgPx": "0",
      "lever": "20",
      "tpTriggerPx": "0",
      "tpOrdPx": "20",
      "slTriggerPx": "0",
      "slOrdPx": "20",
      "feeCcy": "",
      "fee": "",
      "rebateCcy": "",
      "rebate": "",
      "pnl": "",
      "category": "",
      "uTime": "1597026383085",
      "cTime": "1597026383085",
      "reqId": "",
      "amendResult": "",
      "code": "0",
      "msg": ""
    }
  ]
}
```

> Push Data Example

```json
{
  "arg": {
    "channel": "orders",
    "instType": "FUTURES",
    "uly": "BTC-USD"
  },
  "data": [
    {
      "instType": "FUTURES",
      "instId": "BTC-USD-200329",
      "ccy": "BTC",
      "ordId": "123445",
      "clOrdId": "b1",
      "tag": "",
      "px": "999",
      "sz": "3",
      "ordType": "limit",
      "side": "buy",
      "posSide": "long",
      "tdMode": "cross",
      "fillSz": "0",
      "fillPx": "long",
      "tradeId": "0",
      "accFillSz": "323",
      "fillTime": "0",
      "state": "canceled",
      "avgPx": "0",
      "lever": "20",
      "tpTriggerPx": "0",
      "tpOrdPx": "20",
      "slTriggerPx": "0",
      "slOrdPx": "20",
      "feeCcy": "",
      "fee": "",
      "rebateCcy": "",
      "rebate": "",
      "pnl": "",
      "category": "",
      "uTime": "1597026383085",
      "cTime": "1597026383085",
      "reqId": "",
      "amendResult": "",
      "code": "0",
      "msg": ""
    },
    {
      "instType": "FUTURES",
      "instId": "BTC-USD-200829",
      "ccy": "BTC",
      "ordId": "123445",
      "clOrdId": "b1",
      "tag": "",
      "px": "999",
      "sz": "3",
      "ordType": "limit",
      "side": "buy",
      "posSide": "long",
      "tdMode": "cross",
      "fillSz": "0",
      "fillPx": "long",
      "tradeId": "0",
      "accFillSz": "323",
      "fillTime": "0",
      "state": "canceled",
      "avgPx": "0",
      "lever": "20",
      "tpTriggerPx": "0",
      "tpOrdPx": "20",
      "slTriggerPx": "0",
      "slOrdPx": "20",
      "feeCcy": "",
      "fee": "",
      "rebateCcy": "",
      "rebate": "",
      "pnl": "",
      "category": "",
      "uTime": "1597026383085",
      "cTime": "1597026383085",
      "reqId": "",
      "amendResult": "",
      "code": "0",
      "msg": ""
    }
  ]
}
```

#### Push data parameters

| Parameter     | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                               |
| :------------ | :----- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `arg`         | Object | Successfully subscribed channel                                                                                                                                                                                                                                                                                                                                                                                           |
| > channel     | String | Channel name                                                                                                                                                                                                                                                                                                                                                                                                              |
| > instType    | String | Instrument type                                                                                                                                                                                                                                                                                                                                                                                                           |
| > uly         | String | Underlying                                                                                                                                                                                                                                                                                                                                                                                                                |
| > instId      | String | Instrument ID                                                                                                                                                                                                                                                                                                                                                                                                             |
| `data`        | Array  | Subscribed data                                                                                                                                                                                                                                                                                                                                                                                                           |
| > instType    | String | Instrument type                                                                                                                                                                                                                                                                                                                                                                                                           |
| > instId      | String | Instrument ID                                                                                                                                                                                                                                                                                                                                                                                                             |
| > ccy         | String | Margin currency<br />Only applicable to cross `MARGIN` orders in `Single-currency margin`.                                                                                                                                                                                                                                                                                                                                |
| > ordId       | String | Order ID                                                                                                                                                                                                                                                                                                                                                                                                                  |
| > clOrdId     | String | Client-supplied order ID                                                                                                                                                                                                                                                                                                                                                                                                  |
| > tag         | String | Order tag                                                                                                                                                                                                                                                                                                                                                                                                                 |
| > px          | String | Order price                                                                                                                                                                                                                                                                                                                                                                                                               |
| > sz          | String | The original order quantity, `SPOT/MARGIN`, in the unit of currency; `FUTURES/SWAP/OPTION`, in the unit of contract                                                                                                                                                                                                                                                                                                       |
| > ordType     | String | Order type<br />`market`: market order<br />`limit`: limit order<br />`post_only`: Post-only order<br />`fok`: Fill-or-kill order<br />`ioc`: Immediate-or-cancel order                                                                                                                                                                                                                                                   |
| > side        | String | Order side, `buy` `sell`                                                                                                                                                                                                                                                                                                                                                                                                  |
| > posSide     | String | Position side <br />`net` <br />`long` or `short` Only applicable to `FUTURES/SWAP`                                                                                                                                                                                                                                                                                                                                       |
| > tdMode      | String | Trade mode, `cross`: cross `isolated`: isolated `cash`: cash                                                                                                                                                                                                                                                                                                                                                              |
| > fillPx      | String | Last filled price                                                                                                                                                                                                                                                                                                                                                                                                         |
| > tradeId     | String | Last trade ID                                                                                                                                                                                                                                                                                                                                                                                                             |
| > fillSz      | String | Last filled quantity                                                                                                                                                                                                                                                                                                                                                                                                      |
| > fillTime    | String | Last filled time                                                                                                                                                                                                                                                                                                                                                                                                          |
| > accFillSz   | String | Accumulated fill quantity                                                                                                                                                                                                                                                                                                                                                                                                 |
| > avgPx       | String | Average filled price. If none is filled, it will return `0`.                                                                                                                                                                                                                                                                                                                                                              |
| > state       | String | Order state <br />`canceled`<br />`live`<br />`partially_filled`<br />`filled`                                                                                                                                                                                                                                                                                                                                            |
| > lever       | String | Leverage, from `0.01` to `125`.<br />Only applicable to `MARGIN/FUTURES/SWAP`                                                                                                                                                                                                                                                                                                                                             |
| > tpTriggerPx | String | Take-profit trigger price, it must be between 0 and 1,000,000.                                                                                                                                                                                                                                                                                                                                                            |
| > tpOrdPx     | String | Take-profit order price, it must be between 0 and 1,000,000.                                                                                                                                                                                                                                                                                                                                                              |
| > slTriggerPx | String | Stop-loss trigger price, it must be between 0 and 1,000,000.                                                                                                                                                                                                                                                                                                                                                              |
| > slOrdPx     | String | Stop-loss order price, it must be between 0 and 1,000,000.                                                                                                                                                                                                                                                                                                                                                                |
| > feeCcy      | String | Fee currency<br />`SPOT/MARGIN`: If you buy, you will receive BTC; if you sell, you will receive USDT<br />`FUTURES/SWAP/OPTION` What is charged is the margin                                                                                                                                                                                                                                                            |
| > fee         | String | Fee, transaction fee charged by the platform.                                                                                                                                                                                                                                                                                                                                                                             |
| > rebateCcy   | String | Rebate currency, if there is no rebate, this field is "".                                                                                                                                                                                                                                                                                                                                                                 |
| > rebate      | String | Rebate amount, the reward of placing orders from the platform (rebate) given to user who has reached the specified trading level. If there is no rebate, this field is "".                                                                                                                                                                                                                                                |
| > pnl         | String | Profit and loss                                                                                                                                                                                                                                                                                                                                                                                                           |
| > category    | String | Category<br />`normal`<br />`twap`<br />`adl`<br />`full_liquidation`<br />`partial_liquidation`                                                                                                                                                                                                                                                                                                                          |
| > uTime       | String | Update time, Unix timestamp format in milliseconds, e.g. `1597026383085`                                                                                                                                                                                                                                                                                                                                                  |
| > cTime       | String | Creation time, Unix timestamp format in milliseconds, e.g. `1597026383085`                                                                                                                                                                                                                                                                                                                                                |
| > reqId       | String | Client-supplied request ID for order amendment. "" will be returned if there is no order amendment.                                                                                                                                                                                                                                                                                                                       |
| > amendResult | String | The result of amending the order<br />`-1`: failure<br />`0`: success<br />`1`: Automatic cancel (due to successful amendment) <br />When amending the order through API and the amendment failed, `-1` will be returned if `cxlOnFail` is set to `false`. Otherwise `1` will be returned if `cxlOnFail` is set to `true`. <br />When amending the order through Web/APP and the amendment failed, `-1` will be returned. |
| > code        | String | Error Code, the default is 0                                                                                                                                                                                                                                                                                                                                                                                              |
| > msg         | String | Error Message, The default is ""                                                                                                                                                                                                                                                                                                                                                                                          |

### Algo Orders Channel

Retrieve algo orders. Data will not be pushed when first subscribed. Data will only be pushed when triggered by events such as placing/canceling order.

> Request Example : single

```json
{
  "op": "subscribe",
  "args": [
    {
      "channel": "orders-algo",
      "instType": "FUTURES",
      "uly": "BTC-USD",
      "instId": "BTC-USD-200329"
    }
  ]
}
```

> Request Example

```json
{
  "op": "subscribe",
  "args": [
    {
      "channel": "orders-algo",
      "instType": "FUTURES",
      "uly": "BTC-USD"
    }
  ]
}
```

#### Request parameters

| Parameter  | Type   | Required | Description                                                                       |
| :--------- | :----- | -------- | --------------------------------------------------------------------------------- |
| op         | String | Yes      | Operation, `subscribe` `unsubscribe`                                              |
| `args`     | Array  | Yes      | List of subscribed channels                                                       |
| > channel  | String | Yes      | Channel name                                                                      |
| > instType | String | Yes      | Instrument type<br />`SPOT `<br />`MARGIN`<br />` SWAP`<br />`FUTURES`<br />`ANY` |
| > uly      | String | No       | Underlying                                                                        |
| > instId   | String | No       | Instrument ID                                                                     |

> Successful Response Example : single

```json
{
  "event": "subscribe",
  "arg": {
    "channel": "orders-algo",
    "instType": "FUTURES",
    "uly": "BTC-USD",
    "instId": "BTC-USD-200329"
  }
}
```

> Successful Response Example

```json
{
  "event": "subscribe",
  "arg": {
    "channel": "orders-algo",
    "instType": "FUTURES",
    "uly": "BTC-USD"
  }
}
```

> Failure Response Example

```json
{
  "event": "error",
  "code": "60012",
  "msg": "Unrecognized request: {\"op\": \"subscribe\", \"argss\":[{ \"channel\" : \"orders-algo\", \"instType\" : \"FUTURES\"}]}"
}
```

#### Response parameters

| Parameter  | Type   | Required | Description                                                                       |
| :--------- | :----- | -------- | --------------------------------------------------------------------------------- |
| event      | String | Yes      | Event, `subscribe` `unsubscribe` `errror`                                         |
| `arg`      | Object | No       | Subscribed channel                                                                |
| > channel  | String | Yes      | Channel name                                                                      |
| > instType | String | Yes      | Instrument type<br />`SPOT `<br />`MARGIN`<br />` SWAP`<br />`FUTURES`<br />`ANY` |
| > uly      | String | No       | Underlying                                                                        |
| > instId   | String | No       | Instrument ID                                                                     |
| code       | String | No       | Error code                                                                        |
| msg        | String | No       | Error message                                                                     |

> Push Data Example: single

```json
{
  "arg": {
    "channel": "orders-algo",
    "instType": "FUTURES",
    "instId": "BTC-USD-200329"
  },
  "data": [
    {
      "instType": "FUTURES",
      "instId": "BTC-USD-200329",
      "ordId": "123445",
      "ccy": "BTC",
      "algoId": "1234",
      "px": "999",
      "sz": "3",
      "ordType": "trigger",
      "side": "buy",
      "posSide": "long",
      "state": "live",
      "lever": "20",
      "tpTriggerPx": "",
      "tpOrdPx": "",
      "slTriggerPx": "",
      "triggerPx": "99",
      "ordPx": "12",
      "actualSz": "",
      "actualPx": "",
      "actualSide": "",
      "triggerTime": "1597026383085",
      "cTime": "1597026383000"
    }
  ]
}
```

> Push Data Example

```json
{
  "arg": {
    "channel": "orders-algo",
    "instType": "FUTURES",
    "uly": "BTC-USD"
  },
  "data": [
    {
      "instType": "FUTURES",
      "instId": "BTC-USD-200329",
      "ordId": "123445",
      "ccy": "BTC",
      "algoId": "1234",
      "px": "999",
      "sz": "3",
      "ordType": "trigger",
      "side": "buy",
      "posSide": "long",
      "state": "live",
      "lever": "20",
      "tpTriggerPx": "",
      "tpOrdPx": "",
      "slTriggerPx": "",
      "triggerPx": "99",
      "ordPx": "12",
      "actualSz": "",
      "actualPx": "",
      "actualSide": "",
      "triggerTime": "1597026383085",
      "cTime": "1597026383000"
    },
    {
      "instType": "FUTURES",
      "instId": "BTC-USD-200829",
      "ordId": "123445",
      "ccy": "BTC",
      "algoId": "1234",
      "px": "999",
      "sz": "3",
      "ordType": "trigger",
      "side": "buy",
      "posSide": "long",
      "state": "live",
      "lever": "20",
      "tpTriggerPx": "",
      "tpOrdPx": "",
      "slTriggerPx": "",
      "triggerPx": "99",
      "ordPx": "12",
      "actualSz": "",
      "actualPx": "",
      "actualSide": "",
      "triggerTime": "1597026383085",
      "cTime": "1597026383000"
    }
  ]
}
```

#### Response parameters when data is pushed.

| **Parameter** | **Type** | **Description**                                                                                                                        |
| :------------ | :------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| `arg`         | Object   | Successfully subscribed channel                                                                                                        |
| > channel     | String   | Channel name                                                                                                                           |
| > instType    | String   | Instrument type                                                                                                                        |
| > uly         | String   | Underlying                                                                                                                             |
| > instId      | String   | Instrument ID                                                                                                                          |
| `data`        | Array    | Subscribed data                                                                                                                        |
| > instType    | String   | Instrument type                                                                                                                        |
| > instId      | String   | Instrument ID                                                                                                                          |
| > ccy         | String   | Margin currency<br />Only applicable to cross `MARGIN` orders in `Single-currency margin`.                                             |
| > ordId       | String   | Order ID, the order ID associated with the algo order.                                                                                 |
| > algoId      | String   | Algo ID                                                                                                                                |
| > sz          | String   | Quantity to buy or sell. `SPOT/MARGIN`: in the unit of currency. `FUTURES/SWAP/OPTION`: in the unit of contract.                       |
| > ordType     | String   | Order type<br />`conditional`: One-way stop order <br />`oco`: One-cancels-the-other order<br />`trigger`: Trigger order               |
| > side        | String   | Order side, `buy` `sell`                                                                                                               |
| > posSide     | String   | Position side<br />`net` <br />`long` or `short` Only applicable to `FUTURES/SWAP`                                                     |
| > tdMode      | String   | Trade mode, `cross`: cross `isolated`: isolated `cash`: cash                                                                           |
| > lever       | String   | Leverage, from `0.01` to `125`.<br />Only applicable to `MARGIN/FUTURES/SWAP`                                                          |
| > state       | String   | Order status <br /> `live`: to be effective<br /> `effective`: effective<br /> `canceled`: canceled<br /> `order_failed`: order failed |
| > tpTriggerPx | String   | Take-profit trigger price. It must be between 0 and 1,000,000.                                                                         |
| > tpOrdPx     | String   | Take-profit order price. It must be between 0 and 1,000,000.                                                                           |
| > slTriggerPx | String   | Stop-loss trigger price. It must be between 0 and 1,000,000.                                                                           |
| > slOrdPx     | String   | Stop-loss order price. It must be between 0 and 1,000,000.                                                                             |
| > triggerPx   | String   | Trigger price                                                                                                                          |
| > ordPx       | String   | Order price                                                                                                                            |
| > actualSz    | String   | Actual order quantity                                                                                                                  |
| > actualPx    | String   | Actual order price                                                                                                                     |
| > actualSide  | String   | Actual trigger side                                                                                                                    |
| > triggerTime | String   | Trigger time, Unix timestamp format in milliseconds, e.g. `1597026383085`                                                              |
| > cTime       | String   | Creation time, Unix timestamp format in milliseconds, e.g. `1597026383085`                                                             |

## Trade

The `WebSocket Trade` APIs require authentication.

### Place Order

You can place an order only if you have sufficient funds.

#### Rate Limit: 60 requests per 2 seconds

> Request Example

```json
{
  "id": "1512",
  "op": "order",
  "args": [
    {
      "side": "buy",
      "instId": "BTC-USDT",
      "tdMode": "isolated",
      "ordType": "market",
      "sz": "1"
    }
  ]
}
```

#### Request Parameters

| Parameter    | Type    | Required | Description                                                                                                                                                                                                                                           |
| :----------- | :------ | :------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id           | String  | Yes      | Unique identifier of the message <br />Provided by client. It will be returned in response message for identifying the corresponding request.<br />A combination of case-sensitive alphanumerics, all numbers, or all letters of up to 32 characters. |
| op           | String  | Yes      | Operation, e.g. `order`                                                                                                                                                                                                                               |
| args         | Array   | Yes      | Request parameters                                                                                                                                                                                                                                    |
| > instId     | String  | Yes      | Instrument ID,e.g. `BTC-USD-190927-5000-C`                                                                                                                                                                                                            |
| > tdMode     | String  | Yes      | Trade mode<br /> Margin mode `isolated` `cross` <br /> Non-Margin mode `cash`                                                                                                                                                                         |
| > ccy        | String  | No       | Margin currency<br />Only applicable to `cross` `MARGIN` orders in `Single-currency margin`.                                                                                                                                                          |
| > clOrdId    | String  | No       | Client-supplied order ID<br />A combination of case-sensitive alphanumerics beginning with a letter, or alphabets of up to 32 characters.                                                                                                             |
| > tag        | String  | No       | Order tag<br />A combination of case-sensitive alphanumerics, all numbers, or all letters of up to 8 characters.                                                                                                                                      |
| > side       | String  | Yes      | Order side, `buy` `sell`                                                                                                                                                                                                                              |
| > posSide    | String  | No       | Position side <br />The default is `net` in the `net` mode<br />It is required in the `long/short` mode, and can only be `long` or `short`.<br />Only applicable to `FUTURES/SWAP`.                                                                   |
| > ordType    | String  | Yes      | Order type <br /> `market` <br /> `limit`<br /> `post_only` <br /> `fok` <br /> `ioc`                                                                                                                                                                 |
| > sz         | String  | Yes      | Quantity to buy or sell.                                                                                                                                                                                                                              |
| > px         | String  | No       | Price<br />Only applicable to `limit` order.                                                                                                                                                                                                          |
| > reduceOnly | Boolean | No       | Whether to reduce positions only, `true` `false`, and the default is `false`. <br />Only applicable to `MARGIN`.                                                                                                                                      |

> ##### Successful Response Example

```json
{
  "id": "1512",
  "op": "order",
  "data": [
    {
      "clOrdId": "",
      "ordId": "12345689",
      "tag": "",
      "sCode": "0",
      "sMsg": ""
    }
  ],
  "code": "0",
  "msg": ""
}
```

> Failure Response Example

```json
{
  "id": "1512",
  "op": "order",
  "data": [
    {
      "clOrdId": "",
      "ordId": "",
      "tag": "",
      "sCode": "5XXXX",
      "sMsg": "not exist"
    }
  ],
  "code": "1",
  "msg": ""
}
```

> Example Response When Format Error

```json
{
  "id": "1512",
  "op": "order",
  "data": [],
  "code": "60013",
  "msg": "Invalid args"
}
```

#### Response Parameters

| Parameter | Type   | Description                        |
| :-------- | :----- | :--------------------------------- |
| id        | String | Unique identifier of the message   |
| op        | String | Operation                          |
| code      | String | Error Code                         |
| msg       | String | Error message                      |
| data      | Array  | Data                               |
| > ordId   | String | Order ID                           |
| > clOrdId | String | Client-supplied order ID           |
| > tag     | String | Order tag                          |
| > sCode   | String | Order status code, 0 means success |
| > sMsg    | String | Order status message               |

<aside class="notice">
tdMode<br>
Trade Mode, when placing an order, you need to specify the trade mode.<br>
<strong>Simple:</strong><br>
- SPOT and OPTION buyer: cash<br>
<strong>Single-currency margin account:</strong><br>
- Isolated MARGIN: isolated<br>
- Cross MARGIN: cross<br>
- Cross SPOT: cash<br>
- Cross FUTURES/SWAP/OPTION: cross<br>
- Isolated FUTURES/SWAP/OPTION: isolated<br>
<strong>Multi-currency margin account:</strong><br>
- Isolated MARGIN: isolated<br>
- Cross SPOT: cross<br>
- Cross FUTURES/SWAP/OPTION: cross
- Isolated FUTURES/SWAP/OPTION: isolated
</aside>

<aside class="notice">
clOrdId<br>
clOrdId is a user-defined unique ID used to identify the order. It will be included in the response parameters if you fill it in in an order-placement request, and can be used as a request parameter to the endpoints to query, cancel and amend orders.<br />
The format of clOrdId must be a combination of case-sensitive alphanumerics beginning with a letter, or alphabets of up to 32 characters, and must not duplicate the clOrdIds of other pending orders.
</aside>

<aside class="notice">
posSide<br>
Position side, this parameter is not required in <strong>net</strong> mode. If you fill it in, you can fill <strong>net</strong> only.<br>
In <strong>long/short</strong> mode, it is required, and can only be <strong>long</strong> or <strong>short</strong>.<br>
In <strong>long/short</strong> mode, <strong>side</strong> and <strong>posSide</strong> need to be combined to use:<br>
Open long: buy and open long (side: fill in buy; posSide: fill in long)<br>
Open short: sell and open short (side: fill in sell; posSide: fill in short)<br>
Close long: sell and close long (side: fill in sell; posSide: fill in long)<br>
Close short: buy and close short (side: fill in buy; posSide: fill in short)<br>
</aside>

<aside class="notice">
ordType<br />
Order type. When creating a new order, you must specify the order type. The order type you specify will affect: 1) what order parameters are required, and 2) how the matching system executes your order. The following are valid order types:<br />
Limit: Limit order, which requires specified sz and px.<br />
Market: Market order<br />
Post_only: Post-only order, which will only be a maker at the moment the order is placed. If any part of the order is filled by the current pending order, the order will be canceled.<br />
Fok: Fill or kill order. If the order cannot be fully filled, the order will be canceled.<br />
Ioc: Immediate or cancel order. Immediately execute the transaction at the order price, cancel the remaining uncompleted quantity of the order, and the order quantity will not be displayed in the order book.

</aside>

<aside class="notice">
sz<br>
The number of transactions indicates the quantity to be bought or sold.<br />
For SPOT/MARGIN bought and sold at a limit price, it refers to the amount of trading currency.<br />
For SPOT/MARGIN bought at a market price, it refers to the amount of quoted currency.<br />
For SPOT/MARGIN sold at a market price, it refers to the amount of trading currency.<br />
For FUTURES/SWAP/OPTION buying and selling, it refers to the number of contracts.
</aside>

<aside class="notice">
reduceOnly<br>
When placing an order with this parameter set to true, it means that the order is considered reduce-only, which is intended to only reduce a current position.
</aside>

### Place Multiple Orders

Place orders in a batch. Maximum 20 orders can be placed at a time

#### Rate Limit: 300 requests per 2 seconds

> Request Example

```json
{
  "id": "1513",
  "op": "batch-orders",
  "args": [
    {
      "side": "buy",
      "instId": "BTC-USDT",
      "tdMode": "isolated",
      "ordType": "limit",
      "sz": "1"
    },
    {
      "side": "buy",
      "instId": "BTC-USD-200925",
      "tdMode": "isolated",
      "ordType": "limit",
      "sz": "1"
    }
  ]
}
```

#### Request Parameters

| Parameter    | Type    | Required | Description                                                                                                                                                                                                                                           |
| :----------- | :------ | :------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id           | String  | Yes      | Unique identifier of the message <br />Provided by client. It will be returned in response message for identifying the corresponding request.<br />A combination of case-sensitive alphanumerics, all numbers, or all letters of up to 32 characters. |
| op           | String  | Yes      | Operation, e.g. `batch-orders`                                                                                                                                                                                                                        |
| args         | Array   | Yes      | Request Parameters                                                                                                                                                                                                                                    |
| > instId     | String  | Yes      | Instrument ID, e.g. `BTC-USD-190927-5000-C`                                                                                                                                                                                                           |
| > tdMode     | String  | Yes      | Trade mode<br /> Margin mode `isolated` `cross` <br /> Non-Margin mode `cash`                                                                                                                                                                         |
| > ccy        | String  | No       | Margin currency<br />Only applicable to `cross` `MARGIN` orders in `Single-currency margin`.                                                                                                                                                          |
| > clOrdId    | String  | No       | Client-supplied order ID<br />A combination of case-sensitive alphanumerics beginning with a letter, or alphabets of up to 32 characters.                                                                                                             |
| > tag        | String  | No       | Order tag<br />A combination of case-sensitive alphanumerics, all numbers, or all letters of up to 8 characters.                                                                                                                                      |
| > side       | String  | Yes      | Order side, `buy` `sell`                                                                                                                                                                                                                              |
| > posSide    | String  | No       | Position side <br />The default `net` in the `net` mode<br />It is required in the `long/short` mode, and only be `long` or `short`.<br />Only applicable to `FUTURES/SWAP`.                                                                          |
| > ordType    | String  | Yes      | Order type <br /> `market` <br /> `limit`<br /> `post_only` <br /> `fok` <br /> `ioc`                                                                                                                                                                 |
| > sz         | String  | Yes      | The number of transactions indicates the quantity to be bought or sold.                                                                                                                                                                               |
| > px         | String  | No       | Price<br />Only applicable to `limit` order.                                                                                                                                                                                                          |
| > reduceOnly | Boolean | No       | Whether to reduce positions only, `true` `false`, and the default is `false`. <br />Only applicable to `MARGIN`.                                                                                                                                      |

> Example Response When All Succeed

```json
{
  "id": "1513",
  "op": "batch-orders",
  "data": [
    {
      "clOrdId": "",
      "ordId": "12345689",
      "tag": "",
      "sCode": "0",
      "sMsg": ""
    },
    {
      "clOrdId": "",
      "ordId": "12344",
      "tag": "",
      "sCode": "0",
      "sMsg": ""
    }
  ],
  "code": "0",
  "msg": ""
}
```

> Example Response When Partially Successful

```json
{
  "id": "1513",
  "op": "batch-orders",
  "data": [
    {
      "clOrdId": "",
      "ordId": "12345689",
      "tag": "",
      "sCode": "0",
      "sMsg": ""
    },
    {
      "clOrdId": "",
      "ordId": "",
      "tag": "",
      "sCode": "5XXXX",
      "sMsg": "Insufficient margin"
    }
  ],
  "code": "2",
  "msg": ""
}
```

> Example Response When All Failed

```json
{
  "id": "1513",
  "op": "batch-orders",
  "data": [
    {
      "clOrdId": "oktswap6",
      "ordId": "",
      "tag": "",
      "sCode": "5XXXX",
      "sMsg": "Insufficient margin"
    },
    {
      "clOrdId": "oktswap7",
      "ordId": "",
      "tag": "",
      "sCode": "5XXXX",
      "sMsg": "Insufficient margin"
    }
  ],
  "code": "1",
  "msg": ""
}
```

> Example Response When Format Error

```json
{
  "id": "1513",
  "op": "batch-orders",
  "data": [],
  "code": "60013",
  "msg": "Invalid args"
}
```

#### Response Parameters

| Parameter | Type   | Description                        |
| :-------- | :----- | :--------------------------------- |
| id        | String | Unique identifier of the message   |
| op        | String | Operation                          |
| code      | String | Error Code                         |
| msg       | String | Error message                      |
| data      | Array  | Data                               |
| > ordId   | String | Order ID                           |
| > clOrdId | String | Client-supplied order ID           |
| > tag     | String | Order tag                          |
| > sCode   | String | Order status code, 0 means success |
| > sMsg    | String | Order status message               |

### Cancel Order

Cancel an incomplete order

#### Rate Limit: 60 requests per 2 seconds

> Request Example

```json
{
  "id": "1514",
  "op": "cancel-order",
  "args": [
    {
      "instId": "BTC-USDT-200920",
      "ordId": "2510789768709120"
    }
  ]
}
```

#### Request Parameters

| Parameter | Type   | Required | Description                                                                                                                                                                                                                                           |
| :-------- | :----- | -------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id        | String | Yes      | Unique identifier of the message <br />Provided by client. It will be returned in response message for identifying the corresponding request.<br />A combination of case-sensitive alphanumerics, all numbers, or all letters of up to 32 characters. |
| op        | String | Yes      | Operation, e.g. `cancel-order`                                                                                                                                                                                                                        |
| args      | Array  | Yes      | Request Parameters                                                                                                                                                                                                                                    |
| > instId  | String | Yes      | Instrument ID                                                                                                                                                                                                                                         |
| > ordId   | String | Optional | Order ID<br />Either `ordId` or `clOrdId` is required, if both are passed, ordId will be used                                                                                                                                                         |
| > clOrdId | String | Optional | Client-supplied order ID<br />Start with a letter, 1 to 32 letters and numbers                                                                                                                                                                        |

> Successful Response Example

```json
{
  "id": "1514",
  "op": "cancel-order",
  "data": [
    {
      "clOrdId": "",
      "ordId": "2510789768709120",
      "sCode": "0",
      "sMsg": ""
    }
  ],
  "code": "0",
  "msg": ""
}
```

> Failure Response Example

```json
{
  "id": "1514",
  "op": "cancel-order",
  "data": [
    {
      "clOrdId": "",
      "ordId": "2510789768709120",
      "sCode": "5XXXX",
      "sMsg": "Order not exist"
    }
  ],
  "code": "1",
  "msg": ""
}
```

> Example Response When Format Error

```json
{
  "id": "1514",
  "op": "cancel-order",
  "data": [],
  "code": "60013",
  "msg": "Invalid args"
}
```

#### Response Parameters

| Parameter | Type   | Description                        |
| :-------- | :----- | :--------------------------------- |
| id        | String | Unique identifier of the message   |
| op        | String | Operation                          |
| code      | String | Error Code                         |
| msg       | String | Error message                      |
| data      | Array  | Data                               |
| > ordId   | String | Order ID                           |
| > clOrdId | String | Client-supplied order ID           |
| > sCode   | String | Order status code, 0 means success |
| > sMsg    | String | Order status message               |

### Cancel Multiple Orders

Cancel incomplete orders in batches. Maximum 20 orders can be canceled at a time.

#### Rate Limit: 300 requests per 2 seconds

> Request Example

```json
{
  "id": "1515",
  "op": "batch-cancel-orders",
  "args": [
    {
      "instId": "BTC-USDT-200920",
      "ordId": "2517748157541376"
    },
    {
      "instId": "LTC-USDT-200920",
      "ordId": "2517748155771904"
    }
  ]
}
```

#### Request Parameters

| Parameter | Type   | Required | Description                                                                                                                                                                                                                                           |
| :-------- | :----- | -------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id        | String | Yes      | Unique identifier of the message <br />Provided by client. It will be returned in response message for identifying the corresponding request.<br />A combination of case-sensitive alphanumerics, all numbers, or all letters of up to 32 characters. |
| op        | String | Yes      | Operation, e.g. `batch-cancel-orders`                                                                                                                                                                                                                 |
| args      | Array  | Yes      | Request Parameters                                                                                                                                                                                                                                    |
| > instId  | String | Yes      | Instrument ID                                                                                                                                                                                                                                         |
| > ordId   | String | Optional | Order ID<br />Either `ordId` or `clOrdId` is required, if both are passed, ordId will be used                                                                                                                                                         |
| > clOrdId | String | Optional | Client-supplied order ID<br />Start with a letter, 1 to 32 letters and numbers                                                                                                                                                                        |

> Example Response When All Succeed

```json
{
  "id": "1515",
  "op": "batch-cancel-orders",
  "data": [
    {
      "clOrdId": "oktswap6",
      "ordId": "2517748157541376",
      "sCode": "0",
      "sMsg": ""
    },
    {
      "clOrdId": "oktswap7",
      "ordId": "2517748155771904",
      "sCode": "0",
      "sMsg": ""
    }
  ],
  "code": "0",
  "msg": ""
}
```

> Example Response When partially successfully

```json
{
  "id": "1515",
  "op": "batch-cancel-orders",
  "data": [
    {
      "clOrdId": "oktswap6",
      "ordId": "2517748157541376",
      "sCode": "0",
      "sMsg": ""
    },
    {
      "clOrdId": "oktswap7",
      "ordId": "2517748155771904",
      "sCode": "5XXXX",
      "sMsg": "order not exist"
    }
  ],
  "code": "2",
  "msg": ""
}
```

> Example Response When All Failed

```json
{
  "id": "1515",
  "op": "batch-cancel-orders",
  "data": [
    {
      "clOrdId": "oktswap6",
      "ordId": "2517748157541376",
      "sCode": "5XXXX",
      "sMsg": "order not exist"
    },
    {
      "clOrdId": "oktswap7",
      "ordId": "2517748155771904",
      "sCode": "5XXXX",
      "sMsg": "order not exist"
    }
  ],
  "code": "1",
  "msg": ""
}
```

> Example Response When Format Error

```json
{
  "id": "1515",
  "op": "batch-cancel-orders",
  "data": [],
  "code": "60013",
  "msg": "Invalid args"
}
```

#### Response Parameters

| Parameter | Type   | Description                        |
| :-------- | :----- | :--------------------------------- |
| id        | String | Unique identifier of the message   |
| op        | String | Operation                          |
| code      | String | Error Code                         |
| msg       | String | Error message                      |
| data      | Array  | Data                               |
| > ordId   | String | Order ID                           |
| > clOrdId | String | Client-supplied order ID           |
| > sCode   | String | Order status code, 0 means success |
| > sMsg    | String | Order status message               |

### Amend Order

Amend an incomplete order.

#### Rate Limit: 60 requests per 2 seconds

> Request Example

```json
{
  "id": "1512",
  "op": "amend-order",
  "args": [
    {
      "instId": "BTC-USDT-200920",
      "ordId": "2510789768709120",
      "newSz": "2"
    }
  ]
}
```

#### Request Parameters

| Parameter   | Type    | Required | Description                                                                                                                                                                                                                                           |
| :---------- | :------ | -------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id          | String  | Yes      | Unique identifier of the message <br />Provided by client. It will be returned in response message for identifying the corresponding request.<br />A combination of case-sensitive alphanumerics, all numbers, or all letters of up to 32 characters. |
| op          | String  | Yes      | Operation, e.g. `amend-order`                                                                                                                                                                                                                         |
| args        | Array   | Yes      | Request Parameters                                                                                                                                                                                                                                    |
| > instId    | String  | Yes      | Instrument ID                                                                                                                                                                                                                                         |
| > cxlOnFail | Boolean | No       | Whether the order needs to be automatically canceled when amendment fails. <br />`false` or `true`, the default is `false`.                                                                                                                           |
| > ordId     | String  | Optional | Order ID<br />Either `ordId` or `clOrdId` is required, if both are passed, `ordId` will be used.                                                                                                                                                      |
| > clOrdId   | String  | Optional | Client-supplied order ID                                                                                                                                                                                                                              |
| > reqId     | String  | No       | Client-supplied request ID<br />A combination of case-sensitive alphanumerics, all numbers, or all letters of up to 32 characters.                                                                                                                    |
| > newSz     | String  | Optional | New quantity after amendment. Either `newSz` or `newPx` is required. When amending a partially-filled order, the `newSz` should include the amount that has been filled.                                                                              |
| > newPx     | String  | Optional | New price after amendment.                                                                                                                                                                                                                            |

> Successful Response Example

```json
{
  "id": "1512",
  "op": "amend-order",
  "data": [
    {
      "clOrdId": "",
      "ordId": "2510789768709120",
      "reqId": "b12344",
      "sCode": "0",
      "sMsg": ""
    }
  ],
  "code": "0",
  "msg": ""
}
```

> Failure Response Example

```json
{
  "id": "1512",
  "op": "amend-order",
  "data": [
    {
      "clOrdId": "",
      "ordId": "2510789768709120",
      "reqId": "b12344",
      "sCode": "5XXXX",
      "sMsg": "order not exist"
    }
  ],
  "code": "1",
  "msg": ""
}
```

> Example Response When Format Error

```json
{
  "id": "1512",
  "op": "amend-order",
  "data": [],
  "code": "60013",
  "msg": "Invalid args"
}
```

#### Response Parameters

| Parameter | Type   | Description                        |
| :-------- | :----- | :--------------------------------- |
| id        | String | Unique identifier of the message   |
| op        | String | Operation                          |
| code      | String | Error Code                         |
| msg       | String | Error message                      |
| data      | Array  | Data                               |
| > ordId   | String | Order ID                           |
| > clOrdId | String | Client-supplied order ID           |
| > reqId   | String | Client-supplied request ID         |
| > sCode   | String | Order status code, 0 means success |
| > sMsg    | String | Order status message               |

<aside class="notice">
newSz<br />
If the new quantity of the order is less than or equal to the filled quantity when you are amending a partially-filled order, the order status will be changed to filled.
</aside>

### Amend Multiple Orders

Amend incomplete orders in batches. Maximum 20 orders can be amended at a time.

#### Rate Limit: 300 requests per 2 seconds

> Request Example

```json
{
  "id": "1513",
  "op": "batch-amend-orders",
  "args": [
    {
      "instId": "BTC-USDT-200920",
      "ordId": "12345689",
      "newSz": "2"
    },
    {
      "instId": "BTC-USDT-200920",
      "ordId": "12344",
      "newSz": "2"
    }
  ]
}
```

#### Request Parameters

| Parameter   | Type    | Required | Description                                                                                                                                                                                                                                           |
| :---------- | :------ | -------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id          | String  | Yes      | Unique identifier of the message <br />Provided by client. It will be returned in response message for identifying the corresponding request.<br />A combination of case-sensitive alphanumerics, all numbers, or all letters of up to 32 characters. |
| op          | String  | Yes      | Operation, e.g. `batch-amend-orders`                                                                                                                                                                                                                  |
| args        | Array   | Yes      | Request Parameters                                                                                                                                                                                                                                    |
| > instId    | String  | Yes      | Instrument ID                                                                                                                                                                                                                                         |
| > cxlOnFail | Boolean | No       | Whether the order needs to be automatically cancelled when the order amendment fails <br />`false` ` true`, the default is `false`                                                                                                                    |
| > ordId     | String  | Optional | Order ID<br />Either `ordId` or `clOrdId` is required, if both are passed, `ordId` will be used.                                                                                                                                                      |
| > clOrdId   | String  | Optional | Client-supplied order ID                                                                                                                                                                                                                              |
| > reqId     | String  | No       | Client-supplied request ID<br />A combination of case-sensitive alphanumerics, all numbers, or all letters of up to 32 characters.                                                                                                                    |
| > newSz     | String  | Optional | New quantity after amendment. Either `newSz` or `newPx` is required. When amending a partially-filled order, the `newSz` should include the amount that has been filled.                                                                              |
| > newPx     | String  | Optional | New price after amendment.                                                                                                                                                                                                                            |

> Example Response When All Succeed

```json
{
  "id": "1513",
  "op": "batch-amend-orders",
  "data": [
    {
      "clOrdId": "oktswap6",
      "ordId": "12345689",
      "reqId": "b12344",
      "sCode": "0",
      "sMsg": ""
    },
    {
      "clOrdId": "oktswap7",
      "ordId": "12344",
      "reqId": "b12344",
      "sCode": "0",
      "sMsg": ""
    }
  ],
  "code": "0",
  "msg": ""
}
```

> Example Response When All Failed

```json
{
  "id": "1513",
  "op": "batch-amend-orders",
  "data": [
    {
      "clOrdId": "",
      "ordId": "12345689",
      "reqId": "b12344",
      "sCode": "5XXXX",
      "sMsg": "order not exist"
    },
    {
      "clOrdId": "oktswap7",
      "ordId": "",
      "reqId": "b12344",
      "sCode": "5XXXX",
      "sMsg": "order not exist"
    }
  ],
  "code": "1",
  "msg": ""
}
```

> Example Response When Partially Successful

```json
{
  "id": "1513",
  "op": "batch-amend-orders",
  "data": [
    {
      "clOrdId": "",
      "ordId": "12345689",
      "reqId": "b12344",
      "sCode": "0",
      "sMsg": ""
    },
    {
      "clOrdId": "oktswap7",
      "ordId": "",
      "reqId": "b12344",
      "sCode": "5XXXX",
      "sMsg": "order not exist"
    }
  ],
  "code": "2",
  "msg": ""
}
```

> Example Response When Format Error

```json
{
  "id": "1513",
  "op": "batch-amend-orders",
  "data": [],
  "code": "60013",
  "msg": "Invalid args"
}
```

#### Response Parameters

| Parameter | Type   | Description                                                                                                         |
| :-------- | :----- | :------------------------------------------------------------------------------------------------------------------ |
| id        | String | Unique identifier of the message                                                                                    |
| op        | String | Operation                                                                                                           |
| code      | String | Error Code                                                                                                          |
| msg       | String | Error message                                                                                                       |
| data      | Array  | Data                                                                                                                |
| > ordId   | String | Order ID                                                                                                            |
| > clOrdId | String | Client-supplied order ID                                                                                            |
| > reqId   | String | Client-supplied request ID<br />If the user provides reqId in the request, the corresponding reqId will be returned |
| > sCode   | String | Order status code, 0 means success                                                                                  |
| > sMsg    | String | Order status message                                                                                                |

<aside class="notice">
newSz<br />
If the new quantity of the order is less than or equal to the filled quantity when you are amending a partially-filled order, the order status will be changed to filled.
</aside>
