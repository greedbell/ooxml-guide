# DrawingML

图表 OOXML 标准。根据 WordprocessingML、SpreadsheetML、PresentationML 数据样式画图。

## 文件结构

DrawingML 文件结构

> xl
>> chars
>>> chart*.xml
>>>
>>> colors*.xml
>>>
>>> style*.xml

### SpreadsheetML

SpreadsheetML 中的 文件结构

> xl
>> chars
>>> chart*.xml
>>>
>>> colors*.xml
>>>
>>> style*.xml
>>>
>> drawings
>>> drawing*.xml
>>>
>> pivotCache
>>
>> pivotTables
>>> pivotTable*.xml
>>>
>> worksheets
>>> sheet*.xml

SpreadsheetML 中 `sheet*.xml > drawing*.xml > chart*.xml` 实现插入图表功能

## XML 结构

* [a] 代表元素属性

### chart*.xml

参考 `21.2 DrawingML - Charts`

> c:chartSpace
>> c:date1904
>>
>> c:roundedCorners
>>
>> mc:AlternateContent
>>> mc:Choice
>>>
>>> mc:Fallback
>>>
>> `c:pivotSource` 数据透视表
>>> `c:name` 数据透视表名字
>>>
>>> `c:fmtId` pivotTable*.xml 中 chartFormat 的 ID
>>>> [a] `val` fmtId 的值
>>>
>> `c:chart` 图表信息
>>> `c:title` 图表标题
>>>> c:tx
>>>>
>>> c:autoTitleDeleted
>>>
>>> `c:pivotFmts`
>>>> c:pivotFmt
>>>>> c:idx
>>>>>
>>>>> c:spPr
>>>>>> a:solidFill
>>>>>>
>>>>>> a:ln
>>>>>>
>>>>>> a:effectLst
>>>>>>
>>>>> c:marker
>>>>>
>>>>> c:dLbl
>>>>>> c:idx
>>>>>>
>>>>>> c:spPr
>>>>>>
>>>>>> c:txPr
>>>>>>> a:bodyPr
>>>>>>>
>>>>>>> a:lstStyle
>>>>>>>
>>>>>>> a:p
>>>>>>>
>>>>>> c:dLblPos
>>>>>>
>>> `c:plotArea` 图标在数据透视表中的区域
>>>> c:layout
>>>>
>>>> `c:barChart` 条形图
>>>>> `c:barDir` 条形图方向
>>>>>> [a] `val` 条形图方向的值， [bar,col]
>>>>>>
>>>>> c:grouping
>>>>>
>>>>> c:varyColors
>>>>>
>>>>> `c:ser` (Chart Series) 图表系列，会有多个
>>>>>> c:idx
>>>>>>
>>>>>> c:order
>>>>>>
>>>>>> `c:tx` 系列图例轴
>>>>>>> `c:strRef` String Reference
>>>>>>>> `c:f` String Reference 的值，eg: `Sheet0!$T$6:$T$8`
>>>>>>>>
>>>>>>>> `c:strCache` String Cache
>>>>>>>>> c:ptCount
>>>>>>>>>
>>>>>>>>> `c:pt` String Cache 的值
>>>>>>>>>> [a] idx
>>>>>>>>>>
>>>>>>>>>> c:v
>>>>>>>>>
>>>>>>>>
>>>>>>>
>>>>>> c:spPr
>>>>>>
>>>>>> c:invertIfNegative
>>>>>>
>>>>>> `c:cat` Category Axis Data，系列类别轴
>>>>>>> `c:strRef` String Reference
>>>>>>>> `c:f` String Reference 的值，eg：`Sheet0!$S$9:$S$13`
>>>>>>>>
>>>>>>>> c:strCache
>>>>>>>>
>>>>>> `c:val` 系列值
>>>>>>> `c:numRef` Number Reference
>>>>>>>> `c:f` Number Reference 的值，eg：`Sheet0!$AA$9:$AA$13`
>>>>>>>>
>>>>>>>> c:numCache
>>>>>>>
>>>>>> c:extLst
>>>>>
>>>> c:catAx
>>>>
>>>> c:valAx
>>>>
>>>> c:spPr
>>>>
>>> c:legend
>>>
>>> c:plotVisOnly
>>>
>>> c:dispBlanksAs
>>>
>>> c:extLst
>>>
>>> c:showDLblsOverMax
>>>
>> c:spPr
>>
>> c:txPr
>>
>> c:printSettings
>>
>> c:extLst
>>

`c:ser` 中的 `c:tx` `c:cat` `c:val` 是 `c:chart` 图表信息中最重要的三要素

### drawing*.xml

参考 `20.5 DrawingML - SpreadsheetML Drawing`

> xdr:wsDr
>> xdr:twoCellAnchor
>>> xdr:from
>>>> xdr:col
>>>>
>>>> xdr:colOff
>>>>
>>>> xdr:row
>>>>
>>>> xdr:rowOff
>>>>
>>> xdr:to
>>>> xdr:col
>>>>
>>>> xdr:colOff
>>>>
>>>> xdr:row
>>>>
>>>> xdr:rowOff
>>>>
>>> xdr:graphicFrame
>>>> xdr:nvGraphicFramePr
>>>>
>>>> xdr:cNvPr
>>>>> [a] id: 图表 ID
>>>>>
>>>>> [a] name: 图表名
>>>>>
>>>>> a:extLs
>>>>>
>>>> xdr:xfrm
>>>>> a:off
>>>>>> [a] x
>>>>>>
>>>>>> [a] y
>>>>>>
>>>>> a:ext
>>>>>> [a] cx
>>>>>>
>>>>>> [a] cy
>>>>>
>>>> a:graphic
>>>>> a:graphicData
>>>>>> c:chart : 图表引用
>>>>>
>>>>
>>> xdr:clientData
