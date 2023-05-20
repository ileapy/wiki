# 入门

> 阅读本文档之前请先仔细阅读[云闪付小程序官方文档](https://opentools.95516.com/applet/#/)

## 获取小程序参数

小程序参数的获取方法请参考：[小程序接入指南](https://opentools.95516.com/applet/#/docs/introduce/handbook/pre_production)

## 配置小程序参数

一般来说以下配置就足够使用，所有配置请参考[更多配置](https://opentools.95516.com/applet/#/docs/develop/getstart/getstart)

```php
use unionpay\Factory;

$userConfig = [
    'appid' => '********************', // appid
    'secret' => '********************', // 密钥
    'symmetricKey' => '********************', // 对称密钥
    'privateKey' => '********************', // 私钥
    'debug' => true // debug模式
];

$app = Factory::miniProgram($userConfig);

```

## 更多配置

配置优先级：userConfig(用户配置) > defaultConfig(默认配置) > baseConfig(基础配置)

```php
$userConfig = [
    /************基本配置****************/
    'appid' => '********************', // appid
    'secret' => '********************', // 密钥
    'symmetricKey' => '********************', // 对称密钥
    'privateKey' => '********************', // 私钥
    'debug' => true, // debug模式
    /************更多配置****************/
    'http_post_data_type' => 'json', //数据格式
    'http' => [], // http配置 更多请参考 guzzlehttp/guzzle 文档
    'publicKey' => '',// 银联公钥
    /************缓存设置****************/
    'cache' => [
        // 详细参考 http://www.symfonychina.com/doc/current/components/cache/cache_pools.html
        // 可选值 File, Redis, APCu, memcached, Doctrine
        'type' => 'File',
    ],
    'file' => [
        // a string used as the subdirectory of the root cache directory, where cache
        // items will be stored
        'namespace' => '',

        // the default lifetime (in seconds) for cache items that do not define their
        // own lifetime, with a value 0 causing items to be stored indefinitely (i.e.
        // until the files are deleted)
        'defaultLifetime' => 0,

        // the main cache directory (the application needs read-write permissions on it)
        // if none is specified, a directory is created inside the system temporary directory
        'directory' => null
    ],
    'redis' => [
        // redis[s]://[pass@][ip|host|socket[:port]][/db-index]
        'dsn' => 'redis://localhost:6379',
        'redis_options' => [
            'lazy' => false,
            'persistent' => 0,
            'persistent_id' => null,
            'tcp_keepalive' => 0,
            'timeout' => 30,
            'read_timeout' => 0,
            'retry_interval' => 0,
        ],
        // the default lifetime (in seconds) for cache items that do not define their
        // own lifetime, with a value 0 causing items to be stored indefinitely (i.e.
        // until RedisAdapter::clear() is invoked or the server(s) are purged)
        'defaultLifetime' => 0,

        // if ``true``, the values saved in the cache are serialized before storing them
        'storeSerialized' => true
    ],
    'apcu' => [
        // a string prefixed to the keys of the items stored in this cache
        'namespace' => '',

        // the default lifetime (in seconds) for cache items that do not define their
        // own lifetime, with a value 0 causing items to be stored indefinitely (i.e.
        // until the APCu memory is cleared)
        'defaultLifetime' => 0,

        // when set, all keys prefixed by $namespace can be invalidated by changing
        // this $version string
        'version' => null
    ],
    'memcached' => [
        // memcached://[user:pass@][ip|host|socket[:port]][?weight=int]
        'dsn' => 'memcached://localhost:11211',
        'memcached_type' => [
            'compression' => true,
            'libketama_compatible' => true,
            'serializer' => 'igbinary',
        ],
        // a string prefixed to the keys of the items stored in this cache
        'namespace' => '',

        // the default lifetime (in seconds) for cache items that do not define their
        // own lifetime, with a value 0 causing items to be stored indefinitely (i.e.
        // until MemcachedAdapter::clear() is invoked or the server(s) are restarted)
        'defaultLifetime' => 0
    ]
];
```
