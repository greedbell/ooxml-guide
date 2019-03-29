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
>> `pivotFields`: 数据透视表字段集合
>>> `pivotField`: 数据透视表字段
>>>> [a] `name`:
>>>>
>>>> [a] `axis`:
>>>>
>>>> [a] `compact`: ?
>>>>
>>>> [a] `outline`: ?
>>>>
>>>> [a] `multipleItemSelectionAllowed`: ?
>>>>
>>>> [a] `showAll`:
>>>>
>>>> [a] `sortType`: 排序 [descending|asending]
>>>>
>>>> [a] `subtotalTop`
>>>>
>>>> [a] `defaultSubtotal`
>>>>
>>>> [a] `dataField`: 是否为值域，默认 false
>>>>
>>>> [a] `measureFilter`: 是否包含计数项，默认 false
>>>>
>>>> `items`:
>>>>> `item`:
>>>>>> [a] `t`: 数据类型，[avg,sum,max,......,default]
>>>>>>
>>>>>> [a] `x`: 对应 cacheFields 中 shareItems 索引
>>>>>>
>>>>>> [a] `h`: 是否隐藏
>>>>>>
>>>>>> [a] `sd`: Hide Details，是否隐藏详情，默认 true 展开
>>>>>>
>>>>>> [a] `f`: 是否为计数项，默认 false 不是
>>>>
>>>> `autoSortScope`: 排序依据，如果没有该元素，表示按自己排序，有的话按对应值域排序
>>>>> `pivotArea`
>>>>>> `references`
>>>>>>> `reference`
>>>>>>>> [a] `field`: pivotFields 索引。`4294967294` 表示总计，其它情况只能是列
>>>>>>>>
>>>>>>>> `x`: 某个域的 Item 索引。`field` 为 `4294967294` 表示值域索引
>>>>>>>>> [a] `v`: `x` 的值

// 数据1
<autoSortScope>
    <pivotArea dataOnly="0" outline="0" fieldPosition="0">
        <references count="1">
            <reference field="4294967294" count="1" selected="0">
                <x v="0"/>
            </reference>
        </references>
    </pivotArea>
</autoSortScope>

// 字段 1
<autoSortScope>
    <pivotArea dataOnly="0" outline="0" fieldPosition="0">
        <references count="1">
            <reference field="4294967294" count="1" selected="0">
                <x v="1"/>
            </reference>
        </references>
    </pivotArea>
</autoSortScope>

// 数据2
<autoSortScope>
    <pivotArea dataOnly="0" outline="0" fieldPosition="0">
        <references count="1">
            <reference field="4294967294" count="1" selected="0">
                <x v="2"/>
            </reference>
        </references>
    </pivotArea>
</autoSortScope>
>>
>> `rowFields`: 行域
>>> `field`
>>
>> `colFields`: 列域
>>> `field`
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

## pivotCacheDefinition*.xml

> pivotCacheDefinition
>> cacheSource
>>
>> cacheFields
>>> cacheField
>>>> [a] `databaseField`: 是否为数据库字段，默认是，如果不是的则为计数字段
>>
>> calculatedItems
>>> calculatedItem
