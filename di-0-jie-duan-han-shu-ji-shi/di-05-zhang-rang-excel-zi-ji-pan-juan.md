# 第0-5章：让Excel自己"判卷"

“600个广告活动，手工分类要多久？用=IFS(M2>3, "高效", M2>2, "正常", TRUE, "待优化")，向下拖动，3秒完成。这就是逻辑函数的威力——让Excel替你做判断。”

### 现在就动手

打开 「广告日报」 工作表。

在数据右侧的空白列中（比如N列），输入以下公式：

\=IFS(M2>3, "高效", M2>2, "正常", TRUE, "待优化")

按回车。

你看到了什么？这一行的ROAS被自动分到了某一类：“高效”、“正常”或“待优化”。

现在把鼠标移到这个单元格的右下角，双击黑色十字（或向下拖动到所有数据行）——看看发生了什么？

整个600行数据，每一行都被自动打上了标签。

💡 在单元格里试试就知道了。

你刚刚完成的操作，如果用手工做是这样的：看第1行ROAS→判断它是高效还是正常还是待优化→手动输入标签→看第2行……重复600次。

那是至少30分钟的机械劳动。

而你用一条公式，3秒钟，全部完成。

这一章，就是让你学会“让Excel替你做判断”。

### 一、IF——二选一的判断

IF是最基础的逻辑函数。它在做一件事：

条件成立，返回A；条件不成立，返回B。

IF的语法

\=IF(条件, 成立时返回的值, 不成立时返回的值)

<table data-header-hidden><thead><tr><th width="78.4444580078125"></th><th width="244"></th></tr></thead><tbody><tr><td>参数</td><td>说明</td></tr><tr><td>第1个</td><td>条件（结果为TRUE或FALSE）</td></tr><tr><td>第2个</td><td>条件成立时返回什么</td></tr><tr><td>第3个</td><td>条件不成立时返回什么</td></tr></tbody></table>

广告案例：判断ACOS是否达标

在「广告日报」中，K列是ACOS，J列是目标ACOS。

\=IF(K2 <= J2, "达标", "超标")

执行过程：

1\.        Excel读取K2（实际ACOS）和J2（目标ACOS）

2\.        比较：实际ACOS ≤ 目标ACOS？

3\.        是 → “达标”

4\.        否 → “超标”

简单判断ROAS是否合格

\=IF(M2 > 3, "合格", "需优化")

### 二、IFS——多选一的判断

如果你要判断的不止两种情况，而是三种、四种或更多，就需要IFS。

IFS的语法

\=IFS(条件1, 结果1, 条件2, 结果2, ..., TRUE, 默认结果)

核心规则：按顺序检查，返回第一个成立的条件对应的结果。条件必须从最严格到最宽松排列。

广告案例：根据ROAS打三档标签

\=IFS(M2>3, "高效", M2>2, "正常", TRUE, "待优化")

执行过程：

<table data-header-hidden><thead><tr><th width="97.888916015625"></th><th width="412.7777099609375"></th><th width="91.77783203125"></th></tr></thead><tbody><tr><td>ROAS值</td><td>检查过程</td><td>结果</td></tr><tr><td>4.2</td><td>4.2>3成立 → 返回“高效”</td><td>“高效”</td></tr><tr><td>2.5</td><td>2.5>3不成立 → 2.5>2成立 → 返回“正常”</td><td>“正常”</td></tr><tr><td>1.8</td><td>1.8>3不成立 → 1.8>2不成立 → TRUE成立 → “待优化”</td><td>“待优化”</td></tr></tbody></table>

多条件组合

有时候条件不是单一的，要同时满足多个条件。

场景：ROAS > 3 且 花费 > 200 → “⭐明星”

\=IFS(AND(M2>3, E2>200), "⭐明星", M2>3, "高效", M2>2, "正常", TRUE, "待优化")

<table data-header-hidden><thead><tr><th width="99.5555419921875"></th><th width="432.888916015625"></th></tr></thead><tbody><tr><td>条件顺序</td><td>说明</td></tr><tr><td>第1个</td><td>AND(M2>3, E2>200) → 两个条件同时满足才是“明星”</td></tr><tr><td>第2个</td><td>M2>3 → 不满足“明星”但ROAS>3的，是“高效”</td></tr><tr><td>第3个</td><td>M2>2 → 不满足以上但ROAS>2的，是“正常”</td></tr><tr><td>第4个</td><td>TRUE → 其余全部“待优化”</td></tr></tbody></table>

条件顺序极其重要。 如果把M2>3写在AND(M2>3, E2>200)前面，那么ROAS>3且花费>200的活动会先匹配“高效”，永远不会被标记为“明星”。

### 三、AND / OR——组合条件

AND——所有条件都成立

\=AND(条件1, 条件2, 条件3, ...)

全部TRUE才返回TRUE。

广告案例：判断“ROAS>3 且 花费>200”

\=AND(M2>3, E2>200)

OR——任一条件成立

\=OR(条件1, 条件2, 条件3, ...)

只要有一个TRUE就返回TRUE。

广告案例：判断“需关注”（ROAS<2 或 花费>500）

\=OR(M2<2, E2>500)

与IF组合使用

\=IF(AND(M2>3, E2>200), "明星活动", "普通")

### 四、IFERROR——处理错误值

当你计算ROAS或ACOS时，如果花费为0，公式会报错#DIV/0!。

IFERROR的作用就是：如果公式报错，就显示你指定的内容。

IFERROR的语法

\=IFERROR(原公式, 出错时显示的值)

广告案例

不安全写法：

\=I2/E2

如果E2为0，返回#DIV/0!。

安全写法：

\=IFERROR(I2/E2, 0)

如果E2为0，返回0而不是报错。

更友好的写法：

