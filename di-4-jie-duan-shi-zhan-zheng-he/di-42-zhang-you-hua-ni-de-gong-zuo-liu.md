# 第4-2章：优化你的工作流

“找一个你现在工作中最耗时的报表，用学到的技能重新做一遍——原来3小时的工作，现在10分钟。这就是我们5天学习的最终目标。”

### 现在就动手

回想一下，你每周花在广告报表上的时间是多少？

· 导出数据：5分钟

· 清洗数据：10分钟

· 匹配产品信息：5分钟

· 计算指标：10分钟

· 制作图表：10分钟

· 发送邮件：5分钟

· 合计：45分钟/周

现在，打开你搭建的广告分析系统。

点击 Ctrl+Alt+F5 —— 3秒钟，所有数据更新完毕。

然后复制图表到邮件里 —— 2分钟。

本周报表处理：2分钟。

💡 在单元格里试试就知道了。

找一个你现在工作中最耗时的报表，用学到的技能重新做一遍——你会发现，原来45分钟的工作，现在只需要5分钟。

这一章，就是让你把学到的所有技能，真实落地到工作中。

### 一、工作流整合：三步完成

步骤1：诊断你的现状

把本周的工作流画出来，标注每个环节耗时：

【周一上午 9:00】

导出广告后台数据 .......... 5分钟

&#x20;    ↓

【9:05】

手工清洗数据 ............ 10分钟

&#x20;    ↓

【9:15】

用VLOOKUP匹配产品信息 ..... 5分钟

&#x20;    ↓

【9:20】

计算ROAS、打标签 ......... 10分钟

&#x20;    ↓

【9:30】

创建透视表、制作图表 ....... 10分钟

&#x20;    ↓

【9:40】

复制到PPT，发给老板 ....... 5分钟

&#x20;    ↓

【9:45】完成！

找出耗时最长的3个环节，问自己：能用什么技能缩短它？

<table data-header-hidden><thead><tr><th width="127.88885498046875"></th><th width="196.66668701171875"></th><th width="157.888916015625"></th></tr></thead><tbody><tr><td>耗时环节</td><td>可以用什么技能</td><td>能缩短到多少</td></tr><tr><td>清洗数据</td><td>Power Query</td><td>3秒（刷新）</td></tr><tr><td>匹配产品信息</td><td>XLOOKUP / 数据模型</td><td>3秒（刷新）</td></tr><tr><td>计算ROAS</td><td>IFERROR + 公式模板</td><td>0秒（自动）</td></tr><tr><td>打标签</td><td>IFS</td><td>0秒（自动）</td></tr><tr><td>制作图表</td><td>透视表 + 切片器</td><td>3秒（刷新）</td></tr></tbody></table>

步骤2：把“手工”变成“模板”

<table data-header-hidden><thead><tr><th width="190.66668701171875"></th><th width="237.33331298828125"></th></tr></thead><tbody><tr><td>当前做法</td><td>改进后</td></tr><tr><td>每周重新写VLOOKUP</td><td>公式已经存在，刷新即可</td></tr><tr><td>每周重新做透视表</td><td>透视表已经存在，刷新即可</td></tr><tr><td>每周重新画图表</td><td>图表已经存在，刷新即可</td></tr><tr><td>每周重新排版</td><td>模板已经存在，复制即可</td></tr></tbody></table>

你的目标是：把重复劳动从“每周做”变成“只做一次”。

步骤3：一键串联

把所有环节串联成一个“一键完成”的流程：

打开文件 → 粘贴新数据 → Ctrl+Alt+F5 → 复制图表 → 发送邮件

&#x20; 30秒         1分钟         3秒          1分钟        30秒

&#x20;

总计：约3分钟

### 二、常见问题排查手册

公式类问题

