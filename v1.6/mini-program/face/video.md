# 获取人脸识别视频

> 阅读本文档之前请仔细阅读[云闪付小程序官方文档 - 申请签约](https://opentools.95516.com/applet/#/docs/develop/api-backend?id=_02040902)

## 接口调用

```php
/**
 * 获取人脸识别视频
 * @param string $code 用户授权或静默授权获取的code和openid必传其一
 * @param string $openId 用户唯一标识如果未传递code请确保已调用accessToken后再调用此接口
 */
$app->face->video($code = "", $openId = "");
```

## 返回结果

| 序号 | 参数名 | 备注                      |
| ---- | ------ | ------------------------- |
| 1    | vedio  | 活体检测视频；base64 编码 |
