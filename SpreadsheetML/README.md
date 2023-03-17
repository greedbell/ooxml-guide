# SpreadsheetML

Excel OOXML 标准

- `Ecma-376 Part 1 - 12. SpreadsheetML`
- [[MS-XLSX]: Excel (.xlsx) Extensions to the Office Open XML SpreadsheetML File Format](https://learn.microsoft.com/en-us/openspecs/office_standards/ms-xlsx/2c5dee00-eff2-4b22-92b6-0738acd4475e)

## 文件结构

> `[Content_Types].xml`
>
> `_res`
>
> `docProps`
>
> `xl`
>
> > `workbook*.xml`
> >
> > `calcChain.xml` 计数链
> >
> > `styles.xml` 样式
> >
> > `worksheets`
> >
> > > `sheet*.xml`
> >
> > `pivotTables`
> >
> > > `pivotTable*.xml` 数据透视表主要数据
> >
> > `pivotCache`
> >
> > > `pivotCacheDefinition*.xml` 数据透视表行、列、筛选器去重后的数据
> > >
> > > `pivotCacheRecords*.xml` 源数据的缓存
