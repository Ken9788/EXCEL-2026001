\# 第3-2章：在Excel里“跑”Python



“在单元格输入=PY(1+2+3)——这是Excel里的第一行Python代码。数据分析的新世界，正在打开。”



\## 现在就动手



⚠️ \*\*本章功能仅适用于Microsoft 365（Windows版）\*\* 。如果您使用其他版本，可以跳过实操，阅读概念部分了解即可。



打开Excel，在任意空白单元格中输入：



\\=PY(1+2+3)



按回车。



\*\*你看到了什么？\*\*



单元格中出现了数字 \*\*6\*\*。



💡 \*\*在单元格里试试就知道了。\*\*



你刚刚在Excel里运行了第一行Python代码。



不是用Python软件，不是在命令行里——就在Excel的单元格里。



看起来和普通公式差不多，但背后是不同的引擎。这意味着你可以用Python的pandas处理数据，用matplotlib画图，用scikit-learn做机器学习。



\*\*这一章，就是让你打开这扇门——看看Python能在Excel里做什么。\*\*



\## 一、为什么要在Excel里用Python？



\*\*Excel + Python 的互补关系\*\*



| \*\*Excel擅长\*\* | \*\*Python擅长\*\* |

| --- | --- |

| 数据录入、查看 | 大规模数据处理 |

| 基础计算、公式 | 复杂的统计分析 |

| 交互式报表、图表 | 高级可视化（热力图、聚类图） |

| 快速上手、即学即用 | 机器学习、预测建模 |



\*\*当你在Excel里运行Python时，你把两者的优势合在了一起。\*\*



\*\*使用场景\*\*



| \*\*场景\*\* | \*\*为什么用Python in Excel\*\* |

| --- | --- |

| 相关性分析 | 一行代码计算所有相关系数，Excel需要逐个算 |

| 热力图 | Python的seaborn一键绘制，Excel无法原生实现 |

| 数据清洗 | 处理缺失值、异常值，pandas比Excel公式快 |

| 聚类分析 | 用scikit-learn给广告活动自动分群 |



\## 二、=PY()函数基础



\*\*基本语法\*\*



\\=PY(Python代码)



\*\*单行代码\*\*



\\=PY(1+2+3)



→ 6



\\=PY(10 \\\* 5)



→ 50



\*\*多行代码\*\*



在单元格中输入=PY(后按回车，进入多行编辑模式：



\\=PY(



import pandas as pd



df = pd.DataFrame({"广告活动": \\\["品牌词", "竞品词"\\], "ROAS": \\\[3.2, 2.1\\]})



df



)



按回车后，Excel会在单元格中显示DataFrame的内容（一个迷你表格）。



\*\*访问Excel数据——xl()函数\*\*



xl()函数是Python in Excel的“桥梁”，用来读取Excel单元格的数据。



\\=PY(xl("A1").value \\\* 2)



读取A1单元格的值，乘以2后返回。



读取数据区域：



\\=PY(xl("A1:E100", headers=True))



读取A1到E100区域，第一行作为列名。



\## 三、pandas——数据分析的核心库



\*\*读取数据到DataFrame\*\*



\\=PY(



import pandas as pd



df = xl("A1:M600", headers=True)



df.head(10)



)



\*\*分组聚合\*\*



\*\*场景\*\*：按渠道汇总总花费和平均ROAS。



\\=PY(



import pandas as pd



df = xl("A1:M600", headers=True)



result = df.groupby("渠道").agg({



"花费": "sum",



"ROAS": "mean"



}).reset\_index()



result



)



\*\*筛选数据\*\*



\\=PY(



import pandas as pd



df = xl("A1:M600", headers=True)



\\# 筛选ROAS>3且花费>100的行



high\_performers = df\\\[(df\\\["ROAS"\\] > 3) \& (df\\\["花费"\\] > 100)\\]



high\_performers



)



\## 四、matplotlib——数据可视化



\*\*绘制柱状图\*\*



\*\*场景\*\*：各渠道花费对比。



\\=PY(



import pandas as pd



import matplotlib.pyplot as plt



df = xl("A1:M600", headers=True)



channel\_spend = df.groupby("渠道")\\\["花费"\\].sum()



plt.figure(figsize=(8, 5))



plt.bar(channel\_spend.index, channel\_spend.values)



plt.title("各渠道花费对比")



plt.xlabel("渠道")



plt.ylabel("花费（元）")



plt.show()



)



\*\*绘制相关性热力图（进阶）\*\*



\*\*场景\*\*：分析花费、点击、订单、销售额之间的相关性。



\\=PY(



import pandas as pd



import seaborn as sns



import matplotlib.pyplot as plt



df = xl("A1:M600", headers=True)



numeric\_cols = df\\\[\\\["花费", "点击", "订单", "销售额"\\]\\]



corr = numeric\_cols.corr()



plt.figure(figsize=(8, 6))



sns.heatmap(corr, annot=True, cmap="coolwarm", center=0)



plt.title("广告指标相关性分析")



plt.show()



)



\## 五、自然语言查询（AI驱动）



\*\*什么是自然语言查询？\*\*



在Excel 365中，你可以用\*\*中文描述\*\*你的需求，Excel自动生成分析结果。



\*\*如何使用\*\*



1\.  选中数据区域

2\.  开始 → 分析数据

3\.  输入中文描述，如：“各渠道花费占比是多少？”



\*\*示例\*\*



| \*\*输入\*\* | \*\*Excel可能生成的输出\*\* |

| --- | --- |

| “哪个渠道ROAS最高？” | 图表 + 文字回答 |

| “按月汇总花费趋势” | 折线图 |

| “找出花费大于500的广告活动” | 筛选后的数据表 |



\## 六、什么时候用=PY() vs 外部AI工具



| \*\*场景\*\* | \*\*推荐工具\*\* | \*\*原因\*\* |

| --- | --- | --- |

| 写Excel公式 | 外部AI | 更灵活，连续对话 |

| 写VBA代码 | 外部AI | 生成代码+注释更完整 |

| 画高级图表 | \\=PY() | 原生显示在Excel中 |

| 做统计分析 | \\=PY() | 专业统计库 |

| 做机器学习 | \\=PY() | scikit-learn库 |



\## 七、本章思考题



1\.  如果Excel版本不支持Python in Excel，你还能从本章学到什么？

2\.  pandas的groupby和Excel的透视表有什么相似之处？有什么区别？

3\.  相关性热力图能告诉你什么信息？如果花费和销售额强相关，意味着什么？



\## 八、本章学习记录



| \*\*项目\*\* | \*\*完成情况\*\* |

| --- | --- |

| 了解=PY()函数的用途 | ✅ / ⬜ |

| 了解xl()函数的作用 | ✅ / ⬜ |

| 了解pandas分组聚合 | ✅ / ⬜ |

| 了解matplotlib绘图 | ✅ / ⬜ |

| 了解自然语言查询 | ✅ / ⬜ |

| 完成实操任务（如环境支持） | ✅ / ⬜ |



\*\*下一章预告\*\*：第3-3章《把四张表“串”成一张网》。



打开Power Pivot，在关系图视图中把【广告活动ID】从「广告日报」拖到「产品映射表」——一条连线，两张表关联上了。你亲手把分散的数据，整合成了完整的数据模型。



💡 打开EXCEL，在单元格里试试就知道了

