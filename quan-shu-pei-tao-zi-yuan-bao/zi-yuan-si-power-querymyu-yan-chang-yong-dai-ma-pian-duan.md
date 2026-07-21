# 资源四：Power Query M语言常用代码片段

**删除最前面几行**

m

\= Table.Skip(源, 3)

**重命名列**

m

\= Table.RenameColumns(源, \{{"旧列名", "新列名"\}})

**更改数据类型**

m

\= Table.TransformColumnTypes(源, \{{"花费", type number\}})

**拆分列（按分隔符）**

m

\= Table.SplitColumn(源, "广告活动名称", Splitter.SplitTextByDelimiter("-", QuoteStyle.Csv), {"关键词类型", "投放地区"})

**逆透视列**

m

\= Table.UnpivotOtherColumns(源, {"广告活动"}, "属性", "值")

**追加查询**

m

\= Table.Combine({表1, 表2, 表3})
