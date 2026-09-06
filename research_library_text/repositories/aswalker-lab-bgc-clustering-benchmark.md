# aswalker-lab/BGC-clustering-benchmark

- **仓库：** [https://github.com/aswalker-lab/BGC-clustering-benchmark](https://github.com/aswalker-lab/BGC-clustering-benchmark)
- **固定 commit：** `bb8500d60f90cb43397cc41de5aed396725aa800`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 12

## 仓库摘要

该仓库主要是 BGC clustering benchmark 的静态资产集合：包含大量 `benchmark_bgc/*.gbk`、多组聚类/相似度 CSV，以及若干评测脚本；未见训练、推理或 checkpoint。

## 可复用模块与资源

### datasets

- `benchmark_bgc/BGC0000001.gbk`
  - 能力：BGC benchmark 输入集
  - 用途：`benchmark_bgc/` 中的代表性 GenBank 记录，用于聚类基准输入
  - 复用状态：partial；类型：unknown
- `bgc_class.csv`
  - 能力：BGC 类别标注表
  - 用途：BGC class / label 对照表
  - 复用状态：partial；类型：unknown
- `bgc_clusters/bigscape_clusters_1.csv`
  - 能力：聚类结果表
  - 用途：BiG-SCAPE 聚类输出之一
  - 复用状态：partial；类型：unknown
- `bgc_similarities/kcb_similarity_score.csv`
  - 能力：相似度结果表
  - 用途：BGC similarity 比较表之一
  - 复用状态：partial；类型：unknown
- `product_clusters/butina_clusters_pt2.csv`
  - 能力：产物聚类输出
  - 用途：product cluster 分组结果
  - 复用状态：partial；类型：unknown
- `product_scaffolds/bm_scaffolds.csv`
  - 能力：scaffold 输出
  - 用途：scaffold 分组结果
  - 复用状态：partial；类型：unknown
- `source_data/NPAtlas_bm_v1.tsv`
  - 能力：来源数据表
  - 用途：NPAtlas benchmark source table
  - 复用状态：partial；类型：unknown
- `tanimoto_results/NPAtlas_bm_v1.tsv`
  - 能力：Tanimoto 结果表
  - 用途：Tanimoto 比较输出表
  - 复用状态：partial；类型：unknown

### evaluation

- `bgc_sim_tanimoto_comparison.py`
  - 能力：BGC similarity 对比评测
  - 用途：生成 Tanimoto 相关的 BGC 比较与输出
  - 复用状态：ready_for_review；类型：code_entry
- `calculate_clustering_metrics.py`
  - 能力：聚类指标计算
  - 用途：计算聚类质量/一致性指标
  - 复用状态：ready_for_review；类型：code_entry
- `calculate_structural_similarity.py`
  - 能力：结构相似度计算
  - 用途：计算结构相似度相关指标
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `calc_product_clusters_and_scaffolds.py`
  - 能力：数据派生辅助
  - 用途：从现有输入表生成 `product_clusters` 与 `product_scaffolds` 结果文件
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态盘点，未运行任何代码、测试或评测。
- 依赖未安装，无法验证脚本可执行性或输出一致性。
- 路径存在不等于可复现，数据是否为原始/派生仍需人工核查。
- 子模块未初始化，大文件是否完整可用无法确认。

## 仍未知

- `benchmark_bgc/*.gbk` 的具体来源与再分发条款未从静态清单中确认。
- `source_data/NPAtlas_bm_v1.tsv` 的来源和许可细节未读取文件正文确认。
- 仓库中的 CSV/TSV 多为结果表还是中间产物，静态路径无法区分全部边界。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
