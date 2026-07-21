# 第0-3章：让600行数据自己"认亲"

“打开「广告日报」和「产品映射表」。在「广告日报」的空白列输入=XLOOKUP(C2, 产品映射表!A:A, 产品映射表!C:C, "未找到")。看到‘电子产品’‘家居用品’‘服装’瞬间填满整列了吗？这就是查找函数的威力。”

## 现在就动手

打开 **「广告日报」** 工作表，看 **C列**（广告活动ID）。

然后打开 **「产品映射表」** 工作表，看 **A列**（广告活动ID）和 **C列**（产品线）。

现在回到「广告日报」，在数据右侧的空白列中（比如J列），输入以下公式：

\=XLOOKUP(C2, 产品映射表!A:A, 产品映射表!C:C, "未找到")

按回车。

「广告日报」中第一行的广告活动ID对应的产品线，瞬间出现了。

现在把鼠标移到这个单元格的右下角，双击黑色十字（或向下拖动）——看看发生了什么？

**整列600行数据，自动填满了对应的产品线。**

💡 **在单元格里试试就知道了。**

你刚刚完成了一次\*\*“跨表匹配”\*\*：根据600行广告数据中的广告活动ID，从产品映射表中找到对应的产品线，然后填入。

整个操作，从输入公式到填充完毕，**不到10秒钟**。远胜于手工匹配。

**这一章，我们可以亲自体会到：查找函数为什么是Excel里“性价比最高”的函数。**

## 一、为什么需要查找函数？

你每天都会面对这样的场景：

你从广告后台导出了一份广告报表，里面有【广告活动ID】、【花费】、【点击】等数据。但你的老板想看的是“每个产品线的广告花费”。

问题来了——广告报表里没有【产品线】这一列。产品线信息在另一张「产品映射表」里。

两张表唯一的共同点是\*\*【广告活动ID】\*\*：

「广告日报」里每个广告活动有一个ID，而「产品映射表」里同一个ID对应着一条产品线信息。

**查找函数的本质就是：**

根据两表共同的某一个已知值（广告活动ID），在另一张表中找到它，然后返回同一行中另一列的数据（产品线）。

查找值（已知） → 在查找区域找到这一行 → 返回该行的某一列

## 二、VLOOKUP——最经典的查找函数

VLOOKUP是Excel中知名度最高的查找函数。它名字中的“V”代表“垂直”（Vertical），意思是**在列中从上到下查找**。

**VLOOKUP的语法**

\=VLOOKUP(找什么, 在哪里找, 返回第几列, 精确匹配还是近似匹配)

**用VLOOKUP完成刚才的任务**

J2 =VLOOKUP(C2, 产品映射表!$A$2:$E$31, 3, FALSE)

**参数解读**：

<table data-header-hidden><thead><tr><th width="89"></th><th width="221.22222900390625"></th><th width="248.88885498046875"></th></tr></thead><tbody><tr><td><strong>参数</strong></td><td><strong>值</strong></td><td><strong>含义</strong></td></tr><tr><td>第1个</td><td>C2</td><td>找“广告活动ID”</td></tr><tr><td>第2个</td><td>产品映射表!$A$2:$E$31</td><td>在这个区域里找</td></tr><tr><td>第3个</td><td>3</td><td>找到后，返回第3列（产品线）</td></tr><tr><td>第4个</td><td>FALSE</td><td>必须精确匹配</td></tr></tbody></table>

**VLOOKUP的“铁律”——必须记住**

**查找值必须在查找区域的第一列。**

这是VLOOKUP最常出错的地方。如果你要在「产品映射表」的某个区域找“广告活动ID”，那么**查找区域的第一列必须是“广告活动ID”**。

错误：=VLOOKUP(C2, 产品映射表!$B$2:$E$31, 3, FALSE)

↑ 第一列是B列，但C2“广告活动ID”的值在A列，找不到！

