# 案例三：多平台广告整合分析与预算优化

#### 一、业务场景

你同时负责Google、Facebook、Amazon三个平台的广告投放。每个平台的后台数据格式不同，难以统一分析。

你需要回答三个问题：

1\.        哪个平台的整体ROAS最高？

2\.        哪个平台的获客成本最低？

3\.        如何在平台间优化预算分配？

#### 二、数据准备

三个平台的报表结构不同，需要统一：

<table data-header-hidden><thead><tr><th width="114.5555419921875"></th><th width="156.88885498046875"></th><th width="166.888916015625"></th><th></th><th></th></tr></thead><tbody><tr><td>字段</td><td>Google（列名）</td><td>Facebook（列名）</td><td>Amazon（列名）</td><td>统一后的列名</td></tr><tr><td>日期</td><td>Date</td><td>日期</td><td>日期</td><td>日期</td></tr><tr><td>渠道</td><td>-</td><td>-</td><td>-</td><td>渠道</td></tr><tr><td>广告活动ID</td><td>CampaignID</td><td>广告系列ID</td><td>CampaignId</td><td>广告活动ID</td></tr><tr><td>广告活动</td><td>Campaign</td><td>广告系列名称</td><td>CampaignName</td><td>广告活动</td></tr><tr><td>花费</td><td>Cost</td><td>花费</td><td>Spend</td><td>花费</td></tr><tr><td>点击</td><td>Clicks</td><td>点击</td><td>Clicks</td><td>点击</td></tr><tr><td>转化</td><td>Conversions</td><td>转化</td><td>Purchases</td><td>转化</td></tr><tr><td>转化价值</td><td>ConversionValue</td><td>转化价值</td><td>Sales</td><td>转化价值</td></tr></tbody></table>

#### 三、分析目标

1\.        清洗三个平台的报表，统一字段和格式

2\.        合并成一张总表

3\.        按渠道汇总核心指标（ROAS、CPA、CTR）

4\.        制定平台间的预算分配建议

#### 四、解决方案（用Power Query + Power Pivot + 仪表盘）

Step 1：用Power Query分别清洗三个平台的数据

· 删除无用列

· 重命名为统一列名

· 添加“渠道”列（标识数据来源）

· 修正数据类型

Step 2：用追加查询合并三个平台的查询

· 新建空白查询 → 追加查询

· 将三个清洗后的查询添加到列表中

· 确定 → 关闭并上载

Step 3：在Power Pivot中建立数据模型

· 导入合并后的总表

· 创建以下度量值：

总花费 := SUM('合并总表'\[花费])

总转化 := SUM('合并总表'\[转化])

总转化价值 := SUM('合并总表'\[转化价值])

ROAS\_整体 := DIVIDE(\[总转化价值], \[总花费], 0)

CPA\_整体 := DIVIDE(\[总花费], \[总转化], 0)

Step 4：创建渠道分析透视表

<table data-header-hidden><thead><tr><th width="100.6666259765625"></th><th width="357.3333740234375"></th></tr></thead><tbody><tr><td>行区域</td><td>值区域</td></tr><tr><td>渠道</td><td>总花费、总转化价值、总转化、ROAS、CPA</td></tr></tbody></table>

Step 5：搭建仪表盘

· 添加“渠道”切片器

· 添加“日期”日程表

· 创建渠道ROAS对比柱状图

· 创建渠道花费占比环形图

· 创建渠道CPA对比条形图

#### 五、业务输出

<table data-header-hidden><thead><tr><th width="102.44439697265625"></th><th width="86.77777099609375"></th><th width="94.5555419921875"></th><th width="80.66668701171875"></th><th width="77.6666259765625"></th><th width="140.33343505859375"></th></tr></thead><tbody><tr><td>渠道</td><td>花费</td><td>转化价值</td><td>ROAS</td><td>CPA</td><td>建议</td></tr><tr><td>Google</td><td>50,000</td><td>150,000</td><td>3.0</td><td>150</td><td>维持预算</td></tr><tr><td>Facebook</td><td>30,000</td><td>120,000</td><td>4.0</td><td>100</td><td>增加预算20%</td></tr><tr><td>Amazon</td><td>20,000</td><td>50,000</td><td>2.5</td><td>200</td><td>减少预算30%</td></tr></tbody></table>

#### 六、深化应用

· 自动周报：每周一自动更新数据，生成跨平台周报

· 平台间归因：用DAX尝试简单归因分析（如首次点击归因）

· 预算优化公式：创建动态预算分配模板，根据ROAS变化自动调整
