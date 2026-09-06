# scikit-fingerprints/peptides_molecular_fingerprints_classification

- **仓库：** [https://github.com/scikit-fingerprints/peptides_molecular_fingerprints_classification](https://github.com/scikit-fingerprints/peptides_molecular_fingerprints_classification)
- **固定 commit：** `a76d135837d23d41656de20620c5548dd3682515`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 0

## 仓库摘要

这是一个面向 peptide function prediction 的静态基准仓库，汇集 AMPBenchmark、AutoPeptideML、BERT_AMP_benchmark、PeptideReactor、Xu_AMP 等数据，以及 fingerprint/ESM/AA-count 基线、数据加载、分布分析和结果评估脚本；冻结清单中未见训练入口、推理入口或 checkpoint。

## 可复用模块与资源

- 未发现可公开描述的结构化资产。
## 使用限制

- 仅做静态清单审查；仓库代码未执行。
- 未安装依赖，无法验证脚本是否可运行或参数是否完整。
- tests 未运行，无法证明行为正确性或结果可复现。
- 未见 training_entrypoint、inference 或 checkpoint 资产。
- 部分大文件可能为 promisor/截断对象，路径存在不等于内容完整可用。

## 仍未知

- 各数据子集的原始出处、再分发许可与过滤规则未在冻结证据中确证。
- preprocessed_datasets 的具体生成流程只能从命名推断，静态清单不能证明其确为仓库内生成。
- results/ 下的 CSV/PDF/parquet 是否来自已执行实验，静态证据不足以确认。
- README.md 与 pyproject.toml 只在清单中可见，未读取正文，无法补全命令级细节。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
