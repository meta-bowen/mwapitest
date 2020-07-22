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

## 获取主页区块列表信息

```json
curl "http://IP:7216/sharder?requestType=getBizBlocks&firstIndex=0&lastIndex=10"
```

> Response:

```json
[{
	"height": 10461,
	"payloadLength": 834,
	"timestamp": 122235798,
	"generator": "5941498711528046973",
	"generatorRS": "CDW-62DX-M753-B6JT-7K5X6",
	"transactions": [{
		"type": 0,
		"height": 10461,
		"timestamp": 122235298,
		"confirmations": 0,
		"transactionId": "18119931610634187444",
		"hash": "b4f238decbed76fb3f94f11373055b53c327f702c2e960d4cf58281919de974e",
		"index": 0,
		"amount": 135,
		"fee": 1,
		"sender": "CDW-M9L9-BMQK-RPB6-E3G4G",
		"recipient": "CDW-2Y66-BHE8-5UJL-ALKRC"
	}, {
		"type": 0,
		"height": 10461,
		"timestamp": 122235466,
		"confirmations": 0,
		"transactionId": "3791869201739024234",
		"hash": "6a0766e4f26c9f341209879496a73b5f8ef769d983a4b590cceab2091b3fd25d",
		"index": 1,
		"amount": 10,
		"fee": 1,
		"sender": "CDW-LE9X-VYZ8-YRCG-EWTL2",
		"recipient": "CDW-D5EC-54XM-WSKP-2MCZU"
	}],
	"numberOfTransactions": 4,
	"blockId": "4144647700667314519",
	"previousBlockId": "15264552310802187297",
	"totalFee": 3,
	"totalAmount": 11478
}, {
	"height": 10460,
	"payloadLength": 1252,
	"timestamp": 122235197,
	"generator": "13243166401848131907",
	"generatorRS": "CDW-RJC5-PPFS-VTU9-DFBLH",
	"transactions": [{
		"type": 0,
		"height": 10460,
		"timestamp": 122234764,
		"confirmations": 1,
		"transactionId": "9388610240114304842",
		"hash": "4aa79b38450b4b82249cff11ae2f05301bad2303ec9af6cf662a3b0a9503fa60",
		"index": 0,
		"amount": 196,
		"fee": 1,
		"sender": "CDW-M9L9-BMQK-RPB6-E3G4G",
		"recipient": "CDW-5FJ6-HTMW-3RUS-ERXD4"
	}, {
		"type": 0,
		"height": 10460,
		"timestamp": 122234845,
		"confirmations": 1,
		"transactionId": "17131911732168208794",
		"hash": "9ab13b9ff3c6c0ed1b333d674a5e65849a08b0611c62c405bc8325242cc6543f",
		"index": 1,
		"amount": 138,
		"fee": 1,
		"sender": "CDW-M9L9-BMQK-RPB6-E3G4G",
		"recipient": "CDW-PBV3-2Z9X-ES49-87542"
	}],
	"numberOfTransactions": 6,
	"blockId": "15264552310802187297",
	"previousBlockId": "12377623742819441789",
	"totalFee": 5,
	"totalAmount": 2064.8
}]
```

### HTTP Request

`GET http://IP:7216/sharder`

### Query Parameters

Parameter | 是否必须 | Description
--------- | ------- | -----------
requestType | true | 获取主页区块高度类(默认getBizBlocks) 
firstIndex | true | 数据条数起始索引 
 lastIndex   | true | 数据条数结束索引 

### Response Data

| Parameter            | 是否必须 | Description                                           |
| -------------------- | -------- | ----------------------------------------------------- |
| height               | true     | 区块高度                                              |
| payloadLength        |          |                                                       |
| timestamp            | true     | 加上创世纪时间为交易时间(创世纪时间由常量信息API获取) |
| generator            |          | MW 地址元数据                                         |
| generatorRS          |          | MW 地址                                               |
| type                 | true     | 交易类型(0为转账，9为出块)                            |
| confirmations        |          | 区块高度确认值（当前交易区块ID同当前最高区块高度差异值）  |
| transactionId        | true     | 交易ID                                                |
| hash                 | true     | 交易哈希                                              |
| index                |          | 交易顺序号                                            |
| amount               | true     | 交易金额                                              |
| fee                  | true     | 交易手续费                                            |
| sender               | true     | 发送方                                                |
| recipient            | true     | 接收方                                                |
| numberOfTransactions |          | 当前区块交易总数                                       |
| blockId              |          | 区块ID                                                |
| previousBlockId      |          | 上一区块ID                                            |
| totalFee             | true     | 总手续费                                              |
| totalAmount          | true     | 总交易成交额                                          |

## 获取统计数据

```json
curl "http://IP:7216/sharder?requestType=getTxStatistics"
```

> Response:

