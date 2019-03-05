# 数据透视表

## 文件结构

> xl
>> pivotTables
>>> `pivotTable*.xml`  数据透视表主要数据
>>
>> pivotCache
>>> `pivotCacheDefinition*.xml`  数据透视表行、列、筛选器去重后的数据
>>>
>>> `pivotCacheRecords*.xml`  源数据的缓存
>>
>

## XML 说明

参考 `Ecma-376 Part 1 - 18.10 Pivot Tables`

### pivotTable*.xml

> `pivotTableDefinition`
>> `pivotFields`: 数据透视表字段
>>> `pivotField`
>>
>> `rowFields`: 行域
>>
>> `colFields`: 列域
>>
>> `pageFields`: 筛选器
>>
>> `dataFields`: 值域
>>
>> `pivotTableStyleInfo`: 样式
>>
>> `filters`: 行列的筛选器
>>
>> `chartFormats`: 数据透视图信息，包含多个 chartFormat
>>> `chartFormat`: 每个数据透视图系列数据
>>>>
>>>> [a] `chart`: DrawingML charts 索引
>>>>
>>>> [a] `format`: 每个 chartFormat 的 ID
>>>>
>>>> [a] `series`: true -> series, false -> data point
>>>>
>>>> `pivotArea`: 区域规则
>>>>> [a] `type`: PivotTable 的什么区域，[all,button,data,none,normal,normal,topEnd]
>>>>>
>>>>> [a] `outline`: 是否为大纲模式
>>>>>
>>>>> [a] `fieldPosition`
>>>>>
>>>>> `references`
>>>>>> `reference`: @see 18.10.2.1 reference (Reference)
>>>>>>> [a] `field`: pivot field Index，-2 代表值域
>>>>>>>
>>>>>>> [a] `count`: 包含 field 中 item 的数量
>>>>>>>
>>>>>>> [a] `selected`: 是否被选中
>>>>>>>
>>>>>>> `x`: pivot field 中的某个 item
>>>>>>>> [a] `v`: item 在 cache field 中的 index
