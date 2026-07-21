# 案例一：Facebook广告创意归因与素材优化

#### 一、业务场景

你负责Facebook广告投放，发现同一个广告组下多个创意的表现差异很大。问题是：不同创意（图片、标题、正文）如何影响转化？应该把预算集中到哪些创意上？

你有以下数据：

· Facebook广告后台导出的创意级别数据（展示、点击、花费、转化）

· 每个创意对应的图片ID、标题文案、正文文案

· 不同广告组的预算分配

#### 二、数据准备

假设你有以下字段：

<table data-header-hidden><thead><tr><th width="114.5555419921875"></th><th width="89.333251953125"></th><th width="175.222412109375"></th></tr></thead><tbody><tr><td>字段</td><td>类型</td><td>说明</td></tr><tr><td>日期</td><td>日期</td><td>投放日期</td></tr><tr><td>广告组</td><td>文本</td><td>如“再营销-美国”</td></tr><tr><td>图片ID</td><td>文本</td><td>创意图片标识</td></tr><tr><td>标题</td><td>文本</td><td>广告标题文案</td></tr><tr><td>正文</td><td>文本</td><td>广告正文文案</td></tr><tr><td>展示</td><td>数字</td><td>展示次数</td></tr><tr><td>点击</td><td>数字</td><td>点击次数</td></tr><tr><td>花费</td><td>数字</td><td>广告花费</td></tr><tr><td>转化</td><td>数字</td><td>转化次数</td></tr><tr><td>转化价值</td><td>数字</td><td>转化总价值</td></tr></tbody></table>

#### 三、分析目标

1\.        计算每个创意的CTR、CPC、CPA、ROAS

2\.        找出CTR最高的图片+标题组合

3\.        找出ROAS最高的创意组合

4\.        为每个广告组推荐Top 3创意组合

#### 四、解决方案（用Power Query + 透视表）

Step 1：用Power Query清洗创意数据

将导出的创意报表导入Power Query，清洗以下问题：

· 删除空行

· 统一日期格式

· 确认数字列类型

Step 2：在Power Pivot中建立数据模型

数据模型：

· 事实表：创意数据（含图片ID、标题、正文）

· 维度表：广告组信息（可选）

Step 3：创建DAX度量值

CTR := DIVIDE(\[总点击], \[总展示], 0)

CPC := DIVIDE(\[总花费], \[总点击], 0)

CPA := DIVIDE(\[总花费], \[总转化], 0)

ROAS := DIVIDE(\[总转化价值], \[总花费], 0)

Step 4：创建分析透视表

<table data-header-hidden><thead><tr><th width="135.66668701171875"></th><th width="186"></th><th width="140.77777099609375"></th></tr></thead><tbody><tr><td>行区域</td><td>值区域</td><td>排序</td></tr><tr><td>图片ID、标题</td><td>CTR、CPC、ROAS</td><td>按ROAS降序</td></tr></tbody></table>

Step 5：添加切片器

· 广告组切片器 → 可查看不同广告组的表现

· 日期日程表 → 可查看不同时间段的趋势

#### 五、业务输出

<table data-header-hidden><thead><tr><th width="120.111083984375"></th><th width="170.77777099609375"></th><th width="286.00006103515625"></th></tr></thead><tbody><tr><td>广告组</td><td>推荐创意（Top 3）</td><td>理由</td></tr><tr><td>再营销-美国</td><td>图片A + 标题1</td><td>ROAS=4.2，CPA最低</td></tr><tr><td>拉新-美国</td><td>图片C + 标题3</td><td>CTR最高（2.8%），获客成本低</td></tr><tr><td>品牌曝光</td><td>图片B + 标题2</td><td>综合表现稳定，覆盖面广</td></tr></tbody></table>

#### 六、深化应用

· AI辅助优化：将创意表现数据输入AI，让AI生成优化建议

· A/B测试跟踪：用条件格式高亮显示测试组和对照组的差异

· 自动周报：用VBA自动生成创意表现周报并发送给团队

<br>

&#x20;