```json
{
	"transferCount24H": 344,
	"coinBaseCount": 10466,
	"storageDataLength24H": 0,
	"storageDataLength": 0,
	"storageCount": 0,
	"poolCount": 0,
	"transferAmount": 263719243,
	"requestProcessingTime": 50,
	"transferCount": 24306,
	"transferAmount24H": 915804,
	"storageCount24H": 0
}
```

### HTTP Request

`GET http://IP:7216/sharder`

### URL Parameters

| Parameter   | 是否必须 | Description                         |
| ----------- | -------- | ----------------------------------- |
| requestType | true     | 获取统计数据类(默认getTxStatistics) |

### Response Data

| Parameter             | 是否必须 | Description            |
| --------------------- | -------- | ---------------------- |
| transferCount24H      | true     | 24小时转账交易数量     |
| coinBaseCount         |          | 全网转账交易次数       |
| storageDataLength24H  | true     | 24小时数据存储数据大小 |
| storageDataLength     | true     | 全网数据存储数据大小   |
| storageCount          | true     | 全网数据存储数量       |
| poolCount             |          | 全网矿池交易次数       |
| transferAmount        | true     | 全网转账交易金额数     |
| requestProcessingTime | true     |                      |
| transferCount         | true     | 全网转账交易数量       |
| transferAmount24H     | true     | 24小时转账交易金额数   |
| storageCount24H       | true     | 24小时数据存储数量     |

## 获取区块链相关常量信息

```json
curl "http://IP:7216/sharder?requestType=getBizConstants"
```

> Response:

```json
{
	"epochBeginning": 1471334888880,
	"requestProcessingTime": 0
}
```

### HTTP Request

`GET http://IP:7216/sharder`

### URL Parameters

| Parameter   | 是否必须 | Description                                   |
| ----------- | -------- | --------------------------------------------- |
| requestType | true     | 获取区块链相关常量信息类(默认getBizConstants) |

### Response Data

| Data                  | 是否必须 | Description |
| --------------------- | -------- | ----------- |
| epochBeginning        | true     | 创世时间    |
| requestProcessingTime | false    |             |

## 获取区块最新高度

```json
curl "http://IP:7216/sharder?requestType=getLastBlockHeight"
```

> Response:

```json
{
	"requestProcessingTime": 0,
	"height": 10461
}
```

### HTTP Request

`GET http://IP:7216/sharder`

### URL Parameters

| Parameter   | 是否必须 | Description                                |
| ----------- | -------- | ------------------------------------------ |
| requestType | true     | 获取区块最新高度类(默认getLastBlockHeight) |

Response Data

| Data                  | 是否必须 | Description |
| --------------------- | -------- | ----------- |
| height                | true     | 区块高度    |
| requestProcessingTime | false    |             |


## 获取指定区块高度信息

```json
curl "http://IP:7216/sharder?requestType=getTransactions&height=10500&type=0&pageNo=1&pageSize=10"
```

> Response:

```json
[{
	"height": 9739,
	"payloadLength": 2106,
	"timestamp": 121801612,
	"generator": "16774301533949110090",
	"generatorRS": "CDW-9BUC-DVZ7-799H-GCLLK",
	"transactions": [{
		"type": 0,
		"height": 9739,
		"timestamp": 121801361,
		"confirmations": 729,
		"transactionId": "11143166863639983096",
		"hash": "f8332a34397ba49a4230d3aef7d14c68fc581726ce71c75da2dbf335b9499929",
		"index": 6,
		"amount": 12,
		"fee": 1,
		"sender": "CDW-MT45-DF9U-ZGJE-32K3D",
		"recipient": "CDW-J76A-GJYB-KG36-HCF8M"
	}, {
		"type": 0,
		"height": 9739,
		"timestamp": 121801479,
		"confirmations": 729,
		"transactionId": "1364780910761681023",
		"hash": "7f202fe601adf012ad356ba69186fe2df67ef5553614a7e653cd624e1e92a73c",
		"index": 8,
		"amount": 300,
		"fee": 1,
		"sender": "CDW-6JBY-5J87-LVNL-6LW9U",
		"recipient": "CDW-J76A-GJYB-KG36-HCF8M"
	}],
	"numberOfTransactions": 10,
	"blockId": "9666004775109083975",
	"previousBlockId": "14251166280691501714",
	"totalFee": 2.00000007,
	"totalAmount": 1645
}]
```

### HTTP Request

`GET http://IP:7216/sharder`

### URL Parameters

| Parameter   | 是否必须 | Description                             |
| ----------- | -------- | --------------------------------------- |
| requestType | true     | 获取指定区块高度类(默认getTransactions) |
| height      | true     | 区块高度                                |
| type        | true     | 数据类型（ 0代表转账，9代表出块 ）      |
| pageNo      | true     | 获取数据起始索引                        |
| pageSize    | true     | 获取数据结束索引                        |

### Response Data

