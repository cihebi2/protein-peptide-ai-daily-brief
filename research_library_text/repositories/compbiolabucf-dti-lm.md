# compbiolabucf/dti-lm

- **仓库：** [https://github.com/compbiolabucf/dti-lm](https://github.com/compbiolabucf/dti-lm)
- **固定 commit：** `ed71e811fab94a6eb844e2b1faa0d8edfe12b63b`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 33

## 仓库摘要

仓库主要提供 DTI 预测管线：包含 MLP/GAT 模型、ESM/ChemBERT 特征提取、四套数据集的 datamodule 与训练/调参配置；未见独立推理或评测入口，且未发现 LICENSE，复用边界需谨慎核验。

## 可复用模块与资源

### checkpoints

- `datasets/serialized/bindingDB_Kd_ESM.pt`
  - 能力：BindingDB Kd 序列化资产
  - 用途：serialized embedding/checkpoint-like artifact for BindingDB Kd experiments; exact contents unverified
  - 复用状态：unknown；类型：model_weight
- `datasets/serialized/bindingDB_Kd_PubChem10M.pt`
  - 能力：BindingDB Kd 序列化资产
  - 用途：serialized embedding/checkpoint-like artifact for BindingDB Kd experiments; exact contents unverified
  - 复用状态：unknown；类型：model_weight

### datasets

- `datasets/bindingDB/dummy.txt`
  - 能力：BindingDB 数据目录占位
  - 用途：placeholder marker only; no raw bundled dataset evidence
  - 复用状态：unknown；类型：unknown
- `configs/datamodule/bindingDB.yaml`
  - 能力：BindingDB 数据模块配置
  - 用途：dataset path/split wiring for BindingDB
  - 复用状态：blocked；类型：config
- `configs/datamodule/drugbank.yaml`
  - 能力：DrugBank 数据模块配置
  - 用途：dataset path/split wiring for DrugBank
  - 复用状态：blocked；类型：config
- `configs/datamodule/luo.yaml`
  - 能力：Luo 数据模块配置
  - 用途：dataset path/split wiring for Luo benchmark
  - 复用状态：blocked；类型：config
- `configs/datamodule/yamanishi.yaml`
  - 能力：Yamanishi 数据模块配置
  - 用途：dataset path/split wiring for Yamanishi benchmark
  - 复用状态：blocked；类型：config

### evaluation

- `configs/best_params/random_balanced.yaml`
  - 能力：随机/平衡基线评测配置
  - 用途：tuned benchmark setting for random balanced evaluation
  - 复用状态：blocked；类型：config
- `configs/best_params/cold_target_balanced.yaml`
  - 能力：冷靶点评测配置
  - 用途：tuned benchmark setting for cold-target evaluation
  - 复用状态：blocked；类型：config
- `configs/best_params/yamanishi.yaml`
  - 能力：Yamanishi 评测配置
  - 用途：tuned benchmark setting for Yamanishi evaluation
  - 复用状态：blocked；类型：config

### inference

- `configs/module/MLP.yaml`
  - 能力：MLP 推理配置
  - 用途：model structure/config for inference-time scoring
  - 复用状态：blocked；类型：config
- `configs/module/GAT.yaml`
  - 能力：GAT 推理配置
  - 用途：model structure/config for inference-time scoring
  - 复用状态：blocked；类型：config
- `configs/module/yamanishi.yaml`
  - 能力：Yamanishi MLP 模型配置
  - 用途：dataset-specific model config usable for inference wiring
  - 复用状态：blocked；类型：config
- `configs/module/yamanishi_GAT.yaml`
  - 能力：Yamanishi GAT 模型配置
  - 用途：dataset-specific model config usable for inference wiring
  - 复用状态：blocked；类型：config

### reusable_assets

- `module/MLP.py`
  - 能力：DTI 打分模型实现
  - 用途：MLP-based interaction scorer for drug-target pair prediction
  - 复用状态：blocked；类型：code_entry
- `module/GAT.py`
  - 能力：DTI 打分模型实现
  - 用途：GAT-based interaction scorer for drug-target pair prediction
  - 复用状态：blocked；类型：code_entry
- `module/featurizer/prot_featurizer/esm_featurizer.py`
  - 能力：蛋白特征提取
  - 用途：ESM embedding wrapper for protein sequences
  - 复用状态：blocked；类型：code_entry
- `module/featurizer/drug_featurizer/chembert_featurizer.py`
  - 能力：分子特征提取
  - 用途：ChemBERT embedding wrapper for drug representations
  - 复用状态：blocked；类型：code_entry
- `datamodule/dataloader.py`
  - 能力：数据装载助手
  - 用途：generic dataloader for benchmark datasets
  - 复用状态：blocked；类型：code_entry
- `datamodule/dataloader_GAT.py`
  - 能力：GAT 数据装载助手
  - 用途：GAT-oriented dataloader variant
  - 复用状态：blocked；类型：code_entry
- `module/featurizer/prot_featurizer/load_data.py`
  - 能力：蛋白数据读取助手
  - 用途：protein-side data loading helper for featurization pipeline
  - 复用状态：blocked；类型：code_entry
- `utils/preprocess.py`
  - 能力：预处理管线
  - 用途：dataset preprocessing and preparation pipeline
  - 复用状态：blocked；类型：code_entry
- `similarity.py`
  - 能力：相似性分析/辅助计算
  - 用途：similarity computation helper likely used for split or analysis
  - 复用状态：blocked；类型：code_entry

### training

- `configs/preprocess/bindingDB.yaml`
  - 能力：BindingDB 预处理配置
  - 用途：BindingDB preprocessing recipe
  - 复用状态：blocked；类型：config
- `configs/preprocess/drugbank.yaml`
  - 能力：DrugBank 预处理配置
  - 用途：DrugBank preprocessing recipe
  - 复用状态：blocked；类型：config
- `configs/preprocess/luo.yaml`
  - 能力：Luo 预处理配置
  - 用途：Luo preprocessing recipe
  - 复用状态：blocked；类型：config
- `configs/preprocess/yamanishi.yaml`
  - 能力：Yamanishi 预处理配置
  - 用途：Yamanishi preprocessing recipe
  - 复用状态：blocked；类型：config
- `configs/bindingDB_train_MLP.yaml`
  - 能力：BindingDB+MLP 训练配置
  - 用途：training recipe for BindingDB with MLP backbone
  - 复用状态：blocked；类型：config
- `configs/bindingDB_train_GAT.yaml`
  - 能力：BindingDB+GAT 训练配置
  - 用途：training recipe for BindingDB with GAT backbone
  - 复用状态：blocked；类型：config
- `configs/drugbank_train_MLP.yaml`
  - 能力：DrugBank+MLP 训练配置
  - 用途：training recipe for DrugBank with MLP backbone
  - 复用状态：blocked；类型：config
- `configs/drugbank_train_GAT.yaml`
  - 能力：DrugBank+GAT 训练配置
  - 用途：training recipe for DrugBank with GAT backbone
  - 复用状态：blocked；类型：config
- `configs/luo_train.yaml`
  - 能力：Luo 训练配置
  - 用途：training recipe for Luo benchmark
  - 复用状态：blocked；类型：config
- `configs/yamanishi_train.yaml`
  - 能力：Yamanishi 训练配置
  - 用途：training recipe for Yamanishi benchmark
  - 复用状态：blocked；类型：config

## 使用限制

- 仅做静态清点，未运行仓库代码
- 依赖未安装，无法验证可执行性
- 测试未运行，无法证明复现结果
- `.pt` 文件内容与来源未核验，可能是缓存/特征/权重
- tracked `.pyc` 仅反映编译产物存在，不作为源码贡献证据

## 仍未知

- run.py 是否为真实训练/推理入口，冻结清单未将其单独归类
- 模块与配置文件的具体超参、指标和结果未逐文件读取
- `datasets/serialized/*.pt` 的精确语义（checkpoint 还是中间特征）不明
- README 中的项目说明未通过文件内容核验，无法补充方法细节

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
