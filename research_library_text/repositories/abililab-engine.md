# ABILiLab/ENGINE

- **仓库：** [https://github.com/ABILiLab/ENGINE](https://github.com/ABILiLab/ENGINE)
- **固定 commit：** `c6d58ea10e104661020b6620a89a41e94a6a929a`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 18

## 仓库摘要

仓库提供基于 EGNN 的蛋白功能/定位/突变效应预测代码，包含数据加载、训练辅助、推理与评估模块；未见可复用 checkpoint，数据与特征资产许可边界仍不完整。

## 可复用模块与资源

### datasets

- `Dataset/nrPDB-GO_2019.06.18_sequences.fasta`
  - 能力：protein sequence corpus
  - 用途：训练/验证/测试样本的序列输入
  - 复用状态：partial；类型：unknown
- `Dataset/nrPDB-GO_2019.06.18_annot.tsv`
  - 能力：GO annotation labels
  - 用途：GO 标注与监督标签
  - 复用状态：partial；类型：unknown
- `Dataset/nrPDB-GO_2019.06.18_train.txt`
  - 能力：dataset split lists
  - 用途：train/valid/test 划分清单
  - 复用状态：partial；类型：unknown
- `Features/esm-c/4FEZ-A.pkl`
  - 能力：precomputed ESM-C feature cache
  - 用途：示例蛋白的 ESM-C 特征；同目录和 GUI/Features 还有 4RH6-A、6ASO-C 等副本
  - 复用状态：partial；类型：unknown
- `Features/foldseek_3di_token/4FEZ-A.3di`
  - 能力：Foldseek 3Di token cache
  - 用途：示例蛋白的 3Di token/DB type 特征
  - 复用状态：partial；类型：unknown
- `infer_temp/4FEZ-A.pdb`
  - 能力：demo structure inputs
  - 用途：GUI/推理演示的结构输入样例；还有 4RH6-A、6ASO-C
  - 复用状态：partial；类型：unknown

### evaluation

- `src/metrics.py`
  - 能力：task metrics module
  - 用途：计算分类/回归评估指标
  - 复用状态：ready_for_review；类型：code_entry

### inference

- `infer_main.py`
  - 能力：CLI inference
  - 用途：从输入结构/特征运行推理并写出结果
  - 复用状态：ready_for_review；类型：code_entry
- `infer_utils.py`
  - 能力：inference utilities
  - 用途：输入标准化、特征拼装和输出整理
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `src/Module/egnn/egnn_pytorch.py`
  - 能力：EGNN backbone implementation
  - 用途：实现等变图神经网络层，供蛋白表示学习主干调用
  - 复用状态：ready_for_review；类型：code_entry
- `model.py`
  - 能力：model assembly and task heads
  - 用途：把 EGNN 与蛋白功能预测任务头组合成可推理模型
  - 复用状态：ready_for_review；类型：code_entry
- `src/Dataset/protein_dataset.py`
  - 能力：dataset loading
  - 用途：读取 protein/localization/mutant 相关样本与特征
  - 复用状态：ready_for_review；类型：code_entry
- `src/utils/train_utils.py`
  - 能力：training helpers
  - 用途：提供训练/验证循环与优化辅助
  - 复用状态：ready_for_review；类型：code_entry
- `ESM3C_feature_extractor.py`
  - 能力：feature extraction
  - 用途：生成 ESM3C 特征文件供下游输入
  - 复用状态：ready_for_review；类型：code_entry
- `infer_main.py`
  - 能力：CLI inference
  - 用途：从输入结构/特征运行批量推理并写出结果
  - 复用状态：ready_for_review；类型：code_entry
- `infer_utils.py`
  - 能力：inference utilities
  - 用途：输入标准化、特征拼装和输出整理
  - 复用状态：ready_for_review；类型：code_entry

### training

- `src/Egnnconfig/egnn.yaml`
  - 能力：task-specific training configs
  - 用途：配置 egnn_bp/cc/mf/mutant 等任务的训练超参
  - 复用状态：partial；类型：config
- `src/utils/train_utils.py`
  - 能力：training helper routines
  - 用途：提供训练/验证循环与优化辅助
  - 复用状态：partial；类型：code_entry

## 使用限制

- 仅做静态盘点，未执行代码、训练或测试。
- 未发现可复用的模型 checkpoint；`model/a`、`GUI/model/a`、`__pycache__` 之类路径不足以证明存在权重文件。
- `requirements.txt` 与 `GUI/requirements.txt` 已见，但依赖未安装，第三方许可证未逐项核对。
- `GUI/` 与 root/`src/` 存在镜像副本，无法仅凭静态清单确认唯一维护来源。

## 仍未知

- `Features/esm-c/*.pkl` 与 `Features/foldseek_3di_token/*` 是否由仓库生成还是外部下载未证实。
- `Dataset/nrPDB-GO_2019.06.18_*` 的原始来源、再许可与发布边界未单独记录。
- 训练入口虽有配置和 helper，但没有被静态清单标记为明确 training_entrypoint，完整训练流程仍不清楚。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
