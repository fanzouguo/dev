# tMind-core 用例说明
---

## TUtil.inBrowser
``` js
TUtil.inBrowser = false
```
## TUtil.inSvr
```
    TUtil.inSvr = true
```
## TUtil.NUM_TO_STR
```
    TUtil.NUM_TO_STR = [ 零,	一,	二,	三,	四,	五,	六,	七,	八,	九,	十 ]
```
## TUtil.encode.toUniCode
```
    TUtil.encode.toUniCode('tFrameV9 平台');
    // [ 116,	70,	114,	97,	109,	101,	86,	57,	32,	24179,	21488 ]
```
```
    TUtil.encode.wechatNick([ 116, 70, 114, 97, 109, 101, 86, 57, 32, 24179, 21488 ], '微信昵称"特殊字" ℃');
    // '102-117-110-99-116-105-111-110-32-40-41-32-123-13-10-9-32-32-32-32-32-32-32-32-114-101-116-117-114-110-32-95-95-115-116-114-50-117-95-95-40-96-36-123-116-104-105-115-125-96-41-46-106-111-105-110-40-39-45-39-41-59-13-10-9-32-32-32-32-125'
```
	> #### 说明：参数 [sep] 仅当 toStr的首个参数为字符串时有效，用于指定分隔该字符串的符号。
```
    TUtil.decode.toStr([ 116, 70, 114, 97, 109, 101, 86, 57, 32, 24179, 21488 ]);
    // 'tFrameV9 平台'
```
```
    TUtil.decode.toStr ([ 116, 70, 114, 97, 109, 101, 86, 57, 32, 24179, 21488 ], '-');
    // 'tFrameV9 平台'
```
## tCheckType
```
    tCheckType('abc');
    // 'string'
```
```
    tCheckType(2);
    // 'number'
```
```
    tCheckType(true);
    // 'boolean'
```
```
    tCheckType("2021-04-02T07:56:09.305Z");
    // 'date'
```
```
    tCheckType([ 1, 2, 3 ]);
    // 'array'
```
```
    tCheckType({
  "key": "abc"
});
    // 'object'
```
```
    tCheckType({});
    // 'map'
```
```
    tCheckType({});
    // 'set'
```
```
    tCheckType({});
    // 'weakmap'
```
```
    tCheckType({});
    // 'weakset'
```
```
    tCheckType({});
    // 'uint8array'
```
```
    tCheckType({});
    // 'uint16array'
```
```
    tCheckType({});
    // 'uint32array'
```
```
    . = '.'
```
## tDate

> #### 说明：完整格式化字符串为：yyyy-mm-dd hh:mi:ss.ms [年-月-日 时:分:秒.毫秒]

以下用例假设当前时间为：'2021-04-02 15:56:09.304'

```
    tDate();
    // {}
```
	> #### 说明：完整格式化字符串为：yyyy-mm-dd hh:mi:ss.ms [年-月-日 时:分:秒.毫秒]
以下用例假设当前时间为：'2021-04-02 15:56:09.304'
```
    tDate('2020-12-31');
    // {}
```
	> #### 说明：完整格式化字符串为：yyyy-mm-dd hh:mi:ss.ms [年-月-日 时:分:秒.毫秒]
以下用例假设当前时间为：'2021-04-02 15:56:09.304'
```
    tDate(1609372800000);
    // {}
```
	> #### 说明：完整格式化字符串为：yyyy-mm-dd hh:mi:ss.ms [年-月-日 时:分:秒.毫秒]
以下用例假设当前时间为：'2021-04-02 15:56:09.304'
```
    tDate(2021, 4);
    // {}
```
	> #### 说明：完整格式化字符串为：yyyy-mm-dd hh:mi:ss.ms [年-月-日 时:分:秒.毫秒]
以下用例假设当前时间为：'2021-04-02 15:56:09.304'
```
    tDate(2021, 4, 2);
    // {}
```
	> #### 说明：完整格式化字符串为：yyyy-mm-dd hh:mi:ss.ms [年-月-日 时:分:秒.毫秒]
以下用例假设当前时间为：'2021-04-02 15:56:09.304'
```
    tDate(2021, 4, 2, 12, 0, 0);
    // {}
```
```
    tDate().isLeap = false
```
```
    tDate().abs = 8640000000000000
```
```
    tDate().year = 2021
```
```
    tDate().month = 4
```
```
    tDate().day = 2
```
```
    tDate().hour = 15
```
```
    tDate().millisecond = 304
```
```
    tDate().week = 5
```
```
    tDate().quarter = 2
```
```
    tDate().solar = '春分'
```
```
    tDate().sign = '白羊'
```
```
    tDate().animal = '牛'
```
```
    tDate().indexOfQuarter = 2
```
```
    tDate().indexOfYear = 92
```
```
    tDate().daysOfMonth = 30
```
```
    tDate().daysOfQuarter = 91
```
```
    tDate().daysOfYear = 365
```
```
    tDate().ratioOfWeek = 0.7
```
```
    tDate().ratioOfMonth = 0.1
```
```
    tDate().ratioOfQuarter = 0
```
```
    tDate().ratioOfYear = 0.252
```
```
    tDate().weekOfMonth = 1
```
```
    tDate().weekOfYear = 1
```
```
    tDate().tiangan = '辛丑'
```
```
    tDate('2020-10-1').format('yyyy-mm-dd hh:mi:ss.ms');
    // '2020-10-01 00:00:00.000'
```
```
    tDate().format();
    // '2021-04-02'
```
```
    tDate().format('yyyy-mm-dd hh:mi:ss.ms');
    // '2021-04-02 15:56:09.304'
```
```
    tDate().formatAsCn();
    // '四月二日'
```
```
    tDate().formatAsCn(true);
    // '二〇二一年四月二日'
```
```
    tDate().formatAsCn(true, true);
    // '二〇二一年四月二日 一五:五六:九'
```
```
    tDate().formatAsCn(false, true);
    // '四月二日 一五:五六:九'
```
```
    tDate().formatAsLunar();
    // '二月21'
```
```
    tDate().formatAsLunar(false);
    // '2021年二月21'
```
```
    tDate().formatAsBh();
    // '佛历2564年4月2'
```
	> #### 说明：更多区域语言标记，参考 [Intl page](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl#locale_identification_and_negotiation)
