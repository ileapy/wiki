# 应用访问令牌backendToken

<code>backendToken</code> 是应用的服务端 API 的访问令牌，控制对服务端 API 的访问。<code>backendToken</code> 的有效期通过接口返回，目前设置为 7200 秒，
接入方获取相应基础访问令牌后，需放入缓存，定期更新。

> 阅读本文档之前请仔细阅读[云闪付小程序官方文档 - 获取应用访问令牌backendToken](https://opentools.95516.com/applet/#/docs/develop/api-backend?id=_02040201)

## 获取backendToken

```php
$app->backend_token->getToken();

```

## 刷新并获取backendToken，方式一

```php
$app->backend_token->getToken(true);

```

## 刷新并获取backendToken，方式二

```php
$app->backend_token->getRefreshedToken();

```

## 返回参数

| 参数         | 描述                                     |
| ------------ | ---------------------------------------- |
| backendToken | 调用后台接口的基础访问令牌               |
| expiresIn    | backendToken接口调用凭证超时时间，单位秒 |