正确：=VLOOKUP(C2, 产品映射表!$A$2:$E$31, 3, FALSE)

↑ 第一列是A列，C2“广告活动ID”的值就在A列找，没问题！

**VLOOKUP的局限性**

<table data-header-hidden><thead><tr><th width="131.77777099609375"></th><th width="439.55548095703125"></th></tr></thead><tbody><tr><td><strong>局限性</strong></td><td><strong>说明</strong></td></tr><tr><td><strong>只能向右查</strong></td><td>返回值必须在查找区域的右边</td></tr><tr><td><strong>列号固定</strong></td><td>如果在表中间插入一列，公式中的列号要手动改</td></tr><tr><td><strong>默认近似匹配</strong></td><td><strong>第四个参数默认是False（精确匹配）</strong><br><br>如果不写第4个参数默认是近似匹配，初学者容易出错</td></tr></tbody></table>

## 三、XLOOKUP——VLOOKUP的升级版

XLOOKUP是Office 365中推出的新一代查找函数，解决了VLOOKUP几乎所有痛点。

**XLOOKUP的语法**

\=XLOOKUP(找什么, 在哪列找, 在哪列返回, 如果找不到显示什么)

<table data-header-hidden><thead><tr><th width="78.4444580078125"></th><th width="241.77777099609375"></th></tr></thead><tbody><tr><td><strong>参数</strong></td><td><strong>说明</strong></td></tr><tr><td>第1个</td><td>你要找什么</td></tr><tr><td>第2个</td><td>在<strong>哪一列</strong>中查找</td></tr><tr><td>第3个</td><td>找到后，返回<strong>哪一列</strong>的数据</td></tr><tr><td>第4个</td><td>如果找不到，显示什么文字</td></tr></tbody></table>

**用XLOOKUP完成任务**

K2 =XLOOKUP(C2, 产品映射表!A:A, 产品映射表!C:C, "未找到")

**和VLOOKUP的对比**：

<table data-header-hidden><thead><tr><th width="64.5555419921875"></th><th width="350.2222900390625"></th><th></th></tr></thead><tbody><tr><td></td><td><strong>VLOOKUP</strong></td><td><strong>XLOOKUP</strong></td></tr><tr><td>写法</td><td>=VLOOKUP(C2, 表!$A$2:$E$31, 3, FALSE)</td><td>=XLOOKUP(C2, 表!A:A, 表!C:C, "未找到")</td></tr><tr><td>版本</td><td>所有版本通用</td><td>仅限Office 365/Excel 2021</td></tr><tr><td>优劣</td><td>返回值需要数列号、<br><br>查找值必须在第一列</td><td>更简洁、更直观、功能更强</td></tr></tbody></table>

**如果公司用的是Office 365，优先用XLOOKUP。**&#x20;

它更符合人类思维：“找什么 → 在哪列找 → 返回哪列”。

## 四、INDEX+MATCH——最灵活的查找组合

如果你用的是老版本Excel，或者需要复杂查找（比如**向左查**），INDEX+MATCH是最好的选择。

**两个函数各司其职**

<table data-header-hidden><thead><tr><th width="90.11114501953125"></th><th width="129.111083984375"></th><th width="235.44439697265625"></th></tr></thead><tbody><tr><td><strong>函数</strong></td><td><strong>作用</strong></td><td><strong>类比</strong></td></tr><tr><td><strong>MATCH</strong></td><td>根据值找位置</td><td>找到“G-001”在A列的第几行</td></tr><tr><td><strong>INDEX</strong></td><td>根据位置取值</td><td>取C列第3行的值</td></tr></tbody></table>

**组合使用**

\=INDEX(返回列, MATCH(查找值, 查找列, 0))

广告案例：根据广告活动ID匹配产品线

L2 =INDEX(产品映射表!C:C, MATCH(C2, 产品映射表!A:A, 0))

**执行过程**：

