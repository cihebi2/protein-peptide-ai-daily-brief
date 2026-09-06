# biochunan/asep-dataset

- **仓库：** [https://github.com/biochunan/asep-dataset](https://github.com/biochunan/asep-dataset)
- **固定 commit：** `2b653d7bb5aea57c156b90297e3adf6afa290452`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 23

## 仓库摘要

仓库是 AsEP 抗体特异性表位预测基准与实验代码合集，含训练/推理/评测脚本和一个 LoRA checkpoint；冻结清单未见完整内置数据，代码为 MIT，但数据与模型产物的独立许可边界未明。

## 可复用模块与资源

### checkpoints

- `experiments/ESMBind/lora_binding_sites/best_model_esm2_t12_35M_lora_2023-11-09_12-02-07/adapter_model.safetensors`
  - 能力：adapter weights
  - 用途：LoRA 适配器权重（model_weight）
  - 复用状态：partial；类型：model_weight
- `experiments/ESMBind/lora_binding_sites/best_model_esm2_t12_35M_lora_2023-11-09_12-02-07/adapter_config.json`
  - 能力：adapter config
  - 用途：记录 LoRA 结构与超参数（config）
  - 复用状态：partial；类型：config
- `experiments/ESMBind/lora_binding_sites/best_model_esm2_t12_35M_lora_2023-11-09_12-02-07/vocab.txt`
  - 能力：tokenizer asset
  - 用途：tokenizer 词表（tokenizer）
  - 复用状态：partial；类型：tokenizer

### datasets

- `experiments/ESMBind/fine-tuned-esmbind-inference-performance/assets/labels.pkl`
  - 能力：evaluation label cache
  - 用途：保存推理/评测标签缓存（unknown）
  - 复用状态：partial；类型：unknown
- `experiments/ESMBind/fine-tuned-esmbind-inference-performance/assets/seqres.pkl`
  - 能力：sequence record cache
  - 用途：保存序列记录缓存（unknown）
  - 复用状态：partial；类型：unknown
- `experiments/ESMFold/assets/walle1723.fasta`
  - 能力：target fasta
  - 用途：ESMFold 评测目标序列输入（unknown）
  - 复用状态：partial；类型：unknown
- `experiments/EpiPred/assets/ag-chain-ids.txt`
  - 能力：chain id list
  - 用途：EpiPred 评测时的 antigen chain 过滤列表（unknown）
  - 复用状态：partial；类型：unknown

### evaluation

- `asep/model/metric.py`
  - 能力：metric module
  - 用途：定义评测指标与统计逻辑（code_entry）
  - 复用状态：ready_for_review；类型：code_entry
- `experiments/ESMFold/evaluate.py`
  - 能力：evaluation script
  - 用途：ESMFold 实验评估（code_entry）
  - 复用状态：ready_for_review；类型：code_entry
- `experiments/EpiPred/evaluate.py`
  - 能力：evaluation script
  - 用途：EpiPred 实验评估（code_entry）
  - 复用状态：ready_for_review；类型：code_entry
- `experiments/MaSIF-site/evaluate.py`
  - 能力：evaluation script
  - 用途：MaSIF-site 实验评估（code_entry）
  - 复用状态：ready_for_review；类型：code_entry
- `experiments/inference/calculate-mean-metrics.py`
  - 能力：metric aggregation
  - 用途：汇总多次推理/评测指标（code_entry）
  - 复用状态：ready_for_review；类型：code_entry

### inference

- `experiments/inference/inference.py`
  - 能力：inference entrypoint
  - 用途：批量推理主入口（code_entry）
  - 复用状态：ready_for_review；类型：code_entry
- `experiments/inference/evaluate_on_walle.py`
  - 能力：evaluation-driven inference
  - 用途：对 Walle 数据执行推理与评估（code_entry）
  - 复用状态：ready_for_review；类型：code_entry
- `experiments/ESMBind/inference-finetuned-lora-esm2.py`
  - 能力：fine-tuned inference script
  - 用途：对 LoRA 微调模型做推理（code_entry）
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `asep/model/asepv1_model.py`
  - 能力：core model code
  - 用途：定义 AsEP v1 主模型结构（code_entry）
  - 复用状态：ready_for_review；类型：code_entry
- `asep/data/asepv1_dataset.py`
  - 能力：dataset interface
  - 用途：封装 ASePV1 数据读取与样本组织逻辑（code_entry）
  - 复用状态：ready_for_review；类型：code_entry
- `asep/train_model.py`
  - 能力：training recipe
  - 用途：AsEP 主训练入口（code_entry）
  - 复用状态：ready_for_review；类型：code_entry
- `experiments/train-walle/train.py`
  - 能力：training recipe
  - 用途：Walle 相关训练入口（code_entry）
  - 复用状态：ready_for_review；类型：code_entry

### training

- `asep/train_model.py`
  - 能力：training entrypoint
  - 用途：主模型训练入口（code_entry）
  - 复用状态：ready_for_review；类型：code_entry
- `experiments/train-walle-epitope-group/train.py`
  - 能力：training entrypoint
  - 用途：Walle epitope group 训练入口（code_entry）
  - 复用状态：ready_for_review；类型：code_entry
- `experiments/train-walle/conf/config.yaml`
  - 能力：training config
  - 用途：Hydra 训练配置骨架（config）
  - 复用状态：ready_for_review；类型：config
- `experiments/ESMBind/fine-tune-lora-esm2.py`
  - 能力：fine-tuning script
  - 用途：LoRA 微调 ESM2 的训练脚本（code_entry）
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态清点，未运行代码、未安装依赖、未验证输出。
- 冻结清单显示未捆绑完整原始数据集，更多像下载器/清单/评测缓存。
- checkpoint 与数据资产未见独立许可证或来源说明，复用需单独审查。
- 仓库含多套外部方法实验脚手架，路径存在不等于可直接复现。

## 仍未知

- 外部下载器会拉取哪些具体数据、是否仍可获得，未验证。
- adapter_model.safetensors 对应的上游 base model 与训练语料未在冻结清单中明确。
- 各实验脚本对第三方包与环境版本的依赖关系未验证。
- metrics-summary.csv 等结果文件是否来自本仓库当前 commit 的真实运行，无法确认。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
