---
title: MW API 文档

language_tabs: # must be one of https://git.io/vQNgJ
  - json
#  - ruby
#  - python
#  - javascript

toc_footers:
  - <a href='https://mw.run/'>开启您的 MW 之旅</a>

includes:
#  - errors

search: true

code_clipboard: true
---

# 简介

## API 简介

欢迎使用MW API！

此文档是MW API的唯一官方文档，MW API提供的能力会在此持续更新，请大家及时关注。

文档右侧是针对请求参数以及响应结果的示例。

## 请求格式

所有 API 在所有挖矿程序中是一致提供，即访问任何矿机 IP+PORT 规则访问接口均可返回数据。

# 区块浏览器 API

## getLatestCosVersion

```shell
curl "http://192.168.0.234:7216/sharder?requestType=getLatestCosVersion"
```

> Response:

```json
{
  "success": true,
  "requestProcessingTime": 0,
  "cosver": {
    "mode": "incremental",
    "updateTime": "2020-06-09 01:01:01",
    "version": "0.0.3",
    "bakMode": "delete"
  }
}
```

### HTTP Request

`GET http://192.168.0.234:7216/sharder`

### Query Parameters

Parameter | default | Description
--------- | ------- | -----------
requestType | getLatestCosVersion | 获取版本信息定值(getLatestCosVersion) 

### Response Data

| Parameter             | 是否必须 | Description          |
| --------------------- | -------- | -------------------- |
| success               | false    | 版本校验是否为最新版 |
| requestProcessingTime | false    | 请求处理时间         |
| mode                  | true     |                      |
| updateTime            | true     | 版本更新时间         |
| version               | true     | 版本号               |
| bakMode               | true     |                      |

## getBlockchainTransactions

```shell
curl "http://192.168.0.234:7216/sharder?requestType=getBlockchainTransactions&account=CDW-BRNL-6BXD-TM34-5PMMZ&firstIndex=0&lastIndex=9&type=9"
```

> Response:

```json
{
  "requestProcessingTime": 1,
  "transactions": [
    {
      "senderPublicKey": "269670d2f58d5d663dc469ab7cd42e36c096d2d488fb4c7b57279157cb87a417",
      "signature": "bad049107b11c1df8f5e559dcba15d6aa73e9fbd5df4ccf0033ad9fe32061404bc44a7a85a6cc4842e58f287f89b19c42735a2e625e9962ad3e851a306f0e9d5",
      "feeNQT": "0",
      "transactionIndex": 0,
      "type": 9,
      "confirmations": 1714,
      "fullHash": "2ff98e6ae4330d34a00797e7b28788fcfa5a0883a3fb3274c734d64f604b899c",
      "version": 3,
      "phased": false,
      "ecBlockId": "5626458900828322336",
      "accountId": "4597741060539866770",
      "signatureHash": "2657f85a31637b3fe2d2fd0326d92bafab12d5445d458a17d9eecafecec80ac0",
      "attachment": {
        "version.OrdinaryCoinBase": 1,
        "generatorId": "4597741060539866770",
        "creator": "4597741060539866770",
        "consignors": {
          
        },
        "coinBaseType": "BLOCK_REWARD"
      },
      "senderRS": "CDW-BRNL-6BXD-TM34-5PMMZ",
      "subtype": 0,
      "amountNQT": "133300000000",
      "sender": "4597741060539866770",
      "ecBlockHeight": 11053,
      "block": "12144260449748896713",
      "blockTimestamp": 123025077,
      "deadline": 10,
      "transaction": "3750711120802806063",
      "timestamp": 123025077,
      "height": 11774
    },
    {
      "senderPublicKey": "269670d2f58d5d663dc469ab7cd42e36c096d2d488fb4c7b57279157cb87a417",
      "signature": "7c8fa2c598a53e0db28892d8b5804e7e6a2a2cba9acfb6a36f003d805f69f8079d14f9c6e48a5dbab7fe5d5ef2ed59c1973e4857bd350a8abc6c2eca385cab12",
      "feeNQT": "0",
      "transactionIndex": 7,
      "type": 9,
      "confirmations": 1956,
      "fullHash": "35bd1fc749ce761c186a13c4c4f7d2f3854e53fe43e15c15e80ce6a1ebb3d268",
      "version": 3,
      "phased": false,
      "ecBlockId": "4706995141437097583",
      "accountId": "4597741060539866770",
      "signatureHash": "17cb04b3c0f04da220cdfe0b63d849ddc6ec6a08e5379c0038cde84f5ecd038c",
      "attachment": {
        "version.OrdinaryCoinBase": 1,
        "generatorId": "4597741060539866770",
        "creator": "4597741060539866770",
        "consignors": {
          
        },
        "coinBaseType": "BLOCK_REWARD"
      },
      "senderRS": "CDW-BRNL-6BXD-TM34-5PMMZ",
      "subtype": 0,
      "amountNQT": "133300000000",
      "sender": "4597741060539866770",
      "ecBlockHeight": 10811,
      "block": "11877175073298337904",
      "blockTimestamp": 122879633,
      "deadline": 10,
      "transaction": "2051053496582520117",
      "timestamp": 122879633,
      "height": 11532
    }]
}
```

### HTTP Request

`GET http://192.168.0.234:7216/sharder`

### Query Parameters

| Parameter   | 是否必须 | Description                                         |
| ----------- | -------- | --------------------------------------------------- |
| requestType | true     | 获取指定账户交易信息定值(getBlockchainTransactions) |
| account     | true     | MW账户                                              |
| firstIndex  | false    | 获取数据起始索引                                    |
| lastIndex   | false    | 获取数据结束索引                                    |
| type        | false    | 数据类型(0转账,9出块,12节点声明)                    |

### Response Data

