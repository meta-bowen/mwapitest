---
ytitle: MW API 文档

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
curl "http://IP/sharder?requestType=getBizBlocks&firstIndex=0&lastIndex=10"
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

`GET http://IP/sharder`

### Query Parameters

| Parameter   | 是否必须 | Description                          |
| ----------- | -------- | ------------------------------------ |
| requestType | true     | 获取主页区块高度类(默认getBizBlocks) |
| firstIndex  | true     | 数据条数起始索引                     |
| lastIndex   | true     | 数据条数结束索引                     |

### Response Data

| Parameter            | 是否必须 | Description                                              |
| -------------------- | -------- | -------------------------------------------------------- |
| height               | true     | 区块高度                                                 |
| payloadLength        |          |                                                          |
| timestamp            | true     | 加上创世纪时间为交易时间(创世纪时间由常量信息API获取)    |
| generator            |          | MW 地址元数据                                            |
| generatorRS          |          | MW 地址                                                  |
| type                 | true     | 交易类型(0为转账，9为出块)                               |
| confirmations        |          | 区块高度确认值（当前交易区块ID同当前最高区块高度差异值） |
| transactionId        | true     | 交易ID                                                   |
| hash                 | true     | 交易哈希                                                 |
| index                |          | 交易顺序号                                               |
| amount               | true     | 交易金额                                                 |
| fee                  | true     | 交易手续费                                               |
| sender               | true     | 发送方                                                   |
| recipient            | true     | 接收方                                                   |
| numberOfTransactions |          | 当前区块交易总数                                         |
| blockId              |          | 区块ID                                                   |
| previousBlockId      |          | 上一区块ID                                               |
| totalFee             | true     | 总手续费                                                 |
| totalAmount          | true     | 总交易成交额                                             |

## 获取统计数据

```json
curl "http://IP/sharder?requestType=getTxStatistics"
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

`GET http://IP/sharder`

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
| requestProcessingTime | true     |                        |
| transferCount         | true     | 全网转账交易数量       |
| transferAmount24H     | true     | 24小时转账交易金额数   |
| storageCount24H       | true     | 24小时数据存储数量     |

## 获取区块链相关常量信息

```json
curl "http://IP/sharder?requestType=getBizConstants"
```

> Response:

```json
{
	"epochBeginning": 1471334888880,
	"requestProcessingTime": 0
}
```

### HTTP Request

