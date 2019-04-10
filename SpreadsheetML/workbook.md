# Workbook

参考 `Ecma-376 Part 1 - 18.2 Workbook`

## 文件结构

> xl
>> `workbook*.xml`
>

## workbook*.xml

> `workbook`
>> `fileVersion`
>>
>> `workbookPr`
>>
>> `mc:AlternateContent`
>>> `mc:Choice`
>>>
>>> `xr:revisionPtr`
>>>
>>> `bookViews`
>>>
>>> `sheets`
>>>
>>> `calcPr`: Calculation Properties（计算选项）
>>>
>>>> [a] `calcId`: 计算版本
>>>>
>>>> [a] `calcMode`: 什么时候计算公式。  auto(默认):打工 Excel 或任何单元格内容变化时重新计算; autoNoTable: 除模拟运算表外自动计算; manual:用户手动触发
>>>>
>>>> [a] `iterate`: 是否开启迭代计算，默认否
>>>>
>>>> [a] `iterateCount`: 迭代计算最多迭代次数，默认 100
>>>>
>>>> [a] `iterateDelta`: 迭代计算最大误差，默认 0.001。当连续计算的结果差异小于此值时，停止迭代。
>>>
>>> `extLst`
>
