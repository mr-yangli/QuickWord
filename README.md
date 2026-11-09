# QuickWord

.docx 表格导出 + 文档读回 + 不改版式填模板。

MIT 协议，零第三方依赖。

## 安装

```bash
dotnet add package QuickWord --prerelease
```

## 快速上手

```csharp
using QuickWord;

Word.SaveAs("report.docx", employeeList, new WordOptions { Title = "员工花名册", FooterText = "第 {PAGE} 页" });

var doc = Word.Read("report.docx");            // 段落 + 表格块模型
var rows = doc.Tables.First().Query();          // 与 QuickExcel Query 同形状

await Word.SaveAsByTemplateAsync(output, "合同模板.docx", new Dictionary<string, object>
{   // 不改版式：styles/theme 等部件逐字节照抄，run 级字体样式保留
    ["姓名"] = "张萌",
    ["签名"] = ImagePlaceholder.FromFile("sign.png", width: 70, height: 30),
});
```

## 构建与测试

```bash
dotnet build QuickWord.slnx
dotnet test tests/QuickWord.Tests/QuickWord.Tests.csproj
```

## 文档

见 [docs/quickword-usage.md](docs/quickword-usage.md)。

## License

MIT
