# 小程序模板消息

通过小程序运营平台配置小程序消息模板，通过该接口给云闪付用户推送小程序消息, 例如服务通知、动账通知。

> 阅读本文档之前请仔细阅读[云闪付小程序官方文档 - 小程序模板消息](https://opentools.95516.com/applet/#/docs/develop/api-backend?id=_02040601)

## 接口调用

```php
$app->message->send($params);
```

## 参数介绍

| 序号 | 参数名       | 是否必填 | 备注                                                         |
| ---- | ------------ | -------- | ------------------------------------------------------------ |
| 1    | appId        | 是       | 接入方的唯一标识                                             |
| 2    | openId       | 是       | 用户唯一标识                                                 |
| 3    | backendToken | 是       | 授权应用访问令牌                                             |
| 4    | mpId         | 是       | 小程序 id                                                    |
| 5    | isPush       | 否       | 是否系统推送消息 1- 推送（默认） 0- 不推送                   |
| 6    | extra01      | 否       | 扩展字段 01                                                  |
| 7    | extra02      | 否       | 扩展字段 02                                                  |
| 8    | templateId   | 是       | 通知模板 id                                                  |
| 9    | desc         | 是       | 通知详情( 200 个字符以内)                                    |
| 10   | uiType       | 是       | ui类型：1                                                    |
| 11   | adImageUrl   | 否       | 广告图 url                                                   |
| 12   | adTargetUrl  | 否       | 广告落地页 url                                               |
| 13   | destExt      | 否       | 小程序的附加参数                                             |
| 14   | destType     | 是       | 跳转类型 可选值: rn 、 html 、 native 、 applet              |
| 15   | destInfo     | 是       | 类型： applet 就是小程序 id ， rn 就是 rn 的 dest html 就是 url native 就是 native 的 dest |
| 16   | valueList    | 否       | 关键词列表：List                                             |

### MsgValue信息

| 字段  | 是否必须 | 说明                                                         |
| ----- | -------- | ------------------------------------------------------------ |
| key   | 是       | key                                                          |
| value | 是       | value（对应 key 的消息文本内容， 200 个字符以内，换行用 \n ） |

## 返回结果

| 序号 | 参数           | 说明       |
| ---- | -------------- | ---------- |
| 1    | nid            | 推送流水号 |
| 2    | notificationNo | 通知流水号 |
