# weilab-biochem/structural-dpp-iv

- **仓库：** [https://github.com/weilab-biochem/structural-dpp-iv](https://github.com/weilab-biochem/structural-dpp-iv)
- **固定 commit：** `67306ac01ab9868b0f05d7a0a4e04dbf1d64b35f`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 38

## 仓库摘要

静态审查显示该仓库是 StructuralDPPIV 的结构特征 DPP-IV 抑制肽预测实现，包含训练入口、测试入口、Lightning 模块、编码器、配置、分析 notebook 与两份 TSV 数据；未见 checkpoint，且未执行代码。

## 可复用模块与资源

### datasets

- `data/DPP-IV/train/train.tsv`
  - 能力：dataset
  - 用途：训练集数据
  - 复用状态：blocked；类型：unknown
- `data/DPP-IV/test/test.tsv`
  - 能力：dataset
  - 用途：测试集数据
  - 复用状态：blocked；类型：unknown

### evaluation

- `test/test.py`
  - 能力：evaluation
  - 用途：测试与回归验证脚本
  - 复用状态：ready_for_review；类型：code_entry
- `util/util_metric.py`
  - 能力：evaluation
  - 用途：指标计算与评估辅助
  - 复用状态：ready_for_review；类型：code_entry
- `experiments/ablation.ipynb`
  - 能力：evaluation
  - 用途：消融实验分析
  - 复用状态：partial；类型：unknown
- `experiments/cam.ipynb`
  - 能力：evaluation
  - 用途：CAM 可解释性分析
  - 复用状态：partial；类型：unknown
- `experiments/permutation.ipynb`
  - 能力：evaluation
  - 用途：置换重要性分析
  - 复用状态：partial；类型：unknown
- `experiments/perturbation.ipynb`
  - 能力：evaluation
  - 用途：扰动分析
  - 复用状态：partial；类型：unknown

### inference

- `main/test.py`
  - 能力：inference
  - 用途：推理/测试入口
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `model/StructuralDPPIV.py`
  - 能力：model_architecture
  - 用途：主模型结构，定义结构特征到 DPP-IV 抑制肽预测的前向网络
  - 复用状态：ready_for_review；类型：code_entry
- `model/FocalLoss.py`
  - 能力：loss_function
  - 用途：FocalLoss 实现，用于缓解类别不平衡
  - 复用状态：ready_for_review；类型：code_entry
- `main/train.py`
  - 能力：training
  - 用途：训练入口脚本，组织参数、数据模块、模型与优化流程
  - 复用状态：ready_for_review；类型：code_entry
- `main/test.py`
  - 能力：inference
  - 用途：测试/推理入口脚本，用于加载模型并产出预测结果
  - 复用状态：ready_for_review；类型：code_entry
- `module/lightning_frame_module.py`
  - 能力：training
  - 用途：PyTorch Lightning 封装，承载训练步骤、验证步骤与优化逻辑
  - 复用状态：ready_for_review；类型：code_entry
- `module/lightning_data_module.py`
  - 能力：training
  - 用途：Lightning DataModule，封装训练/测试批次与数据划分
  - 复用状态：ready_for_review；类型：code_entry
- `data/StructuralEncode.py`
  - 能力：data_loader
  - 用途：结构编码器，负责把结构信息转成可训练特征
  - 复用状态：ready_for_review；类型：code_entry
- `data/Encode.py`
  - 能力：data_loader
  - 用途：通用编码辅助，参与序列/特征预处理
  - 复用状态：ready_for_review；类型：code_entry
- `config/hparams/StructuralDPPIV.yaml`
  - 能力：configuration
  - 用途：结构模型超参数配置
  - 复用状态：ready_for_review；类型：config
- `config/settings/StructuralDPPIV.yaml`
  - 能力：configuration
  - 用途：任务级配置，定义 StructuralDPPIV 的运行参数
  - 复用状态：ready_for_review；类型：config
- `config/settings/Lightning.yaml`
  - 能力：configuration
  - 用途：Lightning 运行配置
  - 复用状态：ready_for_review；类型：config
- `config/load_config.py`
  - 能力：configuration
  - 用途：配置读取与组装逻辑
  - 复用状态：ready_for_review；类型：config
- `config/load_constant.py`
  - 能力：configuration
  - 用途：常量定义与共享参数
  - 复用状态：ready_for_review；类型：code_entry
- `test/test.py`
  - 能力：evaluation
  - 用途：测试脚本，承接结果验证与回归检查
  - 复用状态：ready_for_review；类型：code_entry
- `util/util_metric.py`
  - 能力：evaluation
  - 用途：指标计算工具，支持测试与分析
  - 复用状态：ready_for_review；类型：code_entry
- `experiments/ablation.ipynb`
  - 能力：analysis_notebook
  - 用途：消融实验分析 notebook
  - 复用状态：partial；类型：unknown
- `experiments/cam.ipynb`
  - 能力：analysis_notebook
  - 用途：CAM 可解释性分析 notebook
  - 复用状态：partial；类型：unknown
- `experiments/permutation.ipynb`
  - 能力：analysis_notebook
  - 用途：置换重要性分析 notebook
  - 复用状态：partial；类型：unknown
- `experiments/perturbation.ipynb`
  - 能力：analysis_notebook
  - 用途：扰动分析 notebook
  - 复用状态：partial；类型：unknown

### training

- `main/train.py`
  - 能力：training
  - 用途：训练入口
  - 复用状态：ready_for_review；类型：code_entry
- `module/lightning_frame_module.py`
  - 能力：training
  - 用途：训练/验证步骤封装
  - 复用状态：ready_for_review；类型：code_entry
- `module/lightning_data_module.py`
  - 能力：training
  - 用途：数据装载与批次组织
  - 复用状态：ready_for_review；类型：code_entry
- `data/Encode.py`
  - 能力：training
  - 用途：训练前数据编码辅助
  - 复用状态：ready_for_review；类型：code_entry
- `data/StructuralEncode.py`
  - 能力：training
  - 用途：结构特征编码与预处理
  - 复用状态：ready_for_review；类型：code_entry
- `config/hparams/StructuralDPPIV.yaml`
  - 能力：training
  - 用途：训练超参数配置
  - 复用状态：ready_for_review；类型：config
- `config/settings/StructuralDPPIV.yaml`
  - 能力：training
  - 用途：任务配置
  - 复用状态：ready_for_review；类型：config
- `config/settings/Lightning.yaml`
  - 能力：training
  - 用途：Lightning 训练配置
  - 复用状态：ready_for_review；类型：config
- `config/load_config.py`
  - 能力：training
  - 用途：配置加载逻辑
  - 复用状态：ready_for_review；类型：config
- `config/load_constant.py`
  - 能力：training
  - 用途：共享常量定义
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态审查，未执行代码、未安装依赖、未运行测试。
- 未发现 checkpoint/模型权重文件，无法验证推理或复现结果。
- data/DPP-IV/*.tsv 未见独立许可与来源链。
- 部分 notebook 可能依赖外部中间产物或大文件，当前未验证。

## 仍未知

- 训练集/测试集是否为原始数据、清洗后数据或二次采样未确认。
- main/test.py 与 test/test.py 的真实运行结果与指标未验证。
- 第三方依赖及其版本锁定信息未在冻结清单中建立。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
