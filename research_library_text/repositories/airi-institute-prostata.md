# AIRI-Institute/PROSTATA

- **仓库：** [https://github.com/AIRI-Institute/PROSTATA](https://github.com/AIRI-Institute/PROSTATA)
- **固定 commit：** `81b109f155ddde67b778fec169d1048e6a060213`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** Apache-2.0
- **资产记录数：** 16

## 仓库摘要

该仓库与 PROSTATA 论文直接对应，静态清单显示其核心是蛋白稳定性评估工作流：数据生成与拆分、fold 测试、跨数据集 ensemble 推理、最终集成训练，以及大量 CSV/PDB/mut 资产；未发现可确认的 checkpoint，数据与模型产物的独立许可也未被静态证明。

## 可复用模块与资源

### datasets

- `DATA/megadataset/train.csv.gz`
  - 能力：主训练/验证/测试数据
  - 用途：megadataset 的训练分片；同目录还有 val/test
  - 复用状态：ready_for_review；类型：unknown
- `DATASETS/S2648.csv`
  - 能力：基准评测表
  - 用途：稳定性评测基准之一；同目录还有 S3421/S3488/s669/ssym/myoglobin/p53/L20 等表
  - 复用状态：ready_for_review；类型：unknown
- `PDB/1UBQ.pdb`
  - 能力：结构输入库
  - 用途：蛋白结构输入；仓库内共有大量 PDB 文件
  - 复用状态：partial；类型：unknown
- `DATA/varibench/vb1423_TS_0.mut`
  - 能力：突变定义与交叉验证切分
  - 用途：Varibench 风格的突变定义；同类文件用于 folds/variant split
  - 复用状态：ready_for_review；类型：unknown
- `DATA/dataset_our_w_clusters_v2.5.pkl`
  - 能力：聚类/索引中间产物
  - 用途：数据分组/聚类缓存；静态清单无法确认是否 checkpoint
  - 复用状态：partial；类型：unknown
- `DATASETS/case_study_dimer_test.csv`
  - 能力：案例研究输入
  - 用途：case study 评测输入；同目录还有 gem/transmembrane 版本及 labels
  - 复用状态：ready_for_review；类型：unknown

### evaluation

- `02.test_models_by_folds.ipynb`
  - 能力：按 fold 测试
  - 用途：交叉验证/折级别评估
  - 复用状态：partial；类型：unknown
- `PROSTATA_experiments_pearson.log`
  - 能力：相关系数日志
  - 用途：记录 Pearson 相关系数式评估结果
  - 复用状态：ready_for_review；类型：unknown
- `ACDC_FOLDS/0_test_preds.csv`
  - 能力：fold 级预测表
  - 用途：保存 fold 评估预测
  - 复用状态：ready_for_review；类型：unknown

### inference

- `03.test_models_on_other_datasets_ensemble.ipynb`
  - 能力：跨数据集 ensemble 推理
  - 用途：在 other datasets 上做 ensemble 预测
  - 复用状态：partial；类型：unknown
- `PROSTATA_tool.ipynb`
  - 能力：交互式推理/工具
  - 用途：工具型推理入口或演示
  - 复用状态：partial；类型：unknown
- `PROSTATA_EXPERIMENTS/train_S2648.S2648_r.Vb.Vb_r_test_myoglobin.myoglobin_r/test_myoglobin_with_predictions.csv`
  - 能力：已保存预测输出
  - 用途：推理结果落盘
  - 复用状态：ready_for_review；类型：unknown

### reusable_assets

- `environment.yml`
  - 能力：依赖环境声明
  - 用途：锁定 Python/包依赖，供静态审查和后续手工复用
  - 复用状态：partial；类型：config

### training

- `00.generate_datasets.ipynb`
  - 能力：数据生成与整理
  - 用途：生成/整理实验数据
  - 复用状态：partial；类型：unknown
- `01.add_megadataset_and_split_on_train_test_sets.ipynb`
  - 能力：megadataset 扩展与拆分
  - 用途：把 megadataset 纳入训练/测试划分
  - 复用状态：partial；类型：unknown
- `04.train_final_ensemble.ipynb`
  - 能力：最终集成训练
  - 用途：训练 final ensemble
  - 复用状态：partial；类型：unknown

## 使用限制

- 仅做静态审计，未运行代码、测试、训练或推理。
- 依赖未安装，无法验证 environment.yml 是否可直接复现。
- 未读取 notebook/CSV/PDB 内容，只能依据路径命名判断用途。
- 路径存在不等于可复现；尤其无法证明 checkpoint 或模型权重可用。

## 仍未知

- `.pkl` 文件更像数据聚类/索引中间产物，但不能排除被当作 checkpoint 的可能。
- 大量 CSV/PDB/mut 资产的上游来源与授权条款在冻结清单中未显式给出。
- `PROSTATA_tool.ipynb` 的具体运行方式与是否包含真实推理逻辑，静态清单无法确认。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
