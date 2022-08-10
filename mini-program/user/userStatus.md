# 查询用户状态

通过该接口可判断用户当前状态。

> 阅读本文档之前请仔细阅读[云闪付小程序官方文档 - 查询用户状态](https://opentools.95516.com/applet/#/docs/develop/api-backend?id=_02040305)

## 查询用户状态方式一

```php
/**
 * 获取用户状态
 * @param string $openId 用户唯一标识，通过获取授权访问令牌获取
 * @param string $markTime 标记时间 (yyyy-MM-dd hh:mm:ss) ,如要上送此字段,必须按照规定格式
 * @param bool $decrypt 是否解密返回
 */
$app->user->userStatus($openId, $markTime = "", $decrypt = true);

```

## 返回结果

| 序号 | 参数名      | 备注                                                         |
| ---- | ----------- | ------------------------------------------------------------ |
| 1    | isRegister  | 是否注册标记：1 - 已注册；0 - 未注册                         |
| 2    | isAuth      | 是否实名标记：1 - 已实名；0 - 未实名                         |
| 3    | certType    | 证件类型，如果已实名，返回证件类型编号                       |
| 4    | isBindCard  | 是否绑卡标识：1 - 绑卡；0 - 未绑卡                           |
| 5    | isOutTrans  | 是否为境外用户标识：1-境内；0-境外                           |
| 6    | newUserMark | 新用户有效标识, 若注册时间早于标记时间，则返回0； 若注册时间晚于或等于标记时间，则返回 1 |

## 自行解密数据

```php
// 参数$data：返回的字段
$app->crypto->decrypt($data);

```