`GET http://IP/sharder`

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
curl "http://IP/sharder?requestType=getLastBlockHeight"
```

> Response:

```json
{
	"requestProcessingTime": 0,
	"height": 10461
}
```

### HTTP Request

`GET http://IP/sharder`

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
curl "https://IP/sharder?requestType=getBlock&block=&includeTransactions=true&height=19032"
```

> Response:

```json
{
	"previousBlockHash": "6d52cd5b84a1f6fe1fdc97d35c24d9a3f95a8552c984d56eefc5854034b24a65",
	"payloadLength": 88733,
	"totalAmountNQT": "19861300000000",
	"generationSignature": "0ba3c68d40e47c009a7199d24b2a836f82de9191ca7361b28cb5f87c3cd6b132",
	"generator": "10313978984520217777",
	"generatorPublicKey": "bd7c0964d296fef262a9ad5030f673cf0f72ad3e012a6cc3ba603e6055ec087b",
	"baseTarget": "1538547747",
	"payloadHash": "640849ba67bcd74649c6ddc4e5f8c36ba301b46c62f4a665b753592d1d93b518",
	"generatorRS": "CDW-RX7K-9QEL-ME83-AXNAY",
	"nextBlock": "17627414698179974537",
	"requestProcessingTime": 34,
	"numberOfTransactions": 3,
	"blockSignature": "4f5a0bc0c6a4bd9417b9116ee557a5f3cae9dd67a9c36ecab24cb9d9f8794c041f9012a077fbb9fab456174da710bb0a82c8ad7d3c7919642229c3e17edf887b",
	"transactions": [{
		"signature": "17cc1d56aaa2490aed070b376bd658fb5db12cbca383240e87a7272279df270998cfa16ac11870bce528522de25f52c76c614ff697aec381c30b789479327700",
		"transactionIndex": 0,
		"type": 0,
		"phased": false,
		"ecBlockId": "16594053589907885347",
		"signatureHash": "728ce6a2975bb7423ca0c10777060daaa69e10b122d0577efa0a29b1f4aa56c4",
		"attachment": {
			"crowdMinerRewardAmount": 66700000000,
			"version.OrdinaryPayment": 0,
			"version.PublicKeyAnnouncement": 1,
			"recipientPublicKey": "0e225838acf7af204c6a414f579dccc9a142a7fbd6876ff6329ab03ef0f22e0b",
			"blockMiningRewardAmount": 66600000000
		},
		"senderRS": "CDW-U6AA-JDEU-HG85-AWB8F",
		"subtype": 0,
		"amountNQT": "19728000000000",
		"recipientRS": "CDW-QPXN-9JKC-EEAG-F7TMM",
		"block": "18349131499253421136",
		"blockTimestamp": 127509962,
		"deadline": 1440,
		"timestamp": 127509455,
		"height": 19012,
		"senderPublicKey": "94455406c8f59c21f2e76aa2a1c1a8b59b641b92110a4bd395ad97420231b73b",
		"feeNQT": "100000000",
		"confirmations": 20,
		"fullHash": "5d03116770d06d404063b7d20c656706f35d5efe3470f4f70ac3255427f3f00c",
		"version": 3,
		"accountId": "-8747894268495064824",
		"sender": "9698849805214486792",
		"recipient": "15694804166619387828",
		"ecBlockHeight": 18290,
		"transaction": "4642595972072932189"
	}, {
		"signature": "79fb96e03e09f6e0a84a420e9ba240b57c615429ec057b183dbe927a2c13ee0127974b4e6209664342d5d7097bcd2ae9621d8d23b3d4dd5d9238c03f3d44a738",
		"transactionIndex": 1,
		"type": 12,
		"phased": false,
		"ecBlockId": "4164114900037633390",
		"signatureHash": "67b726d6ada3c5e9f4ca7014215547dc2cbf323c2975b7e62236781e5a7a1e8e",
		"attachment": {
			"accountId": "-6521365228936986480",
			"version.pocNodeType": 1,
			"ip": "192.168.2.30",
			"type": 4,
			"crowdMinerRewardAmount": 66700000000,
			"diskCapacity": "93138953888",
			"blockMiningRewardAmount": 66600000000
		},
		"senderRS": "CDW-38C9-Z68H-PWKP-FCJTD",
		"subtype": 0,
		"amountNQT": "0",
		"recipientRS": "CDW-326J-W2ZC-Z5Q4-CNVZC",
		"block": "18349131499253421136",
		"blockTimestamp": 127509962,
		"deadline": 10,
		"timestamp": 127509920,
		"height": 19012,
		"senderPublicKey": "1f8089fbec39da5fdbd2ba744ed7354727519260ef4407393d1f67c9cfdf2359",
		"feeNQT": "1",
		"confirmations": 20,
		"fullHash": "d915690fdf25c500641293b1c3783e3b4086f3d875642041328e57a4f4f231d1",
		"version": 3,
		"accountId": "-3033725234207221433",
		"sender": "15413018839502330183",
		"recipient": "11925378844772565136",
		"ecBlockHeight": 18291,
		"transaction": "55492210378479065"
	}, {
		"senderPublicKey": "bd7c0964d296fef262a9ad5030f673cf0f72ad3e012a6cc3ba603e6055ec087b",
		"signature": "bebe604fd8ce4329d42c7ca583fcd39e925da2ccea2770428c5b73b104f81e01eba7a654516b443d1dd3b37dc082f2a5ffc953cfa67f98e9ef8ae5ea85eb6d67",
		"feeNQT": "0",
		"transactionIndex": 2,
		"type": 9,
		"confirmations": 20,
		"fullHash": "6128a91d7a54657a0d5b33825bfaa84665bfd277117dca0845a96d7c50d35625",
		"version": 3,
		"phased": false,
		"ecBlockId": "4164114900037633390",
		"accountId": "-8132765089189333839",
		"signatureHash": "ef42a36273578921b54e9515bbbb96f082cc9ce57a548249ed38319491099e54",
		"attachment": {
			"generatorId": "-8132765089189333839",
			"creator": "-8132765089189333839",
			"version.OrdinaryCoinBase": 1,
			"consignors": {},
			"crowdMiners": [{
				"accountId": -8319463323115108487,
				"accountRS": "CDW-CKVT-7YHX-2FE7-ANU4T",
				"pocScore": 51021000,
				"rewardAmount": 11908764
			}, {
				"accountId": -8132765089189333839,
				"accountRS": "CDW-RX7K-9QEL-ME83-AXNAY",
				"pocScore": -1,
				"rewardAmount": 22336
			}],
			"crowdMinerRewardAmount": 66700000000,
			"coinBaseType": "CROWD_BLOCK_REWARD",
			"blockMiningRewardAmount": 66600000000
		},
		"senderRS": "CDW-RX7K-9QEL-ME83-AXNAY",
		"subtype": 0,
		"amountNQT": "133300000000",
		"sender": "10313978984520217777",
		"ecBlockHeight": 18291,
		"block": "18349131499253421136",
		"blockTimestamp": 127509962,
		"deadline": 10,
		"transaction": "8819548328735352929",
		"timestamp": 127509962,
		"height": 19012
	}],
	"version": 3,
	"totalFeeNQT": "100000001",
	"accountId": "-8132765089189333839",
	"previousBlock": "18372049319752454765",
	"cumulativeDifficulty": "226414775842292",
	"block": "18349131499253421136",
	"height": 19012,
	"timestamp": 127509962
}
```

### HTTP Request

`GET http://IP/sharder`

### URL Parameters

| Parameter           | 是否必须 | Description                      |
| ------------------- | -------- | -------------------------------- |
| requestType         | true     | 获取指定区块高度类(默认getBlock) |
| block               | false    |                                  |
| includeTransactions | true     |                                  |
| height              | true     | 区块高度                         |

### Response Data

