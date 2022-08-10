# 赠送专享红包

接入方给云闪付用户赠送专享红包。

> 阅读本文档之前请仔细阅读[云闪付小程序官方文档 - 赠送专享红包](https://opentools.95516.com/applet/#/docs/develop/api-backend?id=_02040801)

## 接口调用

```php
/**
 * 赠送专享红包
 * @param string $openId 用户唯一标识如果未传递code请确保已调用accessToken后再调用此接口
 * @param array $params 更多参数
 */
$app->redpack->given($openId = "", $params = []);

```

## 更多参数

| 序号 | 参数名       | 是否必填 | 备注                                                         |
| ---- | ------------ | -------- | ------------------------------------------------------------ |
| 2    | transSeqId   | 是       | 交易流水号,不重复，最大 64 位                                |
| 3    | transTs      | 是       | 交易时间,格式: yyyymmddhhmmss                                |
| 5    | insAcctId    | 是       | 机构账户代码，最大32位,对应营销能力包-红包接入方账户         |
| 6    | mobile       | 否       | 交易手机号，若上送，（使用 symmetricKey 对称加密，内容为 base64格式 ） |
| 7    | cardNo       | 否       | 交易卡号，若上送，（使用 symmetricKey 对称加密，内容为 base64格式 ） |
| 9    | acctEntityTp | 是       | 账户主体类型， 2 位，可选： 01 -手机号 02 -卡号 03 -用户（三选一） |
| 10   | pointId      | 是       | 积分 id ，最大 64 位,对应营销能力包-专享红包活动编码         |
| 11   | pointAt      | 是       | 积分额，最大 12 位,单位以分计算                              |
| 12   | validBeginTs | 否       | 有效起始时间，格式：yyyymmddhhmmss                           |
| 13   | validEndTs   | 否       | 有效截止时间，格式：yyyymmddhhmmss                           |
| 14   | busiInfo     | 是       | 业务信息，最大 1024 位,包含自定义活动 ID ,活动名称两个小字段，格式为 {" campaignId ":"活动 ID "," campaignName ":"活动名称"}, ps ：活动ID确保唯一 |
| 15   | transDigest  | 是       | 交易摘要，最大200位,赠送积分说明，用于前台展示               |
| 17   | remark       | 否       | 备注，最大 512 位                                            |

## 返回结果

| 序号 | 参数       | 说明                           |
| ---- | ---------- | ------------------------------ |
| 1    | transSeqId | 原交易流水号                   |
| 2    | retResTime | 结果时间，格式：yyyyMMddHHmmss |
