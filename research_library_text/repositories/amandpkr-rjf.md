# amandpkr/RJF

- **仓库：** [https://github.com/amandpkr/RJF](https://github.com/amandpkr/RJF)
- **固定 commit：** `d24b6a27d0c73ab5f7adfd6da435390942b6dfef`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 11

## 仓库摘要

该仓库主要提供两阶段生成模型/表示学习代码：stage1 是 representation encoder/decoder，stage2 是 DiT 训练与采样，并配有 FID 和 reference IQA 评估；当前仅见配置与源码路径，未见捆绑数据、实际权重文件或 LICENSE，因此只能给出静态目录级结论。

## 可复用模块与资源

### checkpoints

- `configs/stage1/pretrained/DINOv2-B.yaml`
  - 能力：stage1 pretrained backbone recipes
  - 用途：指向 DINOv2-B / DINOv2-B_512 / MAE / SigLIP2 预训练 backbone 的加载配置；未见实际权重文件
  - 复用状态：blocked；类型：config

### datasets

- `configs/stage2/training/ImageNet256/DiT-B_DINOv2-B.yaml`
  - 能力：ImageNet256 referenced dataset
  - 用途：stage2 训练/采样配置中引用的外部数据集名
  - 复用状态：unknown；类型：config

### evaluation

- `src/eval/fid.py`
  - 能力：FID metric
  - 用途：生成样本质量评估
  - 复用状态：blocked；类型：code_entry
- `src/eval/ref_iqa.py`
  - 能力：reference IQA metric
  - 用途：参考图像质量评估
  - 复用状态：blocked；类型：code_entry

### inference

- `src/sample_ddp.sh`
  - 能力：distributed sampling script
  - 用途：多卡采样启动脚本
  - 复用状态：blocked；类型：code_entry
- `configs/stage2/sampling/ImageNet256/DiT-B_DINOv2-B.yaml`
  - 能力：sampling configs for ImageNet256
  - 用途：DiT-B/XL 的采样参数配置
  - 复用状态：blocked；类型：config

### reusable_assets

- `src/stage1/rae.py`
  - 能力：stage1 representation encoder/decoder stack
  - 用途：构建 stage1 表示编码器、解码器及相关封装
  - 复用状态：blocked；类型：code_entry
- `src/stage2/models/lightningDiT.py`
  - 能力：stage2 diffusion/transport model stack
  - 用途：stage2 扩散模型、transport 与 Lightning 封装
  - 复用状态：blocked；类型：code_entry
- `src/eval/fid.py`
  - 能力：evaluation utilities
  - 用途：计算 FID 与 reference IQA
  - 复用状态：blocked；类型：code_entry

### training

- `src/train.py`
  - 能力：stage1 training entrypoint and recipe
  - 用途：stage1 训练入口；配套 DINOv2-B_decXL 训练配置
  - 复用状态：blocked；类型：code_entry
- `src/train.py`
  - 能力：stage2 training entrypoint and recipe
  - 用途：stage2 训练入口；ImageNet256 上的 DiT-B/XL 训练配置
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态审查，未运行任何代码
- 未安装依赖，无法验证训练、采样与评估是否可执行
- 未见实际 checkpoint 权重或 bundled data
- tracked path presence 不能证明可复现
- 未发现 LICENSE，直接复用受限

## 仍未知

- README 正文未读取，无法确认作者声明
- configs 中引用的 DINOv2-B、MAE、SigLIP2 与 ImageNet256 的具体来源和许可证未核实
- src/disc/* 等辅助模块的第三方来源未核实

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
