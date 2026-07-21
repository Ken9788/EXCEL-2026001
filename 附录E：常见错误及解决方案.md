# 附录E：常见错误及解决方案

以下为全书各阶段可能遇到的常见错误及排查方法。

#### E-1 公式类错误

<table data-header-hidden><thead><tr><th width="94.77777099609375"></th><th width="109.22222900390625"></th><th width="284.111083984375"></th><th></th></tr></thead><tbody><tr><td>错误代码</td><td>含义</td><td>常见原因</td><td>排查方法</td></tr><tr><td>#N/A</td><td>找不到匹配值</td><td>VLOOKUP/XLOOKUP找不到查找值；查找值有空格差异；格式不一致</td><td>用TRIM清洗；检查格式（文本vs数字）；确认查找值确实存在</td></tr><tr><td>#DIV/0!</td><td>除以零</td><td>公式试图除以0或空单元格</td><td>用IFERROR或DIVIDE函数处理</td></tr><tr><td>#VALUE!</td><td>值类型错误</td><td>对不同类型的数据做了不该做的运算（如文本+数字）</td><td>检查数据类型是否匹配；用VALUE函数转换</td></tr><tr><td>#REF!</td><td>引用无效</td><td>公式引用的单元格被删除</td><td>检查被引用的区域是否还在</td></tr><tr><td>#NAME?</td><td>函数名错误</td><td>函数名拼写错误</td><td>检查函数名称是否正确</td></tr><tr><td>#NUM!</td><td>数字错误</td><td>计算结果超出Excel范围</td><td>检查参数值是否合理</td></tr><tr><td>#NULL!</td><td>区域无效</td><td>引用的区域没有交集</td><td>检查引用区域的写法</td></tr><tr><td>结果为0</td><td>没有符合条件的数据</td><td>SUMIFS/COUNTIFS条件写错；数据中确实没有符合条件的值</td><td>检查条件写法；手动筛选验证</td></tr></tbody></table>

#### E-2 透视表问题

<table data-header-hidden><thead><tr><th width="154.5555419921875"></th><th width="220.4444580078125"></th><th></th></tr></thead><tbody><tr><td>问题现象</td><td>可能原因</td><td>解决方案</td></tr><tr><td>日期无法分组</td><td>日期列是文本格式</td><td>改为日期格式</td></tr><tr><td>切片器不联动</td><td>透视表数据源不同</td><td>确保基于同一数据模型</td></tr><tr><td>刷新后格式丢失</td><td>格式未设置为“保留”</td><td>右键→透视表选项→布局和格式→勾选“保留单元格格式”</td></tr><tr><td>计数而非求和</td><td>列中有空值或文本</td><td>确保数据列全是数字</td></tr><tr><td>计算字段不显示</td><td>公式中有无效字段名</td><td>检查公式中的字段名是否与实际字段名一致</td></tr><tr><td>值筛选条件不可用</td><td>值区域字段未设置为数值型</td><td>检查值字段的汇总方式是否为“求和”或“平均值”</td></tr></tbody></table>

#### E-3 Power Query问题

<table data-header-hidden><thead><tr><th width="171.22222900390625"></th><th width="178.00006103515625"></th><th width="260.9998779296875"></th></tr></thead><tbody><tr><td>问题现象</td><td>可能原因</td><td>解决方案</td></tr><tr><td>刷新失败</td><td>文件路径或名称变更</td><td>检查数据源路径</td></tr><tr><td>数据类型错误</td><td>列中有混合类型</td><td>先清洗再更改类型</td></tr><tr><td>合并查询结果为空</td><td>关联列有空格差异</td><td>使用“修剪”功能</td></tr><tr><td>逆透视后数据翻倍</td><td>原始表有汇总行</td><td>删除汇总行后再逆透视</td></tr><tr><td>追加查询后顺序混乱</td><td>源表排序不一致</td><td>在PQ中添加索引列确保顺序</td></tr><tr><td>从文件夹导入失败</td><td>文件结构不完全相同</td><td>检查所有文件的列结构是否一致</td></tr></tbody></table>

#### E-4 Power Pivot / DAX问题

<table data-header-hidden><thead><tr><th width="191.22222900390625"></th><th width="175.7777099609375"></th><th width="314.33343505859375"></th></tr></thead><tbody><tr><td>问题现象</td><td>可能原因</td><td>解决方案</td></tr><tr><td>度量值返回空白</td><td>筛选上下文无数据</td><td>检查表间关系是否正确</td></tr><tr><td>时间智能函数报错</td><td>未标记日期表</td><td>标记日历表为日期表</td></tr><tr><td>CALCULATE不生效</td><td>筛选器写错</td><td>检查筛选条件语法</td></tr><tr><td>关系图视图显示空白</td><td>未添加表到数据模型</td><td>确认所有表已添加到模型</td></tr><tr><td>透视表中找不到度量值</td><td>度量值未保存</td><td>在Power Pivot中确认度量值存在且无误</td></tr></tbody></table>

#### E-5 数据类型问题

<table data-header-hidden><thead><tr><th width="191.22222900390625"></th><th width="183.5555419921875"></th><th width="268.77777099609375"></th></tr></thead><tbody><tr><td>问题现象</td><td>可能原因</td><td>解决方案</td></tr><tr><td>文本数字不能求和</td><td>数字存储为文本格式</td><td>用VALUE转换或分列功能</td></tr><tr><td>日期排序错乱</td><td>日期存储为文本</td><td>用DATEVALUE转换为日期格式</td></tr><tr><td>透视表计数而非求和</td><td>列中包含文本或空值</td><td>确保列中只有数字</td></tr><tr><td>VLOOKUP匹配不上</td><td>一个表中是文本，另一个表中是数字</td><td>统一格式，用TEXT或VALUE转换</td></tr><tr><td>导入CSV后数字变文本</td><td>CSV格式导致</td><td>导入时选择正确的数据类型</td></tr></tbody></table>

#### E-6 AI生成代码问题

<table data-header-hidden><thead><tr><th width="170.111083984375"></th><th width="252.4443359375"></th><th width="199.8890380859375"></th></tr></thead><tbody><tr><td>问题现象</td><td>可能原因</td><td>解决方案</td></tr><tr><td>公式报错</td><td>AI写了不存在的函数或引用错误</td><td>把错误信息发给AI修正</td></tr><tr><td>逻辑不对</td><td>需求描述不清晰</td><td>补充业务逻辑描述</td></tr><tr><td>版本不兼容</td><td>AI用了新版Excel函数</td><td>告知AI你的Excel版本</td></tr><tr><td>运行结果与预期不符</td><td>条件顺序错误或引用类型错误</td><td>逐行检查公式逻辑</td></tr></tbody></table>

#### E-7 快速排查流程图

公式报错

&#x20;   ↓

看错误代码（#N/A? #VALUE!? #REF!? #DIV/0!? #NAME?）

&#x20;   ↓

&#x20;   ├── #N/A → 检查查找值是否存在、有无空格、格式是否一致

&#x20;   ├── #VALUE! → 检查数据类型（文本vs数字）

&#x20;   ├── #REF! → 检查引用的单元格/区域是否被删除

&#x20;   ├── #DIV/0! → 检查除数是否为0或空

&#x20;   └── #NAME? → 检查函数名拼写是否正确

&#x20;   ↓

用F9逐步计算，定位出错位置

&#x20;   ↓

修正后，用IFERROR保护边缘情况
