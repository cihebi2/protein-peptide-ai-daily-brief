# hmdlab/arg-bert

- **仓库：** [https://github.com/hmdlab/arg-bert](https://github.com/hmdlab/arg-bert)
- **固定 commit：** `52f252d4dee6d0aa5574bb094d28bce799461b51`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 0

## 仓库摘要

该仓库是 ARG-BERT 的静态代码与分析仓库，包含 ProteinBERT 结构、tokenization、UniRef 预训练/微调、示例数据和作图 notebook；未发现冻结 checkpoint、独立 inference/evaluation 闭环或 LICENSE 文件。

## 可复用模块与资源

- 未发现可公开描述的结构化资产。
## 使用限制

- not_executed_static_analysis_only
- repository_code_not_executed
- tests_not_run
- dependencies_not_installed
- submodules_not_initialized
- license_file_not_found
- no_tracked_checkpoint_artifacts

## 仍未知

- README.md 与 notebook 内容未逐页核验，无法确认论文级结果是否完整可复现。
- 外部 pretrained weights / checkpoint 下载来源未见冻结条目。
- Sample_data 与 fasta 文件的生成来源、许可与是否仅为示例未明。
- `test.py` 的角色未确认是评测还是推理入口。
- 受 clone filter 影响，不能排除未跟踪的大权重文件。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