| Data                 | 是否必须 | Description                                           |
| -------------------- | -------- | ----------------------------------------------------- |
| height               | true     | 区块高度                                              |
| payloadLength        |          | 区块字节长度                                           |
| timestamp            | true     | 加上创世纪时间为交易时间(创世纪时间由常量信息API获取) |
| generator            |          | MW 地址元数据                                          |
| generatorRS          |          | MW 地址                                               |
| type                 | true     | 交易类型(0为转账，9为出块)                            |
| confirmations        |          | 区块高度确认值（当前交易区块ID同当前最高区块高度差异值）  |
| transactionId        | true     | 交易ID                                                |
| hash                 | true     | 交易哈希                                              |
| index                |          | 交易顺序号                                            |
| amount               | true     | 交易金额                                              |
| fee                  | true     | 交易手续费                                            |
| sender               | true     | 发送方                                                |
| recipient            | true     | 接收方                                                |
| numberOfTransactions |          | 当前区块交易总数                                       |
| blockId              |          | 区块ID                                                |
| previousBlockId      |          | 上一区块ID                                            |
| totalFee             | true     | 总手续费                                              |
| totalAmount          | true     | 总交易成交额                                          |

## 获取账户地址信息

```json
curl "http://IP:7216/sharder?requestType=getAccountInfo&account=CDW-7ZUQ-VGGW-EUVW-CFKMS"
```

> Response:

```json
{
	"accountId": "5941498711528046973",
	"balance": 1479.00000006,
	"accountRS": "CDW-62DX-M753-B6JT-7K5X6",
	"frozenBalance": 0,
	"forgedBalance": 14698.00000006,
	"publicKey": "e91e148f62ed97e2689a86a638a6d87dec5aea467353bc1f3651269b5f167859",
	"requestProcessingTime": 1,
	"account": "5941498711528046973",
	"frozenBalanceNQT": "0"
}
```

### HTTP Request

`GET http://IP:7216/sharder`

### URL Parameters

| Parameter   | 是否必须 | Description                        |
| ----------- | -------- | ---------------------------------- |
| requestType | true     | 获取账户信息类(默认getAccountInfo) |
| account     | true     | 账户地址                           |

### Response Data

| Data                  | 是否必须 | Description |
| --------------------- | -------- | ----------- |
| accountId             |          | MW 地址信息 |
| balance               | true     | 账户余额    |
| accountRS             | true     | MW 地址    |
| frozenBalance         |          |             |
| forgedBalance         | true     | 出块奖励    |
| publicKey             | true     | 公钥        |
| requestProcessingTime |          |             |
| account               |          | MW 地址信息  |
| frozenBalanceNQT      |          |             |

## 获取账户交易记录

```json
curl "http://IP:7216/sharder?requestType=getAccountTxs&account=CDW-7ZUQ-VGGW-EUVW-CFKMS&firstIndex=0&lastIndex=9"
```

> Response:

```json
[{
	"type": 9,
	"height": 10461,
	"timestamp": 122235798,
	"confirmations": 6,
	"transactionId": "5850549255532855839",
	"hash": "1f42f6e48c5331512fda3294748e11b7c99ca310b0b27597e665ca886f8e40ff",
	"index": 3,
	"amount": 1333,
	"fee": 0,
	"sender": "CDW-62DX-M753-B6JT-7K5X6"
}, {
	"type": 0,
	"height": 9648,
	"timestamp": 121746646,
	"confirmations": 819,
	"transactionId": "9496177762981627047",
	"hash": "a7c47bce5c33c9830b56c1c991c9945fdfb1ebf040c24488a7a80928405ec9d7",
	"index": 10,
	"amount": 1330,
	"fee": 1,
	"sender": "CDW-62DX-M753-B6JT-7K5X6",
	"recipient": "CDW-Y7HY-PH5L-ECH6-9DMUJ"
}]
```

### HTTP Request

`GET http://IP:7216/sharder`

### URL Parameters

| Parameter   | 是否必须 | Description                           |
| ----------- | -------- | ------------------------------------- |
| requestType | true     | 获取账户交易信息类(默认getAccountTxs) |
| account     | true     | MW 地址                              |
| firstIndex  | true     | 数据起始索引                          |
| lastIndex   | true     | 数据结束索引                          |

### Response Data

| Data          | 是否必须 | Description                                           |
| ------------- | -------- | ----------------------------------------------------- |
| height        | true     | 区块高度                                              |
| timestamp     | true     | 加上创世纪时间为交易时间(创世纪时间由常量信息API获取) |
| type          | true     | 交易类型(0为转账，9为出块)                            |
| confirmations |          | 区块高度确认值（当前交易区块ID同当前最高区块高度差异值）  |
| transactionId | true     | 交易ID                                                |
| hash          | true     | 交易哈希                                              |
| index         |          | 交易顺序号                                            |
| amount        | true     | 交易金额                                              |
| fee           | true     | 交易手续费                                            |
| sender        | true     | 发送方                                                |
| recipient     | true     | 接收方                                                |