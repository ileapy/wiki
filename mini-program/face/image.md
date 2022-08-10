# 获取人脸识别照片

> 阅读本文档之前请仔细阅读[云闪付小程序官方文档 - 获取人脸识别照片](https://opentools.95516.com/applet/#/docs/develop/api-backend?id=_02040901)

## 接口调用

```php
/**
 * 获取人脸识别照片
 * @param string $code 用户授权或静默授权获取的code和openid必传其一
 * @param string $openId 用户唯一标识如果未传递code请确保已调用accessToken后再调用此接口
 */
$app->face->image($code = "", $openId = "");
```

## 返回结果

| 序号 | 参数名 | 备注                 |
| ---- | ------ | -------------------- |
| 1    | image  | 人脸照片；base64编码 |

