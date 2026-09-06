# AI4Science-WestlakeU/flow_guidance

- **仓库：** [https://github.com/AI4Science-WestlakeU/flow_guidance](https://github.com/AI4Science-WestlakeU/flow_guidance)
- **固定 commit：** `b47872e9f72c0b8360c6232fa8ae45f64159bdae`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 29

## 仓库摘要

该仓库是论文《On the Guidance of Flow Matching》的代码库，覆盖 synthetic、image 和 offline RL 三条实验线，包含 flow matching、guidance、value 训练/评估与推理脚本；静态清单未发现随仓库打包的数据集或 checkpoint。

## 可复用模块与资源

### evaluation

- `image/gflow_img/inverse/metrics.py`
  - 能力：image inverse metrics
  - 用途：评估 image inverse 结果。
  - 复用状态：partial；类型：code_entry
- `offline_rl/run/eval.py`
  - 能力：offline RL evaluation harness
  - 用途：评估离线 RL 策略；相关脚本见 `offline_rl/run_scripts/eval_gradient.sh`、`eval_mc.sh`、`eval_sim_mc.sh`。
  - 复用状态：partial；类型：code_entry
- `synthetic/guided_flow/utils/metrics.py`
  - 能力：synthetic metrics
  - 用途：评估 synthetic 分布生成与 guidance 效果。
  - 复用状态：partial；类型：code_entry

### inference

- `image/run/inference_inverse.py`
  - 能力：image inverse inference
  - 用途：执行 inverse problem 的采样与推理。
  - 复用状态：partial；类型：code_entry
- `image/run/inference_unconditional.py`
  - 能力：image unconditional inference
  - 用途：执行无条件生成/采样。
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `synthetic/guided_flow/flow/conditional_flow_matching.py`
  - 能力：synthetic conditional flow matching core
  - 用途：实现 synthetic 分支的条件 flow matching 主体。
  - 复用状态：ready_for_review；类型：code_entry
- `synthetic/guided_flow/guidance/gradient_guidance.py`
  - 能力：synthetic gradient guidance
  - 用途：提供梯度引导算子，用于 guided sampling。
  - 复用状态：ready_for_review；类型：code_entry
- `synthetic/guided_flow/guidance/contrastive_energy.py`
  - 能力：synthetic contrastive energy guidance
  - 用途：提供 contrastive energy guidance 变体。
  - 复用状态：ready_for_review；类型：code_entry
- `synthetic/guided_flow/backbone/transformer.py`
  - 能力：synthetic backbone
  - 用途：为 synthetic 实验提供 Transformer backbone。
  - 复用状态：ready_for_review；类型：code_entry
- `image/gflow_img/cfm/conditional_flow_matching.py`
  - 能力：image conditional flow matching core
  - 用途：实现 image 分支的 conditional flow matching 主逻辑。
  - 复用状态：ready_for_review；类型：code_entry
- `image/gflow_img/cfm/optimal_transport.py`
  - 能力：image optimal transport helper
  - 用途：提供 OT matching / coupling 辅助。
  - 复用状态：ready_for_review；类型：code_entry
- `image/gflow_img/backbone/unet.py`
  - 能力：image backbone
  - 用途：为 image 实验提供 U-Net backbone。
  - 复用状态：ready_for_review；类型：code_entry
- `image/gflow_img/dataset/dataset.py`
  - 能力：image data loader
  - 用途：image 数据读取与预处理；不含原始图像数据本体。
  - 复用状态：partial；类型：code_entry
- `image/gflow_img/config/celeba_hq_splits.json`
  - 能力：image split recipe
  - 用途：定义 CelebA-HQ 的数据划分配置；不是原始数据集。
  - 复用状态：partial；类型：config
- `offline_rl/gflower/models_flow/flow_matcher.py`
  - 能力：offline RL flow model core
  - 用途：实现 offline RL 分支的 flow matching 模型核心。
  - 复用状态：ready_for_review；类型：code_entry
- `offline_rl/gflower/models_flow/flow_policy.py`
  - 能力：offline RL policy wrapper
  - 用途：将 flow matching 组织为可采样策略。
  - 复用状态：ready_for_review；类型：code_entry
- `offline_rl/gflower/models_value/transformer.py`
  - 能力：offline RL value model
  - 用途：提供 value estimator，用于 guidance 与评估。
  - 复用状态：ready_for_review；类型：code_entry
- `offline_rl/gflower/datasets/d4rl.py`
  - 能力：offline RL dataset interface
  - 用途：D4RL 数据接入与预处理入口；实际数据需外部获取。
  - 复用状态：partial；类型：code_entry
- `offline_rl/gflower/environments/registration.py`
  - 能力：offline RL environment registration
  - 用途：注册 locomotion 环境。
  - 复用状态：partial；类型：code_entry
- `offline_rl/environment.yml`
  - 能力：dependency recipe
  - 用途：offline RL 分支的 Conda 依赖清单。
  - 复用状态：partial；类型：config
- `synthetic/environment.yml`
  - 能力：dependency recipe
  - 用途：synthetic 分支的 Conda 依赖清单。
  - 复用状态：partial；类型：config
- `image/requirements.txt`
  - 能力：dependency recipe
  - 用途：image 分支的 Python 依赖清单。
  - 复用状态：partial；类型：unknown

### training

- `synthetic/guided_flow/train/cfm.py`
  - 能力：synthetic CFM training
  - 用途：训练 synthetic flow matching；配套脚本见 `synthetic/script/train_cfm.sh`。
  - 复用状态：partial；类型：code_entry
- `synthetic/guided_flow/train/value_ceg.py`
  - 能力：synthetic value CEG training
  - 用途：训练 value-CEG / contrastive energy guidance 变体；配套脚本见 `synthetic/script/train_ceg.sh`。
  - 复用状态：partial；类型：code_entry
- `synthetic/guided_flow/train/value_guidance_matching.py`
  - 能力：synthetic guidance matching training
  - 用途：训练 guidance matching 变体；配套脚本见 `synthetic/script/train_guidance_matching.sh`。
  - 复用状态：partial；类型：code_entry
- `offline_rl/run/train.py`
  - 能力：offline RL main training entrypoint
  - 用途：offline RL 主训练入口；可由 `offline_rl/run_scripts/train.sh` 调用。
  - 复用状态：partial；类型：code_entry
- `offline_rl/run/train_guide.py`
  - 能力：offline RL guidance training
  - 用途：训练 guidance 分支。
  - 复用状态：partial；类型：code_entry
- `offline_rl/run/train_value.py`
  - 能力：offline RL value training
  - 用途：训练 value 分支；可由 `offline_rl/run_scripts/train_value.sh` 调用。
  - 复用状态：partial；类型：code_entry
- `image/gflow_img/utils/trainer.py`
  - 能力：image trainer
  - 用途：image inverse / unconditional 训练循环。
  - 复用状态：partial；类型：code_entry

## 使用限制

- 仅做静态清单分析，未安装依赖、未运行代码、未执行测试。
- tracked inventory 未发现 bundled 数据集或 checkpoint；运行时若从外部获取 CelebA-HQ、D4RL、MuJoCo 等资源，其许可证不在本仓库 LICENSE 边界内。
- 仓库中存在若干脚本/配置入口，但路径存在不等于可复现执行。
- large blobs over 5MiB may be promisor only；当前清单无法证明全部运行时资源已完整可用。

## 仍未知

- `offline_rl/gflower/models_value/mlp.py` 在清单中为空文件，是否为占位符未知。
- `image/run/main_train.py` 等未进入能力清单的脚本是否为主要训练入口，静态材料不足以确认。
- 外部数据与模型下载路径、缓存位置、以及任何可能的 Git LFS/远程资源依赖未被核实。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
