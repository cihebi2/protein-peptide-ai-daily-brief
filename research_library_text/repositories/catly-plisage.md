# catly/plisage

- **仓库：** [https://github.com/catly/plisage](https://github.com/catly/plisage)
- **固定 commit：** `edb7a8a0fad549440899eb65e1f685b9dfdab1a3`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 26

## 仓库摘要

仓库是 PLiSAGE 的静态代码实现：包含预训练、PLI/DTI 下游训练、多模态蛋白编码器、GVP/Point-MAE、评估和自定义 CUDA 扩展；但未见 LICENSE、内置数据或独立推理入口，因此只能做静态可复用性分层。

## 可复用模块与资源

### checkpoints

- `pre_check/checkpoint.pth.tar`
  - 能力：model weight
  - 用途：仓库内置检查点权重文件
  - 复用状态：unknown；类型：checkpoint_adjacent
- `utils/checkpoint.py`
  - 能力：checkpoint helper
  - 用途：保存、恢复与管理训练检查点
  - 复用状态：blocked；类型：code_entry

### datasets

- `predata_process.py`
  - 能力：pretraining preprocessing
  - 用途：生成预训练样本与几何/表面输入
  - 复用状态：blocked；类型：code_entry
- `downstreamtasks/pli/pli_data_process.py`
  - 能力：PLI preprocessing
  - 用途：构造 PLI 下游样本与特征
  - 复用状态：blocked；类型：code_entry
- `downstreamtasks/dti/dti_data_process.py`
  - 能力：DTI preprocessing
  - 用途：构造 DTI 下游样本与特征
  - 复用状态：blocked；类型：code_entry
- `datasets/protein_dataset.py`
  - 能力：generic protein dataset
  - 用途：通用蛋白数据集封装
  - 复用状态：blocked；类型：code_entry
- `gvp/data.py`
  - 能力：GVP data wrapper
  - 用途：GVP 模型输入的数据组织与特征构造
  - 复用状态：blocked；类型：code_entry
- `utils/data_transforms.py`
  - 能力：shared transforms
  - 用途：坐标与特征变换
  - 复用状态：blocked；类型：code_entry
- `utils/ligand_processing.py`
  - 能力：ligand processing
  - 用途：配体解析与特征处理
  - 复用状态：blocked；类型：code_entry

### evaluation

- `utils/metrics.py`
  - 能力：metrics helper
  - 用途：评估指标计算与结果汇总
  - 复用状态：blocked；类型：code_entry
- `extensions/emd/test_emd_loss.py`
  - 能力：geometry loss smoke test
  - 用途：EMD 扩展的静态校验/回归测试
  - 复用状态：unknown；类型：code_entry

### inference

- `downstreamtasks/pli/models/pli_protein_multimodal.py`
  - 能力：PLI predictor forward path
  - 用途：PLI 分数/类别推理的模型前向模块；未见独立 CLI 推理脚本
  - 复用状态：blocked；类型：code_entry
- `downstreamtasks/dti/models/dti_protein_multimodal.py`
  - 能力：DTI predictor forward path
  - 用途：DTI 预测的模型前向模块；未见独立 CLI 推理脚本
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `configs/pretrain_config.yml`
  - 能力：pretraining config
  - 用途：预训练超参数、数据路径与训练 recipe 配置
  - 复用状态：blocked；类型：config
- `configs/downsteam_config.yml`
  - 能力：downstream training config
  - 用途：PLI/DTI 下游训练的配置模板
  - 复用状态：blocked；类型：config
- `models/protein_multimodal.py`
  - 能力：multimodal protein backbone
  - 用途：蛋白序列/结构多模态编码骨干
  - 复用状态：blocked；类型：code_entry
- `models/Point_MAE.py`
  - 能力：Point-MAE pretraining model
  - 用途：点云/表面表征学习主模型
  - 复用状态：blocked；类型：code_entry
- `models/Point_MAE_Finetune.py`
  - 能力：Point-MAE finetuning model
  - 用途：下游任务微调模型封装
  - 复用状态：blocked；类型：code_entry
- `gvp/models.py`
  - 能力：GVP encoder
  - 用途：几何向量感知蛋白结构编码
  - 复用状态：blocked；类型：code_entry
- `utils/ntxent_loss.py`
  - 能力：contrastive loss
  - 用途：预训练阶段的 NT-Xent 对比学习损失
  - 复用状态：blocked；类型：code_entry
- `extensions/chamfer_dist/setup.py`
  - 能力：custom CUDA geometry extension
  - 用途：Chamfer distance 扩展的编译入口
  - 复用状态：unknown；类型：code_entry
- `extensions/emd/setup.py`
  - 能力：custom CUDA geometry extension
  - 用途：EMD 扩展的编译入口
  - 复用状态：unknown；类型：code_entry

### training

- `pre_train.py`
  - 能力：pretraining script
  - 用途：预训练流程脚本
  - 复用状态：blocked；类型：code_entry
- `downstreamtasks/pli/pli_train.py`
  - 能力：PLI training script
  - 用途：PLI 下游训练脚本
  - 复用状态：blocked；类型：code_entry
- `downstreamtasks/dti/dti_train.py`
  - 能力：DTI training script
  - 用途：DTI 下游训练脚本
  - 复用状态：blocked；类型：code_entry
- `utils/trainer.py`
  - 能力：shared trainer
  - 用途：统一训练循环、日志与 checkpoint 协调
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态清单审查，未执行代码、未安装依赖、未运行测试。
- 仓库未见 LICENSE，直接复用边界无法确认。
- 未见 bundled data，训练/验证/测试数据来源不可从库存确定。
- 未发现独立 inference CLI；推理流程只能从模型模块名推测。
- checkpoint 的训练来源、任务归属与可再分发状态未知。

## 仍未知

- `pre_check/checkpoint.pth.tar` 是预训练权重还是下游权重未知。
- `configs/downsteam_config.yml` 里具体任务、超参与数据划分未知。
- `utils/metrics.py` 支持哪些指标与阈值策略未知。
- `extensions/chamfer_dist` 和 `extensions/emd` 是否为完整 vendored third-party 实现、以及其许可证未知。
- 仓库是否还有未被冻结清单覆盖的推理/部署脚本未知。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