1. MATCH(C2, 产品映射表!A:A, 0) → 在A列找C2，返回它在A列中的行号
2. INDEX(产品映射表!C:C, 行号) → 在C列取该行的值

**INDEX+MATCH的优势**

<table data-header-hidden><thead><tr><th width="139.5555419921875"></th><th width="219.5555419921875"></th></tr></thead><tbody><tr><td><strong>优势</strong></td><td><strong>说明</strong></td></tr><tr><td><strong>可以向左查</strong></td><td>返回值可以在查找列的左边</td></tr><tr><td><strong>不受插入列影响</strong></td><td>增减列不影响公式</td></tr><tr><td><strong>兼容所有版本</strong></td><td>所有Excel版本都支持</td></tr></tbody></table>

虽然写法比XLOOKUP复杂一点，但它“通吃所有版本”，是职场中最稳妥的选择。

## 五、CHOOSE——最简单的“选号”工具

CHOOSE不是查找函数，但常常配合查找一起使用，让结果更直观。

**语法**：

\=CHOOSE(序号, 值1, 值2, 值3, ...)

**示例**：

\=CHOOSE(2, "Q1", "Q2", "Q3", "Q4") → 返回"Q2"

**广告案例**：将广告活动ID中的序号转为季度名称

假设广告活动ID是G-101，第4位（1）代表第1季度：

\=CHOOSE(VALUE(MID(C2, 4, 1)), "Q1", "Q2", "Q3", "Q4")

## 六、HLOOKUP——横向查找（补充）

HLOOKUP是VLOOKUP的“兄弟”，只是方向不同：VLOOKUP垂直找，HLOOKUP**水平找**。

当你遇到数据是横向排列时（表头在左边，数据向右延伸），就用HLOOKUP。

**语法**：

\=HLOOKUP(找什么, 在哪找, 返回第几行, 精确匹配)

## 七、查找函数选择指南

<table data-header-hidden><thead><tr><th width="213.4444580078125"></th><th width="148.111083984375"></th><th width="164.2222900390625"></th></tr></thead><tbody><tr><td><strong>你的情况</strong></td><td><strong>推荐函数</strong></td><td><strong>理由</strong></td></tr><tr><td>公司用Office 365</td><td><strong>XLOOKUP</strong></td><td>最简洁、最直观</td></tr><tr><td>老版本Excel，简单查找</td><td><strong>VLOOKUP</strong></td><td>最简单，上手快</td></tr><tr><td>老版本Excel，需要向左查</td><td><strong>INDEX+MATCH</strong></td><td>最灵活，万能组合</td></tr><tr><td>数据是横向排列的</td><td><strong>HLOOKUP</strong></td><td>专门处理横向数据</td></tr></tbody></table>

💡 **在单元格里试试就知道了。**

把你刚写的XLOOKUP公式，改成VLOOKUP试试。再看INDEX+MATCH怎么写。同一个任务，三种写法，你自己比较哪个更适合你。

## 八、综合实战——让600行数据“认亲”

**任务**

在「广告日报」中新增三列，从「产品映射表」中匹配：

1. 产品线
2. 负责人
3. 目标ACOS

**操作步骤**

**第1步：匹配产品线**

用XLOOKUP（Office 365）：

\=XLOOKUP(C2, 产品映射表!A:A, 产品映射表!C:C, "未分类")

或用VLOOKUP：

\=VLOOKUP(C2, 产品映射表!$A$2:$E$31, 3, FALSE)

**第2步：匹配负责人**

\=XLOOKUP(C2, 产品映射表!A:A, 产品映射表!D:D, "未分配")

**第3步：匹配目标ACOS**

\=XLOOKUP(C2, 产品映射表!A:A, 产品映射表!E:E, "未设定")

**为什么用“未设定”而不是具体数值？** 如果匹配不到时显示“20%”，你会误以为这个活动真的有20%的目标ACOS。用“未设定”可以清晰地告诉你“这里数据缺失了，需要人工跟进”。

