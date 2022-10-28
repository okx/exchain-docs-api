## Get node Info

Get Information about the connected node

#### Rate Limit: 6 requests per second

#### HTTP Request

`GET okexchain/v1/node_info`

> Request Example

```wiki
https://exchainrpc.okex.org/okexchain/v1/node_info
```

#### Request Parameters

None
> Example Response

```json
{
	"node_info": {
		"protocol_version": {
			"p2p": "7",
			"block": "10",
			"app": "0"
		},
		"id": "4466b04f1cf2b55bc8e4225eef72b487a37e3c4f",
		"listen_addr": "tcp://10.1.19.206:20256",
		"network": "exchain-66",
		"version": "0.33.9",
		"channels": "4020212223303800",
		"moniker": "2061",
		"other": {
			"tx_index": "on",
			"rpc_address": "tcp://0.0.0.0:26657"
		}
	},
	"application_version": {
		"name": "exchain",
		"server_name": "exchaind",
		"client_name": "exchaincli",
		"version": "v0.18.6",
		"commit": "2ccd81b14f146a5afd3a52aa9f890cf88988f2a5",
		"build_tags": "netgo",
		"go": "go version go1.16.4 linux/amd64",
		"build_deps": ["github.com/99designs/keyring@v1.1.6", "github.com/ChainSafe/go-schnorrkel@v0.0.0-20200405005733-88cbf1b4c40d", "github.com/Comcast/pulsar-client-go@v0.1.1", "github.com/VictoriaMetrics/fastcache@v1.5.7", "github.com/Workiva/go-datastructures@v1.0.52", "github.com/aliyun/alibaba-cloud-sdk-go@v1.61.18", "github.com/aliyun/aliyun-oss-go-sdk@v2.1.6+incompatible", "github.com/aristanetworks/goarista@v0.0.0-20200331225509-2cc472e8fbd6", "github.com/bartekn/go-bip39@v0.0.0-20171116152956-a05967ea095d", "github.com/beorn7/perks@v1.0.1", "github.com/bgentry/speakeasy@v0.1.0", "github.com/btcsuite/btcd@v0.21.0-beta", "github.com/btcsuite/btcutil@v1.0.2", "github.com/buger/jsonparser@v0.0.0-20181115193947-bf1c66bbce23", "github.com/cespare/xxhash/v2@v2.1.1", "github.com/cosmos/cosmos-sdk@v0.39.2 =\u003e github.com/okex/cosmos-sdk@v0.39.2-exchain5", "github.com/cosmos/go-bip39@v0.0.0-20180819234021-555e2067c45d", "github.com/davecgh/go-spew@v1.1.1", "github.com/deckarep/golang-set@v1.7.1", "github.com/dvsekhvalnov/jose2go@v0.0.0-20200901110807-248326c1351b", "github.com/enigmampc/btcutil@v1.0.3-0.20200723161021-e2fb6adb2a25", "github.com/ethereum/go-ethereum@v1.9.25", "github.com/fsnotify/fsnotify@v1.4.9", "github.com/garyburd/redigo@v1.6.2", "github.com/go-errors/errors@v1.0.1", "github.com/go-kit/kit@v0.10.0", "github.com/go-logfmt/logfmt@v0.5.0", "github.com/go-redis/redis@v6.15.9+incompatible", "github.com/go-sql-driver/mysql@v1.5.0", "github.com/go-stack/stack@v1.8.0", "github.com/godbus/dbus@v0.0.0-20190726142602-4481cbc300e2", "github.com/gogo/protobuf@v1.3.1", "github.com/golang/protobuf@v1.4.2", "github.com/golang/snappy@v0.0.3-0.20201103224600-674baa8c7fc3", "github.com/google/btree@v1.0.0", "github.com/google/uuid@v1.1.1", "github.com/gorilla/handlers@v1.4.2", "github.com/gorilla/mux@v1.8.0", "github.com/gorilla/websocket@v1.4.2", "github.com/gsterjov/go-libsecret@v0.0.0-20161001094733-a6f4afe4910c", "github.com/gtank/merlin@v0.1.1", "github.com/gtank/ristretto255@v0.1.2", "github.com/hashicorp/golang-lru@v0.5.5-0.20210104140557-80c98217689d", "github.com/hashicorp/hcl@v1.0.0", "github.com/holiman/uint256@v1.1.1", "github.com/jinzhu/gorm@v1.9.16", "github.com/jinzhu/inflection@v1.0.0", "github.com/jmespath/go-jmespath@v0.0.0-20180206201540-c2b33e8439af", "github.com/json-iterator/go@v1.1.9", "github.com/lestrrat/go-file-rotatelogs@v0.0.0-20180223000712-d3151e2a480f", "github.com/lestrrat/go-strftime@v0.0.0-20180220042222-ba3bf9c1d042", "github.com/libp2p/go-buffer-pool@v0.0.2", "github.com/magiconair/properties@v1.8.1", "github.com/mattn/go-isatty@v0.0.12", "github.com/mattn/go-runewidth@v0.0.4", "github.com/mattn/go-sqlite3@v1.14.0", "github.com/matttproud/golang_protobuf_extensions@v1.0.1", "github.com/mimoo/StrobeGo@v0.0.0-20181016162300-f8f6d4d2b643", "github.com/minio/highwayhash@v1.0.0", "github.com/mitchellh/go-homedir@v1.1.0", "github.com/mitchellh/mapstructure@v1.1.2", "github.com/modern-go/concurrent@v0.0.0-20180306012644-bacd9c7ef1dd", "github.com/modern-go/reflect2@v1.0.1", "github.com/mtibben/percent@v0.2.1", "github.com/nacos-group/nacos-sdk-go@v1.0.0", "github.com/olekukonko/tablewriter@v0.0.2-0.20190409134802-7e037d187b0c", "github.com/pborman/uuid@v1.2.0", "github.com/pelletier/go-toml@v1.6.0", "github.com/pkg/errors@v0.9.1", "github.com/pmezard/go-difflib@v1.0.0", "github.com/prometheus/client_golang@v1.5.1", "github.com/prometheus/client_model@v0.2.0", "github.com/prometheus/common@v0.9.1", "github.com/prometheus/procfs@v0.0.10", "github.com/prometheus/tsdb@v0.9.1", "github.com/rakyll/statik@v0.1.6", "github.com/rcrowley/go-metrics@v0.0.0-20200313005456-10cdbea86bc0", "github.com/rjeczalik/notify@v0.9.2", "github.com/rs/cors@v1.7.0", "github.com/segmentio/kafka-go@v0.2.2", "github.com/shirou/gopsutil@v2.20.9+incompatible", "github.com/shopspring/decimal@v1.2.0", "github.com/spf13/afero@v1.2.2", "github.com/spf13/cast@v1.3.0", "github.com/spf13/cobra@v1.1.1", "github.com/spf13/jwalterweatherman@v1.1.0", "github.com/spf13/pflag@v1.0.5", "github.com/spf13/viper@v1.7.1", "github.com/status-im/keycard-go@v0.0.0-20190424133014-d95853db0f48", "github.com/steakknife/bloomfilter@v0.0.0-20180922174646-6819c0d2a570", "github.com/steakknife/hamming@v0.0.0-20180906055917-c99c65617cd3", "github.com/stretchr/testify@v1.7.0", "github.com/subosito/gotenv@v1.2.0", "github.com/syndtr/goleveldb@v1.0.1-0.20200815110645-5c35d600f0ca", "github.com/tendermint/btcd@v0.1.1", "github.com/tendermint/crypto@v0.0.0-20191022145703-50d29ede1e15", "github.com/tendermint/go-amino@v0.15.1", "github.com/tendermint/iavl@v0.14.1 =\u003e github.com/okex/iavl@v0.14.3-exchain", "github.com/tendermint/tendermint@v0.33.9 =\u003e github.com/okex/tendermint@v0.33.9-exchain4", "github.com/tendermint/tm-db@v0.5.2", "github.com/toolkits/concurrent@v0.0.0-20150624120057-a4371d70e3e3", "github.com/tyler-smith/go-bip39@v1.0.1-0.20181017060643-dbb3b84ba2ef", "github.com/willf/bitset@v1.1.11", "go.uber.org/atomic@v1.6.0", "go.uber.org/multierr@v1.5.0", "go.uber.org/zap@v1.15.0", "golang.org/x/crypto@v0.0.0-20200709230013-948cd5f35899", "golang.org/x/net@v0.0.0-20201010224723-4f7140c49acb", "golang.org/x/sys@v0.0.0-20201018230417-eeed37f84f13", "golang.org/x/text@v0.3.3", "golang.org/x/time@v0.0.0-20191024005414-555d28b269f0", "google.golang.org/genproto@v0.0.0-20200526211855-cb27e3aa2013", "google.golang.org/grpc@v1.30.0", "google.golang.org/protobuf@v1.25.0", "gopkg.in/ini.v1@v1.51.0", "gopkg.in/yaml.v2@v2.3.0", "gopkg.in/yaml.v3@v3.0.0-20200313102051-9f266ea9e77c"],
		"cosmos_sdk": "v0.39.2",
		"tendermint": "v0.33.9"
	}
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  application_version  | Object    | 				|
| > server_name         | String    | 				|
| > name                | String    | 				|
| > commit              | String    | 				|
| > go                  | String    | 				|
| > cosmos_sdk          | String    | 				|
| > build_deps          | Array    | 				|
| > tendermint          | String    | 				|
| > client_name         | String    | 				|
| > version             | String    | 				|
| > build_tags          | String    | 				|
|  node_info            | Object    | 				|
| > protocol_version    | Object    | 				|
| >> app                | String    | 				|
| >> block              | String    | 				|
| >> p2p                | String    | 				|
| > other               | Object    | 				|
| >> tx_index           | String    | 				|
| >> rpc_address        | String    | 				|
| > channels            | String    | 				|
| > listen_addr         | String    | 				|
| > id                  | String    | 				|
| > moniker             | String    | 				|
| > version             | String    | 				|
| > network             | String    | 				|
