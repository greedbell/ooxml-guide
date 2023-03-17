# Document

参考 `Ecma-376 Part 1 - 17.2 Main Document Story`

## 文件结构

> word
>
> > `document.xml`

## document.xml

> `w:document`
>
> > [a] `w:conformance`: 一致性。[transitional（默认值） | strict]
>
> > `w:body`
> >
> > > `w:p`: Paragraph，段落
> > >
> > > > `w:pPr`: Paragraph Properties, 段落属性
> > > >
> > > > > `w:adjustRightInd`: Automatically Adjust Right Indent When Using Document Grid, 向右缩进
> > > > >
> > > > > `w:autoSpaceDE`
> > > > >
> > > > > `w:pBdr`: Paragraph Borders, 段落边框
> > > > >
> > > > > `w:pStyle`: Paragraph Style, 段落样式
> > > >
> > > > `w:r`: Text Run, 段落中的一系列文本内容
> > > >
> > > > > `w:t`: Text, 文本内容
> > > > >
> > > > > > [a] `xml:space`: 字边框, ["preserve" | ...]
> > > > >
> > > > > `w:rPr`: Run Properties, 文本属性
> > > > >
> > > > > > `w:b`: Bold, 加粗
> > > > > >
> > > > > > > [a] `:val`: Value， 值，["false" | "true"]，没有 `:val` 属性表示 true
> > > > > >
> > > > > > `w:i`: Italics, 斜体
> > > > > >
> > > > > > `w:bdr`: Text Border, 文本边框，相比 w:b 有更丰富的属性。
> > > > > >
> > > > > > `w:color`: 颜色
> > > > >
> > > > > `w:bdo`: Bidirectional Override, 双向覆盖
> > > > >
> > > > > `w:drawing`: DrawingML Object, 图表对象
> > > > >
> > > > > `w:ruby`: Phonetic Guide, 语音指导
> > > >
> > > > `w:del`: Deleted Text, 已删除的文本
> > > >
> > > > `w:fldSimple`: 简单的域，参考 [Field](#field)
> > > >
> > > > `w:hyperlink`: 超链接，参考 [Hyperlink](#hyperlink)
> > > >
> > > > `w:bookmarkStart`: 超链接，参考 [Bookmarks](#bookmarks)
> > > >
> > > > `w:bookmarkEnd`: 超链接，参考 [Bookmarks](#bookmarks)

### Field

参考 `Ecma-376 Part 1 - 17.16 Fields and Hyperlinks`

> `w:fldSimple`: 简单的域
>
> > [a] `w:instr`: ["DATE" | ...]
> >
> > `w:r`
> >
> > > `w:t`: 域内的文本
> >
> > `w:r`
> >
> > > `w:tfldChar`: 复杂的域
> >
> > `w:r`
> >
> > > `w:instrText`: 复杂的域

#### Simple Field（简单域）

参考 `Ecma-376 Part 1 - 17.16.2 XML representation`

```XML
<w:p>
  <w:fldSimple w:instr="AUTHOR">
    <w:r>
      <w:t>Marcel Proust</w:t>
    </w:r>
  </w:fldSimple>
</w:p>
```

#### Complex Field（复杂域）

参考 `Ecma-376 Part 1 - 17.16.2 XML representation`

```XML
<w:p>
  <w:r>
    <w:fldChar w:fldCharType="begin"/>
  </w:r>
  <w:r>
    <w:instrText xml:space="preserve"> DATE </w:instrText>
  </w:r>
  <w:r>
    <w:fldChar w:fldCharType="separate"/>
  </w:r>
  <w:r>
    <w:t>12/31/2005</w:t>
  </w:r>
  <w:r>
    <w:fldChar w:fldCharType="end"/>
  </w:r>
</w:p>
```

`<w:fldChar w:fldCharType="begin"/>` 和 `<w:fldChar w:fldCharType="separate"/>` 之间的文本都用 `w:instrText` 而不是 `w:t`，并带上 `xml:space="preserve"` 属性

### Hyperlink

参考 `Ecma-376 Part 1 - 17.16.22 hyperlink (Hyperlink)`

> `w:hyperlink`: 超链接
>
> > [a] `r:anchor`: Hyperlink Anchor, 当前文档内的书签，如果值为空或书签不存在则指向文档开头
> >
> > [a] `r:id`: Hyperlink Target, 目标超链接 ID，eg：rId10 指向的具体内容参考 [relationship.md](../Shared/relationship.md)，优先级大于 `r:anchor`
> >
> > [a] `w:docLocation`: Location in Target Document, 目标对象的位置
> >
> > [a] `w:history`: Add To Viewed Hyperlinks, 点击后是否把该链接添加到打开链接记录，["true" | "false"]
> >
> > [a] `w:tgtFrame`: Hyperlink Target Frame, ["_top" | "_self" | "_parent" | "_blank" | "all other values"]
> >
> > [a] `w:tooltip`: Associated String，鼠标 hover 上去的提示
> >
> > `w:r`
> >
> > > `w:t`: 超链接文本
> > >
> > > `w:rPr`: 文本属性

### Bookmarks

参考 `Ecma-376 Part 1 - 17.13.6 Bookmarks`

```XML
<w:p>
  <w:r>
      <w:t>Example</w:t>
    </w:r>
  <w:bookmarkStart w:id="0" w:name="sampleBookmark" /> <w:r>
  <w:t xml:space="preserve"> text.</w:t> </w:r>
  </w:p> <w:p>
      <w:r>
        <w:t>Example</w:t>
      </w:r>
      <w:bookmarkEnd w:id="0" />
      <w:r>
  <w:t xml:space="preserve"> text.</w:t> </w:r>
</w:p>
```

> `w:bookmarkStart`
>
> > [a] `w:id`: bookmark ID
> >
> > [a] `w:name`: bookmark 名

> `w:bookmarkEnd`
>
> > [a] `w:id`: bookmark ID，和 ID 相同的 `bookmarkStart`一起构成一个 `bookmark`
