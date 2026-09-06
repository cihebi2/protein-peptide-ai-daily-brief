# viko-3/zerogen

- **仓库：** [https://github.com/viko-3/zerogen](https://github.com/viko-3/zerogen)
- **固定 commit：** `162b81cff087e9545e895f828b884d553c09efd7`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 28

## 仓库摘要

仓库静态上可见 ZeroGEN 的核心模型、训练/采样、评估与预处理链路，但未见 checkpoint 与顶层 LICENSE，复用边界仍需保守处理。

## 可复用模块与资源

### datasets

- `preprocess/prot_cluster/_protein_cluster_dict_0.3`
  - 能力：蛋白聚类字典资源
  - 用途：0.3/0.4/0.5/0.6 阈值聚类查表，服务于蛋白预处理与去冗余。
  - 复用状态：blocked；类型：unknown
- `modeling_smi/metrics/SA_Score/sascorer.py`
  - 能力：SA Score 资源
  - 用途：可合成性评分查表与实现。
  - 复用状态：blocked；类型：code_entry
- `modeling_smi/metrics/NP_Score/npscorer.py`
  - 能力：NP Score 资源
  - 用途：natural product 相似度评分查表与实现。
  - 复用状态：blocked；类型：code_entry
- `modeling_smi/metrics/mcf.csv`
  - 能力：分子过滤规则表
  - 用途：PAINS/MCF 过滤规则数据。
  - 复用状态：blocked；类型：unknown

### evaluation

- `modeling_smi/metrics/metrics.py`
  - 能力：分子评估封装
  - 用途：组织分子性质与过滤指标的评估流程。
  - 复用状态：blocked；类型：code_entry
- `modeling_smi/metrics/utils.py`
  - 能力：评估工具函数
  - 用途：支撑分子评估的公共工具。
  - 复用状态：blocked；类型：code_entry
- `modeling_bert/tape/metrics.py`
  - 能力：TAPE 评估指标
  - 用途：蛋白侧任务的评估指标实现。
  - 复用状态：blocked；类型：code_entry
- `modeling_smi/metrics/SA_Score/sascorer.py`
  - 能力：SA Score 计算器
  - 用途：计算分子可合成性分数。
  - 复用状态：blocked；类型：code_entry
- `modeling_smi/metrics/NP_Score/npscorer.py`
  - 能力：NP Score 计算器
  - 用途：计算 natural product 相似度分数。
  - 复用状态：blocked；类型：code_entry

### inference

- `DeepTarget_scripts/sample.py`
  - 能力：采样/生成推断入口
  - 用途：从训练好的模型执行样本生成或采样。
  - 复用状态：blocked；类型：code_entry
- `scripts/sample.py`
  - 能力：采样/生成推断入口
  - 用途：另一套样本生成或推断脚本。
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `DeepTarget/dataset/dataset.py`
  - 能力：样本与数据加载
  - 用途：构造 DeepTarget 训练/推断所需样本对象。
  - 复用状态：blocked；类型：code_entry
- `modeling_smi/dataset/dataset.py`
  - 能力：样本与数据加载
  - 用途：构造 small-molecule 侧的数据读取与样本组织。
  - 复用状态：blocked；类型：code_entry
- `modeling_bert/tape/datasets.py`
  - 能力：TAPE 序列数据加载
  - 用途：提供 protein language model 相关数据读取接口。
  - 复用状态：blocked；类型：code_entry
- `DeepTarget/modeling/model.py`
  - 能力：核心条件生成模型
  - 用途：定义 ZeroGEN 主体模型与条件生成逻辑。
  - 复用状态：blocked；类型：code_entry
- `modeling_smi/transformer/model.py`
  - 能力：分子 transformer 模型
  - 用途：定义 small-molecule transformer 架构。
  - 复用状态：blocked；类型：code_entry
- `modeling_bert/tape/models/modeling_bert.py`
  - 能力：蛋白语言模型 backbone
  - 用途：提供 protein sequence 表征编码与下游适配。
  - 复用状态：blocked；类型：code_entry
- `preprocess/prot_cluster.py`
  - 能力：蛋白聚类预处理
  - 用途：按阈值生成或使用蛋白聚类字典，用于去冗余/划分。
  - 复用状态：blocked；类型：code_entry
- `preprocess/prot_distance.py`
  - 能力：蛋白距离计算
  - 用途：计算蛋白序列间距离/相似度特征。
  - 复用状态：blocked；类型：code_entry
- `preprocess/prot_ssw.py`
  - 能力：SSW 比对流程
  - 用途：封装序列比对与相关预处理步骤。
  - 复用状态：blocked；类型：code_entry
- `preprocess/ssw_lib.py`
  - 能力：SSW 底层封装
  - 用途：连接本地 SSW 实现，支撑蛋白序列比对。
  - 复用状态：blocked；类型：code_entry
- `preprocess/libssw.so`
  - 能力：SSW native binary
  - 用途：本地二进制比对库。
  - 复用状态：blocked；类型：unknown

### training

- `DeepTarget_scripts/train.py`
  - 能力：训练入口
  - 用途：ZeroGEN/DeepTarget 训练启动脚本。
  - 复用状态：blocked；类型：code_entry
- `scripts/train.py`
  - 能力：训练入口
  - 用途：另一套训练启动脚本或包装入口。
  - 复用状态：blocked；类型：code_entry
- `DeepTarget_scripts/pretrain_lm.py`
  - 能力：语言模型预训练入口
  - 用途：预训练 protein language model 的脚本。
  - 复用状态：blocked；类型：code_entry
- `DeepTarget/modeling/trainer.py`
  - 能力：训练循环
  - 用途：封装 DeepTarget 的训练流程与优化步骤。
  - 复用状态：blocked；类型：code_entry
- `modeling_smi/transformer/trainer.py`
  - 能力：训练循环
  - 用途：封装 small-molecule transformer 的训练流程。
  - 复用状态：blocked；类型：code_entry
- `modeling_bert/tape/training.py`
  - 能力：TAPE 训练框架
  - 用途：蛋白语言模型相关的训练框架。
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态审计，未执行代码、未安装依赖、未运行测试。
- 未见可确认的 checkpoint 文件或权重产物；tracked path 存在不代表可复现。
- submodules 未初始化，部分大文件可能是 promisor/占位内容。
- 仓库级许可未找到，直接复用需先补齐许可核验。

## 仍未知

- `DeepTarget_scripts/train.py` 与 `scripts/train.py` 的主入口角色无法仅凭目录结构确认。
- `preprocess/prot_cluster/_protein_cluster_dict_*` 的生成来源与再分发许可未核实。
- `modeling_smi/metrics/SA_Score`、`NP_Score`、`mcf.csv`、`wehi_pains.csv` 是否为完整 vendored 第三方资源仍需上游比对。
- `modeling_bert/tape` 是否为完整 vendored 副本、以及其具体上游版本未核实。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
