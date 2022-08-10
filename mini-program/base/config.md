# 小程序初始化配置参数(该接口已废弃)

获取<code>upsdk.config</code>初始化配置参数（可开启debug模式）。

## 获取config

```php
// 参数url：前端页面的url地址，不包含#号之后的部分
$app->base->config($url)

```

## 返回参数

| 参数      | 内容                                |
| --------- | ----------------------------------- |
| appId     | 小程序appid |
| timestamp | 时间戳 |
| nonceStr  | 随机字符串       |
| signature | 签名            |
| debug     | 是否调试模式     |
