# 获取用户手机号

通过用户手机号授权 `scope.mobile` 完成后，通过该接口获取用户手机号。

> 阅读本文档之前请仔细阅读[云闪付小程序官方文档 - 获取用户手机号](https://opentools.95516.com/applet/#/docs/develop/api-backend?id=_02040301)

## 获取用户手机号方式一

```php
/**
 * 获取用户手机号
 * @param string $code 用户授权或静默授权获取的code和openid必传其一
 * @param string $openId 用户唯一标识如果未传递code请确保已调用accessToken后再调用此接口
 * @param bool $decrypt 是否解密返回
 */
$app->user->mobile($code, null, true);

```

## 获取用户手机号方式二

使用此方式之前请先通过获取授权访问令牌获取openId，并注意accessToken到期时间

```php
/**
 * 获取用户手机号
 * @param string $code 用户授权或静默授权获取的code和openid必传其一
 * @param string $openId 用户唯一标识如果未传递code请确保已调用accessToken后再调用此接口
 * @param bool $decrypt 是否解密返回
 */
$app->user->mobile(null, $openId, true);

```

## 返回结果

| 序号 | 参数名       | 备注       |
| ---- | ------------ | ---------- |
| 1    | mobile       | 登录手机号 |
| 2    | cntryPhoneCd | 国际区号   |

## 自行解密数据

```php
// 参数$data：返回的mobile
$app->crypto->decrypt($data);

```

