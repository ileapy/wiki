# 申请签约

无感支付签约接口，用户无感签约 scope:upapi_contract 授权且点击”同意授权”后，后台可通过此接口发起支付签约，签约完成后根据协议号走全渠道即可发起交易。

> 阅读本文档之前请仔细阅读[云闪付小程序官方文档 - 申请签约](https://opentools.95516.com/applet/#/docs/develop/api-backend?id=_02040502)

## 接口调用

```php
/**
 * 申请签约
 * @param string $code 用户授权或静默授权获取的code和openid必传其一
 * @param string $openId 用户唯一标识如果未传递code请确保已调用accessToken后再调用此接口
 * @param string $planId 协议模板id由云闪付录入模板并分配给接入方
 * @param string $contractCode 接入方侧的签约协议号，由接入方自行生成
 */
$app->contract->apply($code = "", $openId = "", $planId = "", $contractCode = "");

```

## 返回结果

| 序号 | 参数名        | 备注                                           |
| ---- | ------------- | ---------------------------------------------- |
| 1    | contractCode  | 接入方传来的签约协议号                         |
| 2    | planId        | 接入方传来的协议模板 id                        |
| 3    | openId        | 用户唯一标识                                   |
| 4    | operationTime | 操作时间,例:20210824103521                     |
| 5    | contractId    | 签约成功后，云闪付返回的委托免密支付协议 id 。 |

