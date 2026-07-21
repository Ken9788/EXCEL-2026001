# 附录F：统一工作簿使用说明与数据字典

#### F-1 工作簿概述

文件名称：广告分析学习工作簿.xlsx

适用场景：全书所有章节的实操任务

核心特点：

· 所有章节共用一套数据，保持一致性

· 核心数据表受保护（如需修改可解除保护，密码默认为空）

· 练习区供学员自由操作

日期范围：2025年10月1日 — 2026年4月30日（共212天）

#### F-2 工作表列表

<table data-header-hidden><thead><tr><th width="139.22222900390625"></th><th width="340.888916015625"></th><th width="89.888916015625"></th><th width="91.33331298828125"></th></tr></thead><tbody><tr><td>工作表名称</td><td>说明</td><td>数据量</td><td>保护状态</td></tr><tr><td>「广告日报」</td><td>主数据表，每日广告投放明细</td><td>约600行</td><td>建议只读</td></tr><tr><td>「产品映射表」</td><td>广告活动ID → 产品线、负责人、目标ACOS</td><td>30行</td><td>建议只读</td></tr><tr><td>「日历表」</td><td>日期维度，含年/月/季度/周/是否周末</td><td>212行</td><td>建议只读</td></tr><tr><td>「渠道表」</td><td>渠道代码 → 渠道全称、渠道类型</td><td>3行</td><td>建议只读</td></tr><tr><td>「参考答案」</td><td>各章练习参考答案（默认隐藏）</td><td>动态</td><td>讲师用</td></tr><tr><td>「练习区」</td><td>空白工作表，供学员自由练习</td><td>空白</td><td>无保护</td></tr></tbody></table>

#### F-3 数据字典：广告日报

<table data-header-hidden><thead><tr><th width="124.77777099609375"></th><th width="82.5555419921875"></th><th width="305.5555419921875"></th><th width="189.55560302734375"></th></tr></thead><tbody><tr><td>字段名</td><td>类型</td><td>说明</td><td>示例</td></tr><tr><td>日期</td><td>日期</td><td>投放日期（2025/10/1 — 2026/4/30）</td><td>2025/10/1</td></tr><tr><td>渠道</td><td>文本</td><td>投放渠道</td><td>Google / Facebook / Amazon</td></tr><tr><td>广告活动ID</td><td>文本</td><td>唯一标识</td><td>G-001</td></tr><tr><td>广告活动名称</td><td>文本</td><td>关键词类型-投放地区</td><td>品牌词-美国</td></tr><tr><td>花费</td><td>数字</td><td>广告花费（元）</td><td>125.50</td></tr><tr><td>点击</td><td>整数</td><td>点击次数</td><td>250</td></tr><tr><td>展示</td><td>整数</td><td>展示次数</td><td>5000</td></tr><tr><td>订单</td><td>整数</td><td>转化订单数</td><td>8</td></tr><tr><td>销售额</td><td>数字</td><td>转化销售额（元）</td><td>400.00</td></tr></tbody></table>

数据生成逻辑：

· 日期：2025年10月1日至2026年4月30日，每天3个渠道各1-2条记录

· 广告活动ID：G-001\~G-010（Google），F-001\~F-010（Facebook），A-001\~A-010（Amazon）

· 花费：50-500之间的随机数

· 点击率：1.5%-5.0%

· 转化率：2%-8%

· 客单价：40-100元

#### F-4 数据字典：产品映射表

<table data-header-hidden><thead><tr><th width="130.33331298828125"></th><th width="85"></th><th width="164.888916015625"></th><th width="124.44439697265625"></th></tr></thead><tbody><tr><td>字段名</td><td>类型</td><td>说明</td><td>示例</td></tr><tr><td>广告活动ID</td><td>文本</td><td>与广告日报关联</td><td>G-001</td></tr><tr><td>广告活动名称</td><td>文本</td><td>与广告日报一致</td><td>品牌词-美国</td></tr><tr><td>产品线</td><td>文本</td><td>产品所属类别</td><td>电子产品</td></tr><tr><td>负责人</td><td>文本</td><td>广告投放负责人</td><td>张三</td></tr><tr><td>目标ACOS</td><td>百分比</td><td>目标广告销售成本</td><td>25%</td></tr></tbody></table>

数据映射关系：

· Google系列（G-001\~G-010）：电子产品，负责人张三

· Facebook系列（F-001\~F-010）：家居用品，负责人李四

· Amazon系列（A-001\~A-010）：服装，负责人王五

#### F-5 数据字典：日历表