| Parameter                     | 是否必须 | Description                                           |
| ----------------------------- | -------- | ----------------------------------------------------- |
| previousBlockHash             | true     | 上一区块哈希                                          |
| payloadLength                 |          |                                                       |
| totalAmountNQT                | true     | 区块交易总金额                                        |
| generationSignature           | true     | 出块签名                                              |
| generator                     | true     | 出块者账号ID                                          |
| generatorPublicKey            | true     | 出块者公钥                                            |
| baseTarget                    |          |                                                       |
| payloadHash                   |          |                                                       |
| generatorRS                   | true     | 出块账号                                              |
| nextBlock                     | false    | 下一区块ID                                            |
| requestProcessingTime         |          |                                                       |
| numberOfTransactions          | false    | 区块交易数量                                          |
| blockSignature                | true     | 出块签名                                              |
| signature                     | true     | 签名                                                  |
| transactionIndex              | true     | 交易序列号                                            |
| type                          | true     | 交易类型                                              |
| phased                        |          |                                                       |
| ecBlockId                     |          |                                                       |
| signatureHash                 | true     | 哈希签名                                              |
| accountId                     | true     | 账户ID                                                |
| senderRS                      | true     | 发送者                                                |
| subtype                       |          |                                                       |
| amountNQT                     | true     | 交易金额                                              |
| recipientRS                   | true     | 接收者                                                |
| block                         | false    | 区块ID                                                |
| blockTimestamp                | true     | 加上创世纪时间为区块时间(创世纪时间由常量信息API获取) |
| deadline                      |          |                                                       |
| transactions.timestamp        | true     | 加上创世纪时间为交易时间(创世纪时间由常量信息API获取) |
| height                        | true     | 区块高度                                              |
| senderPublicKey               | true     | 发送者公钥                                            |
| feeNQT                        | true     | 交易手续费                                            |
| confirmations                 | true     | 确认数                                                |
| fullHash                      | true     | 完整哈希                                              |
| version                       | true     | 版本                                                  |
| sender                        | false    | 发送者账户ID                                          |
| recipient                     | false    | 接收者账户ID                                          |
| ecBlockHeight                 |          |                                                       |
| transaction                   | true     | 交易ID                                                |
| totalFeeNQT                   | true     | 区块总交易手续费                                      |
| cumulativeDifficulty          |          |                                                       |
| previousBlock                 | false    | 上一区块ID                                            |
| block                         | false    | 区块ID                                                |
| timestamp                     | true     | 加上创世纪时间为区块时间(创世纪时间由常量信息API获取) |
| attachment.type               |          |                                                       |
| version.pocNodeType           |          |                                                       |
| diskCapacity                  | true     | 硬盘容量                                              |
| ip                            | true     | 矿机IP                                                |
| crowdMinerRewardAmount        |          | 合格矿工奖励总数                                      |
| version.OrdinaryPayment       |          |                                                       |
| version.PublicKeyAnnouncement |          |                                                       |
| blockMiningRewardAmount       | true     | 出块这奖励数                                          |
| accountRS                     | true     | 合格矿工张合                                          |
| pocScore                      | true     | 合格矿工得分                                          |
| rewardAmount                  | true     | 合格矿工奖励                                          |
| coinBaseType                  |          |                                                       |

## 获取账户地址信息

```json
curl "https://IP/sharder?requestType=getAccount&account=CDW-D9EW-Z6R5-S3RN-6GN2A"
```

> Response:

```json
{
	"unconfirmedBalanceNQT": "81300279411",
	"accountId": "4900636545405787548",
	"accountRS": "CDW-D9EW-Z6R5-S3RN-6GN2A",
	"pocScore": 56013000,
	"forgedBalanceNQT": "1011000257219",
	"balanceNQT": "81300279411",
	"publicKey": "61d14a74f7c1b50fb3d6b640e42482ca5999ff1f4ecd9f4d9a50f4ebf19f9e52",
	"requestProcessingTime": 1065,
	"account": "4900636545405787548",
	"frozenBalanceNQT": "66600022192"
}
```

### HTTP Request

`GET http://IP/sharder`

### URL Parameters

| Parameter   | 是否必须 | Description                        |
| ----------- | -------- | ---------------------------------- |
| requestType | true     | 获取账户信息类(默认getAccountInfo) |
| account     | true     | 账户地址                           |

### Response Data

| Data                  | 是否必须 | Description          |
| --------------------- | -------- | -------------------- |
| unconfirmedBalanceNQT | false    | 不包含未确认余额     |
| accountId             | true     | 账户ID               |
| accountRS             | true     | 账户地址             |
| pocScore              | true     | poc得分              |
| forgedBalanceNQT      | true     |                      |
| balanceNQT            | true     | 资产                 |
| publicKey             | true     | 公钥(包含未确认余额) |
| account               |          | 账户ID               |

## 获取账户交易记录

```json
curl "https://IP/sharder?requestType=getBlockchainTransactions&account=CDW-D9EW-Z6R5-S3RN-6GN2A&firstIndex=0&lastIndex=9&type=0"
```

> Response:

```json
{
	"requestProcessingTime": 18,
	"transactions": [{
		"senderPublicKey": "dddd1e628f2637729084c1d2b9179b3008f91c41b7487d4f324b4448b2e2b469",
		"signature": "1271dde3eca1f85ec843a10ef3072c352fcef4f8942e8257498415cf3b2e7909760cb450ee19bc0af09a903d6978177eff9be6cf6a1d954c9d530311abd4d1dc",
		"feeNQT": "0",
		"transactionIndex": 4,
		"type": 9,
		"confirmations": 28,
		"fullHash": "5602d5b2b70c25b9d784eaeff58946f08d885755dc870f08d6d60fb29c355512",
		"version": 3,
		"phased": false,
		"ecBlockId": "9641760708857530191",
		"accountId": "4224284679494006128",
		"signatureHash": "4cb995df898f283dcbf8153c704203fafdb99466a2db7be96c14affa7214d2b3",
		"attachment": {
			"generatorId": "4224284679494006128",
			"creator": "4224284679494006128",
			"version.OrdinaryCoinBase": 1,
			"consignors": {},
			"crowdMiners": [{
				"accountId": -8319463323115108487,
				"accountRS": "CDW-CKVT-7YHX-2FE7-ANU4T",
				"pocScore": 51021000,
				"rewardAmount": 11913547
			}, {
				"accountId": 3242614234900699037,
				"accountRS": "CDW-57WX-GXRG-7ASB-4N22U",
				"pocScore": 56610000,
				"rewardAmount": 13218592
			},],
			"crowdMinerRewardAmount": 66700000000,
			"coinBaseType": "CROWD_BLOCK_REWARD",
			"blockMiningRewardAmount": 66600000000
		},
		"senderRS": "CDW-UXDJ-K5MP-4MYH-5EX9P",
		"subtype": 0,
		"amountNQT": "133300000000",
		"sender": "4224284679494006128",
		"ecBlockHeight": 18287,
		"block": "15027402603411333235",
		"blockTimestamp": 127507558,
		"deadline": 10,
		"transaction": "13341083454273815126",
		"timestamp": 127507558,
		"height": 19008
	}, {
		"signature": "aae46e716c6a57ec0b7280a7a5ecee9b2e4d2a9371a8570904b7cf4bea281705c546412c084ef22151d3285ca6f1ca3f8d35a219632221e7ba8e84d0217852ef",
		"transactionIndex": 40,
		"type": 12,
		"phased": false,
		"ecBlockId": "6828121706591172454",
		"signatureHash": "b260514ee0fc4a7437a606a6dcef9b7adf397e3a153dbf02d2bb4ca2f5299aa6",
		"attachment": {
			"accountId": "4224284679494006128",
			"version.pocNodeType": 1,
			"ip": "8.210.18.74",
			"type": 4,
			"crowdMinerRewardAmount": 66700000000,
			"diskCapacity": "108642222504",
			"blockMiningRewardAmount": 66600000000
		},
		"senderRS": "CDW-38C9-Z68H-PWKP-FCJTD",
		"subtype": 0,
		"amountNQT": "0",
		"recipientRS": "CDW-UXDJ-K5MP-4MYH-5EX9P",
		"block": "6459573796439535632",
		"blockTimestamp": 127088367,
		"deadline": 10,
		"timestamp": 127088330,
		"height": 18311,
		"senderPublicKey": "1f8089fbec39da5fdbd2ba744ed7354727519260ef4407393d1f67c9cfdf2359",
		"feeNQT": "1",
		"confirmations": 725,
		"fullHash": "1494ae012b939f0f1f9f179a3ba1aaeb8beeb1454f55db1d6807401679f463f8",
		"version": 3,
		"accountId": "-3033725234207221433",
		"sender": "15413018839502330183",
		"recipient": "4224284679494006128",
		"ecBlockHeight": 17590,
		"transaction": "1125780244787008532"
	}, {
		"signature": "7dbb812137124a3729ecec7a9fb99b90e9c024b96de45e6b42c2640313a6b804881fec1127bd7cff4eb17cd37275c6fc2f2b8c60b699149dcb40bee8fbcbc796",
		"transactionIndex": 10,
		"type": 0,
		"phased": false,
		"ecBlockId": "6828121706591172454",
		"signatureHash": "a16c51b4cc4c7ff0a31d58c4de7c023ebfd01b8a916332a23b078aa662dcf87b",
		"attachment": {
			"crowdMinerRewardAmount": 66700000000,
			"version.OrdinaryPayment": 0,
			"version.PublicKeyAnnouncement": 1,
			"recipientPublicKey": "dddd1e628f2637729084c1d2b9179b3008f91c41b7487d4f324b4448b2e2b469",
			"blockMiningRewardAmount": 66600000000
		},
		"senderRS": "CDW-AJCK-9H7X-UCUJ-8VRKG",
		"subtype": 0,
		"amountNQT": "425900000000",
		"recipientRS": "CDW-UXDJ-K5MP-4MYH-5EX9P",
		"block": "6459573796439535632",
		"blockTimestamp": 127088367,
		"deadline": 1440,
		"timestamp": 127088281,
		"height": 18311,
		"senderPublicKey": "240ff5044af200a67aeea5e364dc970194d98c4e3bb3a931b5d9ee28361a366d",
		"feeNQT": "100000000",
		"confirmations": 725,
		"fullHash": "210025001b0b4993e625d902da41b0822bbbbb16af19ee48a066fb603727d5cb",
		"version": 3,
		"accountId": "7441911668517650769",
		"sender": "7441911668517650769",
		"recipient": "4224284679494006128",
		"ecBlockHeight": 17590,
		"transaction": "10613026207469731873"
	}]
}
```

### HTTP Request

`GET http://IP/sharder`

### URL Parameters

| Parameter   | 是否必须 | Description                                       |
| ----------- | -------- | ------------------------------------------------- |
| requestType | true     | 获取账户交易信息类(默认getBlockchainTransactions) |
| account     | false    | MW 地址                                           |
| firstIndex  | false    | 数据起始索引                                      |
| lastIndex   | false    | 数据结束索引                                      |
| type        | false    | 交易类型                                          |

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
| accountRS                     | false    | 合格矿工账户                                              |
| pocScore                      | false    | poc得分                                                   |
| rewardAmount                  | false    | 合格矿工奖励                                              |
| blockMiningRewardAmount       | false    | 出块者奖励                                                |
| coinBaseType                  |          |                                                           |
| crowdMinerRewardAmount        | false    | 合格矿工奖励总数                                          |
| ip                            | false    | 声明IP                                                    |
| diskCapacity                  | false    | 声明容量                                                  |
| attachment.type               |          |                                                           |

# 链上 API

## getLatestCosVersion

```shell
curl "http://IP:7216/sharder?requestType=getLatestCosVersion"
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

`GET http://IP:7216/sharder`

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
curl "http://IP:7216/sharder?requestType=getBlockchainTransactions&account=CDW-BRNL-6BXD-TM34-5PMMZ&firstIndex=0&lastIndex=9&type=9"
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

`GET http://IP:7216/sharder`

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
| accountRS                     | false    | 合格矿工账户                                              |
| pocScore                      | false    | poc得分                                                   |
| rewardAmount                  | false    | 合格矿工奖励                                              |
| blockMiningRewardAmount       | false    | 出块者奖励                                                |
| coinBaseType                  |          |                                                           |
| crowdMinerRewardAmount        | false    | 合格矿工奖励总数                                          |
| ip                            | false    | 声明IP                                                    |
| diskCapacity                  | false    | 声明容量                                                  |
| attachment.type               |          |                                                           |

