# Styles

参考 `Ecma-376 Part 1 - 18.8 Styles`

## 文件结构

> xl
>> `styles.xml`
>

## styles.xml

> styleSheet
>> `numFmts`: 格式规则
>>> `numFmt`
>>>> [a]`numFmtId`: 格式规则 ID
>>>>
>>>> [a]`formatCode`: 格式的具体规则
>>
>> fonts
>>
>> `fills`
>>> `fill`
>>>> `patternFill`
>>>>> [a]`patternType`
>>>>>
>>>>> `fgColor`
>>>>>
>>>>> `bgColor`
>>>>>
>>
>> borders
>>
>> cellStyleXfs
>>
>> `cellXfs`: 单元格样式列表
>>> `xf`: 单元格样式
>>>> [a]`numFmtId`: 数字显示样式。0:普通数字显示，14:日期方式显示
>>>>
>>>> [a]`fontId`: 字体样式索引
>>>>
>>>> [a]`fillId`: 填充样式索引
>>>>
>>>> [a]`borderId`: 边框样式索引
>>>>
>>>> [a]`xfId`
>>>>
>>>> [a]`applyFont`: `fontId`是否生效
>>>>
>>>> [a]`applyFill`: `fillId`是否生效
>>>
>>
>> cellStyles
>>
>> dxfs
>>
>> tableStyles
>>
>> extLst

## numFmts

### formatCode

eg:

```
[DBNum1][$-804]yyyy&quot;年&quot;m&quot;月&quot;d&quot;日&quot;;@
```

#### ; 分割

* <正数格式>;<负数格式>;<0 格式>;<字符串格式>
* <正数格式 和 0格式>;<负数 格式>
* <数字格式>

#### [DBNum1] 通用格式

参考

* `Ecma-376 Part 1 - 17.16.4.3.1 General formatting - Numeric Values`

常用值

OOXML 协议中：

* DBNUM1: 12 > 一二
* DBNUM2: 12 > 十二

但是，Excel 中：

* DBNUM1: 12 > 十二
* DBNUM2: 12 > 壹拾贰

#### [$USD-409] 语言

格式： ` [$<Currency String>-<language info>]`

以 `$` 开头。

参考

* `Ecma-376 Part 1 - 18.8.31 numFmts (Number Formats)`
* [LCID Structure](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-lcid/63d3d639-7fd2-4afb-abbe-0d5b5551eef8)

常用值

* 804 zh-CN 简体汉语（中国）
* 404 zh-TW 繁体汉语（中国）
* 411 日语（日本）
* 409 英文（美国）
* 809 英文（英国）

特殊值

* f800: System long date format
* f400: System time format
