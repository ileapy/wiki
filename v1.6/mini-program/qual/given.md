# 抽奖资格赠送

接入方给云闪付用户赠送抽奖资格。

> 阅读本文档之前请仔细阅读[云闪付小程序官方文档 - 抽奖资格赠送](https://opentools.95516.com/applet/#/docs/develop/api-backend?id=_02040804)

## 接口调用

```php
/**
 * 抽奖资格赠送
 * @param array $params 更多参数
 */
$app->qual->given($params = []);
```

## 更多参数

| 序号 | 参数名      | 是否必填 | 备注                                                         |
| ---- | ----------- | -------- | ------------------------------------------------------------ |
| 2    | qualNum     | 是       | 资格池编号,对应营销能力包-抽奖资格池编码                     |
| 3    | qualType    | 是       | 资格类型固定值“ open_id ”、“ mobile ”、“ card_no ”           |
| 4    | qualValue   | 是       | 资格值（使用 symmetricKey 对称加密，内容为 base64 格式）     |
| 5    | count       | 是       | 资格增加次数（使用 symmetricKey 对称加密，内容为 base64 格式） |
| 6    | transNumber | 是       | 流水号（确保唯一）                                           |
| 7    | startDate   | 是       | 资格起始时间 格式为 yyyyMMdd                                 |
| 8    | endDate     | 是       | 资格结束时间 格式为 yyyyMMdd                                 |

## 返回结果

| 序号 | 参数       | 说明                  |
| ---- | ---------- | --------------------- |
| 1    | transSeqId | 交易流水号            |
| 2    | retResTime | 结果时间              |
| 3    | info       | 奖项明细( AwardInfo ) |

### 奖项AwardInfo类：

| 序号 | 参数               | 说明                                 |
| ---- | ------------------ | ------------------------------------ |
| 1    | activityNumber     | 活动编号                             |
| 2    | activityName       | 活动名称                             |
| 3    | beginTime          | 活动开始时间                         |
| 4    | endTime            | 活动结束时间                         |
| 5    | awardId            | 奖项ID                               |
| 6    | awardType          | 奖项类型                             |
| 7    | awardName          | 奖项名称                             |
| 8    | awardValue         | 奖项值                               |
| 9    | awardLevel         | 奖项等级                             |
| 10   | extAcctId          | 外部账户 id                          |
| 11   | extAcctName        | 外部账户名称                         |
| 12   | drawDesc           | 中奖说明                             |
| 13   | couponStartDate    | 生效开始时间                         |
| 14   | couponEndDate      | 生效结束时间                         |
| 15   | couponGoodsUrl     | 跳转链接地址                         |
| 16   | enterCloseDateType | 票券截止日类型， 0 ：指定日 1 ：顺延 |
| 17   | enterCloseDate     | 票券有效期                           |