## getPeers

```shell
curl "http://IP:7216/sharder?requestType=getPeers&state=CONNECTED&random=0.5637220664429662&includeOwn=true&includePeerInfo=true"
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

`GET http://IP:7216/sharder`

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
curl "http://IP:7216/sharder?requestType=getUnconfirmedTransactions&random=1595057247203&account=4597741060539866770"
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

`GET http://IP:7216/sharder`

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
curl "http://IP:7216/sharder?requestType=getUserConfig&random=1595057242079"
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

`GET http://IP:7216/sharder`

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
curl "http://IP:7216/sharder?requestType=getBlockchainStatus&random=0.5325304383349927"
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

`GET http://IP:7216/sharder`

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
curl "http://IP:7216/sharder?requestType=getAccount&account=4597741060539866770&includeAssets=true&includeCurrencies=true&includeLessors=true&includeEffectiveBalance=true&random=0.08781158929285926"
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

`GET http://IP:7216/sharder`

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
| accountId             | false    | 账户ID       |
| accountRS             | true     | 账户地址     |
| pocScore              | true     | poc得分      |
| forgedBalanceNQT      | true     | 账户出块奖励 |
| balanceNQT            | true     | 账户余额     |
| effectiveBalanceNQT   | false    | 可用余额     |
| publicKey             | true     | 账户公钥     |
| requestProcessingTime | false    | 请求处理时间 |
| account               | false    | 账户ID       |
| frozenBalanceNQT      | false    | 冻结金额     |

## getForging

```shell
curl "http://IP:7216/sharder?requestType=getForging"
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

`POST http://IP:7216/sharder`

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
curl "http://IP:7216/sharder?requestType=stopMining"
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

`POST http://IP:7216/sharder`

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
curl "http://IP:7216/sharder?requestType=getDGSPurchaseCount&seller=4597741060539866770&completed=true&random=0.852988454945699"
```

> Response:

```json
{
  "numberOfPurchases": 0,
  "requestProcessingTime": 1
}
```

### HTTP Request

`GET http://IP:7216/sharder`

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
curl "http://IP:7216/sharder?requestType=getDGSPendingPurchases&seller=4597741060539866770&random=0.6369620754760852"
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

`GET http://IP:7216/sharder`

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
curl "http://IP:7216/sharder?requestType=getAliasCount&account=4597741060539866770&random=0.21013835024125904"
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

`GET http://IP:7216/sharder`

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
curl "http://IP:7216/sharder?requestType=getLastTrades&assets=25461532156"
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

`GET http://IP:7216/sharder`

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
curl "http://IP:7216/sharder?requestType=getVoterPhasedTransactions&account=265523835724773959&firstIndex=0&lastIndex=20&random=0.02052225643621064"
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

`GET http://IP:7216/sharder`

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
curl "http://IP:7216/sharder?requestType=getAccountPublicKey&account=4597741060539866770&random=0.7889226609636362"
```

> Response:

```json
{
  "publicKey": "269670d2f58d5d663dc469ab7cd42e36c096d2d488fb4c7b57279157cb87a417",
  "requestProcessingTime": 0
}
```

### HTTP Request

`GET http://IP:7216/sharder`

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
curl "http://IP:7216/sharder?requestType=getBlock&height=6212&block=&includeTransactions=true"
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

`GET http://IP:7216/sharder`

### Query Parameters

| Parameter           | 是否必须 | Description                        |
| ------------------- | -------- | ---------------------------------- |
| requestType         | true     | 获取指定高度交易信息定值(getBlock) |
| height              | true     | 区块高度                           |
| block               | false    | 区块ID                             |
| includeTransactions | false    | 是否包含交易详情(默认false)        |

### Response Data

| Parameter                     | 是否必须 | Description                                           |
| ----------------------------- | -------- | ----------------------------------------------------- |
| previousBlockHash             | true     | 上一区块哈希                                          |
| payloadLength                 |          |                                                       |
| totalAmountNQT                | true     | 区块交易总金额                                        |
| generationSignature           | true     | 出块签名                                              |
| generator                     | true     | 出块者账号ID                                          |
| generatorPublicKey            | true     | 出块者公钥                                            |
| baseTarget                    |          |                                                       |
| payloadHash                   |          |                                                       |
| generatorRS                   | true     | 出块账号                                              |
| nextBlock                     | false    | 下一区块ID                                            |
| requestProcessingTime         |          |                                                       |
| numberOfTransactions          | false    | 区块交易数量                                          |
| blockSignature                | true     | 出块签名                                              |
| signature                     | true     | 签名                                                  |
| transactionIndex              | true     | 交易序列号                                            |
| type                          | true     | 交易类型                                              |
| phased                        |          |                                                       |
| ecBlockId                     |          |                                                       |
| signatureHash                 | true     | 哈希签名                                              |
| accountId                     | true     | 账户ID                                                |
| senderRS                      | true     | 发送者                                                |
| subtype                       |          |                                                       |
| amountNQT                     | true     | 交易金额                                              |
| recipientRS                   | true     | 接收者                                                |
| block                         | false    | 区块ID                                                |
| blockTimestamp                | true     | 加上创世纪时间为区块时间(创世纪时间由常量信息API获取) |
| deadline                      |          |                                                       |
| transactions.timestamp        | true     | 加上创世纪时间为交易时间(创世纪时间由常量信息API获取) |
| height                        | true     | 区块高度                                              |
| senderPublicKey               | true     | 发送者公钥                                            |
| feeNQT                        | true     | 交易手续费                                            |
| confirmations                 | true     | 确认数                                                |
| fullHash                      | true     | 完整哈希                                              |
| version                       | true     | 版本                                                  |
| sender                        | false    | 发送者账户ID                                          |
| recipient                     | false    | 接收者账户ID                                          |
| ecBlockHeight                 |          |                                                       |
| transaction                   | true     | 交易ID                                                |
| totalFeeNQT                   | true     | 区块总交易手续费                                      |
| cumulativeDifficulty          |          |                                                       |
| previousBlock                 | false    | 上一区块ID                                            |
| block                         | false    | 区块ID                                                |
| timestamp                     | true     | 加上创世纪时间为区块时间(创世纪时间由常量信息API获取) |
| attachment.type               |          |                                                       |
| version.pocNodeType           |          |                                                       |
| diskCapacity                  | true     | 硬盘容量                                              |
| ip                            | true     | 矿机IP                                                |
| crowdMinerRewardAmount        |          | 合格矿工奖励总数                                      |
| version.OrdinaryPayment       |          |                                                       |
| version.PublicKeyAnnouncement |          |                                                       |
| blockMiningRewardAmount       | true     | 出块这奖励数                                          |
| accountRS                     | true     | 合格矿工张合                                          |
| pocScore                      | true     | 合格矿工得分                                          |
| rewardAmount                  | true     | 合格矿工奖励                                          |
| coinBaseType                  |          |                                                       |

