# 授权访问令牌accessToken

获取用户授权访问令牌 <code>accessToken</code> , 经过用户授权完成后，可通过授权访问令牌调用对应权限可访问的服务端 API 。

> 阅读本文档之前请仔细阅读[云闪付小程序官方文档 - 获取授权访问令牌accessToken](https://opentools.95516.com/applet/#/docs/develop/api-backend/token?id=_02040202)

## 获取accessToken

```php
// 参数code：用户授权或静默授权获取的code
$app->access_token->getToken($code);

```

## 刷新并获取accessToken，方式一

```php
//  参数code：用户授权或静默授权获取的code
$app->access_token->getToken($code, true);

```

## 刷新并获取accessToken，方式二

```php
//  参数code：用户授权或静默授权获取的code
$app->access_token->getRefreshedToken($code);

```

## 返回参数

| 序号 | 参数名       | 备注                                       |
| ---- | ------------ | ------------------------------------------ |
| 1    | accessToken  | 授权访问接口 API 调用凭证                  |
| 2    | expiresIn    | accessToken 接口调用凭证超时时间，单位(秒) |
| 3    | refreshToken | 用户刷新 accessToken (已废弃)              |
| 4    | openId       | 用户唯一标识                               |
| 5    | scope        | 用户授权的作用域                           |
| 6    | unionId      | 统一用户标识(所有接入方下统一用户标识)     |