\=IFERROR(I2/E2, "无数据")

如果E2为0，显示“无数据”。

### 五、综合实战——让Excel自己“判卷”

场景

在「广告日报」中完成以下判断：

1\.        计算ACOS

2\.        判断ACOS是否达标（对比目标ACOS）

3\.        根据ROAS打三档标签

4\.        标记“明星活动”（ROAS>3 且 花费>200）

5\.        用IFERROR保护所有除法计算

操作步骤

第1步：计算ACOS（用IFERROR保护）

在K列：

\=IFERROR(I2/E2, 0)

第2步：判断ACOS是否达标

在L列：

\=IF(K2 <= J2, "达标", "超标")

第3步：计算ROAS（用IFERROR保护）

在M列：

\=IFERROR(I2/E2, 0)

第4步：根据ROAS打标签

在N列：

\=IFS(M2>3, "高效", M2>2, "正常", TRUE, "待优化")

第5步：标记“明星活动”

在O列： =IF(AND(M2>3, E2>200), "⭐明星", "")

完成后的效果

<table data-header-hidden><thead><tr><th width="78"></th><th width="81.3333740234375"></th><th width="105.77777099609375"></th><th width="118"></th><th width="78"></th><th width="113"></th><th width="108.33331298828125"></th></tr></thead><tbody><tr><td>...</td><td>ACOS</td><td>目标ACOS</td><td>ACOS达标？</td><td>ROAS</td><td>ROAS标签</td><td>明星活动</td></tr><tr><td>...</td><td>22%</td><td>25%</td><td>达标</td><td>3.2</td><td>高效</td><td>⭐明星</td></tr><tr><td>...</td><td>18%</td><td>20%</td><td>达标</td><td>2.8</td><td>正常</td><td></td></tr><tr><td>...</td><td>35%</td><td>25%</td><td>超标</td><td>1.8</td><td>待优化</td><td></td></tr></tbody></table>

💡 在单元格里试试就知道了。 把IFS中的阈值从3改成2.5，观察标签如何批量变化——修改一个数字，所有判断瞬间更新。

### 六、这一章你带走了什么？

<table data-header-hidden><thead><tr><th width="229.55560302734375"></th><th width="260.66668701171875"></th></tr></thead><tbody><tr><td>你之前可能觉得</td><td>你现在知道了</td></tr><tr><td>给600行打标签好麻烦</td><td>IFS一条公式，3秒完成</td></tr><tr><td>条件组合好复杂</td><td>AND/OR让组合变简单</td></tr><tr><td>除法报错好烦人</td><td>IFERROR让错误消失</td></tr><tr><td>改一个判断标准要重做所有</td><td>改一个数字，所有标签自动更新</td></tr></tbody></table>

核心公式对比：

<table data-header-hidden><thead><tr><th width="102.3333740234375"></th><th width="257.5555419921875"></th><th width="152.5555419921875"></th></tr></thead><tbody><tr><td>函数</td><td>语法</td><td>适用场景</td></tr><tr><td>IF</td><td>=IF(条件, 成立值, 不成立值)</td><td>二选一</td></tr><tr><td>IFS</td><td>=IFS(条件1, 值1, 条件2, 值2, ...)</td><td>多选一</td></tr><tr><td>IFERROR</td><td>=IFERROR(原公式, 出错值)</td><td>处理错误</td></tr><tr><td>AND</td><td>=AND(条件1, 条件2, ...)</td><td>全部条件成立</td></tr><tr><td>OR</td><td>=OR(条件1, 条件2, ...)</td><td>任一条件成立</td></tr></tbody></table>

黄金法则：在IFS中，最严格的条件必须写在最前面。

💡 在单元格里试试就知道了。 把IFS中条件的顺序调换一下，看看结果怎么变——你亲眼看一次条件顺序的影响，就永远不会忘记。

### 七、本章实操任务

任务1：ACOS达标判断

在「广告日报」中新增ACOS列（销售额÷花费），用IF判断ACOS是否低于目标ACOS。

任务2：ROAS标签

用IFS根据ROAS打三档标签：高效（>3）、正常（>2）、待优化（≤2）。

任务3：多条件组合

· 新增“明星活动”列：ROAS>3 且 花费>200

· 新增“需关注”列：ROAS<2 或 花费>500

任务4：错误保护

修改ACOS和ROAS的计算公式，用IFERROR保护，确保花费为0时不报错。

### 八、本章思考题

1\.        在IFS中，为什么“最严格的条件必须写在最前面”？如果写反了会发生什么？

2\.        IFERROR能处理哪些类型的错误？它不能处理什么问题？

3\.        你让Excel替你做判断这件事，除了打标签，还能用在哪里？

### 九、本章学习记录

<table data-header-hidden><thead><tr><th width="211.77783203125"></th><th width="157.333251953125"></th></tr></thead><tbody><tr><td>项目</td><td>完成情况</td></tr><tr><td>用IF判断ACOS是否达标</td><td>✅ / ⬜</td></tr><tr><td>用IFS打ROAS三档标签</td><td>✅ / ⬜</td></tr><tr><td>用AND/OR组合条件</td><td>✅ / ⬜</td></tr><tr><td>用IFERROR保护除法</td><td>✅ / ⬜</td></tr><tr><td>完成综合实战</td><td>✅ / ⬜</td></tr><tr><td>完成实操任务</td><td>✅ / ⬜</td></tr></tbody></table>

下一章预告：第0-6章《3个函数“拆开”600个广告名》。

写一行=RIGHT(D2, LEN(D2)-FIND("-", D2))，所有“美国”“欧洲”“日本”瞬间提取出来——你亲手把混乱的文本，变成了可分析的数据。

💡 打开EXCEL，在单元格里试试就知道了
