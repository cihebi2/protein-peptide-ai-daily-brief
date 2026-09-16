# Export Manifest

- Generated: 2026-09-06T12:25:40+08:00
- Source dashboard: `D:\work\汇总知识工作台\research-dashboard\data\research-library.json`
- Source v4 database: `E:\research-intelligence-hub\backfill-2023-2026\manifests\research-knowledge-v4.sqlite`
- Paper documents: 627
- Repository documents: 300
- Repository asset entries: 4839
- Excluded local-private papers: 1
- Verification: source dashboard reports an already-verified v4 snapshot.
- Content rule: Markdown-only derived text; no PDF, full text, SQLite, source code, weights, credentials or logs.

## Merge 2026-09-16

- mass_review_20260916 批次并入主语料：papers/ 新增 479（DOI 命名），repositories/ 新增 75 + 34 个旧卡追加复审补充。
- 合并后卡片总数：论文 1106，仓库 375。
- 两批论文 DOI 零重叠；合并方式为文件级并存，未改写 2026-09-06 基础卡正文。

## Wave3 2026-09-16（第二轮）

- 多源 OA（OpenAlex/Unpaywall/Semantic Scholar/EuropePMC/arXiv 镜像）补下 115 篇 strict-v2 高分论文并完成精读审查。
- papers/ 新增 115（DOI 命名），合并后论文卡片总数 1221。
- 仍有约 156 篇高分论文因出版商 403/无 OA 副本未能获取全文（需校园网 InstSci 通道），清单在本地 wave3-candidates.jsonl。
