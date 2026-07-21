# 案例五：广告活动自动调优触发器

#### 一、业务场景

你管理着200+个广告活动，每天需要决定哪些活动需要调整。你想建立一个自动触发器系统：当活动表现达到某个阈值时，自动标记需要执行的操作。

#### 二、触发规则

<table data-header-hidden><thead><tr><th width="89"></th><th width="282.3333740234375"></th><th width="162.22216796875"></th></tr></thead><tbody><tr><td>规则</td><td>条件</td><td>建议操作</td></tr><tr><td>规则1</td><td>ROAS > 3.5 且 花费 &#x3C; 预算的80%</td><td>增加预算10%</td></tr><tr><td>规则2</td><td>ROAS &#x3C; 2.0 且 花费 > 500</td><td>暂停或优化</td></tr><tr><td>规则3</td><td>ROAS &#x3C; 2.0 且 花费 ≤ 500</td><td>降低出价20%</td></tr><tr><td>规则4</td><td>转化率 > 5% 且 花费 > 1000</td><td>增加预算15%</td></tr><tr><td>规则5</td><td>CPA > 目标CPA 且 花费 > 200</td><td>检查关键词/素材</td></tr></tbody></table>

#### 三、解决方案

Step 1：在Power Pivot中创建触发条件度量值

规则1\_触发 := IF(AND(\[ROAS]>3.5, \[花费]<\[预算]\*0.8), "增加预算10%", "")

规则2\_触发 := IF(AND(\[ROAS]<2.0, \[花费]>500), "暂停或优化", "")

规则3\_触发 := IF(AND(\[ROAS]<2.0, \[花费]<=500), "降低出价20%", "")

规则4\_触发 := IF(AND(\[转化率]>0.05, \[花费]>1000), "增加预算15%", "")

规则5\_触发 := IF(AND(\[CPA]>\[目标CPA], \[花费]>200), "检查关键词/素材", "")

Step 2：创建触发汇总表

用透视表汇总每个广告活动的所有触发规则：

<table data-header-hidden><thead><tr><th width="118.77777099609375"></th><th width="81.3333740234375"></th><th width="80.22222900390625"></th><th width="86.888916015625"></th><th width="81.111083984375"></th><th width="76.888916015625"></th><th width="140.44439697265625"></th></tr></thead><tbody><tr><td>广告活动</td><td>规则1</td><td>规则2</td><td>规则3</td><td>规则4</td><td>规则5</td><td>建议操作</td></tr><tr><td>品牌词-美国</td><td>-</td><td>-</td><td>-</td><td>增加预算15%</td><td>-</td><td>增加预算15%</td></tr><tr><td>竞品词-美国</td><td>-</td><td>暂停或优化</td><td>-</td><td>-</td><td>-</td><td>暂停或优化</td></tr><tr><td>长尾词-欧洲</td><td>-</td><td>-</td><td>降低出价20%</td><td>-</td><td>检查关键词</td><td>降低出价20% + 检查关键词</td></tr></tbody></table>

Step 3：用条件格式高亮

· 红色高亮：需要立即优化（规则2触发）

· 黄色高亮：需要关注（规则5触发）

· 绿色高亮：可以增加预算（规则1或规则4触发）

#### 四、业务价值

· 从每天手动检查200+活动 → 系统自动标记需优化的活动

· 节省时间：约2小时/天 → 15分钟/天

· 减少遗漏：不会再有“漏看”的低效活动

#### 五、深化应用

· 与AI结合：将触发规则输出到AI，让AI生成具体优化文案

· 邮件提醒：用VBA设置自动邮件提醒，当触发规则时发送通知

· 历史追踪：记录每次触发和操作，分析优化效果

总结：各场景对应技能一览

<table data-header-hidden><thead><tr><th width="115.88885498046875"></th><th width="300"></th><th width="147.1112060546875"></th><th width="149.44439697265625"></th></tr></thead><tbody><tr><td>场景</td><td>主要技能</td><td>所需数据</td><td>核心输出</td></tr><tr><td>创意归因</td><td>Power Query + 透视表</td><td>创意级别数据</td><td>创意排名 + 推荐</td></tr><tr><td>预算分配</td><td>透视表 + 计算 + AI预测</td><td>广告组级别数据</td><td>预算调整方案</td></tr><tr><td>多平台整合</td><td>Power Query + Power Pivot + 仪表盘</td><td>多平台报表</td><td>跨平台仪表盘</td></tr><tr><td>LTV分析</td><td>Power Pivot + DAX</td><td>客户订单数据</td><td>LTV/CAC分析</td></tr><tr><td>自动调优</td><td>Power Pivot + 条件格式</td><td>广告活动数据</td><td>触发器系统</td></tr></tbody></table>

实施建议

<table data-header-hidden><thead><tr><th width="111.22222900390625"></th><th width="135.77783203125"></th><th width="207.66656494140625"></th></tr></thead><tbody><tr><td>场景</td><td>实施优先级</td><td>预计时间</td></tr><tr><td>多平台整合</td><td>⭐⭐⭐ 最高</td><td>2-3小时</td></tr><tr><td>自动调优</td><td>⭐⭐⭐ 最高</td><td>1-2小时</td></tr><tr><td>预算分配</td><td>⭐⭐ 高</td><td>1-2小时</td></tr><tr><td>创意归因</td><td>⭐⭐ 高</td><td>1-2小时</td></tr><tr><td>LTV分析</td><td>⭐ 中等</td><td>2-3小时（需额外数据）</td></tr></tbody></table>

***

选项B全部输出完毕。 以上5个案例覆盖了广告投手日常工作中最核心的分析场景，可根据自身业务需求选择实施，也可将多个案例组合成一个完整的广告分析系统。
