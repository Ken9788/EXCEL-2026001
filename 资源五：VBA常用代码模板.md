

\## 资源五：VBA常用代码模板



\*\*刷新所有数据\*\*



vba



Sub 一键刷新()



ThisWorkbook.RefreshAll



MsgBox "✅ 数据已刷新！"



End Sub



\*\*备份当前表\*\*



vba



Sub 备份当前表()



ActiveSheet.Copy After:=Sheets(Sheets.Count)



ActiveSheet.Name = "备份\_" \& Format(Date, "yyyy-mm-dd")



End Sub



\*\*另存为PDF\*\*



vba



Sub 另存为PDF()



Dim path As String



path = CreateObject("WScript.Shell").SpecialFolders("Desktop") \& "\\\\报表.pdf"



ActiveSheet.ExportAsFixedFormat Type:=xlTypePDF, fileName:=path



End Sub



\*\*复制并粘贴数值\*\*



vba



Sub 粘贴为数值()



Selection.Copy



Selection.PasteSpecial Paste:=xlPasteValues



End Sub



