# 专享红包余额查询

根据专享红包活动 id 查询用户的该专享红包余额。

> 阅读本文档之前请仔细阅读[云闪付小程序官方文档 - 专享红包余额查询](https://opentools.95516.com/applet/#/docs/develop/api-backend?id=_02040803)

## 接口调用

```php
/**
 * 专享红包余额查询
 * @param array $params 更多参数
 */
$app->redpack->excQuery($params = []);

```

## 更多参数

| 序号 | 参数名       | 是否必填 | 备注                                                         |
| ---- | ------------ | -------- | ------------------------------------------------------------ |
| 2    | pointId      | 是       | 专享活动活动id,对应营销能力包-专享红包活动编码               |
| 3    | acctEntityTp | 是       | 账户主体类型：01 -手机号；02 -卡号；03 -用户，即 openId      |
| 4    | acctEntityId | 是       | 账户主体值，类型填写 01 ，则对应填写具体手机号，类型填写 02 ，则对应填写具体卡号，类型填写 03 ，则对应填写具体 openId （ 3 种类型值均需要使用 symmetricKey 对称密钥加密，内容为 base64 格式） |
| 6    | transTs      | 是       | 交易时间 yyyyMMddhhmmss                                      |
| 7    | accessId     | 是       | 专享红包来源： UP -银联； SC -其他                           |
| 8    | transSeq     | 是       | 流水号                                                       |
| 9    | remark       | 是       | 备注                                                         |

## 返回结果

| 序号 | 参数名          | 备注         |
| ---- | --------------- | ------------ |
| 1    | acctSt          | 账户状态     |
| 2    | avlBalance      | 可用金额     |
| 3    | frozenBalance   | 冻结金额     |
| 4    | operBalance     | 消费金额     |
| 5    | expireBalance   | 过期金额     |
| 6    | todeductBalance | 待抵扣金额   |
| 7    | acctOpenTp      | 开户方式     |
| 8    | acctOpenDt      | 开户日期     |
| 9    | reservedField   | 保留字段     |
| 10   | recUpdTs        | 记录更新时间 |
