# 未完成订单查询

查询已签约用户在云闪付侧是否存在业务未完成的订单。

> 阅读本文档之前请仔细阅读[云闪付小程序官方文档 - 未完成订单查询](https://opentools.95516.com/applet/#/docs/develop/api-backend/payoff?id=_02040505)

## 接口调用

```php
/**
 * 未完成订单查询
 * @param string $openId 用户唯一标识
 */
$app->contract->unFinishedOrder($openId = "");

```

## 返回结果

| 序号 | 参数名 | 备注                                                         |
| ---- | ------ | ------------------------------------------------------------ |
| 1    | enable | 返回 0 ，表示无未完成订单；返回 1-N ，表示存在 N 笔未完成订单。 |

