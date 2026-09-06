# blazerye/drugassist

- **仓库：** [https://github.com/blazerye/drugassist](https://github.com/blazerye/drugassist)
- **固定 commit：** `838b75521bcf40224164de4ecd56b0ba1724a34a`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 14

## 仓库摘要

该仓库是 DrugAssist 的分子优化实现，静态清单可见训练、合并、评估和 Web 部署代码，但没有冻结 checkpoint/权重；同时未发现 LICENSE，因而只能给出静态、未执行的复用判断。

## 可复用模块与资源

### datasets

- `evaluate/testset.csv`
  - 能力：评估测试集
  - 用途：评估输入/测试样本表。
  - 复用状态：blocked；类型：unknown
- `evaluate/mol_DB.csv`
  - 能力：molecule database
  - 用途：评估所用分子库/候选库。
  - 复用状态：blocked；类型：unknown

### evaluation

- `evaluate/main_eval.py`
  - 能力：主评估入口
  - 用途：评估主流程。
  - 复用状态：blocked；类型：code_entry
- `evaluate/small_molecule_editing.py`
  - 能力：small molecule editing 评估
  - 用途：面向分子编辑任务的评估逻辑。
  - 复用状态：blocked；类型：code_entry
- `evaluate/utils.py`
  - 能力：评估工具
  - 用途：评估辅助函数。
  - 复用状态：blocked；类型：code_entry

### inference

- `gradio_service.py`
  - 能力：Gradio 推理/演示服务
  - 用途：Web demo 或服务端推理入口。
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `merge_model.py`
  - 能力：模型合并 / 权重整理
  - 用途：将训练产物合并或整理为可部署模型的代码入口。
  - 复用状态：blocked；类型：code_entry
- `utils/attn_and_long_ctx_patches.py`
  - 能力：长上下文 / attention patch
  - 用途：修改 attention 与长上下文行为的辅助代码。
  - 复用状态：blocked；类型：code_entry
- `config/ds_zero1_no_offload.json`
  - 能力：训练配置
  - 用途：DeepSpeed ZeRO-1 配置。
  - 复用状态：blocked；类型：config
- `config/ds_zero2_no_offload.json`
  - 能力：训练配置
  - 用途：DeepSpeed ZeRO-2 配置。
  - 复用状态：blocked；类型：config
- `requirements.txt`
  - 能力：运行环境依赖
  - 用途：Python 依赖清单，供环境复现参考。
  - 复用状态：blocked；类型：unknown

### training

- `run_sft_lora.py`
  - 能力：SFT/LoRA 训练
  - 用途：训练入口脚本；从文件名看用于 SFT + LoRA。
  - 复用状态：blocked；类型：code_entry
- `run_sft_lora.sh`
  - 能力：SFT/LoRA 训练包装
  - 用途：调用/封装训练命令的 shell 脚本。
  - 复用状态：blocked；类型：code_entry
- `utils/build_dataset.py`
  - 能力：数据构建/预处理
  - 用途：生成或整理训练数据的辅助脚本。
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态审查，未执行代码或测试。
- 冻结清单未见 checkpoint/模型权重，无法从仓库本身验证可运行推理状态。
- 未发现 LICENSE，直接复用边界不清。
- 依赖未安装，无法验证训练/评估/部署路径。

## 仍未知

- `run_sft_lora.py` 的实际超参、数据来源与输出权重路径未核验。
- `evaluate/testset.csv` 与 `evaluate/mol_DB.csv` 的来源和许可未核验。
- `gradio_service.py` 是否直接加载最终模型、是否依赖外部权重未核验。
- `merge_model.py` 产生的目标格式与是否覆盖最终发布模型未核验。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
