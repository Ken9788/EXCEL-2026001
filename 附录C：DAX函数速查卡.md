# 附录C：DAX函数速查卡

以下为Power Pivot中常用的DAX函数，按类别整理。

#### C-1 基础聚合函数

<table data-header-hidden><thead><tr><th width="161.4444580078125"></th><th width="227.22222900390625"></th><th width="97.888916015625"></th><th></th></tr></thead><tbody><tr><td>函数</td><td>语法</td><td>用途</td><td>示例</td></tr><tr><td>SUM</td><td>SUM('表'[列])</td><td>求和</td><td>SUM('广告日报'[花费])</td></tr><tr><td>AVERAGE</td><td>AVERAGE('表'[列])</td><td>平均值</td><td>AVERAGE('广告日报'[点击])</td></tr><tr><td>COUNTROWS</td><td>COUNTROWS('表')</td><td>行数计数</td><td>COUNTROWS('广告日报')</td></tr><tr><td>DISTINCTCOUNT</td><td>DISTINCTCOUNT('表'[列])</td><td>去重计数</td><td>DISTINCTCOUNT('广告日报'[广告活动ID])</td></tr><tr><td>DIVIDE</td><td>DIVIDE(分子, 分母, 0)</td><td>安全除法</td><td>DIVIDE([总销售额], [总花费], 0)</td></tr></tbody></table>

#### C-2 筛选上下文函数

<table data-header-hidden><thead><tr><th width="119.22216796875"></th><th width="176.77783203125"></th><th width="152.666748046875"></th><th></th></tr></thead><tbody><tr><td>函数</td><td>语法</td><td>用途</td><td>示例</td></tr><tr><td>CALCULATE</td><td>CALCULATE(表达式, 条件1, 条件2, ...)</td><td>修改筛选上下文</td><td>CALCULATE([总花费], '广告日报'[渠道]="Google")</td></tr><tr><td>ALL</td><td>ALL('表'[列])</td><td>忽略指定列上的筛选</td><td>CALCULATE([总花费], ALL('广告日报'[渠道]))</td></tr><tr><td>ALLEXCEPT</td><td>ALLEXCEPT('表', '表'[列])</td><td>忽略除指定列外的筛选</td><td>CALCULATE([总花费], ALLEXCEPT('广告日报', '广告日报'[渠道]))</td></tr><tr><td>FILTER</td><td>FILTER('表', 条件)</td><td>返回满足条件的行</td><td>CALCULATE([总花费], FILTER('广告日报', [ROAS]>3))</td></tr></tbody></table>

#### C-3 时间智能函数

<table data-header-hidden><thead><tr><th width="135.888916015625"></th><th width="186.33331298828125"></th><th width="91.77783203125"></th><th></th></tr></thead><tbody><tr><td>函数</td><td>语法</td><td>用途</td><td>示例</td></tr><tr><td>TOTALYTD</td><td>TOTALYTD(表达式, '日历表'[日期])</td><td>年初至今累计</td><td>TOTALYTD([总销售额], '日历表'[日期])</td></tr><tr><td>TOTALMTD</td><td>TOTALMTD(表达式, '日历表'[日期])</td><td>月初至今累计</td><td>TOTALMTD([总花费], '日历表'[日期])</td></tr><tr><td>TOTALQTD</td><td>TOTALQTD(表达式, '日历表'[日期])</td><td>季初至今累计</td><td>TOTALQTD([总订单], '日历表'[日期])</td></tr><tr><td>SAMEPERIODLASTYEAR</td><td>SAMEPERIODLASTYEAR('日历表'[日期])</td><td>去年同期</td><td>CALCULATE([总销售额], SAMEPERIODLASTYEAR('日历表'[日期]))</td></tr><tr><td>DATEADD</td><td>DATEADD('日历表'[日期], -1, MONTH)</td><td>日期偏移</td><td>CALCULATE([总花费], DATEADD('日历表'[日期], -1, MONTH))</td></tr></tbody></table>

#### C-4 DAX语法速记

<table data-header-hidden><thead><tr><th width="126.77777099609375"></th><th width="222.22216796875"></th><th width="152.33343505859375"></th></tr></thead><tbody><tr><td>规则</td><td>说明</td><td>示例</td></tr><tr><td>表名用单引号</td><td>引用表时用单引号括起来</td><td>'广告日报'</td></tr><tr><td>列名用方括号</td><td>引用列时用方括号</td><td>[花费]</td></tr><tr><td>字段引用</td><td>完整格式：'表名'[列名]</td><td>'广告日报'[花费]</td></tr><tr><td>度量值引用</td><td>只写度量值名称，不加表名</td><td>[总花费]</td></tr><tr><td>注释</td><td>双斜杠表示注释</td><td>// 这是注释</td></tr></tbody></table>

&#x20;

#### 常用DAX度量值模板

dax

_// 基础聚合_

总花费 := SUM('广告日报'\[花费])

总点击 := SUM('广告日报'\[点击])

总订单 := SUM('广告日报'\[订单])

总销售额 := SUM('广告日报'\[销售额])

&#x20;

_// 计算指标_

ROAS := DIVIDE(\[总销售额], \[总花费], 0)

ACOS := DIVIDE(\[总花费], \[总销售额], 0)

平均点击成本 := DIVIDE(\[总花费], \[总点击], 0)

&#x20;

_// 带筛选的度量值_

Google花费 := CALCULATE(\[总花费], '广告日报'\[渠道] = "Google")

高效活动花费 := CALCULATE(\[总花费], '广告日报'\[ROAS标签] = "高效")

&#x20;

_// 时间智能_

花费YTD := TOTALYTD(\[总花费], '日历表'\[日期])

花费同比 :=

VAR CurrentSales = \[总销售额]

VAR LastYearSales = CALCULATE(\[总销售额], SAMEPERIODLASTYEAR('日历表'\[日期]))

RETURN DIVIDE(CurrentSales - LastYearSales, LastYearSales, 0)
