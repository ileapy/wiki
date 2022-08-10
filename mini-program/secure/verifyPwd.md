# 获取验证支付密码流水号

获取验证支付密码流水号，用于唤起验证支付密码控件。

> 阅读本文档之前请仔细阅读[云闪付小程序官方文档 - 获取验证支付密码流水号](https://opentools.95516.com/applet/#/docs/develop/api-backend?id=_02040701)

## 接口调用

```php
/**
 * 获取验证支付密码流水号
 * @param string $code 用户授权或静默授权获取的code和openid必传其一
 * @param string $openId 用户唯一标识如果未传递code请确保已调用accessToken后再调用此接口
 * @param array $params 其它参数
 */
$app->secure->verifyPwd($code = "", $openId = "", $params = []);
```
## 参数介绍

| 序号 | 参数       | 是否必须 | 说明                     |
| ---- | ---------- | -------- | ------------------------ |
| 3    | clientIp   | 否       | 终端IP                   |
| 4    | bizOrderId | 是       | 业务操作流水号（自定义） |
| 5    | bizType    | 是       | 业务类型 （小程序: 4p ） |
| 6    | merchantId | 否       | 商户号(小程序同 appId )  |
| 8    | notifyUrl  | 是       | 通知地址                 |

## 返回结果

| 序号 | 参数        | 是否必须 | 说明                                                         |
| ---- | ----------- | -------- | ------------------------------------------------------------ |
| 1    | appId       | 是       | 接入方的唯一标识                                             |
| 2    | openId      | 是       | 用户唯一标识                                                 |
| 3    | clientIp    | 否       | 终端IP                                                       |
| 4    | bizOrderId  | 是       | 业务操作流水号（自定义）                                     |
| 5    | bizType     | 是       | 业务类型 （小程序: 4p ）                                     |
| 6    | merchantId  | 是       | 商户号(小程序同 appId )                                      |
| 7    | nonceStr    | 是       | 生成签名的随机串                                             |
| 8    | notifyUrl   | 是       | 通知地址                                                     |
| 9    | timestamp   | 是       | 生成签名的时间戳                                             |
| 10   | accessToken | 是       | 授权访问令牌                                                 |
| 11   | signature   | 是       | RSA 签名值，输出格式为base64，参见 [数据安全](https://opentools.95516.com/applet/#/docs/develop/api-backend?id=_02040102) - RSA签名 |

## 支付密码验证结果通知

根据获取验证支付密码流水号接口上送的通知地址，通知接入方支付密码验证成功结果。

| 序号 | 参数       | 说明                                                         |
| ---- | ---------- | ------------------------------------------------------------ |
| 1    | appId      | 接入方的唯一标识                                             |
| 2    | timestamp  | 生成签名的时间戳                                             |
| 3    | nonceStr   | 生成签名的随机串                                             |
| 4    | openId     | 用户唯一标识                                                 |
| 5    | bizOrderId | 原请求的业务操作流水号                                       |
| 6    | merchantId | 商户号(小程序同appId)                                        |
| 7    | bizType    | 原业务类型4p                                                 |
| 8    | transNo    | 原transNo                                                    |
| 9    | signature  | RSA签名值，base64格式输出，请使用 [通知类接口验签银联公钥](https://opentools.95516.com/applet/#/docs/develop/api-backend?id=_02040103) 进行验签 |

## 需返回参数

| 序号 | 参数名 | 备注                                 |
| ---- | ------ | ------------------------------------ |
| 1    | resp   | 成功通知以后发送 {‘resp’: ‘00’} 返回 |
