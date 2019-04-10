# Styles

参考 `Ecma-376 Part 1 - 18.8 Styles`

## 文件结构

> xl
>> `styles.xml`
>

## styles.xml

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
