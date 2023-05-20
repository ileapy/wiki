# 签约关系查询

查询用户与接入方的签约关系状态，5分钟缓存机制，为保证查询结果准确性，建议间隔5分钟以上再进行状态查询。

> 阅读本文档之前请仔细阅读[云闪付小程序官方文档 - 签约关系查询](https://opentools.95516.com/applet/#/docs/develop/api-backend/payoff?id=_02040504)

## 接口调用

```php
/**
 * 签约关系查询
 * @param string $openId 用户唯一标识
 * @param string $planId 协议模板id由云闪付录入模板并分配给接入方
 */
$app->contract->signStatus($openId = "", $planId = "");

```

## 返回结果

| 序号 | 参数名         | 备注                                  |
| ---- | -------------- | ------------------------------------- |
| 1    | contractId     | 签约协议号                            |
| 2    | contractStatus | 签约状态：空-未签约 1-已签约 3-已解约 |
