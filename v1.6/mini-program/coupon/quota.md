# 优惠券活动剩余名额查询

返回营销系统配置的优惠券活动剩余名额。

> 阅读本文档之前请仔细阅读[云闪付小程序官方文档 - 优惠券活动剩余名额查询](https://opentools.95516.com/applet/#/docs/develop/api-backend?id=_02040811)

## 接口调用

```php
/**
 * 优惠券活动剩余名额查询
 * @param array $params 更多参数
 */
$app->coupon->quota($params = []);
```

## 更多参数

| 序号 | 参数名       | 是否必填 | 备注                                                         |
| ---- | ------------ | -------- | ------------------------------------------------------------ |
| 2    | transSeqId   | 是       | 唯一流水号                                                   |
| 3    | activityNo   | 是       | 活动编号                                                     |
| 4    | activityType | 是       | 活动类型: 1 .u点全场立减（同原线上立减）、 2 .u点全场券、 3 .线下立减、 4 .折扣券、 5 .代金券、 6 .满抵券、 7 .随机立减券、 8 .凭证券、 9 .提货券、 10 .送货券、 11 .精准营销展示券、 12 .单品券、 13 .单品立减 |

## 返回结果

| 序号 | 参数                 | 说明                                                         |
| ---- | -------------------- | ------------------------------------------------------------ |
| 1    | resp                 | 00 ,成功；其他，失败                                         |
| 2    | msg                  | 信息描述                                                     |
| 3    | transSeqId           | 请求流水号                                                   |
| 4    | activityNo           | 活动编号                                                     |
| 5    | activityName         | 活动名称                                                     |
| 6    | activityType         | 活动类型: 1 .u点全场立减（同原线上立减）、 2 .u点全场券、 3 .线下立减、 4 .折扣券、 5 .代金券、 6 .满抵券、 7 .随机立减券、 8 .凭证券、 9 .提货券、 10 .送货券、 11 .精准营销展示券、 12 .单品券、 13 .单品立减 |
| 7    | beginTime            | 活动开始时间                                                 |
| 8    | endTime              | 活动结束时间                                                 |
| 9    | activityStatus       | 活动状态，00 :停用, 01 :启用                                 |
| 10   | limitType            | 限制类型：01 :金额限制，02 :次数限制，03 :金额次数同时限制   |
| 11   | activityMark         | 活动标识：01 :活动或票券全部分配，02 :活动或票券按日平均分配，03 :活动或票券按指定日或周几分配，04 :活动或票券按月平均分配，05 :活动或票券按年分配 |
| 12   | startMark            | 启动标识，1 :今天是活动日，2 :今天不是活动日                 |
| 13   | allAmount            | 总金额，单位分                                               |
| 14   | allRemainAmount      | 总剩余金额，单位分                                           |
| 15   | allAmountUseupTime   | 总金额用完时间                                               |
| 16   | monthAmount          | 当月总金额                                                   |
| 17   | monthRemainAmount    | 当月总剩余金额                                               |
| 18   | monthAmountUseupTime | 当月总金额用完时间                                           |
| 19   | dayAmount            | 当天总金额                                                   |
| 20   | dayRemainAmount      | 当天总剩余金额                                               |
| 21   | dayAmountUseupTime   | 当天总金额用完时间                                           |
| 22   | allCount             | 总次数                                                       |
| 23   | allRemainCount       | 总剩余次数                                                   |
| 24   | allCountUseupTime    | 总次数用完时间                                               |
| 25   | monthCount           | 当月总次数                                                   |
| 26   | monthRemainCount     | 当月总剩余次数                                               |
| 27   | monthCountUseupTime  | 当月总次数用完时间                                           |
| 28   | dayCount             | 当天总次数                                                   |
| 29   | dayRemainCount       | 当天总剩余次数                                               |
| 30   | dayCountUseupTime    | 当天总次数用完时间                                           |
| 31   | yearAmount           | 当年总金额                                                   |
| 32   | yearRemainAmount     | 当年总剩余金额                                               |
| 33   | yearAmountUseupTime  | 当年总金额用完时间                                           |
| 34   | yearCount            | 当年总次数                                                   |
| 35   | yearRemainCount      | 当年总剩余次数                                               |
| 36   | yearCountUseupTime   | 当年总次数用完时间                                           |
| 37   | awardShowInfoList    | 奖项剩余额度列表，List                                       |

## AwardShowInfo信息

| 序号 | 参数                 | 说明                                                         |
| ---- | -------------------- | ------------------------------------------------------------ |
| 1    | activityNo           | 活动编号                                                     |
| 2    | activityName         | 活动名称                                                     |
| 3    | activityType         | 活动类型: 1 .u点全场立减（同原线上立减）、2 .u点全场券、3 线下立减、4 折扣券、5 代金券、6 满抵券、7 随机立减券、8 凭证券、9 提货券、10 送货券、11 精准营销展示券、12 单品券、13 单品立减 |
| 4    | beginTime            | 活动开始时间                                                 |
| 5    | endTime              | 活动结束时间                                                 |
| 6    | activityStatus       | 活动状态，00 :停用,01 :启用                                  |
| 7    | limitType            | 限制类型：01 :金额限制，02 :次数限制，03 :金额次数同时限制   |
| 8    | activityMark         | 活动标识：01 :活动或票券全部分配，02 :活动或票券按日平均分配，03 :活动或票券按指定日或周几分配，04 :活动或票券按月平均分配，05 :活动或票券按年分配 |
| 9    | startMark            | 启动标识，1 :今天是活动日，2 :今天不是活动日                 |
| 10   | allAmount            | 总金额，单位分                                               |
| 11   | allRemainAmount      | 总剩余金额，单位分                                           |
| 12   | allAmountUseupTime   | 总金额用完时间                                               |
| 13   | monthAmount          | 当月总金额                                                   |
| 14   | monthRemainAmount    | 当月总剩余金额                                               |
| 15   | monthAmountUseupTime | 当月总金额用完时间                                           |
| 16   | dayAmount            | 当天总金额                                                   |
| 17   | dayRemainAmount      | 当天总剩余金额                                               |
| 18   | dayAmountUseupTime   | 当天总金额用完时间                                           |
| 19   | allCount             | 总次数                                                       |
| 20   | allRemainCount       | 总剩余次数                                                   |
| 21   | allCountUseupTime    | 总次数用完时间                                               |
| 22   | monthCount           | 当月总次数                                                   |
| 23   | monthRemainCount     | 当月总剩余次数                                               |
| 24   | monthCountUseupTime  | 当月总次数用完时间                                           |
| 25   | dayCount             | 当天总次数                                                   |
| 26   | dayRemainCount       | 当天总剩余次数                                               |
| 27   | dayCountUseupTime    | 当天总次数用完时间                                           |
| 28   | yearAmount           | 当年总金额                                                   |
| 29   | yearRemainAmount     | 当年总剩余金额                                               |
| 30   | yearAmountUseupTime  | 当年总金额用完时间                                           |
| 31   | yearCount            | 当年总次数                                                   |
| 32   | yearRemainCount      | 当年总剩余次数                                               |
| 33   | yearCountUseupTime   | 当年总次数用完时间                                           |

