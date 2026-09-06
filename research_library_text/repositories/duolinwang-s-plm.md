# duolinwang/S-PLM

- **仓库：** [https://github.com/duolinwang/S-PLM](https://github.com/duolinwang/S-PLM)
- **固定 commit：** `6fa9398d59b0408a24f1db5109406e167305b6ee`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 26

## 仓库摘要

仓库围绕 S-PLM 提供主模型、数据管线、任务训练脚本与序列嵌入生成工具；冻结清单里可确认代码层 MIT 许可，但数据集与预训练/检查点边界仍需单独核验。

## 可复用模块与资源

### checkpoints

- `esm_adapterH/pretrained.py`
  - 能力：预训练/检查点注册入口
  - 用途：定义或加载预训练模型名称与权重入口；未见二进制权重文件
  - 复用状态：partial；类型：code_entry

### datasets

- `dataset/Rep_subfamily_basedon_S40pdb.fa`
  - 能力：结构/序列预训练语料
  - 用途：FASTA 形式的代表性子家族序列集合
  - 复用状态：partial；类型：unknown
- `dataset/kinase_alllabels.fa`
  - 能力：kinase 标注序列
  - 用途：kinase 相关标签序列资源
  - 复用状态：partial；类型：unknown
- `SPLM_Data/EC_data/EC_train.csv`
  - 能力：EC 任务数据包
  - 用途：EC 的 train/valid/test 与注释表
  - 复用状态：partial；类型：unknown
- `SPLM_Data/GO_data/GO_train.csv`
  - 能力：GO 任务数据包
  - 用途：GO 的 train/valid/test 与注释表
  - 复用状态：partial；类型：unknown
- `SPLM_Data/Fold_data/train.csv`
  - 能力：Fold 任务数据包
  - 用途：Fold 的 train/valid/test 与多个 holdout 划分
  - 复用状态：partial；类型：unknown
- `SPLM_Data/SS_data/train.csv`
  - 能力：SS 任务数据包
  - 用途：secondary structure 的 train/valid/test 划分
  - 复用状态：partial；类型：unknown
- `SPLM_Data/Enzyme_Reaction_data/train.csv`
  - 能力：Enzyme Reaction 任务数据包
  - 用途：enzyme reaction 的 train/validation/test 划分
  - 复用状态：partial；类型：unknown
- `dataset/GPS5.0_homo_hasPK_with_kinasedomain.txt`
  - 能力：kinase 辅助表
  - 用途：含 kinase domain 的辅助样本/索引表
  - 复用状态：partial；类型：unknown

### evaluation

- `SPLM_Data/EC_data/EC_test.csv`
  - 能力：EC 测试划分
  - 用途：EC 任务测试/评估输入
  - 复用状态：partial；类型：unknown
- `SPLM_Data/GO_data/GO_test.csv`
  - 能力：GO 测试划分
  - 用途：GO 任务测试/评估输入
  - 复用状态：partial；类型：unknown
- `SPLM_Data/Fold_data/test_family_holdout.csv`
  - 能力：Fold holdout 评估划分
  - 用途：Fold 评估协议中的 family holdout
  - 复用状态：partial；类型：unknown
- `SPLM_Data/SS_data/test.csv`
  - 能力：SS 测试划分
  - 用途：secondary structure 任务测试/评估输入
  - 复用状态：partial；类型：unknown
- `SPLM_Data/Enzyme_Reaction_data/test.csv`
  - 能力：Enzyme Reaction 测试划分
  - 用途：enzyme reaction 任务测试/评估输入
  - 复用状态：partial；类型：unknown

### inference

- `utils/generate_seq_embedding.py`
  - 能力：序列 embedding 生成
  - 用途：批量生成 sequence embedding 供下游任务或检索使用
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `model.py`
  - 能力：主模型封装
  - 用途：组织 S-PLM 的前向、任务接口和核心建模逻辑
  - 复用状态：ready_for_review；类型：code_entry
- `data.py`
  - 能力：通用数据管线
  - 用途：读取序列、标签与批处理
  - 复用状态：ready_for_review；类型：code_entry
- `cath_with_seq.py`
  - 能力：CATH/序列辅助构造
  - 用途：构造或整理带序列信息的辅助样本
  - 复用状态：ready_for_review；类型：code_entry
- `esm_adapterH/adapter.py`
  - 能力：adapter tuning 模块
  - 用途：实现 adapterH 相关参数高效微调层
  - 复用状态：partial；类型：code_entry
- `esm_adapterH/prompt_tuning.py`
  - 能力：prompt tuning 模块
  - 用途：实现软提示/提示向量参数化
  - 复用状态：partial；类型：code_entry
- `esm_adapterH/model/esm2.py`
  - 能力：backbone 兼容层
  - 用途：提供 ESM2 相关 backbone 适配/前向实现
  - 复用状态：partial；类型：code_entry

### training

- `train_ec.py`
  - 能力：EC 训练入口
  - 用途：EC 任务训练；配置族包含 ec_config_adapterH_adapterH.yaml、ec_config_adapterH_finetune.yaml、ec_config_adapterH_lora.yaml
  - 复用状态：ready_for_review；类型：code_entry
- `train_go.py`
  - 能力：GO 训练入口
  - 用途：GO 任务训练；配置族覆盖 bp/cc/mf 的 adapterH、finetune、lora 变体
  - 复用状态：ready_for_review；类型：code_entry
- `train_fold.py`
  - 能力：Fold 训练入口
  - 用途：Fold 任务训练；包含 freeze 与 finetune 两类配置
  - 复用状态：ready_for_review；类型：code_entry
- `train_ss.py`
  - 能力：SS 训练入口
  - 用途：secondary structure 任务训练；包含 adapterH、finetune、lora 配置
  - 复用状态：ready_for_review；类型：code_entry
- `train_er.py`
  - 能力：Enzyme Reaction 训练入口
  - 用途：enzyme reaction 任务训练；包含 freeze 与 finetune 配置
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态审查，未安装依赖、未运行训练/推理/评测。
- 仓库存在多组数据划分，但未见独立 evaluation harness，指标实现可能嵌在训练脚本中。
- 未见可核验的二进制 checkpoint 权重；`esm_adapterH/pretrained.py` 仅像加载/注册入口。
- bundled 数据与模型相关资产未见逐文件许可标注，复用边界需要额外核验。

## 仍未知

- `esm_adapterH` 内部是否为 vendored/改写自第三方 ESM 代码，静态清单无法判定。
- `dataset/*.fa` 与 `SPLM_Data/*` 是否完全属于项目自建数据，还是来源于外部基准集合，许可未明。
- 训练与评测是否依赖外部下载的权重或隐藏文件，当前冻结清单未能证明。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
