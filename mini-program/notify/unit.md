# 异步通知处理

通过此接口可以统一处理异步回调数据

## 接口调用

```php
// 默认自动验签，第二个参数设置为false就不自动验签，可自行验签, 注意验签失败会抛异常
$response = $app->notify->unit(function ($message) use ($app){
    // 自行验签
    $res = $app->signature->validate($message);
    if ($res) {
        // 验签成功
        echo "验签成功";
    } else {
        // 验签失败
        echo "验签失败";
    }
}, false);
// 响应已接收到请求
$response->send();
```
