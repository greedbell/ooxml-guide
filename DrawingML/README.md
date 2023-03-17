# DrawingML

图表 OOXML 标准。根据 WordprocessingML、SpreadsheetML、PresentationML 数据样式画图。

- `Ecma-376 Part 1 - 14. DrawingML`
- [[MS-ODRAWXML]: Office Drawing Extensions to Office Open XML Structure](https://learn.microsoft.com/en-us/openspecs/office_standards/ms-odrawxml/06cff208-c6e1-4db7-bb68-665135e5f0de)

## 基本概念

- Category Axis 类别轴，横轴，对应数据透视表行域，列出所有类别。
- Value Axis 值轴，纵轴，对应数据透视表值的刻度，列出值的刻度。
- Legend 图例，对应数据透视表的列域。
- Series 系列，图例与类别轴组合后在值轴上的值的集合

## 文件结构

DrawingML 文件结构

> xl
>
> > chars
> >
> > > chart\*.xml
> > >
> > > colors\*.xml
> > >
> > > style\*.xml

### SpreadsheetML

SpreadsheetML 中的 文件结构

> xl
>
> > chars
> >
> > > chart\*.xml
> > >
> > > colors\*.xml
> > >
> > > style\*.xml
> > >
> > > drawings
> > > drawing\*.xml
> > >
> > > pivotCache
> >
> > pivotTables
> >
> > > pivotTable\*.xml
> > >
> > > worksheets
> > > sheet\*.xml

SpreadsheetML 中 `sheet*.xml > drawing*.xml > chart*.xml` 实现插入图表功能

## XML 结构

- [a] 代表元素属性

### chart\*.xml

参考 `Ecma-376 Part 1 - 21.2 DrawingML - Charts`

> `c:chartSpace`
>
> > `c:date1904`
> >
> > `c:roundedCorners`
> >
> > `mc:AlternateContent`
> >
> > > `mc:Choice`
> > >
> > > `mc:Fallback`
> > >
> > > `c:pivotSource` 数据透视表源信息
> > > `c:name` 数据透视表名字，eg：[pivot-table.xlsx]Sheet0!PivotTable2
> > >
> > > `c:fmtId` pivotTable\*.xml 中 chartFormat 元素 chart 值
> > >
> > > > [a] `val` fmtId 的值
> > >
> > > `c:chart` 图表信息
> > > `c:title` 图表标题
> > >
> > > > c:tx
> > > >
> > > > c:autoTitleDeleted
> > >
> > > `c:pivotFmts`
> > >
> > > > c:pivotFmt
> > > >
> > > > > c:idx
> > > > >
> > > > > c:spPr
> > > > >
> > > > > > a:solidFill
> > > > > >
> > > > > > a:ln
> > > > > >
> > > > > > a:effectLst
> > > > > >
> > > > > > c:marker
> > > > >
> > > > > c:dLbl
> > > > >
> > > > > > c:idx
> > > > > >
> > > > > > c:spPr
> > > > > >
> > > > > > c:txPr
> > > > > >
> > > > > > > a:bodyPr
> > > > > > >
> > > > > > > a:lstStyle
> > > > > > >
> > > > > > > a:p
> > > > > > >
> > > > > > > c:dLblPos
> > > > > >
> > > > > > `c:plotArea` 绘制区域
> > > > > > c:layout
> > > >
> > > > `c:barChart` 条形图
> > > >
> > > > > `c:barDir` 条形图方向
> > > > >
> > > > > > [a] `val` 条形图方向的值， [bar,col]
> > > > > >
> > > > > > `c:dLbls` Data Labels，数据标签
> > > > > > `c:showLegendKey`: 是否显示图例
> > > > > >
> > > > > > `c:showVal`: 是否显示值
> > > > > >
> > > > > > `c:showCatName`: 是否显示类别名
> > > > > >
> > > > > > `c:showSerName`: 是否显示系列名
> > > > > >
> > > > > > `c:showPercent`: 是否显示百分比
> > > > > >
> > > > > > `c:showBubbleSize`: 是否显示值气泡尺寸
> > > > >
> > > > > c:grouping
> > > > >
> > > > > c:varyColors
> > > > >
> > > > > `c:ser` (Chart Series) 图表系列，会有多个
> > > > >
> > > > > > c:idx
> > > > > >
> > > > > > c:order
> > > > > >
> > > > > > **c:tx** 系列图例轴
> > > > > >
> > > > > > > `c:strRef` String Reference
> > > > > > >
> > > > > > > > `c:f` String Reference 的值，eg: `Sheet0!$T$6:$T$8`
> > > > > > > >
> > > > > > > > `c:strCache` String Cache
> > > > > > > >
> > > > > > > > > c:ptCount
> > > > > > > > >
> > > > > > > > > `c:pt` String Cache 的值
> > > > > > > > >
> > > > > > > > > > [a] idx
> > > > > > > > > >
> > > > > > > > > > c:v
> > > > > > >
> > > > > > > c:spPr
> > > > > >
> > > > > > c:invertIfNegative
> > > > > >
> > > > > > **c:cat** Category Axis Data，系列类别轴
> > > > > >
> > > > > > > `c:strRef` String Reference
> > > > > > >
> > > > > > > > `c:f` String Reference 的值，eg：`Sheet0!$S$9:$S$13`
> > > > > > > >
> > > > > > > > c:strCache
> > > > > > > >
> > > > > > > > **c:val** 系列值
> > > > > > > > `c:numRef` Number Reference
> > > > > > > > `c:f` Number Reference 的值，eg：`Sheet0!$AA$9:$AA$13`
> > > > > > > >
> > > > > > > > c:numCache
> > > > > > >
> > > > > > > c:extLst
> > > > > > > `c:axId`: `c:catAx` 的 ID
> > > > > > > `val`: `c:axId` 的值
> > > > >
> > > > > `c:axId`: `c:valAx` 的 ID
> > > > >
> > > > > > `val`: `c:axId` 的值
> > > >
> > > > `c:catAx`: (Category Axis Data) 类别轴
> > > >
> > > > > `c:axId`: 类别轴 ID
> > > > >
> > > > > `c:scaling`
> > > > >
> > > > > `c:delete`: 是否删除
> > > > >
> > > > > `c:axPos`: Axis Position，轴位置
> > > > >
> > > > > `c:crossAx`: Crossing Axis ID，交叉的轴的 ID
> > > > >
> > > > > `c:crosses`: 与纵轴交叉的点的值
> > > > >
> > > > > `c:auto`: 自动显示
> > > >
> > > > `c:valAx`: Value Axis，值轴
> > > >
> > > > > `c:axId`: 值轴 ID
> > > > >
> > > > > > [a]`val`: 值
> > > > >
> > > > > `c:scaling`
> > > > >
> > > > > `c:delete`: 是否删除
> > > > >
> > > > > `c:axPos`: Axis Position，轴位置
> > > > >
> > > > > `c:majorGridlines`: Major Gridlines，主网格线
> > > > >
> > > > > `c:spPr`: Shape Properties，刻度属性
> > > > >
> > > > > `c:crossAx`: Crossing Axis ID，交叉的轴的 ID
> > > > >
> > > > > `c:crosses`: 与纵轴交叉的点的值
> > > >
> > > > c:spPr
> > > >
> > > > c:legend
> > >
> > > `c:plotVisOnly`: (Plot Visible Only) 是否只绘制可见的
> > >
> > > c:dispBlanksAs
> > >
> > > c:extLst
> > >
> > > c:showDLblsOverMax
> > >
> > > `c:spPr`: Shape Properties，刻度属性
> >
> > c:txPr
> >
> > c:printSettings
> >
> > c:extLst

`c:ser` 中的 `c:tx` `c:cat` `c:val` 是 `c:chart` 图表信息中最重要的三要素

### drawing\*.xml

参考 `20.5 DrawingML - SpreadsheetML Drawing`

> xdr:wsDr
>
> > xdr:twoCellAnchor
> >
> > > xdr:from
> > >
> > > > xdr:col
> > > >
> > > > xdr:colOff
> > > >
> > > > xdr:row
> > > >
> > > > xdr:rowOff
> > > >
> > > > xdr:to
> > > > xdr:col
> > > >
> > > > xdr:colOff
> > > >
> > > > xdr:row
> > > >
> > > > xdr:rowOff
> > > >
> > > > xdr:graphicFrame
> > > > xdr:nvGraphicFramePr
> > > >
> > > > xdr:cNvPr
> > > >
> > > > > [a] id: 图表 ID
> > > > >
> > > > > [a] name: 图表名
> > > > >
> > > > > a:extLs
> > > > >
> > > > > xdr:xfrm
> > > > > a:off
> > > > >
> > > > > > [a] x
> > > > > >
> > > > > > [a] y
> > > > > >
> > > > > > a:ext
> > > > > > [a] cx
> > > > > >
> > > > > > [a] cy
> > > > >
> > > > > a:graphic
> > > > > a:graphicData
> > > > >
> > > > > > `c:chart` : 图表引用
> > > >
> > > > xdr:clientData

## 实例

### 数据透视表生成数据透视图

从数据透视表生成数据透视图，需要生成 `drawing*.xml` 和 `chart*.xml`

`chart*.xml` 必须要有的元素如下：

```XML
<?xml version="1.0" encoding="UTF-8"?>
<c:chartSpace
    xmlns:c="http://schemas.openxmlformats.org/drawingml/2006/chart"
    xmlns:a="http://schemas.openxmlformats.org/drawingml/2006/main">
    <c:roundedCorners val="false"/>
    <c:pivotSource>
        <c:name>[export-pivot-table.xlsx]Sheet0!PivotTable2</c:name>
        <c:fmtId val="0"/>
    </c:pivotSource>
    <c:chart>
        <c:autoTitleDeleted val="false"/>
        <c:plotArea>
            <c:layout/>
            <c:barChart>
                <c:barDir val="col"/>
                <c:axId val="1"/>
                <c:axId val="2"/>
            </c:barChart>
            <c:catAx>
                <c:axId val="1"/>
                <c:scaling>
                    <c:orientation val="minMax"/>
                </c:scaling>
                <c:delete val="false"/>
                <c:axPos val="b"/>
                <c:majorTickMark val="cross"/>
                <c:minorTickMark val="none"/>
                <c:tickLblPos val="nextTo"/>
                <c:crossAx val="2"/>
                <c:crosses val="autoZero"/>
                <c:auto val="true"/>
                <c:lblAlgn val="ctr"/>
                <c:lblOffset val="100"/>
                <c:noMultiLvlLbl val="false"/>
            </c:catAx>
            <c:valAx>
                <c:axId val="2"/>
                <c:scaling>
                    <c:orientation val="minMax"/>
                </c:scaling>
                <c:delete val="false"/>
                <c:axPos val="l"/>
                <c:majorGridlines>
                    <c:spPr>
                        <a:ln w="9525" cap="flat" cmpd="sng" algn="ctr">
                            <a:solidFill>
                                <a:schemeClr val="tx1">
                                    <a:lumMod val="15000"/>
                                    <a:lumOff val="85000"/>
                                </a:schemeClr>
                            </a:solidFill>
                        </a:ln>
                    </c:spPr>
                </c:majorGridlines>
                <c:majorTickMark val="cross"/>
                <c:minorTickMark val="none"/>
                <c:tickLblPos val="nextTo"/>
                <c:spPr>
                    <a:noFill/>
                    <a:ln>
                        <a:noFill/>
                    </a:ln>
                </c:spPr>
                <c:crossAx val="1"/>
                <c:crosses val="autoZero"/>
                <c:crossBetween val="between"/>
            </c:valAx>
        </c:plotArea>
        <c:legend>
            <c:overlay val="false"/>
        </c:legend>
        <c:plotVisOnly val="true"/>
    </c:chart>
    <c:printSettings>
        <c:headerFooter/>
        <c:pageMargins b="0.75" l="0.7" r="0.7" t="0.75" header="0.3" footer="0.3"/>
        <c:pageSetup/>
    </c:printSettings>
</c:chartSpace>
```

## Tmp
