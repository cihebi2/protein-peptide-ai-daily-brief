# Wangchentong/Proteus

- **仓库：** [https://github.com/Wangchentong/Proteus](https://github.com/Wangchentong/Proteus)
- **固定 commit：** `cda22f68001359e213bb4d5e69367deb1cc6b3b2`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 23

## 仓库摘要

静态清单显示该仓库主要服务于蛋白结构生成/设计：包含 SE(3) diffusion 相关实现、ProteinMPNN 与 OpenFold 子树、训练/推理/评估入口及多组 checkpoint。未见独立 bundled dataset；许可边界为混合状态，需要分别核查根目录与子树许可证。

## 可复用模块与资源

### checkpoints

- `ProteinMPNN/ca_model_weights/v_48_002.pt`
  - 能力：ProteinMPNN CA checkpoint
  - 用途：CA-only 模型权重
  - 复用状态：partial；类型：model_weight
- `ProteinMPNN/ca_model_weights/v_48_010.pt`
  - 能力：ProteinMPNN CA checkpoint
  - 用途：CA-only 模型权重
  - 复用状态：partial；类型：model_weight
- `ProteinMPNN/ca_model_weights/v_48_020.pt`
  - 能力：ProteinMPNN CA checkpoint
  - 用途：CA-only 模型权重
  - 复用状态：partial；类型：model_weight
- `ProteinMPNN/vanilla_model_weights/v_48_002.pt`
  - 能力：ProteinMPNN vanilla checkpoint
  - 用途：通用模型权重
  - 复用状态：partial；类型：model_weight
- `ProteinMPNN/vanilla_model_weights/v_48_010.pt`
  - 能力：ProteinMPNN vanilla checkpoint
  - 用途：通用模型权重
  - 复用状态：partial；类型：model_weight
- `ProteinMPNN/vanilla_model_weights/v_48_020.pt`
  - 能力：ProteinMPNN vanilla checkpoint
  - 用途：通用模型权重
  - 复用状态：partial；类型：model_weight
- `ProteinMPNN/vanilla_model_weights/v_48_030.pt`
  - 能力：ProteinMPNN vanilla checkpoint
  - 用途：通用模型权重
  - 复用状态：partial；类型：model_weight
- `weights/paper_weights.pt`
  - 能力：Proteus paper checkpoint
  - 用途：仓库内主 checkpoint / 推理权重候选
  - 复用状态：unknown；类型：model_weight

### evaluation

- `analysis/metrics.py`
  - 能力：指标计算
  - 用途：评估生成或设计结果的指标计算
  - 复用状态：ready_for_review；类型：code_entry
- `analysis/plotting.py`
  - 能力：结果可视化
  - 用途：分析与绘图辅助
  - 复用状态：ready_for_review；类型：code_entry
- `analysis/utils.py`
  - 能力：分析工具
  - 用途：评估/分析过程中的通用函数
  - 复用状态：ready_for_review；类型：code_entry

### inference

- `experiments/inference_se3_diffusion.py`
  - 能力：SE(3) diffusion 推理入口
  - 用途：驱动结构生成/采样与模型加载
  - 复用状态：ready_for_review；类型：code_entry
- `ProteinMPNN/protein_mpnn_run.py`
  - 能力：ProteinMPNN 推理脚本
  - 用途：序列设计/打分推理
  - 复用状态：partial；类型：code_entry
- `ProteinMPNN/protein_mpnn_pyrosetta.py`
  - 能力：PyRosetta 相关推理封装
  - 用途：结合 PyRosetta 的设计/推理流程
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `experiments/inference_se3_diffusion.py`
  - 能力：SE(3) diffusion 推理/采样入口
  - 用途：加载配置并驱动蛋白结构生成/采样流程
  - 复用状态：ready_for_review；类型：code_entry
- `model/score_network.py`
  - 能力：score_network 核心模块
  - 用途：结构生成主干的分数网络实现
  - 复用状态：ready_for_review；类型：code_entry
- `data/se3_diffuser.py`
  - 能力：SE(3)/SO(3)/R3 diffusion 组件
  - 用途：实现扩散与几何扰动过程
  - 复用状态：ready_for_review；类型：code_entry
- `openfold/model/model.py`
  - 能力：OpenFold 结构模型骨干
  - 用途：复用/封装结构预测骨干模块
  - 复用状态：partial；类型：code_entry
- `ProteinMPNN/protein_mpnn_run.py`
  - 能力：ProteinMPNN 设计/推理脚本
  - 用途：蛋白序列设计与推理执行入口
  - 复用状态：partial；类型：code_entry

### training

- `ProteinMPNN/training/training.py`
  - 能力：ProteinMPNN 训练入口
  - 用途：训练/微调脚本
  - 复用状态：partial；类型：code_entry
- `ProteinMPNN/training/model_utils.py`
  - 能力：训练辅助函数
  - 用途：模型构建与训练辅助工具
  - 复用状态：partial；类型：code_entry
- `ProteinMPNN/training/utils.py`
  - 能力：训练通用工具
  - 用途：训练过程中的通用辅助函数
  - 复用状态：partial；类型：code_entry
- `ProteinMPNN/training/colab_training_example.ipynb`
  - 能力：示例训练 notebook
  - 用途：交互式训练示例与说明
  - 复用状态：partial；类型：unknown

## 使用限制

- 仅做静态清单审查，未执行代码、未安装依赖、未运行测试
- submodules_not_initialized
- large_blobs_over_5MiB_may_be_promisor_only
- 路径存在不等于可复现或可运行
- ProteinMPNN 与 OpenFold 子树很可能是 vendored 依赖，不能直接当作论文特有贡献
- 未见独立 bundled dataset 清单，示例 PDB 输入未标注数据授权

## 仍未知

- `weights/paper_weights.pt` 的训练来源、版本兼容性与是否可直接用于当前推理入口未被静态证实
- `ProteinMPNN/inputs/PDB_*/*.pdb` 仅见示例输入，是否可作为正式数据集或可再分发数据未确认
- OpenFold 与 ProteinMPNN 子树是否为未修改上游拷贝或含局部改动未确认
- 各 checkpoint 与当前配置/代码的精确匹配关系未确认
- 训练数据来源与超参数仅凭目录无法完整还原

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
