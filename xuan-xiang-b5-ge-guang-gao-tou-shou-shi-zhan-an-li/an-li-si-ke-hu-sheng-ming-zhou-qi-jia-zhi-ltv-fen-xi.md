# 案例四：客户生命周期价值（LTV）分析

#### 一、业务场景

你发现不同渠道获取的客户，长期价值不同。Facebook获取的客户虽然首单ROAS很高，但复购率低；Google获取的客户首单ROAS中等，但复购率高。

你需要计算不同渠道的LTV，优化“首单ROAS vs 长期LTV”的权衡。

#### 二、数据准备

假设你有客户级别的订单数据：

<table data-header-hidden><thead><tr><th width="103.4444580078125"></th><th width="83.111083984375"></th><th width="187"></th></tr></thead><tbody><tr><td>字段</td><td>类型</td><td>说明</td></tr><tr><td>客户ID</td><td>文本</td><td>唯一标识</td></tr><tr><td>订单日期</td><td>日期</td><td>下单日期</td></tr><tr><td>订单金额</td><td>数字</td><td>订单金额</td></tr><tr><td>获取渠道</td><td>文本</td><td>客户首次来源渠道</td></tr><tr><td>订单序号</td><td>整数</td><td>该客户的第几次订单</td></tr></tbody></table>

#### 三、分析目标

1\.        按渠道计算平均首单金额、平均复购金额、平均复购次数

2\.        估算各渠道的90天LTV

3\.        计算LTV/CAC比率，评估渠道健康度

#### 四、DAX度量值

平均首单金额 :=

AVERAGEX(

&#x20;   VALUES('订单表'\[客户ID]),

&#x20;   CALCULATE(SUM('订单表'\[订单金额]), '订单表'\[订单序号] = 1)

)

&#x20;

平均复购次数 :=

AVERAGEX(

&#x20;   VALUES('订单表'\[客户ID]),

&#x20;   CALCULATE(COUNTROWS('订单表'), '订单表'\[订单序号] > 1)

)

&#x20;

客户数 := DISTINCTCOUNT('订单表'\[客户ID])

新客户数 := CALCULATE(\[客户数], '订单表'\[订单序号] = 1)

&#x20;

CAC := DIVIDE(\[总花费], \[新客户数], 0)

LTV\_90天 := \[平均首单金额] + \[平均复购次数] \* \[平均复购金额]

LTV\_CAC比率 := DIVIDE(\[LTV\_90天], \[CAC], 0)

#### 五、业务输出

<table data-header-hidden><thead><tr><th width="105.77777099609375"></th><th width="79.11114501953125"></th><th width="94.4444580078125"></th><th width="93.77783203125"></th><th width="105.888916015625"></th><th width="100.1109619140625"></th></tr></thead><tbody><tr><td>渠道</td><td>CAC</td><td>首单金额</td><td>复购次数</td><td>LTV(90天)</td><td>LTV/CAC</td></tr><tr><td>Google</td><td>150</td><td>200</td><td>1.2</td><td>350</td><td>2.3</td></tr><tr><td>Facebook</td><td>100</td><td>180</td><td>0.5</td><td>240</td><td>2.4</td></tr><tr><td>Amazon</td><td>200</td><td>250</td><td>0.8</td><td>380</td><td>1.9</td></tr></tbody></table>

结论：虽然Amazon的CAC最高，但LTV也最高；Facebook的LTV/CAC最优。建议在Facebook和Google之间平衡预算，同时优化Amazon的获客效率。

#### 六、深化应用

· LTV趋势图：按月展示各渠道LTV变化趋势

· 客户分层：按LTV将客户分为高/中/低价值群，定向投放

· 渠道归因：分析不同渠道获取的客户在不同时间段的复购行为差异
