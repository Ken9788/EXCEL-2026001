# 第0-4章：3秒汇总，告别手动筛选

“老板问Google渠道总花费是多少？写一行  =SUMIFS(E:E, B:B, "Google")，3秒出结果。这就是统计函数的价值——告别手动筛选求和。”

### 现在就动手

打开 「广告日报」 工作表。

看看 B列（渠道）和 E列（花费）。

现在找一个空白单元格，输入以下公式：

\=SUMIFS(E:E, B:B, "Google")

按回车。

你看到了什么？Google渠道的总花费，瞬间出现在你眼前。

现在把公式中的“Google”改成“Facebook”：

\=SUMIFS(E:E, B:B, "Facebook")

又是1秒钟，Facebook的总花费出现了。

再改成“Amazon”，还是1秒钟。

💡 在单元格里试试就知道了。

你刚刚完成的操作，如果手工做是这样的：筛选出Google的所有行 → 选中花费列 → 看右下角求和 → 记下来 → 取消筛选 → 再筛选Facebook……重复三次，3-5分钟。

而你用公式，3秒钟，三个渠道全部算完。

这一章，就是让你掌握这套“按条件汇总”的方法。

### 一、统计函数的本质

统计函数做的事情，用一句话就能说清楚：

筛选出符合条件的行 → 对指定列做计算 → 返回结果

你刚才写的 SUMIFS(E:E, B:B, "Google") 就是在做三件事：

1\.        在B列中筛选出所有等于“Google”的行

2\.        取出这些行对应的E列（花费）数值

3\.        把它们加起来

### 二、SUMIFS——按条件求和

SUMIFS是广告投手最常用的统计函数。它的任务：对符合条件的所有行，把某一列的数字加起来。

SUMIFS的语法

\=SUMIFS(求和区域, 条件区域1, 条件1, 条件区域2, 条件2, ...)

<table data-header-hidden><thead><tr><th width="108.44439697265625"></th><th width="259.55560302734375"></th></tr></thead><tbody><tr><td>参数</td><td>说明</td></tr><tr><td>第1个</td><td>对哪一列求和（通常是数字列）</td></tr><tr><td>第2个</td><td>第一个条件对应的列</td></tr><tr><td>第3个</td><td>第一个条件的具体内容</td></tr><tr><td>第4个+</td><td>更多条件（最多127对）</td></tr></tbody></table>

核心规则：条件区域和条件必须成对出现。先写“在哪一列筛选”，再写“筛选什么值”。

单条件求和

Google渠道总花费：

\=SUMIFS(E:E, B:B, "Google")

产品线为“电子产品”的总花费（需先匹配好产品线列）：

\=SUMIFS(E:E, L:L, "电子产品")

多条件求和

Google渠道在2025年10月的总花费：

\=SUMIFS(E:E, B:B, "Google", A:A, ">=2025/10/1", A:A, "<=2025/10/31")

条件写法速查：

<table data-header-hidden><thead><tr><th width="110.111083984375"></th><th width="173.55560302734375"></th><th width="162.11114501953125"></th></tr></thead><tbody><tr><td>条件类型</td><td>写法</td><td>示例</td></tr><tr><td>等于某值</td><td>"值" 或 单元格引用</td><td>"Google" 或 B2</td></tr><tr><td>大于某值</td><td>">数值"</td><td>">100"</td></tr><tr><td>小于某值</td><td>"&#x3C;数值"</td><td>"&#x3C;50"</td></tr><tr><td>大于等于</td><td>">=数值"</td><td>">=100"</td></tr><tr><td>包含某文本</td><td>"*文本*"</td><td>"*品牌*"</td></tr><tr><td>日期条件</td><td>">=日期"</td><td>">=2025/10/1"</td></tr></tbody></table>

### 三、COUNTIFS——按条件计数

COUNTIFS和SUMIFS几乎一样，只是它不求和，而是数数。

COUNTIFS的语法

\=COUNTIFS(条件区域1, 条件1, 条件区域2, 条件2, ...)

注意：COUNTIFS没有“求和区域”，因为它只数行数。

广告案例

Google渠道有多少条记录？

\=COUNTIFS(B:B, "Google")

ROAS大于3的广告活动有多少个？

\=COUNTIFS(M:M, ">3")

Google渠道中，ROAS大于3的有多少个？

\=COUNTIFS(B:B, "Google", M:M, ">3")

### 四、AVERAGEIFS——按条件求平均

AVERAGEIFS的任务：对符合条件的所有行，计算某一列的平均值。

AVERAGEIFS的语法

\=AVERAGEIFS(平均区域, 条件区域1, 条件1, 条件区域2, 条件2, ...)

广告案例

Google渠道中，ROAS大于3的广告活动的平均销售额：

\=AVERAGEIFS(I:I, B:B, "Google", M:M, ">3")

### 五、SUBTOTAL——筛选状态下只算“看到的”

SUM vs SUBTOTAL的区别

SUM计算的是所有行——不管你有没有筛选，它都算全部。

SUBTOTAL只计算当前可见的行——你筛选后看到多少，它就只算多少。

SUBTOTAL的语法

\=SUBTOTAL(功能编号, 区域)

<table data-header-hidden><thead><tr><th width="106.22222900390625"></th><th width="258.44439697265625"></th></tr></thead><tbody><tr><td>功能编号</td><td>含义</td></tr><tr><td>9</td><td>求和（SUBTOTAL中的“SUM”）</td></tr><tr><td>1</td><td>平均值</td></tr><tr><td>2</td><td>计数</td></tr><tr><td>3</td><td>非空计数</td></tr></tbody></table>