| Parameter                     | 是否必须 | Description                                               |
| ----------------------------- | -------- | --------------------------------------------------------- |
| requestProcessingTime         | false    | 请求处理时间                                              |
| signature                     | true     | 签名                                                      |
| transactionIndex              | true     | 交易序列号                                                |
| type                          | true     | 数据类型(0转账,9出块,12节点声明)                          |
| ecBlockId                     | true     | 版本                                                      |
| signatureHash                 | true     | 哈希签名                                                  |
| version.OrdinaryPayment       |          |                                                           |
| version.PublicKeyAnnouncement |          |                                                           |
| recipientPublicKey            | false    | 接收者公钥                                                |
| senderRS                      | true     | 转出MW账户                                                |
| subtype                       |          |                                                           |
| amountNQT                     | true     | 交易金额                                                  |
| recipientRS                   | true     | 接受者                                                    |
| block                         | false    | 区块ID                                                    |
| blockTimestamp                | true     | 加上创世纪时间为高度出块时间(创世纪时间由常量信息API获取) |
| deadline                      |          |                                                           |
| timestamp                     | true     | 加上创世纪时间为交易时间(创世纪时间由常量信息API获取)     |
| height                        | true     | 区块高度                                                  |
| senderPublicKey               | true     | 发送者公钥                                                |
| feeNQT                        | true     | 手续费                                                    |
| confirmations                 | true     | 确认数量                                                  |
| fullHash                      | true     | 完整哈希                                                  |
| version                       | true     | 版本                                                      |
| accountId                     | false    | 账户ID                                                    |
| sender                        | false    | 发送者账户ID                                              |
| recipient                     | false    | 接收者账户ID                                              |
| ecBlockHeight                 |          |                                                           |
| transaction                   | true     | 交易ID                                                    |
| generatorId                   | true     | 出块这账户ID                                              |
| creator                       | true     | 创建者账户ID                                              |

## getPeers

```shell
curl "http://192.168.0.234:7216/sharder?requestType=getPeers&state=CONNECTED&random=0.5637220664429662&includeOwn=true&includePeerInfo=true"
```

> Response 1:

```json
{
  "declaredPeerSize": 7770,
  "peers": [
    "47.96.135.218",
    "121.40.185.101",
    "47.107.244.55",
    "178.32.219.211",
    "120.26.72.74"
  ],
  "requestProcessingTime": 0
}
```

> Response 2:

```json
{
  "declaredPeerSize": 7945,
  "peers": [
    "118.125.65.49",
    "120.79.84.130",
    "183.61.189.198",
    "183.61.189.194",
    {
      "cosUpdateTime": "2020-06-09 01:01:01",
      "lastBlockHeight": 13365,
      "isOwn": "true",
      "lastBlockHash": "b00df7aad135a4dd9d2c0d10d9b663a686135d08eae81b1857a912a4e1e3b7de",
      "apiServerIdleTimeout": 30000,
      "runningMode": "COMMAND",
      "lastBlockTimestamp": "2020-07-21 07:22:50",
      "services": "116",
      "version": "0.0.3",
      "platform": "Linux amd64",
      "useNATService": false,
      "enableStorage": true,
      "announcedAddress": "120.79.46.68",
      "apiPort": 7216,
      "application": "COS",
      "lastBlockId": -8281095228126820378,
      "currentFork": "MainFork",
      "peerLoad": {
        "load": -1,
        "port": 7216,
        "lastUpdate": 1595245281998,
        "host": "127.0.0.1",
        "uri": "http://127.0.0.1:7216"
      },
      "enableBizAPIs": true,
      "bindRsAccount": "CDW-BRNL-6BXD-TM34-5PMMZ",
      "cumulativeDifficulty": "159024373345047",
      "lastBlockGenerator": "CDW-HMC9-3SL9-9LA7-CCXXY",
      "disabledAPIs": "",
      "shareAddress": true
    }
  ],
  "requestProcessingTime": 1
}
```

> Response 3:

```json
"declaredPeerSize": 7938,
  "peers": [
    {
      "lastBlockHash": "6edb0a971beb06b3c79bcf0be0dfda5698bca8132fb0b6b91aeeb31826214afe",
      "inbound": false,
      "blockchainState": "UP_TO_DATE",
      "lastBlockTimestamp": "2020-07-21 05:42:40",
      "type": 3,
      "platform": "Linux amd64",
      "inboundWebSocket": false,
      "lastUpdated": 123975695,
      "announcedAddress": "118.125.65.49",
      "lastBlockId": -1975220378463702535,
      "currentFork": "MainFork",
      "outboundWebSocket": true,
      "cumulativeDifficulty": "158904476227077",
      "state": 1,
      "lastBlockHeight": 13355,
      "downloadedVolume": 91841,
      "address": "118.125.65.49",
      "weight": 0,
      "uploadedVolume": 909831,
      "services": [
        "API",
        "CORS",
        "BAPI",
        "STORAGE"
      ],
      "version": "0.0.3",
      "blacklisted": false,
      "apiPort": 7216,
      "application": "COS",
      "port": 7219,
      "peerLoad": {
        "load": -1,
        "port": 7216,
        "lastUpdate": 1595245282089,
        "host": "118.125.65.49",
        "uri": "http://118.125.65.49:7216"
      },
      "lastConnectAttempt": 123975695,
      "lastBlockGenerator": "CDW-79PW-V763-ZS5X-3Y29X",
      "shareAddress": true
    },
    {
      "lastBlockHash": "6edb0a971beb06b3c79bcf0be0dfda5698bca8132fb0b6b91aeeb31826214afe",
      "inbound": false,
      "blockchainState": "UP_TO_DATE",
      "lastBlockTimestamp": "2020-07-21 13:42:40",
      "type": 3,
      "platform": "Linux amd64",
      "inboundWebSocket": false,
      "lastUpdated": 123975836,
      "announcedAddress": "120.79.84.130",
      "lastBlockId": -1975220378463702535,
      "currentFork": "MainFork",
      "outboundWebSocket": true,
      "cumulativeDifficulty": "158904476227077",
      "state": 1,
      "lastBlockHeight": 13355,
      "downloadedVolume": 50535,
      "address": "120.79.84.130",
      "weight": 0,
      "uploadedVolume": 584689,
      "services": [
        "API",
        "CORS",
        "BAPI",
        "STORAGE"
      ],
      "version": "0.0.3",
      "blacklisted": false,
      "apiPort": 7216,
      "application": "COS",
      "port": 7219,
      "peerLoad": {
        "load": -1,
        "port": 7216,
        "lastUpdate": 1595245322635,
        "host": "120.79.84.130",
        "uri": "http://120.79.84.130:7216"
      },
      "lastConnectAttempt": 123975836,
      "lastBlockGenerator": "CDW-79PW-V763-ZS5X-3Y29X",
      "shareAddress": true
    }],
  "requestProcessingTime": 0
}
```

### HTTP Request

`GET http://192.168.0.234:7216/sharder`

### Query Parameters

| Parameter       | 是否必须 | Description                                  |
| --------------- | -------- | -------------------------------------------- |
| requestType     | true     | 获取节点信息定值(getPeers)                   |
| state           | true     | (CONNECTED,DISCONNECTED,NON_CONNECTED)       |
| random          | true     | 随机数                                       |
| includeOwn      | false    | 默认false,当为true时返回该账户的矿机声明信息 |
| includePeerInfo | false    | 默认false,当为true时返回所有声明信息         |

### Response Data

