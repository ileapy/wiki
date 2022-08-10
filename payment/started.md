## 入门
> 阅读本文档之前请先仔细阅读[手机支付控件](https://open.unionpay.com/tjweb/acproduct/list?apiSvcId=450)

## 获取支付参数

支付参数的获取方法请前往：[我要入网](https://open.unionpay.com/tjweb/acproduct/list?apiservId=450)

## 配置支付参数

一般来说以下配置就足够使用，所有配置请参考SDK&Demo[更多配置](https://open.unionpay.com/tjweb/acproduct/list?apiSvcId=450&index=5)

```php
use unionpay\Factory;

$userConfig = [
    'merId' => '777290058184531', // 商户编号
    'signCertPath' => 'E:\study\php\acp_test_sign.pfx', // 签名证书路径pfx结尾
    'signCertPwd' => '000000', // 签名证书密码
    'encryptCertPath' => 'E:\study\php\acp_test_enc.cer', // 敏感信息加密证书路径 cer结尾
    'payment_model' => true, // 支付模式，true为测试环境，false为生产环境，默认false
];

$app = Factory::miniProgram($userConfig);

```

## 更多配置

配置优先级：userConfig(用户配置) > defaultConfig(默认配置) > baseConfig(基础配置)

```php
$userConfig = [
    /**********基础配置**************/
    'merId' => '777290058184531', // 商户编号
    'signCertPath' => 'E:\study\php\acp_test_sign.pfx', // 签名证书路径pfx结尾
    'signCertPwd' => '000000', // 签名证书密码
    'encryptCertPath' => 'E:\study\php\acp_test_enc.cer', // 敏感信息加密证书路径 cer结尾
    'payment_model' => true, // 支付模式，true为测试环境，false为生产环境，默认false
    /************更多配置****************/
    // 生成环境
    'cert' => [
        'middleCertPath' => __DIR__ . DIRECTORY_SEPARATOR . 'cert' . DIRECTORY_SEPARATOR . 'acp_prod_middle.cer', // 中级证书
        'rootCertPath' => __DIR__ . DIRECTORY_SEPARATOR . 'cert' . DIRECTORY_SEPARATOR . 'acp_prod_root.cer' // 根证书
    ],
    // 测试环境基础证书
    'test_cert' => [
        'middleCertPath' => __DIR__ . DIRECTORY_SEPARATOR . 'cert' . DIRECTORY_SEPARATOR . 'acp_test_middle.cer',
        'rootCertPath' => __DIR__ . DIRECTORY_SEPARATOR . 'cert' . DIRECTORY_SEPARATOR . 'acp_test_root.cer',
    ],
    'http' => [
        'headers' => [
            'Content-Type' => 'application/x-www-form-urlencoded;charset=UTF-8'
        ]
    ], // http配置
    'payConfig' => [
        // 报文版本号，固定5.1.0，请勿改动
        'version'          =>          '5.1.0',
            // 	默认取值：UTF-8
        'encoding'         =>          'utf-8',
        // 后台返回商户结果时使用，如上送，则发送商户后台交易结果通知，不支持换行符等不可见字符，如需通过专线通知，需要在通知地址前面加上前缀：专线的首字母加竖线ZX|如果不需要发后台通知，可以固定上送http://www.specialUrl.com
        'backUrl'          =>          'http://www.specialUrl.com',
        // 默认为 156
        'currencyCode'     =>          '156',
        // 接入类型 0：商户直连接入 1：收单机构接入 2：平台商户接入
        'accessType'       =>          '0',
        // 签名方法 非对称签名： 01（表示采用RSA签名） HASH表示散列算法 11：支持散列方式验证SHA-256 12：支持散列方式验证SM3
        'signMethod'       =>          '01',
        // 渠道类型 07-PC，08-手机
        'channelType'      =>          '08'
    ]
];

```
