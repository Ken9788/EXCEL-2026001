# 资源五：VBA常用代码模板

**刷新所有数据**

vba

Sub 一键刷新()

&#x20;   ThisWorkbook.RefreshAll

&#x20;   MsgBox "✅ 数据已刷新！"

End Sub

**备份当前表**

vba

Sub 备份当前表()

&#x20;   ActiveSheet.Copy After:=Sheets(Sheets.Count)

&#x20;   ActiveSheet.Name = "备份\_" & Format(Date, "yyyy-mm-dd")

End Sub

**另存为PDF**

vba

Sub 另存为PDF()

&#x20;   Dim path As String

&#x20;   path = CreateObject("WScript.Shell").SpecialFolders("Desktop") & "\报表.pdf"

&#x20;   ActiveSheet.ExportAsFixedFormat Type:=xlTypePDF, fileName:=path

End Sub

**复制并粘贴数值**

vba

Sub 粘贴为数值()

&#x20;   Selection.Copy

&#x20;   Selection.PasteSpecial Paste:=xlPasteValues

End Sub
