# SpreadsheetML

Excel OOXML 标准

## 文件结构

> `xl`
>> `workbook*.xml`
>>
>> `calcChain.xml` 计数链
>>
>> `styles.xml` 样式
>>
>> `worksheets`
>>
>>> `sheet*.xml`
>>
>> `pivotTables`
>>> `pivotTable*.xml`  数据透视表主要数据
>>
>> `pivotCache`
>>> `pivotCacheDefinition*.xml`  数据透视表行、列、筛选器去重后的数据
>>>
>>> `pivotCacheRecords*.xml`  源数据的缓存
>