```
    tDate().formatAsWorld();
    // '2021-04-02'
```
	> #### 说明：更多区域语言标记，参考 [Intl page](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl#locale_identification_and_negotiation)
```
    tDate().formatAsWorld('fr-ca');
    // '2021-04-02'
```
	> #### 说明：更多区域语言标记，参考 [Intl page](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl#locale_identification_and_negotiation)
```
    tDate().formatAsWorld('en-gb');
    // '02/04/2021'
```
	> #### 说明：更多区域语言标记，参考 [Intl page](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl#locale_identification_and_negotiation)
```
    tDate().formatAsWorld('ko-KR');
    // '2021. 4. 2.'
```
```
    tDate().getWeek('zh');
    // '周五'
```
```
    tDate().getWeek('en');
    // 'Fri'
```
```
    tDate().getWeekOfMonth('zh');
    // '一'
```
```
    tDate().getWeekOfMonth('en');
    // '一'
```
```
    tDate().getWeekOfYear('zh');
    // 14
```
```
    tDate().getWeekOfYear('en');
    // 14
```
```
    tDate().getQuarter('zh');
    // '二季度'
```
```
    tDate().getQuarter('en');
    // '二季度'
```
```
    tDate().getOffset(3, 'day');
    // '2021-04-05'
```
```
    tDate().getOffset(-3, 'day');
    // '2021-03-30'
```
```
    tDate().getOffset(3, 'week');
    // '2021-04-23'
```
```
    tDate().getOffset(3, 'month');
    // '2021-07-01'
```
```
    tDate().getOffset(3, 'year');
    // '2024-04-01'
```
```
    tDate().getDiff("1970-01-01T00:00:01.977Z", 'day');
    // -18719
```
```
    tDate().getDiff('2020-12-31', 'day');
    // -92
```
```
    tDate().getDiff(1609372800000, 'day');
    // -92
```
```
    tDate().getDiff('2020-12-31', 'ms');
    // -7977369304
```
```
    tDate().getDiff('2020-12-31', 'second');
    // -7977369
```
```
    tDate().getDiff('2020-12-31', 'minute');
    // -132956
```
```
    tDate().getDiff('2020-12-31', 'hour');
    // -2215.9
```
```
    tDate().getDiff('2020-12-31', 'day');
    // -92
```
```
    tDate().getDiff('2020-12-31', 'week');
    // -13.1
```
```
    tDate().getDiff('2020-12-31', 'month');
    // -3.1
```
```
    tDate().getDiff('2020-12-31', 'year');
    // -0.252
```
	> #### 说明：仅当首个参数为 True 时，可以自定义数字模板
```
    tDate().toNumber();
    // 1617350169304
```
	> #### 说明：仅当首个参数为 True 时，可以自定义数字模板
```
    tDate().toNumber(true);
    // 20210402155609304
```
	> #### 说明：仅当首个参数为 True 时，可以自定义数字模板
```
    tDate().toNumber(true, 'yyyymmdd');
    // 20210402
```
```
    tDate().toJson();
    // {"year":2021,"month":4,"day":2,"hour":15,"minutes":56,"second":9,"millisecond":304,"week":5,"weekOfMonth":1,"weekOfYear":14,"quarter":2,"isLeap":false,"lunar":"二月21","buddhist":"佛历2564年4月2"}
```
```
    tDate().toJson('zh');
    // {"year":2021,"month":4,"day":2,"hour":15,"minutes":56,"second":9,"millisecond":304,"week":"周五","weekOfMonth":"一","weekOfYear":14,"quarter":"二季度","isLeap":false,"lunar":"二月21","buddhist":"佛历2564年4月2"}
```
```
    tDate().toJson('en');
    // {"year":2021,"month":4,"day":2,"hour":15,"minutes":56,"second":9,"millisecond":304,"week":"Fri","weekOfMonth":"一","weekOfYear":14,"quarter":"二季度","isLeap":false,"lunar":"二月21","buddhist":"佛历2564年4月2"}
```
```
    tDate().toArr();
    // [ 2021,	4,	2 ]
```
```
    tDate().toArr(true);
    // [ 2021,	4,	2,	15,	56,	9,	304 ]
```
## tVerifi().getRules
```
    tVerifi().getRules();
    // {"isNum":"为纯数字","hasSpace":"是否包含空格","hasSpecial":"是否包含特殊字符"}
```
## tPinyin.groupByFirstLetter
```
    tPinyin.groupByFirstLetter([ 可, 测, 啊, 深 ]);
    // {"k":["可"],"c":["测"],"a":["啊"],"s":["深"]}
```
```
    tPinyin.groupByFirstLetter([ 可, 测, 啊, 深 ], true);
    // {"a":["啊"],"b":[],"c":["测"],"d":[],"e":[],"f":[],"g":[],"h":[],"j":[],"k":["可"],"l":[],"m":[],"n":[],"o":[],"p":[],"q":[],"r":[],"s":["深"]}
```
```
    tPinyin.getFirstLetter('可以');
    // 'k'
```