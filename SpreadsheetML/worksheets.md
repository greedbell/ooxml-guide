# Worksheets

参考 `Ecma-376 Part 1 - 18.3.1 Worksheets`

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
>>> row
>>>> c
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
## styles*.xml

> styleSheet
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
>> `cellXfs`: 第个 cell 样式
>>> `xf`
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
