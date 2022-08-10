# 获取用户实名信息

通过用户实名授权 scope.auth 完成后，通过该接口获取用户实名信息。

> 阅读本文档之前请仔细阅读[云闪付小程序官方文档 - 获取用户实名信息](https://opentools.95516.com/applet/#/docs/develop/api-backend?id=_02040302)

## 获取用户实名信息方式一

```php
/**
 * 获取用户实名信息
 * @param string $code 用户授权或静默授权获取的code和openid必传其一
 * @param string $openId 用户唯一标识如果未传递code请确保已调用accessToken后再调用此接口
 * @param bool $decrypt 是否解密返回
 */
$app->user->auth($code, null, false);

```

## 获取用户实名信息方式二

使用此方式之前请先通过获取授权访问令牌获取openId，并注意accessToken到期时间

```php
/**
 * 获取用户实名信息
 * @param string $code 用户授权或静默授权获取的code和openid必传其一
 * @param string $openId 用户唯一标识如果未传递code请确保已调用accessToken后再调用此接口
 * @param bool $decrypt 是否解密返回
 */
$app->user->auth(null, $openId, false);

```

## 返回结果

| 序号 | 参数名   | 备注                                                 |
| ---- | -------- | ---------------------------------------------------- |
| 1    | realName | 用户姓名                                             |
| 2    | certTp   | 证件类型（01:身份证，03:护照，04:回乡证，05:台胞证） |
| 3    | certId   | 证件号                                               |

## 自行解密数据

```php
// 参数$data：返回的字段
$app->crypto->decrypt($data);

```