**完成后的效果**

<table data-header-hidden><thead><tr><th width="112.3333740234375"></th><th width="80.22222900390625"></th><th width="112.77783203125"></th><th width="88.77783203125"></th><th width="109.44427490234375"></th></tr></thead><tbody><tr><td><strong>广告活动ID</strong></td><td><strong>...</strong></td><td><strong>产品线</strong></td><td><strong>负责人</strong></td><td><strong>目标ACOS</strong></td></tr><tr><td>G-001</td><td>...</td><td>电子产品</td><td>张三</td><td>25%</td></tr><tr><td>G-002</td><td>...</td><td>电子产品</td><td>张三</td><td>20%</td></tr><tr><td>F-001</td><td>...</td><td>家居用品</td><td>李四</td><td>25%</td></tr></tbody></table>

你亲手把600行数据，跟另一张表“认了亲”。之前需要1-2小时手工查找的工作，现在10秒钟完成。

## 九、这一章你带走了什么？

<table data-header-hidden><thead><tr><th width="295.111083984375"></th><th width="301.77783203125"></th></tr></thead><tbody><tr><td><strong>你之前可能觉得</strong></td><td><strong>你现在知道了</strong></td></tr><tr><td>两张表的数据匹配好麻烦</td><td>一行XLOOKUP/VLOOKUP就搞定</td></tr><tr><td>查找函数好复杂，参数记不住</td><td>理解了“找什么→在哪找→返回什么”，参数只是形式</td></tr><tr><td>VLOOKUP、XLOOKUP、INDEX+MATCH都学不会</td><td>选一个先学会，其他一通百通</td></tr></tbody></table>

💡 **在单元格里试试就知道了。**

打开「广告日报」和「产品映射表」，写完XLOOKUP公式，看到“电子产品”“家居用品”“服装”瞬间填满整列的那一刻——你就再也不会问“为什么要学查找函数”了。

## 十、本章实操任务

**任务1：匹配产品线**

在「广告日报」中新增“产品线”列，用XLOOKUP或VLOOKUP从「产品映射表」中匹配。

**任务2：匹配负责人和目标ACOS**

用同样的方法匹配“负责人”和“目标ACOS”两列。

**任务3：尝试三种写法**

分别用VLOOKUP、XLOOKUP、INDEX+MATCH完成匹配，比较三种写法的差异。

**十一、本章思考题**

1. 为什么VLOOKUP要求“查找值必须在查找区域的第一列”？如果你把这个规则忘了，会发生什么？
2. 公司用Office 365，你用XLOOKUP；同事用Excel 2016，他们打开你的文件会怎么样？怎么解决？
3. 第3步中，匹配目标ACOS时为什么用“未设定”而不是“0”？这给你什么启示？

**十二、本章学习记录**

<table data-header-hidden><thead><tr><th width="260.66668701171875"></th><th width="140.66668701171875"></th></tr></thead><tbody><tr><td><strong>项目</strong></td><td><strong>完成情况</strong></td></tr><tr><td>完成XLOOKUP匹配产品线</td><td>✅ / ⬜</td></tr><tr><td>完成VLOOKUP匹配产品线</td><td>✅ / ⬜</td></tr><tr><td>完成INDEX+MATCH匹配产品线</td><td>✅ / ⬜</td></tr><tr><td>理解三种查找函数的区别</td><td>✅ / ⬜</td></tr><tr><td>完成综合实战</td><td>✅ / ⬜</td></tr><tr><td>完成实操任务</td><td>✅ / ⬜</td></tr></tbody></table>

**下一章预告**：第0-4章《3秒汇总，告别手动筛选》。

写一行=SUMIFS(E:E, B:B, "Google")，Google总花费瞬间出现。把“Google”改成“Facebook”，又是一个1秒。你亲眼看到——不是Excel变快了，是你会用了。

💡 打开EXCEL，在单元格里试试就知道了
