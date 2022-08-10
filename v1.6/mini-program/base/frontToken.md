# 基础访问令牌frontToken(该接口已废弃)

调用小程序插件 UPSDK 的基础访问令牌 <code>frontToken</code> 。

## 获取frontToken

```php
$app->accessToken->getToken();

```

## 刷新并获取frontToken，方式一

```php
$app->frontToken->getToken(true);

```

## 刷新并获取frontToken，方式二

```php
$app->frontToken->getRefreshedToken();

```

## 返回参数

| 参数       | 内容                                |
| ---------- | ----------------------------------- |
| frontToken | 调用小程序插件 UPSDK 的基础访问令牌 |
| expiresIn  | 有效期，单位秒                      |
