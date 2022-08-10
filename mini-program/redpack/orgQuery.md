# 机构账户（红包）余额查询

查询银联红包接入方账户余额查询。

> 阅读本文档之前请仔细阅读[云闪付小程序官方文档 - 机构账户（红包）余额查询](https://opentools.95516.com/applet/#/docs/develop/api-backend?id=_02040802)

## 接口调用

```php
/**
 * 机构账户（红包）余额查询
 * @param array $params 更多参数
 */
$app->redpack->orgQuery($params = []);

```

## 更多参数

| 序号 | 参数名      | 是否必填 | 备注                                                  |
| ---- | ----------- | -------- | ----------------------------------------------------- |
| 2    | insAcctId   | 是       | 机构账户代码 必须 18 位,对应营销能力包-红包接入方账户 |
| 3    | transNumber | 是       | 接入方交易流水号                                      |
| 4    | transDt     | 是       | 请求日期 YYYYMMDD例：20190712                         |
| 5    | transTm     | 是       | 请求时间 YYYYMMDDHHMMSS 例：20190712144820            |
| 7    | insAcctType | 否       | 机构类型，UP23：专用红包，UP21：老红包                |

## 返回结果

| 序号 | 参数名         | 备注                                                       |
| ---- | -------------- | ---------------------------------------------------------- |
| 1    | acctSt         | 账户状态（使用 symmetricKey 对称加密，内容为 base64 格式） |
| 2    | acctBalance    | 账户余额（使用 symmetricKey 对称加密，内容为 base64 格式） |
| 3    | validBeginDtTm | 有效开始时间                                               |
| 4    | validEndDtTm   | 有效结束时间                                               |
