# athanzli/CancerMOBI-Bench

- **仓库：** [https://github.com/athanzli/CancerMOBI-Bench](https://github.com/athanzli/CancerMOBI-Bench)
- **固定 commit：** `f44e7d0063b963ca66abc3237a29f7d4a01cbac1`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 28

## 仓库摘要

该仓库是一个面向癌症多组学 biomarker discovery 的 benchmark 套件，打包了多种 selected_models、数据预处理、评测与结果分析脚本；静态审计未见代码执行或测试证据，根目录为 MIT，但子项目存在独立许可与未知边界，整体应按 mixed 处理。

## 可复用模块与资源

### checkpoints

- `code/selected_models/GENIUS/Training/saved_models/best_model.pb`
  - 能力：saved model artifact
  - 用途：GENIUS 目录下的已保存模型文件；仅能确认静态存在，未验证可直接复用
  - 复用状态：unknown；类型：model_weight

### datasets

- `code/selected_models/DeePathNet/data/graph_predefined/LCPathways/LCPathways_genes.csv`
  - 能力：LCPathways graph prior
  - 用途：DeePathNet 的 pathway/genes 图先验输入
  - 复用状态：partial；类型：unknown
- `code/selected_models/GENIUS/data/TCGA_cpg2gene_mapping.csv`
  - 能力：TCGA mapping tables
  - 用途：把 CpG/蛋白映射到 gene，用于 GENIUS 多组学对齐
  - 复用状态：partial；类型：unknown
- `code/selected_models/GENIUS/data/example_data/all_genes_ordered_by_chr_no_sex_chr.csv`
  - 能力：gene order reference
  - 用途：示例 gene 排序与输入对齐参考
  - 复用状态：partial；类型：unknown
- `code/selected_models/GNNSubNet/GNNSubNet/datasets/synthetic/FEATURES_synthetic.txt`
  - 能力：synthetic graph benchmark inputs
  - 用途：GNNSubNet synthetic 任务的特征、网络、target 与 mask 输入
  - 复用状态：unknown；类型：unknown
- `code/selected_models/PNet/data/pathway/ReactomePathways.gmt`
  - 能力：Reactome pathway resources
  - 用途：PNet 的 pathway 先验与关系图构建
  - 复用状态：partial；类型：unknown
- `code/selected_models/Pathformer/reference/Pathformer_pathway.txt`
  - 能力：Pathformer reference gene/pathway lists
  - 用途：Pathformer 的 pathway、基因筛选与 crosstalk network 参考
  - 复用状态：partial；类型：unknown

### evaluation

- `benchmark_pipeline.py`
  - 能力：benchmark aggregation and scoring
  - 用途：汇总不同方法在各任务上的预测与排名结果
  - 复用状态：ready_for_review；类型：code_entry
- `code/metrics.py`
  - 能力：shared metrics helpers
  - 用途：统一分类/生存等评估指标计算
  - 复用状态：ready_for_review；类型：code_entry
- `code/selected_models/CustOmics/src/metrics/classification.py`
  - 能力：classification metrics
  - 用途：CustOmics 分类任务指标实现
  - 复用状态：partial；类型：code_entry
- `code/selected_models/CustOmics/src/metrics/survival.py`
  - 能力：survival metrics
  - 用途：CustOmics 生存分析指标实现
  - 复用状态：partial；类型：code_entry
- `code/selected_models/Stabl/stabl/metrics.py`
  - 能力：stability metrics
  - 用途：Stabl 的性能/稳定性评估指标
  - 复用状态：partial；类型：code_entry
- `code/result_analysis/collect_pred_perf_tcga_RF_SVM_for_classifiability_test.py`
  - 能力：classifiability analysis
  - 用途：RF/SVM 可分性对照分析与结果收集
  - 复用状态：ready_for_review；类型：code_entry

### inference

- `code/run_model_tcga.py`
  - 能力：TCGA benchmark runner
  - 用途：主 benchmark 推理/预测入口之一
  - 复用状态：ready_for_review；类型：code_entry
- `code/run_model_intersim.py`
  - 能力：InterSIM benchmark runner
  - 用途：合成数据 InterSIM 的推理/预测入口之一
  - 复用状态：ready_for_review；类型：code_entry
- `code/selected_models/DeePathNet/scripts/deepathnet_independent_test.py`
  - 能力：DeePathNet independent test
  - 用途：DeePathNet 独立测试与预测
  - 复用状态：partial；类型：code_entry
- `code/selected_models/PNet/run_pnet.py`
  - 能力：PNet run wrapper
  - 用途：PNet 的预测/评估入口
  - 复用状态：partial；类型：code_entry
- `code/selected_models/Pathformer/Pathformer_code/run_pathformer_for_evalbk.py`
  - 能力：Pathformer evaluation runner
  - 用途：Pathformer 的评测型推理入口
  - 复用状态：partial；类型：code_entry
- `code/selected_models/GENIUS/Training/run_genius_for_bk.py`
  - 能力：GENIUS benchmark wrapper
  - 用途：为 benchmark 运行 GENIUS 的封装入口
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `benchmark_pipeline.py`
  - 能力：benchmark orchestration
  - 用途：统一调度多模型 benchmark、汇总预测与排序结果
  - 复用状态：ready_for_review；类型：code_entry
- `code/data_preprocessing/task_data_prep.py`
  - 能力：data normalization and task preparation
  - 用途：整理癌种/任务输入、对齐样本与 omics 变量
  - 复用状态：ready_for_review；类型：code_entry
- `code/result_analysis/collect_pred_perf_tcga.py`
  - 能力：result analysis and plotting
  - 用途：收集 TCGA 预测性能并支撑对比、稳定性、可分性分析
  - 复用状态：ready_for_review；类型：code_entry

### training

- `code/selected_models/GENIUS/Training/train.py`
  - 能力：GENIUS training entrypoint
  - 用途：主训练脚本，配合 Dataloader 和 model 定义训练 GENIUS
  - 复用状态：partial；类型：code_entry
- `code/selected_models/DeePathNet/scripts/deepathnet_cv.py`
  - 能力：DeePathNet training CV runner
  - 用途：DeePathNet 的交叉验证训练/评估流程
  - 复用状态：partial；类型：code_entry
- `code/selected_models/TMONet/train/train_tcga_pancancer_multitask.py`
  - 能力：TMONet multi-task training
  - 用途：TCGA/pancancer 多任务训练
  - 复用状态：partial；类型：code_entry
- `code/selected_models/MOGONET/train_test.py`
  - 能力：graph model train-test harness
  - 用途：图模型的训练-测试一体脚本
  - 复用状态：partial；类型：code_entry
- `code/selected_models/MOGLAM/train_test.py`
  - 能力：multi-omics train-test harness
  - 用途：多组学模型的训练-测试一体脚本
  - 复用状态：partial；类型：code_entry
- `code/selected_models/MORE/Code/train_test.py`
  - 能力：multi-omics train-test harness
  - 用途：多组学模型的训练-测试一体脚本
  - 复用状态：partial；类型：code_entry

## 使用限制

- 仅做静态审计，未执行仓库代码或测试
- 依赖未安装，运行时可用性与环境兼容性无法确认
- selected_models 多为第三方方法打包，许可与 notice 需要逐子目录核查
- 若干数据表/路径先验可能来自外部资源，静态路径存在不等于可复现来源已核实
- best_model.pb 只证明文件存在，不证明其为可直接复用的正式 checkpoint

## 仍未知

- DeePathNet、GENIUS、MOGLAM、MORE、MoAGLSA、PNet 等子树的上游来源与许可边界未逐一核实
- result/baseline_results 下的 pkl 更像已生成评测产物，是否由当前提交脚本生成未验证
- GNNSubNet synthetic 数据与 masks 的原始生成流程未从静态证据中确认
- GENIUS/Training/saved_models/best_model.pb 是否对应最终训练产物或仅示例文件尚不确定
- 部分 selected_models 目录缺少单独 LICENSE 的情况，需要额外上游审查

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
