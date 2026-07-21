# 案例二：Google Ads预算分配与效果预测

#### 一、业务场景

你负责Google Ads投放，每月预算有限。当前预算平均分配到所有广告组，但不同广告组的ROAS差异很大。

你需要回答两个问题：

1\.        按ROAS排序，预算应该如何重新分配？

2\.        如果调整预算，预计ROAS会如何变化？

#### 二、数据准备

假设你有以下数据：

<table data-header-hidden><thead><tr><th width="111.22222900390625"></th><th width="81.3333740234375"></th><th width="200.99993896484375"></th></tr></thead><tbody><tr><td>字段</td><td>类型</td><td>说明</td></tr><tr><td>广告组</td><td>文本</td><td>广告组名称</td></tr><tr><td>关键词类型</td><td>文本</td><td>品牌词/竞品词/长尾词</td></tr><tr><td>匹配类型</td><td>文本</td><td>精确/短语/广泛</td></tr><tr><td>花费</td><td>数字</td><td>历史花费</td></tr><tr><td>转化价值</td><td>数字</td><td>历史转化价值</td></tr><tr><td>点击</td><td>数字</td><td>历史点击</td></tr><tr><td>转化</td><td>数字</td><td>历史转化</td></tr></tbody></table>

#### 三、分析目标

1\.        计算每个广告组的ROAS、CPA、转化率

2\.        按ROAS排序识别高效和低效广告组

3\.        制定预算重新分配方案

4\.        预测调整后的效果

#### 四、解决方案（用透视表 + 数据模型 + 简单预测）

Step 1：用透视表汇总各广告组表现

<table data-header-hidden><thead><tr><th width="88.4444580078125"></th><th width="386.2222900390625"></th></tr></thead><tbody><tr><td>行区域</td><td>值区域</td></tr><tr><td>广告组</td><td>花费总和、转化价值总和、转化总和、点击总和</td></tr></tbody></table>

Step 2：创建计算字段

<table data-header-hidden><thead><tr><th width="99.55560302734375"></th><th width="161.7777099609375"></th></tr></thead><tbody><tr><td>计算字段</td><td>公式</td></tr><tr><td>ROAS</td><td>=转化价值/花费</td></tr><tr><td>CPA</td><td>=花费/转化</td></tr><tr><td>转化率</td><td>=转化/点击</td></tr></tbody></table>

Step 3：按ROAS排序，分为三类

<table data-header-hidden><thead><tr><th width="184.5555419921875"></th><th width="109.888916015625"></th><th width="186.888916015625"></th></tr></thead><tbody><tr><td>类别</td><td>ROAS范围</td><td>策略</td></tr><tr><td>高效（Top 20%）</td><td>>3.5</td><td>增加预算20%</td></tr><tr><td>正常（中间60%）</td><td>2.0-3.5</td><td>维持预算</td></tr><tr><td>低效（Bottom 20%）</td><td>&#x3C;2.0</td><td>减少预算30%或暂停</td></tr></tbody></table>

Step 4：预算调整模拟

用辅助列计算调整后的花费：

调整后花费 = 原花费 × (1 + 调整比例)

预测转化价值 = 调整后花费 × 原ROAS

Step 5：用AI生成预测分析

向AI提问：

我有以下数据：

广告组、原花费、原ROAS、调整比例、调整后花费

请帮我写一个公式，计算调整后的预测转化价值和整体ROAS变化。

#### 五、业务输出

<table data-header-hidden><thead><tr><th width="120.22222900390625"></th><th width="84.6666259765625"></th><th width="79.77777099609375"></th><th width="90.5555419921875"></th><th width="108.4444580078125"></th><th width="125.88897705078125"></th></tr></thead><tbody><tr><td>广告组</td><td>原ROAS</td><td>原花费</td><td>调整比例</td><td>调整后花费</td><td>预测转化价值</td></tr><tr><td>品牌词-精确</td><td>4.5</td><td>10,000</td><td>+20%</td><td>12,000</td><td>54,000</td></tr><tr><td>竞品词-短语</td><td>2.1</td><td>8,000</td><td>0%</td><td>8,000</td><td>16,800</td></tr><tr><td>长尾词-广泛</td><td>1.5</td><td>5,000</td><td>-30%</td><td>3,500</td><td>5,250</td></tr></tbody></table>

结论：预算重新分配后，预计整体ROAS从2.8提升到3.2。

#### 六、深化应用

· 预算可视化：用环形图显示调整前后的预算占比变化

· 敏感性分析：用数据表模拟不同调整比例对整体ROAS的影响

· 周期性复盘：每月对比预测值与实际值，调整模型参数