| Parameter             | 是否必须 | Description      |
| --------------------- | -------- | ---------------- |
| declaredPeerSize      | false    | 声明矿机数量     |
| cosUpdateTime         | false    | 声明更新时间     |
| lastBlockHeight       | false    | 最新出块高度     |
| isOwn                 | false    | 是否为账号拥有者 |
| lastBlockHash         | false    | 最新出块交易哈希 |
| apiServerIdleTimeout  |          |                  |
| runningMode           |          |                  |
| lastBlockTimestamp    | false    | 最新出块交易时间 |
| services              |          |                  |
| version               | false    | 声明动作版本     |
| platform              | false    | 矿机系统         |
| useNATService         | false    | 使用NAT服务      |
| enableStorage         |          |                  |
| announcedAddress      | true     | 矿机IP           |
| apiPort               |          |                  |
| application           | false    | 应用软件         |
| lastBlockId           | false    | 最新出块账户ID   |
| currentFork           | false    | 当前分叉         |
| peerLoad.load         |          |                  |
| peerLoad.port         | false    | 本地端口         |
| peerLoad.lastUpdate   | false    | 本地更新时间     |
| peerLoad.host         | false    | localhost        |
| peerLoad.uri          | false    | 请求地址         |
| enableBizAPIs         |          |                  |
| bindRsAccount         | false    | 矿机绑定MW账户   |
| cumulativeDifficulty  |          |                  |
| lastBlockGenerator    | false    | 最新出块账户     |
| disabledAPIs          |          |                  |
| shareAddress          |          |                  |
| requestProcessingTime |          |                  |

## getUnconfirmedTransactions

```shell
curl "http://192.168.0.234:7216/sharder?requestType=getUnconfirmedTransactions&random=1595057247203&account=4597741060539866770"
```

> Response:

```json
{
  "unconfirmedTransactions": [
    
  ],
  "requestProcessingTime": 1
}
```

### HTTP Request

`GET http://192.168.0.234:7216/sharder`

### Query Parameters

| Parameter   | 是否必须 | Description                                        |
| ----------- | -------- | -------------------------------------------------- |
| requestType | true     | 获取待认证交易信息定值(getUnconfirmedTransactions) |
| account     | true     | 账户ID或者账户名                                   |
| random      | true     | 随机数                                             |

### Response Data

| Parameter               | 是否必须 | Description  |
| ----------------------- | -------- | ------------ |
| requestProcessingTime   | false    | 请求处理时间 |
| unconfirmedTransactions | false    | 未确认的交易 |

## getUserConfig

```shell
curl "http://192.168.0.234:7216/sharder?requestType=getUserConfig&random=1595057242079"
```

> Response:

```json
{
  "sharder.debugTraceSeparator": "\t",
  "sharder.blockGap": "10",
  "sharder.disableAdminPassword": "false",
  "sharder.db.backup.cron": "0 4 * * *",
  "sharder.NodeType": "Soul",
  "sharder.phase": "Pioneer",
  "sharder.storage.provider.default": "i",
  "sharder.testnetBlockGap": "10",
  "sharder.deleteFinishedShufflings": "false",
  "sharder.db.backup.retainDays": "15",
  "sharder.debugTraceAccounts": "",
  "sharder.siteAccount": "bright",
  "sharder.debugTraceQuote": "",
  "sharder.HubBind": "true",
  "sharder.manualReset": "false",
  "sharder.cosUpdateDate": "2020-06-09 01:01:01",
  "sharder.debugLogUnconfirmed": "false",
  "sharder.debugTraceLog": "sharder-trace.csv",
  "sharder.useNATService": "false",
  "sharder.devnetBlockGap": "1",
  "requestProcessingTime": 2,
  "sharder.defaultDesktopAccount": "",
  "sharder.myAddress": "120.79.46.68",
  "sharder.communicationLoggingMask": "0",
  "sharder.db.enableBackup": "false",
  "sharder.launchDesktopApplication": "true",
  "sharder.db.backup.path": "backup",
  "sharder.diskCapacity": 19338066340,
  "sharder.enableLogTraceback": "true",
  "sharder.HubBindAddress": "CDW-BRNL-6BXD-TM34-5PMMZ",
  "sharder.NATClientKey": "",
  "sharder.xxx": "PM00000000000A0018",
  "sharder.useStrongSecureRandom": "false",
  "sharder.enableStackTraces": "true",
  "sharder.NATServicePort": "",
  "sharder.maxNumberOfShufflers": "100",
  "sharder.NATServiceAddress": ""
}
```

### HTTP Request

`GET http://192.168.0.234:7216/sharder`

### Query Parameters

| Parameter   | 是否必须 | Description                         |
| ----------- | -------- | ----------------------------------- |
| requestType | true     | 获取本地节点信息定值(getUserConfig) |
| random      | true     | 随机数                              |

### Response Data

| Parameter                        | 是否必须 | Description          |
| -------------------------------- | -------- | -------------------- |
| sharder.debugTraceSeparator      |          |                      |
| sharder.blockGap                 |          |                      |
| sharder.disableAdminPassword     |          |                      |
| sharder.db.backup.cron           |          |                      |
| sharder.NodeType                 | false    | 节点类型             |
| sharder.phase                    |          |                      |
| sharder.storage.provider.default |          |                      |
| sharder.testnetBlockGap          |          |                      |
| sharder.deleteFinishedShufflings |          |                      |
| sharder.db.backup.retainDays     |          |                      |
| sharder.debugTraceAccounts       |          |                      |
| sharder.siteAccount              | false    | 管理账号             |
| sharder.debugTraceQuote          |          |                      |
| sharder.HubBind                  |          |                      |
| sharder.manualReset              |          |                      |
| sharder.cosUpdateDate            |          |                      |
| sharder.debugLogUnconfirmed      |          |                      |
| sharder.debugTraceLog            |          |                      |
| sharder.useNATService            |          |                      |
| sharder.devnetBlockGap           |          |                      |
| requestProcessingTime            |          |                      |
| sharder.defaultDesktopAccount    |          |                      |
| sharder.myAddress                | false    | IP地址               |
| sharder.communicationLoggingMask |          |                      |
| sharder.db.enableBackup          |          |                      |
| sharder.launchDesktopApplication |          |                      |
| sharder.db.backup.path           |          |                      |
| sharder.diskCapacity             | false    | 硬盘容量             |
| sharder.enableLogTraceback       |          |                      |
| sharder.HubBindAddress           | false    | 矿机对应绑定的MW账号 |
| sharder.NATClientKey             |          |                      |
| sharder.xxx                      | false    | 机器序列号           |
| sharder.useStrongSecureRandom    |          |                      |
| sharder.enableStackTraces        |          |                      |
| sharder.NATServicePort           |          |                      |
| sharder.maxNumberOfShufflers     |          |                      |
| sharder.NATServiceAddress        |          |                      |