<table data-header-hidden><thead><tr><th width="105.66668701171875"></th><th width="198.77783203125"></th><th width="337.99981689453125"></th></tr></thead><tbody><tr><td>错误</td><td>可能原因</td><td>解决方案</td></tr><tr><td>#N/A</td><td>XLOOKUP/VLOOKUP找不到匹配值</td><td>检查是否有空格（用TRIM）、格式是否一致（文本vs数字）</td></tr><tr><td>#DIV/0!</td><td>除数为0</td><td>用IFERROR或DIVIDE函数</td></tr><tr><td>#VALUE!</td><td>数据类型错误</td><td>检查单元格格式，用VALUE转换</td></tr><tr><td>#REF!</td><td>引用无效</td><td>检查是否删除了被引用的列或行</td></tr><tr><td>结果为0</td><td>没有符合条件的数据</td><td>检查SUMIFS/COUNTIFS条件是否正确</td></tr></tbody></table>

透视表类问题

<table data-header-hidden><thead><tr><th width="142.33331298828125"></th><th width="178.6666259765625"></th><th></th></tr></thead><tbody><tr><td>问题</td><td>可能原因</td><td>解决方案</td></tr><tr><td>日期无法分组</td><td>日期列是文本格式</td><td>改为日期格式</td></tr><tr><td>切片器不联动</td><td>透视表数据源不同</td><td>确保基于同一数据模型</td></tr><tr><td>刷新后格式丢失</td><td>格式未设置为“保留”</td><td>右键→透视表选项→布局和格式→勾选“保留单元格格式”</td></tr><tr><td>计数而非求和</td><td>列中有空值或文本</td><td>确保数据列全是数字</td></tr></tbody></table>

Power Query问题

<table data-header-hidden><thead><tr><th width="157.888916015625"></th><th width="161.6666259765625"></th><th width="160.666748046875"></th></tr></thead><tbody><tr><td>问题</td><td>可能原因</td><td>解决方案</td></tr><tr><td>刷新失败</td><td>文件路径变更</td><td>检查数据源路径</td></tr><tr><td>数据类型错误</td><td>列中有混合类型</td><td>先清洗再更改类型</td></tr><tr><td>合并查询结果为空</td><td>关联列有空格差异</td><td>使用“修剪”功能</td></tr></tbody></table>

AI生成代码的问题

<table data-header-hidden><thead><tr><th width="126.22222900390625"></th><th width="274"></th></tr></thead><tbody><tr><td>问题</td><td>解决方案</td></tr><tr><td>AI公式报错</td><td>把错误信息发给AI，让它修正</td></tr><tr><td>公式逻辑不对</td><td>补充描述业务逻辑，让AI重新生成</td></tr><tr><td>版本不兼容</td><td>告知AI你的Excel版本</td></tr></tbody></table>

### 三、进阶学习路径

三条路径

完成本书学习后，你可以继续学习：

<table data-header-hidden><thead><tr><th width="94.77777099609375"></th><th width="171.6666259765625"></th><th width="277.111083984375"></th><th width="102.22222900390625"></th></tr></thead><tbody><tr><td>路径</td><td>方向</td><td>推荐理由</td><td>学习时长</td></tr><tr><td>Power BI</td><td>可视化+云端协作</td><td>已有Power Pivot基础，技能可迁移</td><td>1-2周</td></tr><tr><td>SQL</td><td>数据库查询</td><td>广告数据常存储在数据库中</td><td>1-2周</td></tr><tr><td>Python</td><td>数据分析+机器学习</td><td>处理更大数据量，预测建模</td><td>2-4周</td></tr></tbody></table>

路径一：Power BI

· 为什么学：可视化能力远超Excel，云端分享，移动端查看

· 学习目标：搭建企业级广告看板

· 推荐资源：Microsoft Learn - Power BI

· 与Excel的关系：DAX完全通用，Power Query完全通用

路径二：SQL

· 为什么学：广告数据常存储在数据库中，SQL是取数的标准语言

· 学习目标：能写SELECT、JOIN、GROUP BY查询广告数据

· 推荐资源：SQLZoo、W3Schools SQL Tutorial

路径三：Python数据分析

· 为什么学：处理Excel无法处理的大数据、机器学习、自动化

· 学习目标：用pandas处理数据，用matplotlib绘图

· 推荐资源：廖雪峰Python教程、Python Data Science Handbook

### 四、学习资源推荐

免费资源

