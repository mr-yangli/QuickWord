# 更新日志

QuickWord 各版本的变更，倒序排列（最新在上）。

> **口径**
> - 版本号跟 .NET 主版本走（.NET 10 → 10.x）；Quick 五族同批发布时对齐全主版本。破坏性改动升次版本号（10.0.0 → 10.1.0），缺陷修复升修订号。
> - 「未发布」收 main 已合入、尚未定版的改动；定版时改节名为版本号并标「待发布」（`Directory.Build.props` 的 `<Version>` 同步就位），上包那天把「待发布」换成日期。
> - 分档为 新增 / 变更 / 修复 / 移除；标 **破坏性** 的改动，消费方升级时要动代码。
> - 版本日期取该版本在 NuGet 上可还原之日，不是提交日。

## 未发布

暂无。

## 10.0.0 — 2026-11-09

首个公开版本：QuickWord 从内部单仓拆为独立仓库（GitHub `mr-yangli/QuickWord`、Gitee `mr_yangli/quick-word`），本族 1 颗包 `QuickWord` 上 NuGet。零第三方依赖，MIT。下面列的是发布内容面，不是相对上一版的 diff——10.0.0 之前没有公开版本。

### 新增

- **表格导出**：`Word.SaveAs` 把集合写成 .docx 表格；`WordOptions` 提供 `Title`、`FooterText`（`{PAGE}` 页码占位）等版式项。
- **文档读回**：`Word.Read` 给出段落 + 表格的块模型；`doc.Tables.*.Query()` 的行装配形状与 QuickExcel 的 `Query` 一致，两族的读法对得上。
- **模板填充（不改版式）**：`Word.SaveAsByTemplateAsync` 按占位键填值；`styles` / `theme` 等部件逐字节照抄，run 级字体样式保留，不做版式重排。
- **图片占位**：`ImagePlaceholder.FromFile(path, width, height)` 作为填充值，按给定尺寸入文。
- **测试面**：`tests/QuickWord.Tests` —— 导出（`WordExportTests`）、读回（`WordReadTests`）、模板填充（`TemplateTests`）、包完整性（`PackageGuardTests`：带 XML 1.0 控制字符的值不让包失解析）。
