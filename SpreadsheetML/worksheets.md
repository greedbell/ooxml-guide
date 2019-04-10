# Worksheets

参考 `Ecma-376 Part 1 - 18.3 Worksheets`

## 文件结构

> xl
>> worksheets
>>> `sheet*.xml`
>>
>

## sheet*.xml

> worksheet
>> sheetPr
>>
>> dimension
>>
>> sheetViews
>>
>> sheetFormatPr
>>
>> cols
>>
>> sheetData
>>> `row`
>>>> [a]`r`: 行号
>>>>
>>>> `c`: 单元格
>>>>> [a]`r`: 单元格索引，Eg A1
>>>>>
>>>>> [a]`s`: 单元格样式
>>>>>
>>>>> [a]`t`: 单元格类型，参考 `18.18.11 ST_CellType (Cell Type)`，b (Boolean),d (Date),e (Error),inlineStr (Inline String),n (Number),s (Shared String):普通字符串,str (String):公式字符串
>>>>>
>>>>> `f`: 公式
>>>>>> [a]`ca`: 该公式在下次计算时是否需要重新计算，默认否
>>>>>
>>>>> `v`: 值
>>
>> mergeCells
>>> mergeCell
>>
>> phoneticPr
>>
>> pageMargins
>>
>> pageSetup
>>
>> colBreaks
>>> brk
>>
>> drawing
>