## getBlockchainStatus

```shell
curl "http://192.168.0.234:7216/sharder?requestType=getBlockchainStatus&random=0.5325304383349927"
```

> Response:

```json
{
  "lastBlockHash": "d6b033903085cc6f10659addb56aa464525217726b3bab67760c6362afe55ddf",
  "correctInvalidFees": false,
  "ledgerTrimKeep": 30000,
  "maxAPIRecords": 1000,
  "blockchainState": "UP_TO_DATE",
  "includeExpiredPrunable": true,
  "lastBlockTimestamp": "2020-07-18 08:35:44",
  "maxRollback": 800,
  "lastBlockId": 3094358192047540404,
  "currentFork": "MainFork",
  "isScanning": false,
  "isDownloading": false,
  "cumulativeDifficulty": "153940735543119",
  "lastBlockHeight": 12941,
  "apiProxy": false,
  "currentMinRollbackHeight": 0,
  "numberOfBlocks": 12942,
  "isTestnet": "Testnet",
  "isLightClient": false,
  "services": [
    "API",
    "CORS",
    "BAPI",
    "STORAGE"
  ],
  "requestProcessingTime": 0,
  "version": "0.0.3",
  "fullVersion": "0.0.3-Pioneer",
  "lastBlock": "3094358192047540404",
  "application": "COS",
  "lastBlockchainFeederHeight": 12941,
  "maxPrunableLifetime": 7776000,
  "lastBlockGenerator": "CDW-W9EA-8WGT-FSU3-82VRD",
  "time": 123726913,
  "cosLastUpgradeDate": "2020-06-09 01:01:01",
  "lastBlockchainFeeder": "testboot.mw.run"
}
```

### HTTP Request

`GET http://192.168.0.234:7216/sharder`

### Query Parameters

| Parameter   | 是否必须 | Description                                 |
| ----------- | -------- | ------------------------------------------- |
| requestType | true     | 获取区块链状态信息定值(getBlockchainStatus) |
| random      | true     | 随机数                                      |

### Response Data

| Parameter                  | 是否必须 | Description      |
| -------------------------- | -------- | ---------------- |
| lastBlockHash              | true     | 最新交易哈希     |
| correctInvalidFees         | true     | 当前费用是否有效 |
| ledgerTrimKeep             |          |                  |
| maxAPIRecords              | false    | 最大API请求记录  |
| blockchainState            |          |                  |
| includeExpiredPrunable     | false    | 是否包含失效记录 |
| lastBlockTimestamp         | false    | 最新交易时间     |
| maxRollback                | false    | 最大回滚         |
| lastBlockId                | false    | 最新交易ID       |
| currentFork                | false    | 当前分叉         |
| isScanning                 | false    | 是否扫描         |
| isDownloading              | false    | 是否加载中       |
| cumulativeDifficulty       |          |                  |
| lastBlockHeight            | false    | 最新区块高度     |
| apiProxy                   | false    | 是否代理         |
| currentMinRollbackHeight   |          |                  |
| numberOfBlocks             | false    | 当前交易高度     |
| isTestnet                  | false    | 是否检测网络     |
| isLightClient              | false    | 是否驱动客户端   |
| services                   |          |                  |
| requestProcessingTime      | false    | 请求处理时间     |
| version                    | false    | 版本             |
| fullVersion                | true     | 完整版本名       |
| lastBlock                  | true     | 最新出块ID       |
| application                | false    | 应用软件         |
| lastBlockchainFeederHeight |          |                  |
| maxPrunableLifetime        |          |                  |
| lastBlockGenerator         |          | 最新出块账户     |
| time                       |          |                  |
| cosLastUpgradeDate         |          |                  |
| lastBlockchainFeeder       |          |                  |

## getAccount

```shell
curl "http://192.168.0.234:7216/sharder?requestType=getAccount&account=4597741060539866770&includeAssets=true&includeCurrencies=true&includeLessors=true&includeEffectiveBalance=true&random=0.08781158929285926"
```

> Response:

```json
{
  "unconfirmedBalanceNQT": "684100000004",
  "guaranteedBalanceNQT": "684100000004",
  "accountId": "4597741060539866770",
  "accountRS": "CDW-BRNL-6BXD-TM34-5PMMZ",
  "pocScore": 10912000,
  "forgedBalanceNQT": "400600000004",
  "balanceNQT": "684100000004",
  "effectiveBalanceNQT": "684100000004",
  "publicKey": "269670d2f58d5d663dc469ab7cd42e36c096d2d488fb4c7b57279157cb87a417",
  "requestProcessingTime": 2,
  "account": "4597741060539866770",
  "frozenBalanceNQT": "0"
}
```

### HTTP Request

`GET http://192.168.0.234:7216/sharder`

### Query Parameters

| Parameter               | 是否必须 | Description                  |
| ----------------------- | -------- | ---------------------------- |
| requestType             | true     | 获取账户信息定值(getAccount) |
| account                 | true     | MW账户ID或账户名             |
| random                  | false    | 随机数                       |
| includeAssets           | false    |                              |
| includeCurrencies       | false    |                              |
| includeLessors          | false    |                              |
| includeEffectiveBalance | false    | 是否包含有效余额默认false    |

### Response Data

| Parameter             | 是否必须 | Description  |
| --------------------- | -------- | ------------ |
| unconfirmedBalanceNQT | false    | 未确认金额   |
| guaranteedBalanceNQT  | false    | 抵押金额     |
| accountId             | true     | 账户ID       |
| accountRS             | true     | 账户         |
| pocScore              | true     | poc得分      |
| forgedBalanceNQT      | true     | 挖矿收入     |
| balanceNQT            | true     | 账户余额     |
| effectiveBalanceNQT   | true     | 可用余额     |
| publicKey             | true     | 公钥         |
| requestProcessingTime | false    | 请求处理时间 |
| account               | false    | 账户ID       |
| frozenBalanceNQT      | true     | 冻结金额     |

## getForging

```shell
curl "http://192.168.0.234:7216/sharder?requestType=getForging"
```

> Response:

```json
{
	"generators": [{
		"detailedPocScore": {
			"networkScore": 0,
			"bcScore": 0,
			"onlineRateScore": 0,
			"effectiveBalance": 6841,
			"poc_score": 10912000,
			"performanceScore": 0,
			"nodeTypeScore": 1875,
			"accountId": 4597741060539866770,
			"serverScore": 0,
			"ssScore": 1162,
			"hardwareScore": 7875,
			"blockMissScore": 0,
			"height": 11778
		},
		"accountRS": "CDW-BRNL-6BXD-TM34-5PMMZ",
		"pocScore": 10912000,
		"bindPeerType": "Soul Node",
		"deadline": 664,
		"account": "4597741060539866770",
		"effectiveBalanceSS": 6841,
		"remaining": 437,
		"hitTime": 124061882
	}],
	"requestProcessingTime": 0
}
```