## getAccountId

```shell
curl "http://IP:7216/sharder?requestType=getAccountId&accoutId=-3532411906506360547,4597741060539866770"
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

`GET http://IP:7216/sharder`

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
curl "http://IP:7216/sharder?requestType=getTransaction&transaction=13854539770161423054"
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

`GET http://IP:7216/sharder`

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
curl "http://IP:7216/sharder?requestType=getTxStatistics"
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

`GET http://IP:7216/sharder`

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
curl "http://IP:7216/sharder?requestType=getBizConstants"
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

`GET http://IP:7216/sharder`

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
curl "http://IP:7216/sharder?requestType=getNextBlockGenerators&limit=99999"
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

`GET http://IP:7216/sharder`

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

# 链上转账交易API

## 根据密钥获取账户地址信息

```shell
curl "https://IP:7216/sharder?requestType=getAccountId&secretPhrase=peaceful small both lord arrow son wrote courage valley tiny month return"
```

> Response:

```json
{
  "accountId": "-6408431511638602249",
  "accountRS": "CDW-T5HR-HTCP-8A97-CF76G",
  "publicKey": "be9531ebf8fa65128d562daa01ed49dbb0540e8119213f91921eeb51020cc410",
  "requestProcessingTime": 0,
  "account": "12038312562070949367"
}
```

### HTTP Request

`GET http://IP:7216/sharder`

### Query Parameters

| Parameter    | 是否必须 | Description                        |
| ------------ | -------- | ---------------------------------- |
| requestType  | true     | 根据账户地址信息定值(getAccountId) |
| secretPhrase | true     | 密钥                               |

### Response Data

| Parameter             | type | Description                |
| --------------------- | ---- | -------------------------- |
| accountId             | str  | 账号id(可用于获取账户地址) |
| accountRS             | str  | 账户地址                   |
| publicKey             | 公钥 |                            |
| requestProcessingTime | int  | 请求处理时间               |
| account               | str  | 账户编号                   |

## 根据账户地址获取公钥

```shell
curl "http://IP:7216/sharder?requestType=getAccountPublicKey&account=CDW-5MUB-G7LB-FT9S-FVJKS"
```

> Response:

```json
{
  "publicKey": "e3f81347569688e38041a7315e8edc7598770cede832c55957d01bd9dd5e741b",
  "requestProcessingTime": 0
}
```

### HTTP Request

`GET http://IP:7216/sharder`

### Query Parameters

| Parameter   | 是否必须 | Description                                   |
| ----------- | -------- | --------------------------------------------- |
| requestType | true     | 根据账户地址获取公钥定值(getAccountPublicKey) |
| account     | true     | 账户地址                                      |

### Response Data

| Parameter             | type | Description  |
| --------------------- | ---- | ------------ |
| publicKey             | str  | 公钥         |
| requestProcessingTime | int  | 请求处理时间 |

## 根据账户编号或账户地址获取可用于交易的余额

```shell
curl "https://IP:7216/sharder?requestType=getAccount&account=CDW-T5HR-HTCP-8A97-CF76G&includeLessors=true&includeAssets=true&includeEffectiveBalance=true&includeCurrencies=true"
```

> Response:

```json
{
  "unconfirmedBalanceNQT": "10800000000",//108MW
  "guaranteedBalanceNQT": "10800000000",//108MW
  "accountId": "-6408431511638602249",
  "accountRS": "CDW-T5HR-HTCP-8A97-CF76G",
  "pocScore": 3580000,
  "forgedBalanceNQT": "0",
  "balanceNQT": "10800000000",//108MW
  "effectiveBalanceNQT": "10800000000",//108MW
  "publicKey": "be9531ebf8fa65128d562daa01ed49dbb0540e8119213f91921eeb51020cc410",
  "requestProcessingTime": 5,
  "account": "12038312562070949367",
  "frozenBalanceNQT": "0"
}
```

### HTTP Request

`GET http://IP:7216/sharder`

### Query Parameters

| Parameter               | 是否必须 | Description                      |
| ----------------------- | -------- | -------------------------------- |
| getAccount              | true     | 根据账户余额信息定值(getAccount) |
| account                 | true     | 账户地址或账户编号               |
| includeLessors          | true     | 值必须为true                     |
| includeAssets           | true     | 值必须为true                     |
| includeEffectiveBalance | true     | 值必须为true                     |
| includeCurrencies       | true     | 值必须为true                     |

### Response Data

