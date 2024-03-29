# 预授权接口

预授权交易用于受理方向持卡人的发卡方确认交易许可。受理方将预估的消费金额作为预授权金额，发送给持卡人的发卡方。

> 阅读本文之前请仔细阅读[手机支付控件 - 预授权接口](https://open.unionpay.com/tjweb/acproduct/APIList?acpAPIId=769&apiservId=450&version=V2.2&bussType=0)

## 接口调用

返回结果需自行验签

```php
$params = [
    'orderId' => date('YmdHis'), // 订单号
    'txnAmt' => '1'
];

$res = $app->preorder->pay($params);

if ($app->signature->validate($res)) {
    echo "验签成功";
}else
{
    echo "验签失败";
}
```

## 更多参数

| 中文名称                 | 英文名称       | 域类型         | 默认值 | 请求要求     | 备注                                                         |
| :----------------------- | :------------- | :------------- | :----- | :----------- | :----------------------------------------------------------- |
| 版本号                   | version        | NS5            | 无     | M-必填       | 固定填写                                                     |
| 编码方式                 | encoding       | ANS1..20       | UTF-8  | M-必填       | 默认取值：UTF-8                                              |
| 产品类型                 | bizType        | N6             | 无     | M-必填       |                                                              |
| 订单发送时间             | txnTime        | YYYYMMDDhhmmss | 无     | M-必填       | 商户发送交易时间                                             |
| 后台通知地址             | backUrl        | ANS1..256      | 无     | M-必填       | 后台返回商户结果时使用，如上送，则发送商户后台交易结果通知，不支持换行符等不可见字符，如需通过专线通知，需要在通知地址前面加上前缀：专线的首字母加竖线ZX\|如果不需要发后台通知，可以固定上送http://www.specialUrl.com |
| 交易币种                 | currencyCode   | AN3            | 无     | M-必填       | 默认为156                                                    |
| 交易金额                 | txnAmt         | N1..12         | 无     | M-必填       | 单位为分                                                     |
| 交易类型                 | txnType        | N2             | 无     | M-必填       | 取值：02                                                     |
| 交易子类                 | txnSubType     | N2             | 无     | M-必填       | 01：预授权 通过地址区分前台与后台交易                        |
| 接入类型                 | accessType     | N1             | 无     | M-必填       | 0：商户直连接入1：收单机构接入2：平台商户接入                |
| 签名                     | signature      | ANS1..1024     | 0      | M-必填       | 填写对报文摘要的签名                                         |
| 签名方法                 | signMethod     | N2             | 无     | M-必填       | 非对称签名： 01（表示采用RSA签名） HASH表示散列算法 11：支持散列方式验证SHA-256 12：支持散列方式验证SM3 |
| 渠道类型                 | channelType    | N2             | 无     | M-必填       |                                                              |
| 商户代码                 | merId          | AN15           | 无     | M-必填       |                                                              |
| 商户订单号               | orderId        | AN8..40        | 无     | M-必填       | 商户订单号，不能含“-”或“_”;商户自定义，同一交易日期内不可重复;商户代码merId、商户订单号orderId、订单发送时间txnTime三要素唯一确定一笔交易。 |
| 订单描述                 | orderDesc      | ANS1..32       | 无     | C-按条件必填 | 移动支付上送                                                 |
| 二级商户代码             | subMerId       | AN5..15        | 无     | C-按条件必填 | 商户类型为平台类商户接入时必须上送                           |
| 二级商户简称             | subMerAbbr     | ANS1…16        | 无     | C-按条件必填 | 商户类型为平台类商户接入时必须上送                           |
| 二级商户名称             | subMerName     | ANS1..40       | 无     | C-按条件必填 | 商户类型为平台类商户接入时必须上送                           |
| 前台通知地址             | frontUrl       | ANS1..256      | 无     | C-按条件必填 | 前台返回商户结果时使用，前台类交易需上送                     |
| 账号                     | accNo          | AN1..1024      | 无     | C-按条件必填 | 1、 后台类消费交易时上送全卡号或卡号后4位 2、 跨行收单且收单机构收集银行卡信息时上送、 3、前台类交易可通过配置后返回，卡号可选上送 |
| 证书ID                   | certId         | N1..128        | 无     | C-按条件必填 |                                                              |
| 支付卡类型               | payCardType    | N2             | 无     | C-按条件必填 | 特殊商户交易控制用（如借贷分离）                             |
| 保留域                   | reserved       | ANS1..2048     | 无     | O-选填       |                               |
| 发卡机构代码             | issInsCode     | AN1..11        | 无     | O-选填       |                                                              |
| 分账域                   | accSplitData   | ANS1..512      | 无     | O-选填       |                              |
| 风控信息域               | riskRateInfo   | ANS 1..2048    | 无     | O-选填       |                             |
| 默认支付方式             | defaultPayType | N4             | 无     | O-选填       | 取值参考数据元说明                                           |
| 请求方保留域             | reqReserved    | ANS1..1024     | 无     | O-选填       | 商户自定义保留域，交易应答时会原样返回                       |
| 银行卡验证信息及身份信息 | customerInfo   | ANS1..1024     | 无     | O-选填       |                           |
| 支付超时时间             | payTimeout     | YYYYMMDDhhmmss | 无     | O-选填       | 订单支付超时时间                                             |

## 返回结果

| 中文名称       | 英文名称       | 域类型         | 默认值 | 请求要求     | 备注                                                         |
| :------------- | :------------- | :------------- | :----- | :----------- | :----------------------------------------------------------- |
| 签名           | signature      | ANS1..1024     | 0      | M-必填       |                                                              |
| 签名方法       | signMethod     | N2             | 无     | M-必填       |                                                              |
| 应答码         | respCode       | AN2            | 无     | M-必填       |                                                              |
| 应答信息       | respMsg        | ANS1..256      | 无     | M-必填       |                                                              |
| 签名公钥证书   | signPubKeyCert | AN1..2048      | 无     | C-按条件必填 | 此域填写银联签名公钥证书，使用RSA签名方式时，默认返回，如果ctrlRule第五位为1时，不返。 |
| 银联受理订单号 | tn             | N21            | 无     | C-按条件必填 | 商户推送订单后银联移动支付系统返回该流水号，商户调用支付控件时使用 |
| 版本号         | version        | NS5            | 无     | R-需要返回   |                                                              |
| 编码方式       | encoding       | ANS1..20       | UTF-8  | R-需要返回   |                                                              |
| 产品类型       | bizType        | N6             | 无     | R-需要返回   |                                                              |
| 订单发送时间   | txnTime        | YYYYMMDDhhmmss | 无     | R-需要返回   |                                                              |
| 交易类型       | txnType        | N2             | 无     | R-需要返回   |                                                              |
| 交易子类       | txnSubType     | N2             | 无     | R-需要返回   |                                                              |
| 接入类型       | accessType     | N1             | 无     | R-需要返回   | 0：商户直连接入1：收单机构接入2：平台商户接入                |
| 请求方保留域   | reqReserved    | ANS1..1024     | 无     | R-需要返回   |                                                              |
| 商户代码       | merId          | AN15           | 无     | R-需要返回   |                                                              |
| 商户订单号     | orderId        | AN8..40        | 无     | R-需要返回   | 商户订单号，不能含“-”或“_”;商户自定义，同一交易日期内不可重复;商户代码merId、商户订单号orderId、订单发送时间txnTime三要素唯一确定一笔交易。 |
| 保留域         | reserved       | ANS1..2048     | 无     | O-选填       |                            |

## 异步通知

| 中文名称     | 英文名称           | 域类型         | 默认值 | 请求要求     | 备注                                                         |
| :----------- | :----------------- | :------------- | :----- | :----------- | :----------------------------------------------------------- |
| 查询流水号   | queryId            | AN20..21       | 无     | M-必填       | 预授权交易的流水号，供后续查询用                             |
| 交易币种     | currencyCode       | AN3            | 无     | M-必填       | 默认为156                                                    |
| 交易传输时间 | traceTime          | MMDDhhmmss     | 无     | M-必填       |                                                              |
| 签名         | signature          | ANS1..1024     | 0      | M-必填       |                                                              |
| 签名方法     | signMethod         | N2             | 无     | M-必填       |                                                              |
| 清算币种     | settleCurrencyCode | AN3            | 无     | M-必填       |                                                              |
| 清算金额     | settleAmt          | N1..12         | 无     | M-必填       |                                                              |
| 清算日期     | settleDate         | MMDD           | 无     | M-必填       |                                                              |
| 请求方保留域 | reqReserved        | ANS1..1024     | 无     | M-必填       |                                                              |
| 系统跟踪号   | traceNo            | N6             | 无     | M-必填       |                                                              |
| 应答码       | respCode           | AN2            | 无     | M-必填       |                                                              |
| 应答信息     | respMsg            | ANS1..256      | 无     | M-必填       |                                                              |
| 兑换日期     | exchangeDate       | MMDD           | 无     | C-按条件必填 | 交易成功，交易币种和清算币种不一致的时候返回                 |
| 签名公钥证书 | signPubKeyCert     | AN1..2048      | 无     | C-按条件必填 | 此域填写银联签名公钥证书，使用RSA签名方式时，默认返回，如果ctrlRule第五位为1时，不返。 |
| 清算汇率     | exchangeRate       | N8             | 无     | C-按条件必填 | 交易成功，交易币种和清算币种不一致的时候返回                 |
| 账号         | accNo              | AN1..1024      | 无     | C-按条件必填 | 根据商户配置返回                                             |
| 支付方式     | payType            | N4             | 无     | C-按条件必填 | 根据商户配置返回                                             |
| 支付卡标识   | payCardNo          | ANS1..19       | 无     | C-按条件必填 | 移动支付交易时，根据商户配置返回                             |
| 支付卡类型   | payCardType        | N2             | 无     | C-按条件必填 | 根据商户配置返回                                             |
| 支付卡名称   | payCardIssueName   | ANS1..64       | 无     | C-按条件必填 | 移动支付交易时，根据商户配置返回                             |
| 版本号       | version            | NS5            | 无     | R-需要返回   |                                                              |
| 绑定标识号   | bindId             | ANS1..128      | 无     | R-需要返回   | 绑定支付时，根据商户配置返回                                 |
| 编码方式     | encoding           | ANS1..20       | UTF-8  | R-需要返回   |                                                              |
| 产品类型     | bizType            | N6             | 无     | R-需要返回   |                                                              |
| 订单发送时间 | txnTime            | YYYYMMDDhhmmss | 无     | R-需要返回   |                                                              |
| 交易金额     | txnAmt             | N1..12         | 无     | R-需要返回   |                                                              |
| 交易类型     | txnType            | N2             | 无     | R-需要返回   |                                                              |
| 交易子类     | txnSubType         | N2             | 无     | R-需要返回   |                                                              |
| 接入类型     | accessType         | N1             | 无     | R-需要返回   | 0：商户直连接入1：收单机构接入2：平台商户接入                |
| 商户代码     | merId              | AN15           | 无     | R-需要返回   |                                                              |
| 商户订单号   | orderId            | AN8..40        | 无     | R-需要返回   | 商户订单号，不能含“-”或“_”;商户自定义，同一交易日期内不可重复;商户代码merId、商户订单号orderId、订单发送时间txnTime三要素唯一确定一笔交易。 |
| 保留域       | reserved           | ANS1..2048     | 无     | O-选填       |                             |
| 分账域       | accSplitData       | ANS1..512      | 无     | O-选填       |                               |