### HTTP Request

`POST http://192.168.0.234:7216/sharder`

### Query Parameters

| Parameter   | 是否必须 | Description                          |
| ----------- | -------- | ------------------------------------ |
| requestType | true     | 获取指定账户得分情况定值(getForging) |

### Request Data

| Parameter     | 是否必须 | Description  |
| ------------- | -------- | ------------ |
| networkScore  | true     | 密钥         |
| adminPassword | true     | 节点管理密码 |
| loadPoolInfo  | true     | 是否为矿池   |

### Response Data

| Data               | 是否必须 | Description  |
| ------------------ | -------- | ------------ |
| networkScore       | true     | 网络得分     |
| bcScore            |          |              |
| onlineRateScore    |          |              |
| effectiveBalance   | false    | 有效余额     |
| poc_score          | false    | poc总得分    |
| performanceScore   | true     | 交易性能得分 |
| nodeTypeScore      | true     | 节点类型得分 |
| accountId          | false    | 账户ID       |
| serverScore        | false    | 服务得分     |
| ssScore            | true     | MW抵押得分   |
| hardwareScore      | true     | 硬件得分     |
| blockMissScore     |          |              |
| height             | false    | 区块高度     |
| accountRS          | true     | MW账户       |
| pocScore           | true     | POC总得分    |
| bindPeerType       | true     | 类型         |
| deadline           |          |              |
| account            | true     | 账户ID       |
| effectiveBalanceSS | false    | 有效余额抵押 |
| remaining          |          |              |
| hitTime            | true     | 预计出块时间 |

## stopMining

```shell
curl "http://192.168.0.234:7216/sharder?requestType=stopMining"
```

> Response:

```json
{
	"foundAndStopped": false,
	"forgersCount": 0,
	"requestProcessingTime": 1
}
```

### HTTP Request

`POST http://192.168.0.234:7216/sharder`

### Query Parameters

| Parameter   | 是否必须 | Description      |
| ----------- | -------- | ---------------- |
| requestType | true     | 定值(stopMining) |

### Response Data

| Parameter             | 是否必须 | Description              |
| --------------------- | -------- | ------------------------ |
| foundAndStopped       | true     | 检测是否矿机是否停止挖矿 |
| forgersCount          | true     | 关闭数                   |
| requestProcessingTime | false    | 请求响应时间             |

## getDGSPurchaseCount

```shell
curl "http://192.168.0.234:7216/sharder?requestType=getDGSPurchaseCount&seller=4597741060539866770&completed=true&random=0.852988454945699"
```

> Response:

```json
{
  "numberOfPurchases": 0,
  "requestProcessingTime": 1
}
```

### HTTP Request

`GET http://192.168.0.234:7216/sharder`

### Query Parameters

| Parameter   | 是否必须 | Description               |
| ----------- | -------- | ------------------------- |
| requestType | true     | 定值(getDGSPurchaseCount) |
| completed   | false    |                           |
| seller      | false    | 卖方ID                    |
| buyer       | false    | 买方ID                    |
| random      | false    | 随机数                    |

### Response Data

| Parameter             | 是否必须 | Description  |
| --------------------- | -------- | ------------ |
| numberOfPurchases     | true     | 收益数量     |
| requestProcessingTime | false    | 请求处理时间 |

## getDGSPendingPurchases

```shell
curl "http://192.168.0.234:7216/sharder?requestType=getDGSPendingPurchases&seller=4597741060539866770&random=0.6369620754760852"
```

> Response:

```json
{
  "purchases": [
    
  ],
  "requestProcessingTime": 0
}
```

### HTTP Request

`GET http://192.168.0.234:7216/sharder`

### Query Parameters

| Parameter   | 是否必须 | Description                  |
| ----------- | -------- | ---------------------------- |
| requestType | true     | 定值(getDGSPendingPurchases) |
| seller      | true     | 卖方ID                       |
| random      | false    | 随机数                       |

### Response Data

| Parameter             | 是否必须 | Description |
| --------------------- | -------- | ----------- |
| requestProcessingTime |          |             |

## getAliasCount

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://192.168.0.234:7216/sharder?requestType=getAliasCount&account=4597741060539866770&random=0.21013835024125904"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
{
  "numberOfAliases": 0,
  "requestProcessingTime": 1
}
```

### HTTP Request

`GET http://192.168.0.234:7216/sharder`

### Query Parameters

| Parameter   | 是否必须 | Description                     |
| ----------- | -------- | ------------------------------- |
| requestType | true     | 获取别名信息定值(getAliasCount) |
| account     | true     | 账户或账户ID                    |
| random      | false    | 随机数                          |

### Response Data

| Parameter             | 是否必须 | Description  |
| --------------------- | -------- | ------------ |
| requestProcessingTime | false    | 请求处理时间 |
| numberOfAliases       | true     | 别名数量     |

## getLastTrades

```shell
curl "http://192.168.0.234:7216/sharder?requestType=getLastTrades&assets=25461532156"
```

> Response:

```json
{
  "trades": [
    
  ],
  "requestProcessingTime": 1
}
```

### HTTP Request

`GET http://192.168.0.234:7216/sharder`

### Query Parameters

| Parameter   | 是否必须 | Description                           |
| ----------- | -------- | ------------------------------------- |
| requestType | true     | 或崎岖最新交易信息定值(getLastTrades) |
| random      | false    | 随机数                                |

### Response Data

| Parameter             | 是否必须 | Description  |
| --------------------- | -------- | ------------ |
| requestProcessingTime | false    | 请求处理时间 |

## getVoterPhasedTransactions

```shell
curl "http://192.168.0.231:7216/sharder?requestType=getVoterPhasedTransactions&account=265523835724773959&firstIndex=0&lastIndex=20&random=0.02052225643621064"
```

> Response:

```json
{
  "requestProcessingTime": 1,
  "transactions": [
    
  ]
}
```

### HTTP Request

`GET http://192.168.0.234:7216/sharder`

### Query Parameters

| Parameter   | 是否必须 | Description                      |
| ----------- | -------- | -------------------------------- |
| requestType | true     | 定值(getVoterPhasedTransactions) |
| account     | true     | 账户ID或账户名                   |
| firstIndex  | false    | 请求数据起始索引                 |
| lastIndex   | false    | 请求数据结束索引                 |
| random      | false    | 随机数                           |

