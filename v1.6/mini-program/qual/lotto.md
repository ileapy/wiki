# 抽奖

接入方通过资格赠送云闪付抽奖（红包/票券）接口资格，给用户赠送（非定额/定额）红包或者商城券。

> 阅读本文档之前请仔细阅读[云闪付小程序官方文档 - 抽奖](https://opentools.95516.com/applet/#/docs/develop/api-backend?id=_02040806)

## 接口调用

```php
/**
 * 抽奖
 * @param array $params 更多参数
 */
$app->qual->lotto($params = []);
```

## 更多参数

| 序号 | 参数名         | 是否必填 | 备注                                                       |
| ---- | -------------- | -------- | ---------------------------------------------------------- |
| 2    | activityNumber | 是       | 活动编号,对应营销能力包-抽奖/票券活动编码                  |
| 3    | orderAmount    | 否       | 订单金额                                                   |
| 4    | qualNum        | 是       | 资格池编号,对应营销能力包-抽奖资格池编码                   |
| 5    | qualType       | 是       | 资格类型固定值“ open_id ”、“ mobile ”、“ card_no ”         |
| 6    | qualValue      | 是       | 资格值（使用 symmetricKey 对称加密，内容为 base64 格式）   |
| 7    | certId         | 否       | 身份证号（使用 symmetricKey 对称加密，内容为 base64 格式） |
| 8    | icTerminal     | 否       | 设备终端                                                   |
| 9    | qrCode         | 否       | 红包码                                                     |
| 10   | transNumber    | 是       | 流水号（确保唯一）                                         |

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
