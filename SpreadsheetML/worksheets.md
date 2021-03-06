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
>>> `tabColor`: tab 颜色
>>>> [a]`theme`: 主题，<clrScheme> 的索引，eg: 8
>>>>
>>>> [a]`tint`: Specifies the tint value applied to the color. eg: -0.499984740745262
>>>>
>>>> [a]`rgb`: ARGB 色值，eg: FFFF0000
>>
>> dimension
>>
>> sheetViews
>>
>> sheetFormatPr
>>
>> cols
>>
>> `sheetData`
>>> `row`
>>>> [a]`r`: 行号
>>>>
>>>> `c`: 单元格
>>>>> [a]`r`: 单元格索引，Eg A1
>>>>>
>>>>> [a]`spans`:
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
>> `hyperlinks`: 超链接
>>> `hyperlink`: 超链接
>>>> [a]`ref`: 使用该超链接的区域。eg1: `A1:B2`，eg2: `A1`
>>>>
>>>> [a]`tooltip`: 鼠标放上去的时候显示的内容。
>>>>
>>>> [a]`location`: 内部链接跳转的位置。单元格位置或者自定义名称，自定义名称只能是对应单元格，不能是 sheet，否则不能跳转。单元格位置格式：`[sheet name]!<area references>`。 eg1: `Sheet1!A1`. eg2: `Sheet1!A1:B9`. eg3: `custom_name`
>>>>
>>>> [a]`display`: 显示内容。
>>>>
>>>> [a]`r:id`: 外部链接 `_rels/sheet*.xml.rels` 中 `Relationship` 的 ID. eg: `rId1`
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
>> `extLst`
>

### extLst

参考 <https://docs.microsoft.com/en-us/openspecs/office_standards/ms-xlsx/07d607af-5618-4ca2-b683-6a78dc0d9627>

### formula

* COUNT: 数值计算 函数计算包含数字的单元格个数以及参数列表中数字的个数。
* COUNTA: 计算  函数计算范围中不为空的单元格的个数。