### Response Data

| Parameter             | 是否必须 | Description  |
| --------------------- | -------- | ------------ |
| requestProcessingTime | true     | 请求处理时间 |

## getAccountPublicKey

```shell
curl "http://192.168.0.234:7216/sharder?requestType=getAccountPublicKey&account=4597741060539866770&random=0.7889226609636362"
```

> Response:

```json
{
  "publicKey": "269670d2f58d5d663dc469ab7cd42e36c096d2d488fb4c7b57279157cb87a417",
  "requestProcessingTime": 0
}
```

### HTTP Request

`GET http://192.168.0.234:7216/sharder`

### Query Parameters

| Parameter   | 是否必须 | Description                               |
| ----------- | -------- | ----------------------------------------- |
| requestType | true     | 获取账户公钥信息定值(getAccountPublicKey) |
| account     | true     | 账户或账户ID                              |
| random      | false    | 随机数                                    |

### Response Data

| Parameter             | 是否必须 | Description  |
| --------------------- | -------- | ------------ |
| publicKey             | true     | 账户公钥     |
| requestProcessingTime | false    | 请求处理时间 |

## getBlock

```shell
curl "http://192.168.0.234:7216/sharder?requestType=getBlock&height=6212&block=&includeTransactions=true"
```

> Response:

```json
{
	"previousBlockHash": "1e0ee58e34b2ac1cd34108cbccaa0a8740f631a81536cbd1e8ad34dfae0e7614",
	"payloadLength": 1681,
	"totalAmountNQT": "1133400000000",
	"generationSignature": "aa2c8a9563839f00d849adc2d17012549ed395d03b76f2a271bc4dc5f63dc6c0",
	"generator": "7299850594251227620",
	"generatorPublicKey": "ef24774fdd90ad2f8b322117b103ac8e08ecb678ef2d0b2e006a135cd5ac5173",
	"baseTarget": "1538547747",
	"payloadHash": "3d4ddbcf18b90f4c583c2a7911b21f9df974597a61e5c0956bd5d3e10528377e",
	"generatorRS": "CDW-BJH6-G3RW-AM86-89LMC",
	"nextBlock": "11901345062343865859",
	"requestProcessingTime": 3,
	"numberOfTransactions": 8,
	"blockSignature": "b26aec8319d7ae64e40cde43582b20e72f74c3e1c4e224228b0b5fabd3db980c5b3111a2ad44d83b9aae6dba7fa8b55d9842a6f6a656329e8e32b5b2184030d4",
	"transactions": [{
			"signature": "8abe4d46018c9f1cead896581e7a9e3318fc30c3af75a6e3ddfa88d5a9d8d60abb41d03d679d1a65be483d72f968308a33d15c48a9db5092a757ccb35c81950c",
			"transactionIndex": 0,
			"type": 12,
			"phased": false,
			"ecBlockId": "12600364957761285016",
			"signatureHash": "bc5a6afcfb3ee0b4ddfe03e0d0f75619ba8be09819b6b7262de22e2892d96947",
			"attachment": {
				"accountId": "-3532411906506360547",
				"type": 4,
				"version.pocNodeType": 1,
				"diskCapacity": "93131240612",
				"ip": "192.168.4.27"
			},
			"senderRS": "CDW-38C9-Z68H-PWKP-FCJTD",
			"subtype": 0,
			"amountNQT": "0",
			"recipientRS": "CDW-9YAX-4SN7-P7YN-EULYX",
			"block": "13643736609632326671",
			"blockTimestamp": 119666081,
			"deadline": 10,
			"timestamp": 119665608,
			"height": 6212,
			"senderPublicKey": "1f8089fbec39da5fdbd2ba744ed7354727519260ef4407393d1f67c9cfdf2359",
			"feeNQT": "1",
			"confirmations": 6738,
			"fullHash": "30d8b832b0830249302794137e1ee05f3553103fc6bef899bb01b764e50e4ba2",
			"version": 3,
			"accountId": "-3033725234207221433",
			"sender": "15413018839502330183",
			"recipient": "14914332167203191069",
			"ecBlockHeight": 5491,
			"transaction": "5260912107510618160"
		},
		{
			"signature": "210fdb4267e92ef91534732a1b7659433de86ee829926af103082a4aa926b509651128a8a231b4d7b4f5b40727841dfc7dbf1d3befd1f4b251ba41a76624f33b",
			"transactionIndex": 1,
			"type": 12,
			"phased": false,
			"ecBlockId": "12600364957761285016",
			"signatureHash": "9ac3b6f827ca07ed629e38b1ea0279da9bd6f3ce42c69128cc40fb56e78d9b28",
			"attachment": {
				"accountId": "4597741060539866770",
				"type": 4,
				"version.pocNodeType": 1,
				"diskCapacity": "15493424732",
				"ip": "120.79.46.68"
			},
			"senderRS": "CDW-38C9-Z68H-PWKP-FCJTD",
			"subtype": 0,
			"amountNQT": "0",
			"recipientRS": "CDW-BRNL-6BXD-TM34-5PMMZ",
			"block": "13643736609632326671",
			"blockTimestamp": 119666081,
			"deadline": 10,
			"timestamp": 119665727,
			"height": 6212,
			"senderPublicKey": "1f8089fbec39da5fdbd2ba744ed7354727519260ef4407393d1f67c9cfdf2359",
			"feeNQT": "1",
			"confirmations": 6738,
			"fullHash": "45ddeec93fbb489219e69fe8f416f3b30874c957f5f609cee085efc9f4e86ca3",
			"version": 3,
			"accountId": "-3033725234207221433",
			"sender": "15413018839502330183",
			"recipient": "4597741060539866770",
			"ecBlockHeight": 5491,
			"transaction": "10540880810505854277"
		}
	],
	"version": 3,
	"totalFeeNQT": "100000006",
	"accountId": "7299850594251227620",
	"previousBlock": "2066222267861634590",
	"cumulativeDifficulty": "73773263617938",
	"block": "13643736609632326671",
	"height": 6212,
	"timestamp": 119666081
}
```

### HTTP Request

`GET http://192.168.0.234:7216/sharder`

### Query Parameters

| Parameter           | 是否必须 | Description                        |
| ------------------- | -------- | ---------------------------------- |
| requestType         | true     | 获取指定高度交易信息定值(getBlock) |
| height              | true     | 区块高度                           |
| block               | false    | 区块ID                             |
| includeTransactions | false    | 是否包含交易详情(默认false)        |

### Response Data

