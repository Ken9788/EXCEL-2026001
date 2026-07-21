# 附录D：AI提问模板30例

以下为向AI提问生成Excel公式或代码的模板，按场景分类。

#### D-1 查找匹配类（5例）

<table data-header-hidden><thead><tr><th width="71.77777099609375"></th><th></th></tr></thead><tbody><tr><td>序号</td><td>模板</td></tr><tr><td>D-1.1</td><td>我有两张表：表A「广告日报」C列是广告活动ID，E列是花费；表B「产品映射表」A列是广告活动ID，C列是产品线。请帮我写一个XLOOKUP公式，在表A中根据广告活动ID匹配产品线，如果找不到显示"未分类"。请解释公式每个部分的含义。</td></tr><tr><td>D-1.2</td><td>我的数据中C列是广告活动ID，J列是目标ACOS。请帮我写一个VLOOKUP公式，从「产品映射表」中匹配目标ACOS，如果找不到显示"未设定"。</td></tr><tr><td>D-1.3</td><td>请帮我写一个INDEX+MATCH组合公式，根据「广告日报」的广告活动ID匹配「产品映射表」的负责人。请解释MATCH返回的是什么，INDEX接收这个返回值后又做了什么。</td></tr><tr><td>D-1.4</td><td>我有两张表需要根据广告活动ID和日期两个条件匹配花费。请帮我写一个XLOOKUP多条件查找公式。</td></tr><tr><td>D-1.5</td><td>我需要同时匹配产品线和负责人两列。请帮我写一个XLOOKUP返回多列的公式。</td></tr></tbody></table>

#### D-2 统计汇总类（5例）

<table data-header-hidden><thead><tr><th width="78.4444580078125"></th><th width="500.666748046875"></th></tr></thead><tbody><tr><td>序号</td><td>模板</td></tr><tr><td>D-2.1</td><td>我的数据中B列是渠道，E列是花费。请帮我写一个SUMIFS公式，统计Google渠道的总花费。</td></tr><tr><td>D-2.2</td><td>我的数据中M列是ROAS。请帮我写一个COUNTIFS公式，统计ROAS大于3的记录有多少条。</td></tr><tr><td>D-2.3</td><td>我的数据中I列是销售额，M列是ROAS。请帮我写一个AVERAGEIFS公式，计算ROAS大于3的广告的平均销售额。</td></tr><tr><td>D-2.4</td><td>我的数据中A列是日期，E列是花费。请帮我用SUMIFS统计2025年10月的总花费。</td></tr><tr><td>D-2.5</td><td>我想在筛选后只计算可见行的总花费。请帮我写一个SUBTOTAL公式，并解释9和109的区别。</td></tr></tbody></table>

#### D-3 逻辑判断类（5例）

<table data-header-hidden><thead><tr><th width="80.66668701171875"></th><th width="630.6666870117188"></th></tr></thead><tbody><tr><td>序号</td><td>模板</td></tr><tr><td>D-3.1</td><td>我的数据中K列是ACOS，J列是目标ACOS。请帮我写一个IF公式，判断ACOS是否达标，达标显示"达标"，超标显示"超标"。</td></tr><tr><td>D-3.2</td><td>我的数据中M列是ROAS。请帮我写一个IFS公式：ROAS>3显示"高效"，ROAS>2显示"正常"，否则显示"待优化"。</td></tr><tr><td>D-3.3</td><td>我的数据中E列是花费，M列是ROAS。请帮我写一个IFS公式：花费>200且ROAS>3显示"⭐明星"，ROAS>3显示"高效"，ROAS>2显示"正常"，否则显示"待优化"。</td></tr><tr><td>D-3.4</td><td>我的数据中I列是销售额，E列是花费。请帮我写一个IFERROR公式计算ROAS，如果花费为0则显示"无数据"。</td></tr><tr><td>D-3.5</td><td>请解释以下嵌套IF公式的执行顺序：=IF(M2>3,"高效",IF(M2>2,"正常","待优化"))</td></tr></tbody></table>

#### D-4 文本处理类（5例）

<table data-header-hidden><thead><tr><th width="78.44439697265625"></th><th width="551.7778930664062"></th></tr></thead><tbody><tr><td>序号</td><td>模板</td></tr><tr><td>D-4.1</td><td>我的数据中D列是"广告活动名称"，格式为"关键词类型-投放地区"。请帮我写LEFT和RIGHT公式，分别提取关键词类型和投放地区。</td></tr><tr><td>D-4.2</td><td>我的数据中D列是"广告活动名称"，格式为"关键词类型-投放地区"。请帮我写一个FIND公式，找到"-"的位置，再用LEFT和RIGHT提取文本。</td></tr><tr><td>D-4.3</td><td>我的数据中D列有首尾空格。请帮我写TRIM公式清洗文本，并用LEN验证清洗前后的长度变化。</td></tr><tr><td>D-4.4</td><td>我的数据中A列是日期，B列是渠道，C列是广告活动ID。请帮我用&#x26;拼接生成"日期-渠道-广告活动ID"格式的唯一标识。</td></tr><tr><td>D-4.5</td><td>我的数据中C列是广告活动ID（格式为"渠道-序号"）。请帮我用MID提取序号部分。</td></tr></tbody></table>

#### D-5 日期时间类（5例）

<table data-header-hidden><thead><tr><th width="70.6666259765625"></th><th width="685.1112060546875"></th></tr></thead><tbody><tr><td>序号</td><td>模板</td></tr><tr><td>D-5.1</td><td>我的数据中A列是日期。请帮我用MONTH和WEEKDAY分别提取月份和星期几。</td></tr><tr><td>D-5.2</td><td>我的数据中A列是日期。请帮我用WEEKDAY判断是工作日还是周末。</td></tr><tr><td>D-5.3</td><td>假设每个广告活动从2025年10月1日开始投放。请帮我用DATEDIF计算截至今天的投放天数。</td></tr><tr><td>D-5.4</td><td>请帮我用TODAY和TEXT生成一个动态报告标题："数据更新至 XXXX年XX月XX日"。</td></tr><tr><td>D-5.5</td><td>请帮我用SUMIFS和MONTH组合，统计10月份的总花费（不新增辅助列）。</td></tr></tbody></table>

#### D-6 VBA代码类（5例）

<table data-header-hidden><thead><tr><th width="81.77777099609375"></th><th width="539.5556030273438"></th></tr></thead><tbody><tr><td>序号</td><td>模板</td></tr><tr><td>D-6.1</td><td>请帮我写一段VBA代码，将"广告日报"工作表中A列到I列按"花费"列降序排序，并自动调整列宽。请逐行注释。</td></tr><tr><td>D-6.2</td><td>请帮我写一段VBA代码，将当前工作表复制一份，重命名为"周报_YYYY-MM-DD"，在新工作表中删除第2行及以下所有数据（保留表头）。</td></tr><tr><td>D-6.3</td><td>请帮我写一段VBA代码，刷新所有数据连接，保存工作簿，并在状态栏显示"更新完成！"3秒后恢复。</td></tr><tr><td>D-6.4</td><td>请帮我写一段VBA代码，将"仪表盘"工作表中A1到J20区域导出为图片，保存到桌面。</td></tr><tr><td>D-6.5</td><td>请帮我写一段VBA代码，打开Outlook，创建新邮件，附加当前工作簿，收件人为team@company.com，主题为"广告周报"。</td></tr></tbody></table>