| Parameter             | type | Description                            |
| --------------------- | ---- | -------------------------------------- |
| unconfirmedBalanceNQT | str  | 可用于交易的余额(注意返回示例中的换算) |
| guaranteedBalanceNQT  | str  |                                        |
| accountId             | str  | 账户ID                                 |
| accountRS             | str  | 账户地址                               |
| pocScore              | int  | poc得分                                |
| forgedBalanceNQT      | str  |                                        |
| balanceNQT            | str  | 资产(注意返回示例中的换算)             |
| effectiveBalanceNQT   | str  |                                        |
| publicKey             | str  | 公钥                                   |
| requestProcessingTime | int  | 请求处理时间                           |
| account               | str  | 账户编号                               |
| frozenBalanceNQT      | str  |                                        |

## MW转账接口

```shell
curl "http://IP:7216/sharder?requestType=sendMoney"
```

> request data:

```json
{
    "recipient": "CDW-5MUB-G7LB-FT9S-FVJKS",
    "recipientPublicKey": "e3f81347569688e38041a7315e8edc7598770cede832c55957d01bd9dd5e741b",
    "deadline": 1440,
    "phased": False,
    "phasingLinkedFullHash": '',
    "phasingHashedSecret": '',
    "phasingHashedSecretAlgorithm": 2,
    "publicKey": '',
    "feeNQT": 100000000,//1MW
    "amountNQT": 100000000,//1MW
    "secretPhrase": "hill pants completely pack nice pathetic slide fail sail message agree destroy"

}
```

> Response:

```json
//发送成功返回
{
	"signatureHash": "01fe4ec3f84b2914b363d201635c681908020439edf3e2b050d1b7b2501d4ace",
	"transactionJSON": {
		"senderPublicKey": "be9531ebf8fa65128d562daa01ed49dbb0540e8119213f91921eeb51020cc410",
		"signature": "500fd5105669c06f4b6a5a4570c25ff32c5f55701a496ddb63842469ad59930f7762a8d32baf569643dee287bf8bd05e4b53696f9c7640e6c1a2a01ef002eb63",
		"feeNQT": "100000000",//1MW
		"type": 0,
		"fullHash": "6af42738eb54ebd22150e6d5f446ae55cba2e0ef61435dd9176fe5494c86d606",
		"version": 3,
		"phased": false,
		"ecBlockId": "16226261798395275171",
		"accountId": "-6408431511638602249",
		"signatureHash": "01fe4ec3f84b2914b363d201635c681908020439edf3e2b050d1b7b2501d4ace",
		"attachment": {
			"crowdMinerRewardAmount": 66700000000, // 667MW
			"version.OrdinaryPayment": 0,
			"version.PublicKeyAnnouncement": 1,
			"recipientPublicKey": "e3f81347569688e38041a7315e8edc7598770cede832c55957d01bd9dd5e741b",
			"blockMiningRewardAmount": 66600000000 //666MW
		},
		"senderRS": "CDW-T5HR-HTCP-8A97-CF76G",
		"subtype": 0,
		"amountNQT": "100000000", //1MW
		"sender": "12038312562070949367",
		"recipientRS": "CDW-5MUB-G7LB-FT9S-FVJKS",
		"recipient": "15872404110546423625",
		"ecBlockHeight": 17591,
		"deadline": 1440,
		"transaction": "15198334736728061034",
		"timestamp": 127088938,
		"height": 2147483647
	},
	"unsignedTransactionBytes": "00302a399307a005be9531ebf8fa65128d562daa01ed49dbb0540e8119213f91921eeb51020cc41049cf9164711b46dc00e1f5050000000000e1f5050000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000004000000b7440000a367d79d22432fe101e3f81347569688e38041a7315e8edc7598770cede832c55957d01bd9dd5e741b",
	"broadcasted": true,
	"requestProcessingTime": 6,
	"transactionBytes": "00302a399307a005be9531ebf8fa65128d562daa01ed49dbb0540e8119213f91921eeb51020cc41049cf9164711b46dc00e1f5050000000000e1f505000000000000000000000000000000000000000000000000000000000000000000000000500fd5105669c06f4b6a5a4570c25ff32c5f55701a496ddb63842469ad59930f7762a8d32baf569643dee287bf8bd05e4b53696f9c7640e6c1a2a01ef002eb6304000000b7440000a367d79d22432fe101e3f81347569688e38041a7315e8edc7598770cede832c55957d01bd9dd5e741b",
	"fullHash": "6af42738eb54ebd22150e6d5f446ae55cba2e0ef61435dd9176fe5494c86d606",
	"transaction": "15198334736728061034"
}
//发送失败返回
{
    "errorDescription":"Unknown account",
    "errorCode":5
}
```

### HTTP Request

`POST http://IP:7216/sharder`

### Query Parameters

| Parameter  | 是否必须 | Description                     |
| ---------- | -------- | ------------------------------- |
| getAccount | true     | 根据账户余额信息定值(sendMoney) |

### Request Data

| Parameter                    | 是否必须 | Description                                     |
| ---------------------------- | -------- | ----------------------------------------------- |
| recipient                    | true     | 接收者账户地址                                  |
| recipientPublicKey           | false    | 接收者公钥                                      |
| deadline                     | true     |                                                 |
| phased                       | true     |                                                 |
| phasingLinkedFullHash        | true     |                                                 |
| phasingHashedSecret          | true     |                                                 |
| phasingHashedSecretAlgorithm | true     |                                                 |
| publicKey                    | false    | 发送者公钥                                      |
| feeNQT                       | true     | 转账手续费(最小值少为1MW, 注意请求示例中的换算) |
| amountNQT                    | true     | 转账数量(注意请求示例中的换算)                  |
| secretPhrase                 | true     | 发送者密钥                                      |

### Response Data