| Parameter              | 是否必须 | Description                                           |
| ---------------------- | -------- | ----------------------------------------------------- |
| previousBlockHash      | true     | 上一区块哈希                                          |
| payloadLength          |          |                                                       |
| totalAmountNQT         | true     | 区块交易总金额                                        |
| generationSignature    | true     | 出块签名                                              |
| generator              | true     | 出块者账号ID                                          |
| generatorPublicKey     | true     | 出块者公钥                                            |
| baseTarget             |          |                                                       |
| payloadHash            |          |                                                       |
| generatorRS            | true     | 出块账号                                              |
| nextBlock              | false    | 下一区块ID                                            |
| requestProcessingTime  |          |                                                       |
| numberOfTransactions   | false    | 区块交易数量                                          |
| blockSignature         | true     | 出块签名                                              |
| signature              | true     | 签名                                                  |
| transactionIndex       | true     | 交易序列号                                            |
| type                   | true     | 交易类型                                              |
| phased                 |          |                                                       |
| ecBlockId              |          |                                                       |
| signatureHash          | true     | 哈希签名                                              |
| accountId              | true     | 账户ID                                                |
| senderRS               | true     | 发送者                                                |
| subtype                |          |                                                       |
| amountNQT              | true     | 交易金额                                              |
| recipientRS            | true     | 接收者                                                |
| block                  | false    | 区块ID                                                |
| blockTimestamp         | true     | 加上创世纪时间为区块时间(创世纪时间由常量信息API获取) |
| deadline               |          |                                                       |
| transactions.timestamp | true     | 加上创世纪时间为交易时间(创世纪时间由常量信息API获取) |
| height                 | true     | 区块高度                                              |
| senderPublicKey        | true     | 发送者公钥                                            |
| feeNQT                 | true     | 交易手续费                                            |
| confirmations          | true     | 确认数                                                |
| fullHash               | true     | 完整哈希                                              |
| version                | true     | 版本                                                  |
| sender                 | false    | 发送者账户ID                                          |
| recipient              | false    | 接收者账户ID                                          |
| ecBlockHeight          |          |                                                       |
| transaction            | true     | 交易ID                                                |
| totalFeeNQT            | true     | 区块总交易手续费                                      |
| cumulativeDifficulty   |          |                                                       |
| previousBlock          | false    | 上一区块ID                                            |
| block                  | false    | 区块ID                                                |
| timestamp              | true     | 加上创世纪时间为区块时间(创世纪时间由常量信息API获取) |
| attachment.type        |          |                                                       |
| version.pocNodeType    |          |                                                       |
| diskCapacity           | true     | 硬盘容量                                              |
| ip                     | true     | 矿机IP                                                |

## getAccountId

```shell
curl "http://192.168.0.234:7216/sharder?requestType=getAccountId&accoutId=-3532411906506360547,4597741060539866770"
```

> Response:

```json
{
  "rsAccountInfo": [
    {
      "accountId": "-3532411906506360547",
      "rsaccountId": "CDW-9YAX-4SN7-P7YN-EULYX"
    },
    {
      "accountId": "4597741060539866770",
      "rsaccountId": "CDW-BRNL-6BXD-TM34-5PMMZ"
    }
  ],
  "requestProcessingTime": 0
}
```

### HTTP Request

`GET http://192.168.0.234:7216/sharder`

### Query Parameters

| Parameter   | 是否必须 | Description                            |
| ----------- | -------- | -------------------------------------- |
| requestType | true     | 根据账户ID获取账户名定值(getAccountId) |
| accoutId    | true     | 账户ID                                 |

### Response Data

| Parameter             | 是否必须 | Description  |
| --------------------- | -------- | ------------ |
| requestProcessingTime | false    | 请求处理时间 |
| accountId             | false    | 账户ID       |
| rsaccountId           | true     | 账户名       |

## getTransaction

```shell
curl "http://192.168.0.234:7216/sharder?requestType=getTransaction&transaction=13854539770161423054"
```

> Response:

```json

  "signature": "913a77f48439bbe07f29f805323a8107a4ea19af7a9df8b90b708d6c20b89501cf2dcd67c44fbae43e910e0d527e377567c5211aa7f0aefb9395c58f0cc679a8",
  "transactionIndex": 3,
  "type": 12,
  "phased": false,
  "ecBlockId": "12600364957761285016",
  "signatureHash": "fb68deaf90a1697fe8659c86aaf394e8e282e90e10c0fd1839e7c05d06f66bdb",
  "attachment": {
    "accountId": "4597741060539866770",
    "type": 4,
    "version.pocNodeType": 1,
    "diskCapacity": "15493424732",
    "ip": "120.79.46.68"
  },
  "senderRS": "CDW-38C9-Z68H-PWKP-FCJTD",
  "subtype": 0,
  "amountNQT": "0",
  "recipientRS": "CDW-BRNL-6BXD-TM34-5PMMZ",
  "block": "13643736609632326671",
  "blockTimestamp": 119666081,
  "deadline": 10,
  "timestamp": 119665820,
  "height": 6212,
  "senderPublicKey": "1f8089fbec39da5fdbd2ba744ed7354727519260ef4407393d1f67c9cfdf2359",
  "feeNQT": "1",
  "requestProcessingTime": 1,
  "confirmations": 7303,
  "fullHash": "ce62fe36843645c09dbade199385cbda3b2f717843bc3a2d0dbf32f83d53b886",
  "version": 3,
  "accountId": "-3033725234207221433",
  "sender": "15413018839502330183",
  "recipient": "4597741060539866770",
  "ecBlockHeight": 5491,
  "transaction": "13854539770161423054"
}
```

### HTTP Request

`GET http://192.168.0.234:7216/sharder`

### Query Parameters

| Parameter   | 是否必须 | Description                                |
| ----------- | -------- | ------------------------------------------ |
| requestType | true     | 根据交易ID获取交易信息定值(getTransaction) |
| transaction | true     | 交易ID                                     |

### Response Data

