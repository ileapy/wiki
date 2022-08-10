# 获取用户授权卡token

通过用户授权卡 token `scope.token` ，获取用户授权指定卡 `token` 。

> 阅读本文档之前请仔细阅读[云闪付小程序官方文档 - 获取用户授权卡token](https://opentools.95516.com/applet/#/docs/develop/api-backend?id=_02040304)

## 获取用户授权卡token

注意：code和openid两者必传其一

```php
/**
 * 获取银行卡token
 * @param string $code 用户授权或静默授权获取的code和openid必传其一
 * @param string $openId 用户唯一标识如果未传递code请确保已调用accessToken后再调用此接口
 * @param bool $decrypt 是否解密返回
 */
$app->user->cardToken($code = "", $openId = "", $decrypt = true);

```

## 返回结果

| 序号 | 参数名   | 备注                                                         |
| ---- | -------- | ------------------------------------------------------------ |
| 1    | cardNo   | 银行卡(卡 bin ,带掩码)                                       |
| 2    | headName | 发卡总行名称                                                 |
| 3    | headCode | 发卡总行机构代码                                             |
| 4    | cardTp   | 卡性质（ 01 ：借记卡， 02 ：贷记卡， 03 ：准贷记卡， 04 ：借贷合一卡， 05 ：预付费卡） |
| 5    | token    | 银行卡 token                                                 |

## 自行解密数据

```php
// 参数$data：返回的字段
$app->crypto->decrypt($data);

```

