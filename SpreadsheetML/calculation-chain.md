# 计算链

参考 `Ecma-376 Part 1 - 18.6 Calculation Chain`

## 文件结构

> xl
>> `calcChain.xml` 计数链
>

## calcChain.xml

> `calcChain`
>> `c`: Cell
>>> [a] `a`: Array，是否为 array formula
>>>
>>> [a] `r`: Cell Reference， A1 格式的索引
>>>
>>> [a] `i`: Sheet Id，Cell 所属的 sheet 的 ID。如果没有，取上个 cell 的
>>>
>>> [a] `l`: New Dependency Level， 单元格公式是否开启新的依赖
>>>
>>> [a] `s`: Child Chain，cell 公式是否在子链上？？如果未设置，取上一个 cell 的值
>