<table data-header-hidden><thead><tr><th width="104.77777099609375"></th><th width="78.4444580078125"></th><th width="274.2222900390625"></th><th width="102.77777099609375"></th></tr></thead><tbody><tr><td>字段名</td><td>类型</td><td>说明</td><td>示例</td></tr><tr><td>日期</td><td>日期</td><td>日期（2025/10/1 — 2026/4/30）</td><td>2025/10/1</td></tr><tr><td>年</td><td>整数</td><td>年份</td><td>2025</td></tr><tr><td>月</td><td>整数</td><td>月份（1-12）</td><td>10</td></tr><tr><td>月名称</td><td>文本</td><td>中文月份名称</td><td>十月</td></tr><tr><td>季度</td><td>整数</td><td>季度（1-4）</td><td>4</td></tr><tr><td>周</td><td>整数</td><td>年内第几周</td><td>40</td></tr><tr><td>是否周末</td><td>文本</td><td>是/否</td><td>否</td></tr></tbody></table>

#### F-6 数据字典：渠道表

<table data-header-hidden><thead><tr><th width="107"></th><th width="89.6666259765625"></th><th width="99.4444580078125"></th><th width="133.0001220703125"></th></tr></thead><tbody><tr><td>字段名</td><td>类型</td><td>说明</td><td>示例</td></tr><tr><td>渠道代码</td><td>文本</td><td>简称</td><td>Google</td></tr><tr><td>渠道全称</td><td>文本</td><td>全称</td><td>Google Ads</td></tr><tr><td>渠道类型</td><td>文本</td><td>投放类型</td><td>搜索广告</td></tr><tr><td>所属公司</td><td>文本</td><td>平台公司</td><td>Google</td></tr></tbody></table>

#### F-7 各章节使用数据表对照

<table data-header-hidden><thead><tr><th width="109"></th><th width="275.66668701171875"></th><th width="267.77777099609375"></th></tr></thead><tbody><tr><td>章节</td><td>使用数据表</td><td>操作说明</td></tr><tr><td>第0-1章</td><td>无</td><td>理论导入</td></tr><tr><td>第0-2章</td><td>任意空白表</td><td>手动输入数据练习引用</td></tr><tr><td>第0-3章</td><td>「广告日报」+「产品映射表」</td><td>匹配产品线、负责人、目标ACOS</td></tr><tr><td>第0-4章</td><td>「广告日报」</td><td>统计汇总各渠道数据</td></tr><tr><td>第0-5章</td><td>「广告日报」+「产品映射表」</td><td>判断ACOS、打ROAS标签</td></tr><tr><td>第0-6章</td><td>「广告日报」</td><td>拆分广告活动名称</td></tr><tr><td>第0-7章</td><td>「广告日报」</td><td>提取月份和星期</td></tr><tr><td>第0-8章</td><td>「广告日报」+「产品映射表」</td><td>综合实战</td></tr><tr><td>第1-2章</td><td>「广告日报」</td><td>快捷键和数据规范练习</td></tr><tr><td>第1-3章</td><td>「广告日报」+「产品映射表」</td><td>AI辅助公式练习</td></tr><tr><td>第2-1章</td><td>「广告日报」</td><td>透视表创建</td></tr><tr><td>第2-2章</td><td>「广告日报」</td><td>透视表进阶操作</td></tr><tr><td>第2-3章</td><td>「广告日报」</td><td>切片器、日程表、仪表盘</td></tr><tr><td>第2-4章</td><td>「广告日报」→复制到「练习区」</td><td>Power Query清洗</td></tr><tr><td>第2-5章</td><td>「广告日报」</td><td>Power Query多表合并</td></tr><tr><td>第3-1章</td><td>灵活</td><td>AI生成VBA</td></tr><tr><td>第3-2章</td><td>「广告日报」</td><td>Python in Excel</td></tr><tr><td>第3-3章</td><td>全部四张核心表</td><td>Power Pivot建模</td></tr><tr><td>第3-4章</td><td>「广告日报」+「产品映射表」+「日历表」</td><td>DAX进阶、KPI</td></tr><tr><td>第4-1章</td><td>全部四张核心表</td><td>完整系统搭建</td></tr><tr><td>第4-2章</td><td>全部</td><td>工作流整合</td></tr></tbody></table>

#### F-8 工作簿使用建议

对学员

1\.        学习期间：始终在「练习区」中操作，不要修改核心数据表

2\.        若误操作：可从讲师处重新获取工作簿副本，或从「参考答案」表中还原

3\.        数据更新：「广告日报」中的数据可根据需要追加新行（需取消工作表保护）

4\.        版本保存：建议每位学员保存自己的版本，命名格式为“学员姓名\_广告分析学习工作簿.xlsx”

对讲师

1\.        发放方式：开课前将工作簿分发给学员，建议使用云盘共享链接

2\.        参考答案：将「参考答案」工作表设为隐藏（开始 → 格式 → 隐藏工作表）

3\.        数据保护：如需保护核心数据表，可使用工作表保护功能（密码可设为统一值）

4\.        模拟数据：如需要更多数据，可自行使用RAND函数生成扩充行