| Parameter             | 是否必须 | Description                                           |
| --------------------- | -------- | ----------------------------------------------------- |
| signature             | false    | 签名                                                  |
| transactionIndex      | false    | 交易序列号                                            |
| type                  | true     | 交易类型                                              |
| phased                |          |                                                       |
| ecBlockId             |          |                                                       |
| signatureHash         | true     | 哈希签名                                              |
| attachment.tpye       |          |                                                       |
| version.pocNodeType   |          |                                                       |
| diskCapacity          | true     | 硬盘容量                                              |
| ip                    | true     | 矿机IP                                                |
| senderRS              | true     | 发送者                                                |
| subtype               |          |                                                       |
| amountNQT             | true     | 交易金额                                              |
| recipientRS           | true     | 接收者                                                |
| block                 | false    | 区块ID                                                |
| blockTimestamp        | true     | 加上创世纪时间为区块时间(创世纪时间由常量信息API获取) |
| deadline              |          |                                                       |
| timestamp             | true     | 加上创世纪时间为交易时间(创世纪时间由常量信息API获取) |
| height                | true     | 区块高度                                              |
| senderPublicKey       | true     | 发送者公钥                                            |
| feeNQT                | true     | 交易手续费                                            |
| requestProcessingTime | false    | 请求处理时间                                          |
| confirmations         | true     | 确认数                                                |
| fullHash              | true     | 完整哈希                                              |
| version               | true     | 版本                                                  |
| accountId             | true     | 账户ID                                                |
| sender                | true     | 发送者ID                                              |
| recipient             | false    | 接收者ID                                              |
| ecBlockHeight         |          |                                                       |
| transaction           | true     | 交易ID                                                |

## getTxStatistics

```shell
curl "http://192.168.0.234:7216/sharder?requestType=getTxStatistics"
```

> Response:

```json
{
  "transferCount24H": 400,
  "coinBaseCount": 13520,
  "storageDataLength24H": 0,
  "storageDataLength": 0,
  "storageCount": 0,
  "poolCount": 0,
  "transferAmount": 281847657,
  "requestProcessingTime": 332,
  "transferCount": 32976,
  "transferAmount24H": 2833361,
  "storageCount24H": 0
}
```

### HTTP Request

`GET http://192.168.0.234:7216/sharder`

### Query Parameters

| Parameter   | 是否必须 | Description                                      |
| ----------- | -------- | ------------------------------------------------ |
| requestType | true     | 获取24H及全网交易和存储数据定值(getTxStatistics) |

### Response Data

| Parameter             | 是否必须 | Description            |
| --------------------- | -------- | ---------------------- |
| transferCount24H      | false    | 24小时转账交易数量     |
| coinBaseCount         |          |                        |
| storageDataLength24H  | true     | 24小时数据存储数据大小 |
| storageDataLength     | true     | 全网数据存储数据大小   |
| storageCount          | true     | 全网数据存储数量       |
| poolCount             |          |                        |
| transferAmount        | true     | 全网转账交易金额数     |
| requestProcessingTime | false    | 请求处理时间           |
| transferCount         | true     | 全网转账交易数量       |
| transferAmount24H     | true     | 24小时转账交易金额数   |
| storageCount24H       | true     | 24小时数据存储数量     |

## getBizConstants

```shell
curl "http://192.168.0.234:7216/sharder?requestType=getBizConstants"
```

> Response:

> The above command returns JSON structured like this:

```json
{
  "epochBeginning": 1471334888171,
  "requestProcessingTime": 0
}
```

### HTTP Request

`GET http://192.168.0.10:7216/sharder`

### URL Parameters

| Parameter   | 是否必须 | Description                       |
| ----------- | -------- | --------------------------------- |
| requestType | true     | 获取时间常亮定值(getBizConstants) |

### Response Data

| Data                  | 是否必须 | Description  |
| --------------------- | -------- | ------------ |
| epochBeginning        | true     | 创世时间     |
| requestProcessingTime | false    | 请求处理时间 |

## getNextBlockGenerators

```shell
curl "http://192.168.0.234:7216/sharder?requestType=getNextBlockGenerators&limit=99999"
```

> Response:

```json
{
	"activeCount": 2197,
	"lastBlock": "10027198035769277872",
	"generators": [{
		"detailedPocScore": {
			"networkScore": 0,
			"bcScore": 0,
			"onlineRateScore": 0,
			"effectiveBalance": 1470,
			"poc_score": 51061000,
			"performanceScore": 0,
			"nodeTypeScore": 1875,
			"accountId": 4376809670326948357,
			"serverScore": 0,
			"ssScore": 249,
			"hardwareScore": 48937,
			"blockMissScore": 0,
			"height": 11000
		},
		"accountRS": "CDW-C6J7-8LSP-SLA8-5FEHT",
		"pocScore": 51061000,
		"bindPeerType": "Soul Node",
		"deadline": 0,
		"account": "4376809670326948357",
		"effectiveBalanceSS": 1470,
		"remaining": 0,
		"hitTime": 123992702
	}, {
		"detailedPocScore": {
			"networkScore": 0,
			"bcScore": 0,
			"onlineRateScore": 0,
			"effectiveBalance": 4141,
			"poc_score": 56015000,
			"performanceScore": 0,
			"nodeTypeScore": 1875,
			"accountId": -1684102143573770859,
			"serverScore": 0,
			"ssScore": 703,
			"hardwareScore": 53437,
			"blockMissScore": 0,
			"height": 12647
		},
		"accountRS": "CDW-ZHEP-2RRE-XP7M-GY8AK",
		"pocScore": 56015000,
		"bindPeerType": "Soul Node",
		"deadline": 0,
		"account": "16762641930135780757",
		"effectiveBalanceSS": 4141,
		"remaining": 0,
		"hitTime": 123992702
	}],
	"requestProcessingTime": 10,
	"timestamp": 123992102,
	"height": 13383
}
```

### HTTP Request

`GET http://192.168.0.10:7216/sharder`

### URL Parameters

| Parameter   | 是否必须 | Description                  |
| ----------- | -------- | ---------------------------- |
| requestType | true     | 定值(getNextBlockGenerators) |
| limit       | true     | 获取数据量上限               |

### Response Data

| Data                  | 是否必须 | Description  |
| --------------------- | -------- | ------------ |
| activeCount           | true     | 在线总数     |
| lastBlock             | false    |              |
| networkScore          | true     | 网络得分     |
| bcScore               |          |              |
| onlineRateScore       |          |              |
| effectiveBalance      | false    | 有效余额     |
| poc_score             |          |              |
| performanceScore      | true     | 交易性能得分 |
| nodeTypeScore         | true     | 节点类型得分 |
| accountId             | false    | 账户ID       |
| serverScore           | false    | 服务得分     |
| ssScore               | true     | MW抵押得分   |
| hardwareScore         | true     | 硬件得分     |
| blockMissScore        |          |              |
| height                | false    | 声明高度     |
| accountRS             | true     | MW账户       |
| pocScore              | true     | POC总得分    |
| bindPeerType          | true     | 类型         |
| deadline              |          |              |
| account               | true     | 账户ID       |
| effectiveBalanceSS    | false    | 有效余额抵押 |
| remaining             |          |              |
| hitTime               | true     | 预计出块时间 |
| requestProcessingTime | false    | 请求处理时间 |
| timestamp             | false    | 请求时间     |