# patrickbryant1/Umol

- **仓库：** [https://github.com/patrickbryant1/Umol](https://github.com/patrickbryant1/Umol)
- **固定 commit：** `4c0c72484b853a3d0cf2a2226284ac0fd8cb9a0b`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 16

## 仓库摘要

仓库提供蛋白-配体复合物结构预测的模型、推理脚本与示例输入，但未见训练入口、独立评测流水线或 checkpoint 文件；当前仅能做静态审查，且缺少明确许可证边界。

## 可复用模块与资源

### datasets

- `data/test_case/7NB4/7NB4.fasta`
  - 能力：示例蛋白序列
  - 用途：单个 test_case 的序列输入
  - 复用状态：blocked；类型：unknown
- `data/test_case/7NB4/7NB4_pocket_indices.npy`
  - 能力：示例口袋索引
  - 用途：单个 test_case 的口袋/残基索引输入
  - 复用状态：blocked；类型：unknown

### evaluation

- `src/net/model/map_ligand_test.py`
  - 能力：单元测试/回归检查
  - 用途：验证 ligand mapping 逻辑；不是独立 benchmark 评测
  - 复用状态：blocked；类型：code_entry
- `src/net/model/tf/protein_features_test.py`
  - 能力：单元测试/回归检查
  - 用途：验证 protein features 相关实现
  - 复用状态：blocked；类型：code_entry
- `src/net/model/tf/shape_helpers_test.py`
  - 能力：单元测试/回归检查
  - 用途：验证 shape helpers 相关实现
  - 复用状态：blocked；类型：code_entry

### inference

- `predict.sh`
  - 能力：命令行推理入口
  - 用途：封装推理执行命令
  - 复用状态：blocked；类型：code_entry
- `src/predict.py`
  - 能力：主推理脚本
  - 用途：从序列/特征生成复合物预测结果
  - 复用状态：blocked；类型：code_entry
- `src/predict_colab.py`
  - 能力：Colab 推理脚本
  - 用途：面向 Colab 的推理变体
  - 复用状态：blocked；类型：code_entry
- `src/relax/openmm_relax.py`
  - 能力：结构松弛/后处理
  - 用途：基于 OpenMM 的结构松弛；同目录还有 add_plddt_to_relaxed.py、align_ligand_conformer.py、align_ligand_conformer_colab.py
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `src/net/model/r3.py`
  - 能力：几何与表示工具
  - 用途：3D 向量/旋转相关基础工具，可供几何模块复用
  - 复用状态：blocked；类型：code_entry
- `src/net/model/quat_affine.py`
  - 能力：仿射与四元数变换
  - 用途：四元数/仿射坐标变换组件，可供结构建模复用
  - 复用状态：blocked；类型：code_entry
- `src/net/model/common_modules.py`
  - 能力：通用网络模块
  - 用途：通用神经网络层与辅助模块
  - 复用状态：blocked；类型：code_entry

### training

- `src/net/model/tf/input_pipeline.py`
  - 能力：输入管线与特征准备
  - 用途：构建训练/批处理输入流的辅助管线
  - 复用状态：blocked；类型：code_entry
- `src/net/model/tf/proteins_dataset.py`
  - 能力：数据集封装
  - 用途：训练数据集抽象与样本组织
  - 复用状态：blocked；类型：code_entry
- `src/net/model/tf/data_transforms.py`
  - 能力：特征变换
  - 用途：训练/输入特征转换与增强的辅助逻辑
  - 复用状态：blocked；类型：code_entry
- `src/net/model/tf/protein_features.py`
  - 能力：蛋白特征生成
  - 用途：训练前蛋白特征构建与编码
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态审查，未执行仓库代码、测试或下载外部依赖
- 未见训练入口或训练配置，训练流程只能从辅助模块间接推断
- 未见 checkpoint 文件，无法确认模型权重是否需要外部获取
- 仓库缺少明确许可证文件，直接复用存在边界不清风险
- `data/test_case/7NB4` 中其余 `.a3m` / `.pdb1` / `.pkl` 文件的来源与授权未能从静态清单确认

## 仍未知

- `data/test_case/7NB4/7NB4.a3m`、`7NB4.pdb1`、`7nb4.pdb1`、`ligand_inp_features.pkl`、`msa_features.pkl` 是否为生成中间产物、示例输入或外部数据派生物，静态清单不足以判定
- 推理脚本是否默认依赖外部 checkpoint 或下载步骤，静态清单未能确认
- `environment.yml` 仅表明依赖声明存在，未验证其可安装性与版本兼容性

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