广告场景：你筛选出“花费>100”的活动后，想只看筛选后这些活动的总花费：

\=SUBTOTAL(9, E:E)

当你筛选不同渠道时，这个公式自动跟随变化——只算你当前看到的行。

### 六、综合实战——3秒汇总你的广告数据

场景

打开「广告日报」，你要回答老板的3个问题：

1\.        “Facebook上个月（2025年10月）花了多少钱？”

2\.        “ROAS大于3的广告活动有多少个？”

3\.        “高效活动（ROAS>3）的平均ROAS是多少？”

操作步骤

第1步：统计Facebook在2025年10月的总花费

\=SUMIFS(E:E, B:B, "Facebook", A:A, ">=2025/10/1", A:A, "<=2025/10/31")

第2步：统计ROAS>3的记录数

假设ROAS在M列：

\=COUNTIFS(M:M, ">3")

第3步：计算ROAS>3的平均ROAS

\=AVERAGEIFS(M:M, M:M, ">3")

完成后的效果

<table data-header-hidden><thead><tr><th width="186.77777099609375"></th><th width="343.333251953125"></th><th width="140.11126708984375"></th></tr></thead><tbody><tr><td>问题</td><td>公式</td><td>结果（示例值）</td></tr><tr><td>Facebook 10月总花费</td><td>=SUMIFS(E:E, B:B, "Facebook", A:A, ">=2025/10/1", A:A, "&#x3C;=2025/10/31")</td><td>约8,500</td></tr><tr><td>ROAS>3的记录数</td><td>=COUNTIFS(M:M, ">3")</td><td>约120</td></tr><tr><td>ROAS>3的平均ROAS</td><td>=AVERAGEIFS(M:M, M:M, ">3")</td><td>约4.2</td></tr></tbody></table>

💡 在单元格里试试就知道了。 把SUMIFS的条件从"Google"改成"_G_"，观察结果变化——通配符的威力一试便知。

### 七、这一章你带走了什么？

<table data-header-hidden><thead><tr><th width="206.22222900390625"></th><th width="205.11114501953125"></th></tr></thead><tbody><tr><td>你之前可能觉得</td><td>你现在知道了</td></tr><tr><td>筛选复制粘贴求和好麻烦</td><td>一行SUMIFS，3秒钟</td></tr><tr><td>统计要手工数数</td><td>COUNTIFS帮你数</td></tr><tr><td>平均要手动算</td><td>AVERAGEIFS自动算</td></tr><tr><td>筛选后汇总总不对</td><td>SUBTOTAL只算看到的</td></tr></tbody></table>

核心公式对比：

<table data-header-hidden><thead><tr><th width="126.77777099609375"></th><th width="334.4444580078125"></th><th width="124.55560302734375"></th></tr></thead><tbody><tr><td>函数</td><td>公式结构</td><td>作用</td></tr><tr><td>SUMIFS</td><td>=SUMIFS(求和列, 条件列1, 条件1, ...)</td><td>按条件求和</td></tr><tr><td>COUNTIFS</td><td>=COUNTIFS(条件列1, 条件1, ...)</td><td>按条件计数</td></tr><tr><td>AVERAGEIFS</td><td>=AVERAGEIFS(平均列, 条件列1, 条件1, ...)</td><td>按条件求平均</td></tr></tbody></table>

💡 在单元格里试试就知道了。 打开「广告日报」，亲手敲一遍这三个公式。看到数字瞬间出现的那一刻，你就再也不想手动筛选求和了。

### 八、本章实操任务

任务1：渠道汇总

用SUMIFS分别统计Google、Facebook、Amazon三个渠道的总花费和总订单。

任务2：ROAS分析

先计算ROAS（销售额÷花费），然后用COUNTIFS统计ROAS>2、>3、>4的记录各有多少条。

任务3：月度汇总

用SUMIFS统计2025年10月、11月、12月的总花费各是多少。

任务4：SUBTOTAL体验

在「广告日报」中插入SUBTOTAL公式，然后分别筛选不同渠道，观察结果变化。

### 九、本章思考题

1\.        SUMIFS和SUM有什么区别？什么场景必须用SUMIFS而不是SUM？

2\.        如果你的SUMIFS返回了0，但你确认数据中确实存在符合条件的行，可能是什么原因？

3\.        SUBTOTAL和SUM的区别是什么？你会在什么场景下用SUBTOTAL？

### 十、本章学习记录

<table data-header-hidden><thead><tr><th width="350.99993896484375"></th><th width="115.111083984375"></th></tr></thead><tbody><tr><td>项目</td><td>完成情况</td></tr><tr><td>用SUMIFS统计了Google总花费</td><td>✅ / ⬜</td></tr><tr><td>用COUNTIFS统计了ROAS>3的记录数</td><td>✅ / ⬜</td></tr><tr><td>用AVERAGEIFS计算了高效活动的平均ROAS</td><td>✅ / ⬜</td></tr><tr><td>用SUBTOTAL体验了筛选后汇总</td><td>✅ / ⬜</td></tr><tr><td>完成综合实战</td><td>✅ / ⬜</td></tr><tr><td>完成实操任务</td><td>✅ / ⬜</td></tr></tbody></table>

&#x20;

下一章预告：第0-5章《让Excel自己“判卷”》。

写一行=IFS(M2>3, "高效", M2>2, "正常", TRUE, "待优化")，向下拖动——600个标签，一次成型。你亲眼看到Excel在替你做判断，而不是等你一个一个手动分类。

💡 打开EXCEL，在单元格里试试就知道了