| Parameter                | type | Description                                                  |
| ------------------------ | ---- | ------------------------------------------------------------ |
| signatureHash            | str  | 可用于交易的余额                                             |
| senderPublicKey          | str  | 发送者公钥                                                   |
| signature                | str  | 签名                                                         |
| feeNQT                   | str  | 交易手续费(注意返回示例中的换算)                             |
| type                     | int  | 交易类型                                                     |
| fullHash                 | str  | 完整哈希                                                     |
| version                  | str  | 版本                                                         |
| phased                   | bool |                                                              |
| ecBlockId                | str  |                                                              |
| accountId                | str  | 账户ID                                                       |
| signatureHash            | str  | 哈希签名                                                     |
| crowdMinerRewardAmount   | int  |                                                              |
| version.OrdinaryPayment  | int  |                                                              |
| blockMiningRewardAmount  | int  |                                                              |
| senderRS                 | str  | 发送者账户地址                                               |
| subtype                  | int  |                                                              |
| amountNQT                | str  | 交易金额(注意返回示例中的换算)                               |
| sender                   | str  | 发送者账户编号                                               |
| recipientRS              | str  | 接收者账户地址                                               |
| recipient                | str  | 接收者账户编号                                               |
| ecBlockHeight            | int  |                                                              |
| deadline                 | int  |                                                              |
| transaction              | str  | 交易ID                                                       |
| timestamp                | int  | 交易时间戳(需要加上创世纪时间,其可通过getBizConstants接口获得) |
| height                   | int  |                                                              |
| unsignedTransactionBytes | str  |                                                              |
| broadcasted              | bool | true为转账发送成功,false为转账发送失败                       |
| requestProcessingTime    | int  |                                                              |
| transactionBytes         | str  |                                                              |
| errorDescription         | str  | 失败描述                                                     |
| errorCode                | int  | 失败编号                                                     |

## 查看交易是否确认

```shell
curl "http://IP:7216/sharder?requestType=getUnconfirmedTransactions&account=12038312562070949367"
```

> Response:

```json
{
  "unconfirmedTransactions": [
    {
      "senderPublicKey": "be9531ebf8fa65128d562daa01ed49dbb0540e8119213f91921eeb51020cc410",
      "signature": "fd95f380a00a9a7233e95e43574728662394bc7d0695a4f4545788e2f946b90c82be46abdf75a0fb6913209f5ad44a5f90ee6bbd731a88f069b991bea040796f",
      "feeNQT": "100000000",//1MW
      "type": 0,
      "fullHash": "3733a7352e96e181cb2b8df08141b5a448ddb211db2f4763f457bb4a49e97a26",
      "version": 3,
      "phased": false,
      "ecBlockId": "15572281294683334810",
      "accountId": "-6408431511638602249",
      "signatureHash": "61d524a75884b27d17be61ad60cdbfcc8b94c205911e7746849194135d6622db",
      "attachment": {
        "crowdMinerRewardAmount": 66700000000,//667MW
        "version.OrdinaryPayment": 0,
        "version.PublicKeyAnnouncement": 1,
        "recipientPublicKey": "e3f81347569688e38041a7315e8edc7598770cede832c55957d01bd9dd5e741b",
        "blockMiningRewardAmount": 66600000000 //666MW
      },
      "senderRS": "CDW-T5HR-HTCP-8A97-CF76G",
      "subtype": 0,
      "amountNQT": "100000000", //1MW
      "sender": "12038312562070949367",
      "recipientRS": "CDW-5MUB-G7LB-FT9S-FVJKS",
      "recipient": "15872404110546423625",
      "ecBlockHeight": 17586,
      "deadline": 1440,
      "transaction": "9358926625865413431",
      "timestamp": 127086010,
      "height": 2147483647
    }
  ],
  "requestProcessingTime": 0
}
```

### HTTP Request

`GET http://IP:7216/sharder`

### Query Parameters

| Parameter  | 是否必须 | Description                                      |
| ---------- | -------- | ------------------------------------------------ |
| getAccount | true     | 根据账户余额信息定值(getUnconfirmedTransactions) |
| account    | true     | 账户地址或账户编号                               |

### Response Data

| Parameter                     | type | Description                                                  |
| ----------------------------- | ---- | ------------------------------------------------------------ |
| senderPublicKey               | str  | 发送者公钥                                                   |
| signature                     | str  | 签名                                                         |
| feeNQT                        | str  | 交易手续费(注意返回示例中的换算)                             |
| type                          | str  | 交易类型                                                     |
| fullHash                      | int  | 完整哈希                                                     |
| version                       | str  | 版本                                                         |
| phased                        | str  |                                                              |
| ecBlockId                     | str  |                                                              |
| accountId                     | str  | 账户ID                                                       |
| signatureHash                 | int  |                                                              |
| crowdMinerRewardAmount        | str  | 合格旷工总奖励数(注意返回示例中的换算)                       |
| version.OrdinaryPayment       | str  |                                                              |
| version.PublicKeyAnnouncement |      |                                                              |
| recipientPublicKey            |      | 接收者公钥                                                   |
| blockMiningRewardAmount       |      | 出块者奖励数(注意返回示例中的换算)                           |
| senderRS                      |      | 发送者账户地址                                               |
| subtype                       |      |                                                              |
| amountNQT                     |      | 转账数量(注意返回示例中的换算)                               |
| sender                        |      | 发送者账户编号                                               |
| recipientRS                   |      | 接收者账户地址                                               |
| recipient                     |      | 接收者账户编号                                               |
| ecBlockHeight                 |      |                                                              |
| deadline                      |      |                                                              |
| transaction                   |      | 交易ID                                                       |
| timestamp                     |      | 交易时间戳(需要加上创世纪时间,其可通过getBizConstants接口获得) |
| height                        |      |                                                              |