<table data-header-hidden><thead><tr><th width="101.22222900390625"></th><th width="209.66668701171875"></th><th width="191.5555419921875"></th></tr></thead><tbody><tr><td>类型</td><td>资源</td><td>说明</td></tr><tr><td>函数查询</td><td>ExcelJet</td><td>函数速查，有示例</td></tr><tr><td>视频教程</td><td>ExcelIsFun（YouTube）</td><td>海量免费教程</td></tr><tr><td>官方文档</td><td>Microsoft Support</td><td>Excel函数完整文档</td></tr><tr><td>DAX参考</td><td>DAX Guide</td><td>所有DAX函数详解</td></tr></tbody></table>

AI工具推荐

<table data-header-hidden><thead><tr><th width="106.77777099609375"></th><th width="175.5555419921875"></th><th width="104.55560302734375"></th></tr></thead><tbody><tr><td>工具</td><td>用途</td><td>免费额度</td></tr><tr><td>DeepSeek</td><td>Excel公式/VBA生成</td><td>完全免费</td></tr><tr><td>ChatGPT</td><td>通用AI辅助</td><td>有限免费</td></tr><tr><td>Claude</td><td>长文本、代码解释</td><td>有限免费</td></tr></tbody></table>

### 五、全书总结

你完成的14天路线

第0阶段：函数基石（8章）

&#x20;   ↓

第1阶段：思维重塑（3章）

&#x20;   ↓

第2阶段：核心能力（5章）

&#x20;   ↓

第3阶段：智能飞跃（5章）

&#x20;   ↓

第4阶段：实战整合（2章）

你掌握的技能

<table data-header-hidden><thead><tr><th width="132.888916015625"></th><th width="539.5555419921875"></th></tr></thead><tbody><tr><td>类别</td><td>具体技能</td></tr><tr><td>Excel函数</td><td>XLOOKUP、SUMIFS、IFS、LEFT/RIGHT、IFERROR等20+核心函数</td></tr><tr><td>数据透视表</td><td>透视表创建、计算字段、切片器、日程表、交互仪表盘</td></tr><tr><td>Power Query</td><td>数据清洗、追加查询、合并查询、逆透视、从文件夹导入</td></tr><tr><td>Power Pivot</td><td>数据建模、表间关系、DAX度量值、CALCULATE、时间智能、KPI</td></tr><tr><td>AI辅助</td><td>AI生成公式、AI生成VBA、提问黄金公式</td></tr><tr><td>Python</td><td>pandas数据处理、matplotlib绘图（可选）</td></tr></tbody></table>

&#x20;

三个核心原则

回顾全书，记住这三个原则：

① 80/20法则：20%的Excel技能能解决80%的问题，不要追求100%

② AI是你的副驾驶：遇到问题，先问AI，再验证结果，最后应用

③ 在单元格里试试就知道了：动手操作一次，胜过阅读十遍

### 六、本章实操任务

任务1：优化一个真实工作流

选择你工作中一个经常做的Excel任务，用学到的技能重新做一遍，记录优化前后的时间对比。

任务2：制定进阶计划

根据你的职业目标，选择一条进阶路径（Power BI/SQL/Python），制定30天学习计划。

任务3：分享你的系统

把你的广告分析系统分享给同事，收集反馈，持续迭代。

### 七、本章思考题

1\.        你工作中最耗时的Excel任务是什么？现在你能用哪个技能把它从X分钟缩短到Y分钟？

2\.        三条进阶路径中，哪一条最适合你？为什么？

3\.        全书学完，你最有成就感的瞬间是哪一个？是第一次XLOOKUP匹配成功？还是第一次搭建完整系统？

### 八、本章学习记录

<table data-header-hidden><thead><tr><th width="185.111083984375"></th><th width="138.44439697265625"></th></tr></thead><tbody><tr><td>项目</td><td>完成情况</td></tr><tr><td>诊断当前工作流</td><td>✅ / ⬜</td></tr><tr><td>找出可优化的环节</td><td>✅ / ⬜</td></tr><tr><td>制定个人进阶计划</td><td>✅ / ⬜</td></tr><tr><td>完成本章思考题</td><td>✅ / ⬜</td></tr></tbody></table>

🎉 全书完
