# 文件传输类交易接口（貌似该接口银联已关闭）

商户可以通过此接口获取对账文件。

> 阅读本文之前请仔细阅读[手机支付控件 - 文件传输类交易接口](https://open.unionpay.com/tjweb/acproduct/APIList?acpAPIId=774&apiservId=450&version=V2.2&bussType=0)

## 接口调用

返回结果自行验签

```php
$params = [
    'settleDate' => date('md'),
];

$res = $app->file->download($params);

if ($app->signature->validate($res)) {
    echo "验签成功";
}else
{
    echo "验签失败";
}
```

## 更多参数

| 中文名称     | 英文名称    | 域类型         | 默认值 | 请求要求     | 备注                                                         |
| :----------- | :---------- | :------------- | :----- | :----------- | :----------------------------------------------------------- |
| 版本号       | version     | NS5            | 无     | M-必填       | 固定填写                                                     |
| 编码方式     | encoding    | ANS1..20       | UTF-8  | M-必填       | 默认取值：UTF-8                                              |
| 产品类型     | bizType     | N6             | 无     | M-必填       | 默认:000000                                                  |
| 订单发送时间 | txnTime     | YYYYMMDDhhmmss | 无     | M-必填       |                                                              |
| 交易类型     | txnType     | N2             | 无     | M-必填       | 取值:76                                                      |
| 交易子类     | txnSubType  | N2             | 无     | M-必填       | 01：对账文件下载                                             |
| 接入类型     | accessType  | N1             | 无     | M-必填       | 0：商户直连接入1：收单机构接入2：平台商户接入                |
| 签名         | signature   | ANS1..1024     | 0      | M-必填       | 填写对报文摘要的签名                                         |
| 签名方法     | signMethod  | N2             | 无     | M-必填       | 非对称签名： 01（表示采用RSA签名） HASH表示散列算法 11：支持散列方式验证SHA-256 12：支持散列方式验证SM3 |
| 清算日期     | settleDate  | MMDD           | 无     | M-必填       |                                                              |
| 商户代码     | merId       | AN15           | 无     | M-必填       |                                                              |
| 文件类型     | fileType    | N2             | 无     | M-必填       | 依据实际业务情况定义 参考7.1：商户索取的文件类型约定         |
| 证书ID       | certId      | N1..128        | 无     | C-按条件必填 |                                                              |
| 请求方保留域 | reqReserved | ANS1..1024     | 无     | O-选填       | 商户自定义保留域，交易应答时会原样返回                       |

## 返回数据

| 中文名称     | 英文名称    | 域类型         | 默认值 | 请求要求     | 备注                                          |
| :----------- | :---------- | :------------- | :----- | :----------- | :-------------------------------------------- |
| 批量文件内容 | fileContent | ANS1..1000000  | 无     | M-必填       | 文件流方式                                    |
| 签名         | signature   | ANS1..1024     | 0      | M-必填       |                                               |
| 签名方法     | signMethod  | N2             | 无     | M-必填       |                                               |
| 文件名       | fileName    | ANS1..64       | 无     | M-必填       |                                               |
| 应答码       | respCode    | AN2            | 无     | M-必填       |                                               |
| 应答信息     | respMsg     | ANS1..256      | 无     | M-必填       |                                               |
| 证书ID       | certId      | N1..128        | 无     | C-按条件必填 |                                               |
| 版本号       | version     | NS5            | 无     | R-需要返回   |                                               |
| 编码方式     | encoding    | ANS1..20       | UTF-8  | R-需要返回   |                                               |
| 产品类型     | bizType     | N6             | 无     | R-需要返回   |                                               |
| 订单发送时间 | txnTime     | YYYYMMDDhhmmss | 无     | R-需要返回   |                                               |
| 交易类型     | txnType     | N2             | 无     | R-需要返回   | 取值:76                                       |
| 交易子类     | txnSubType  | N2             | 无     | R-需要返回   | 01：对账文件下载                              |
| 接入类型     | accessType  | N1             | 无     | R-需要返回   | 0：商户直连接入1：收单机构接入2：平台商户接入 |
| 清算日期     | settleDate  | MMDD           | 无     | R-需要返回   |                                               |
| 请求方保留域 | reqReserved | ANS1..1024     | 无     | R-需要返回   |                                               |
| 商户代码     | merId       | AN15           | 无     | R-需要返回   |                                               |
| 文件类型     | fileType    | N2             | 无     | R-需要返回   |                                               |

## 保存对账文件

```php
$params = [
    'settleDate' => date('md')
];

$res = $app->file->download($params);

if ($app->signature->validate($res)) {

    // 保存文件
    $app->file->save($res, "D:\\");

    echo "验签成功";
}else
{
    echo "验签失败";
}
```
