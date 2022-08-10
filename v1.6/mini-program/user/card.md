# 获取用户绑定的银行卡列表（仅限银行小程序使用）

通过用户银行卡授权 `scope.bank` 完成后，银行小程序可获取用户绑定的该行银行卡列表信息。

> 阅读本文档之前请仔细阅读[云闪付小程序官方文档 - 获取用户绑定的银行卡列表](https://opentools.95516.com/applet/#/docs/develop/api-backend?id=_02040303)

## 获取用户绑定的银行卡列表

注意：code和openid两者必传其一

```php
/**
 * 获取银行卡列表
 * @param string $code 用户授权或静默授权获取的code和openid必传其一
 * @param string $openId 用户唯一标识如果未传递code请确保已调用accessToken后再调用此接口
 * @param string $cardTp 需要获取的卡列表类型：（ 00 ：全部， 01 ：借记卡， 02 ：贷记卡， 03 ：准贷记卡， 04 ：借贷合一卡）
 * @param string $needSameName 是否要求卡同名：（ 0 :不需要，同名卡和非同名卡都返回， 1 :需要，只返回同名卡）
 * @param string $needPay 是否要求开通支付的卡（ 0 ：不需要，支付卡和非支付卡都返回， 1 ：需要，只返回开通支付支付卡）
 * @param bool $decrypt 是否解密返回
 */
$app->user->card($code = "", $openId = "", $cardTp = "00", $needSameName = "0", $needPay = "0", $decrypt = false);

```

## 返回结果

| 序号 | 参数名   | 备注                   |
| ---- | -------- | ---------------------- |
| 1    | cardList | List，返回的卡列表信息 |

Card信息：

| 序号 | 参数名         | 备注                                                         |
| ---- | -------------- | ------------------------------------------------------------ |
| 1    | cardNo         | 卡号                                                         |
| 2    | issHeadCode    | 卡机构代码                                                   |
| 3    | issHeadName    | 卡机构名称                                                   |
| 4    | cardTp         | 卡性质（ 01 ：借记卡， 02 ：贷记卡， 03 ：准贷记卡， 04 ：借贷合一卡， 05 ：预付费卡） |
| 5    | isCardPay      | 是否是支付卡（ 0 ：否， 1 ：是）                             |
| 6    | isSameName     | 是否是同名卡（ 0 ：否， 1 ：是）                             |
| 7    | reservedMobile | 卡的银行预留手机号                                           |

## 自行解密数据

```php
// 参数$data：返回的字段
$app->crypto->decrypt($data);

```

