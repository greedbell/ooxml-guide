# WordprocessingML

Word OOXML 标准

- `Ecma-376 Part 1 - 11. WordprocessingML`
- [[MS-DOCX]: Word Extensions to the Office Open XML (.docx) File Format](https://learn.microsoft.com/en-us/openspecs/office_standards/ms-docx/b839fe1f-e1ca-4fa6-8c26-5954d0abbccd)

## 文件结构

> `[Content_Types].xml`
>
> `_res`
>
> > `.rels`: 记录各个 XML 文件的作用
>
> `docProps`
>
> `word`
>
> > `_res`
> >
> > > `document.xml.rels`: 记录各种关系，eg：链接
> >
> > `document.xml`: 主文档
> >
> > `settings.xml`
> >
> > `styles.xml`: 样式
