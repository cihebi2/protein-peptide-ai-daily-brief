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

## Wave3 2026-09-16（第二轮）

- 多源 OA（OpenAlex/Unpaywall/Semantic Scholar/EuropePMC/arXiv 镜像）补下 115 篇 strict-v2 高分论文并完成精读审查。
- papers/ 新增 115（DOI 命名），合并后论文卡片总数 1221。
- 仍有约 156 篇高分论文因出版商 403/无 OA 副本未能获取全文（需校园网 InstSci 通道），清单在本地 wave3-candidates.jsonl。

## Wave4 2026-09-17（校园网内置浏览器批次）

- ZCode 内置浏览器 + 校园 IP 机构认证（无需登录），从 Wiley/ACS/OUP/RSC/Science/MDPI 等出版商补下 70 篇 strict-v2 高分论文并完成精读审查。
- papers/ 新增 70，合并后论文卡片总数 1291。
- 剩余 73 篇为无 OA 副本且浏览器会话无法通过 CF 的硬块，跳过（清单在本地 wave4-iab.jsonl）。
- 已知 3 篇 DOI-内容错配已在卡片 novelty_boundary 中标注。

## Wave3 2026-09-16（第二轮）

- 多源 OA（OpenAlex/Unpaywall/Semantic Scholar/EuropePMC/arXiv 镜像）补下 115 篇 strict-v2 高分论文并完成精读审查。
- papers/ 新增 115（DOI 命名），合并后论文卡片总数 1221。
- 仍有约 156 篇高分论文因出版商 403/无 OA 副本未能获取全文（需校园网 InstSci 通道），清单在本地 wave3-candidates.jsonl。

## Wave3 2026-09-16（第二轮）

- 多源 OA（OpenAlex/Unpaywall/Semantic Scholar/EuropePMC/arXiv 镜像）补下 115 篇 strict-v2 高分论文并完成精读审查。
- papers/ 新增 115（DOI 命名），合并后论文卡片总数 1221。
- 仍有约 156 篇高分论文因出版商 403/无 OA 副本未能获取全文（需校园网 InstSci 通道），清单在本地 wave3-candidates.jsonl。

## Lane Expansion 2026-09-17（五方向扩展批次）

- 扩展课题关切至五方向：L1 蛋白设计、L2 蛋白语言模型、L3 肽性质预测、L4 肽生成、L5 肽优化。
- OpenAlex 实时扫描（2023-08 以来、引用降序）429 候选，期刊门（T1/T2 或引用>=40）+ 信号门（标题领域词x方法词x强动词）筛出 287，下载 110（requests 校园直连 77 + 内置浏览器渲染提取 33）。
- 110 篇全部精读审查（subagent 分片，零跳过），带 lane/tier/cited/venue 标注；部分综述类条目存在 lane 标签漂移，已在 novelty_boundary 中标注。
- papers/ 新增 110，合并后论文卡片总数 1404。
