# marsico-lab/transfactor

- **仓库：** [https://github.com/marsico-lab/transfactor](https://github.com/marsico-lab/transfactor)
- **固定 commit：** `b907a87dee6dbf39e240e3ed55aec700895409f5`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 25

## 仓库摘要

该仓库围绕 TransFactor 与 baseline 模型提供数据预处理、训练/调参、推理、benchmark 和富集分析代码；静态检查未见 checkpoint。

## 可复用模块与资源

### datasets

- `data/uniprot-9606_proteome_human_reviewed_canonical_isoforms_191008.fasta`
  - 能力：human proteome 输入序列
  - 用途：第三方 human proteome 序列输入，供特征提取或候选筛选使用。
  - 复用状态：partial；类型：unknown
- `data/mmseqs_clusters/seqs_and_labels_cov_0.1_min_seq_id_0.1_e_0.001_cluster.tsv`
  - 能力：MMseqs 聚类结果/标签表
  - 用途：序列聚类与标签/分组支持，可能用于 split 或 cluster purity 分析。
  - 复用状态：partial；类型：unknown
- `data/training_data.pickle`
  - 能力：训练集序列与标签容器
  - 用途：序列与标签的序列化训练数据容器。
  - 复用状态：partial；类型：unknown
- `data/all_with_candidates.pickle`
  - 能力：候选集合容器
  - 用途：候选项与训练/评估相关的序列化容器。
  - 复用状态：partial；类型：unknown

### evaluation

- `manuscript/benchmark/Benchmarking Figures and Values.ipynb`
  - 能力：benchmark 汇总与制图
  - 用途：汇总 benchmark 指标并生成图表/数值结果。
  - 复用状态：partial；类型：unknown
- `manuscript/benchmark/prediction_values_all_models.csv.zip`
  - 能力：benchmark 预测值汇总表
  - 用途：保存多模型预测值的汇总表，供 benchmark notebook 读取或比较。
  - 复用状态：partial；类型：unknown
- `manuscript/Figures/Frozen backbone predictions.ipynb`
  - 能力：冻结 backbone 预测分析
  - 用途：分析 frozen backbone 条件下的预测表现。
  - 复用状态：partial；类型：unknown
- `manuscript/Figures/Supp. Figure 2 and 3 - Cluster purity.ipynb`
  - 能力：cluster purity 分析
  - 用途：评估序列聚类纯度或相关分组质量。
  - 复用状态：partial；类型：unknown
- `manuscript/Figures/Supp. Table 3 - Experimental screen performance.ipynb`
  - 能力：实验筛选性能分析
  - 用途：整理实验筛选性能对照表。
  - 复用状态：partial；类型：unknown
- `manuscript/Figures/Supp. Table 8 - Sequence Truncation at 2048.ipynb`
  - 能力：序列截断敏感性分析
  - 用途：评估序列截断到 2048 的影响。
  - 复用状态：partial；类型：unknown
- `manuscript/go_term_enrichment/Plot DAVID gene enrichment.ipynb`
  - 能力：DAVID/GO 富集绘图
  - 用途：绘制 GO/DAVID 富集结果。
  - 复用状态：partial；类型：unknown

### inference

- `predict.py`
  - 能力：预测入口脚本
  - 用途：对新序列运行已定义模型并输出预测结果。
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `transfactor_model.py`
  - 能力：TransFactor 主模型结构
  - 用途：定义主模型网络与前向逻辑，支撑 host-factor 预测。
  - 复用状态：ready_for_review；类型：code_entry
- `baseline_model.py`
  - 能力：baseline 对照模型结构
  - 用途：定义 baseline 网络，实现对照实验。
  - 复用状态：ready_for_review；类型：code_entry
- `dataloader.py`
  - 能力：数据加载与 batch 组织
  - 用途：把序列、标签或中间 pickle 数据组织成训练/推理输入。
  - 复用状态：ready_for_review；类型：code_entry
- `utils.py`
  - 能力：通用工具函数
  - 用途：支撑训练、评估或数据处理的公共函数集合。
  - 复用状态：ready_for_review；类型：code_entry
- `configs/optuna_transfactor.py`
  - 能力：TransFactor 超参数配置
  - 用途：定义 TransFactor 的 Optuna 搜索空间和训练配置。
  - 复用状态：ready_for_review；类型：code_entry
- `configs/optuna_baseline.py`
  - 能力：baseline 超参数配置
  - 用途：定义 baseline 的 Optuna 搜索空间和训练配置。
  - 复用状态：ready_for_review；类型：code_entry
- `data/Preprocessing.ipynb`
  - 能力：预处理流程记录
  - 用途：记录数据预处理、清洗与中间特征生成流程。
  - 复用状态：partial；类型：unknown
- `requirements.txt`
  - 能力：Python 依赖清单
  - 用途：冻结 Python 依赖版本，便于环境复现。
  - 复用状态：partial；类型：unknown
- `environment.yml`
  - 能力：Conda 环境规格
  - 用途：提供 Conda 环境定义。
  - 复用状态：partial；类型：config

### training

- `baseline_train.py`
  - 能力：baseline 训练脚本
  - 用途：训练 baseline 模型。
  - 复用状态：ready_for_review；类型：code_entry
- `transfactor_train.py`
  - 能力：TransFactor 训练脚本
  - 用途：训练 TransFactor 主模型。
  - 复用状态：ready_for_review；类型：code_entry
- `baseline_optuna.py`
  - 能力：baseline 超参数搜索脚本
  - 用途：执行 baseline 的 Optuna 搜索。
  - 复用状态：ready_for_review；类型：code_entry
- `transfactor_optuna.py`
  - 能力：TransFactor 超参数搜索脚本
  - 用途：执行 TransFactor 的 Optuna 搜索。
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态审查；未安装依赖、未执行训练/推理/测试。
- 未发现 tracked checkpoint 权重或可恢复模型文件。
- notebooks、zip 表格与 pickle 数据仅作静态证据，未运行验证。
- 数据产物的生成链路与具体 schema 未完全展开。
- 仓库级 MIT 许可证不自动覆盖第三方数据源。

## 仍未知

- training_data.pickle 与 all_with_candidates.pickle 的具体内容与 schema 未见。
- data/uniprot-9606_proteome_human_reviewed_canonical_isoforms_191008.fasta 的上游许可与获取方式未在仓库内展开。
- baseline_train.py / transfactor_train.py 是否为唯一训练入口，静态清单无法最终确认。
- 仓库外是否存在额外 checkpoint 或模型发布未在冻结清单中体现。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
