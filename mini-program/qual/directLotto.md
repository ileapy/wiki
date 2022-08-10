# 直接抽奖

用于营销活动直接抽奖。

> 阅读本文档之前请仔细阅读[云闪付小程序官方文档 - 直接抽奖](https://opentools.95516.com/applet/#/docs/develop/api-backend?id=_02040807)

## 接口调用

```php
/**
 * 直接抽奖
 * @param array $params 更多参数
 */
$app->qual->directLotto($params = []);
```

## 更多参数

| 序号 | 参数名       | 是否必填 | 备注                                                         |
| ---- | ------------ | -------- | ------------------------------------------------------------ |
| 2    | transSeqId   | 是       | 交易流水号,不重复，最大64位                                  |
| 3    | transTs      | 是       | 请求日期,格式: yyyyMMdd                                      |
| 4    | orderAt      | 否       | 订单金额                                                     |
| 5    | nonceStr     | 是       | 随机字符串，用于验签                                         |
| 6    | mobile       | 否       | 交易手机号，若上送，（使用 symmetricKey 对称加密，内容为 base64 格式） |
| 7    | cardNo       | 否       | 交易卡号，若上送，（使用 symmetricKey 对称加密，内容为 base64 格式） |
| 8    | openId       | 否       | 用户唯一标识                                                 |
| 9    | icTmn        | 否       | 设备终端                                                     |
| 10   | certId       | 否       | 证件号，若上送，（使用 symmetricKey 对称加密，内容为 base64 格式） |
| 11   | activityNo   | 是       | 活动编号,对应营销能力包-抽奖/票券活动编码                    |
| 12   | qrCode       | 否       | 红包码                                                       |
| 13   | acctEntityTp | 是       | 赠送维度， 2 位，可选：01 -手机号 02 -卡号 03 -用户（三选一） |

## 返回结果

| 序号 | 参数名      | 备注                                 |
| ---- | ----------- | ------------------------------------ |
| 1    | resp        | 成功通知以后发送 {‘resp’: ‘00’} 返回 |
| 2    | respTime    | 结果时间 yyyyMMddHHmmss              |
| 3    | awardInfo   | 奖项信息                             |
| 4    | transNumber | 订单流水号                           |

### awardInfo奖项信息：

| 数据名称        | 中文名称                 | 说明                                 |
| --------------- | ------------------------ | ------------------------------------ |
| activityNumber  | 活动编号                 | 对应营销能力包-抽奖/票券活动编码     |
| activityName    | 活动名称                 |                                      |
| beginTime       | 活动开始时间             |                                      |
| endTime         | 活动结束时间             |                                      |
| awardId         | 奖项Id                   |                                      |
| awardType       | 奖项类型                 | 06 ：红包 07 ：商城券                |
| awardName       | 奖项名称                 |                                      |
| awardValue      | 奖项值                   | 红包为红包金额，单位:分 商城券为张数 |
| extAcctId       | 外部账户 id              | 商城券为券ID                         |
| extAcctName     | 外部账户名称             | 商城券为券名称                       |
| drawDesc        | 中奖说明                 |                                      |
| couponStartDate | 商城券生效开始时间       |                                      |
| couponEndDate   | 商城券生效结束时间       |                                      |
| couponGoodsUrl  | 商城券对应商品的链接地址 |                                      |
