# deagogishvili/chapter-multi-task

- **仓库：** [https://github.com/deagogishvili/chapter-multi-task](https://github.com/deagogishvili/chapter-multi-task)
- **固定 commit：** `0cee8f731726d778228105dc5be59bf941915e8c`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 14

## 仓库摘要

这是 PatchProt 的静态仓库清点：包含多任务蛋白属性预测代码、vendored ESM 依赖、若干训练/验证/基准数据与结果文件；未见可直接复用的模型权重或可验证的执行记录。

## 可复用模块与资源

### checkpoints

- `patchprot/PROT/esm/esm/pretrained.py`
  - 能力：ESM pretrained reference
  - 用途：ESM 预训练模型加载引用；未发现实际权重文件
  - 复用状态：blocked；类型：code_entry

### datasets

- `data/patches/Train_LHP.csv`
  - 能力：LHP training/benchmark splits
  - 用途：LHP 训练、验证与测试/benchmark 划分
  - 复用状态：partial；类型：unknown
- `data/benchmarking/test_data.csv`
  - 能力：benchmark prediction artifacts
  - 用途：保存模型在基准集上的预测与对照输出
  - 复用状态：partial；类型：unknown
- `data/case_example/154L.csv`
  - 能力：case example bundle
  - 用途：单个蛋白案例的结构、特征与结果展示
  - 复用状态：partial；类型：unknown
- `data/validation/casp14/targets/T1024.pdb`
  - 能力：validation structures and classes
  - 用途：CASP14 验证输入、AlphaFold 对应结构和目标类别
  - 复用状态：unknown；类型：unknown

### evaluation

- `patchprot/PROT/eval/eval.py`
  - 能力：metric computation
  - 用途：计算评估指标并汇总模型表现
  - 复用状态：ready_for_review；类型：code_entry
- `benchmarking/benchmarking.ipynb`
  - 能力：benchmark notebooks/results
  - 用途：基准比较和验证分析的静态记录
  - 复用状态：partial；类型：unknown

### inference

- `patchprot/PROT/predict/predict.py`
  - 能力：prediction entrypoint
  - 用途：对训练好的模型进行推断并导出预测结果
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `patchprot/PROT/main.py`
  - 能力：training/inference orchestration
  - 用途：入口与命令行封装，用于选择配置并启动训练或推理流程
  - 复用状态：ready_for_review；类型：code_entry
- `patchprot/configs/patchprot.yml`
  - 能力：experiment configuration
  - 用途：定义 PatchProt、ESM2、baseline 与 LoRA 变体的实验超参和流程开关
  - 复用状态：ready_for_review；类型：config
- `patchprot/PROT/models/ESM2_multitask/model.py`
  - 能力：model architecture
  - 用途：多任务、扩展多任务和原始模型定义
  - 复用状态：ready_for_review；类型：code_entry
- `patchprot/PROT/esm/esm/model/esm2.py`
  - 能力：vendored foundation model dependency
  - 用途：ESM2 预训练模型加载与模型定义的第三方依赖代码
  - 复用状态：ready_for_review；类型：code_entry

### training

- `patchprot/PROT/trainer/trainer.py`
  - 能力：training loop
  - 用途：执行批次训练、验证与模型保存调度
  - 复用状态：ready_for_review；类型：code_entry
- `jobs/patchprot.sh`
  - 能力：job scripts
  - 用途：封装不同实验配置的启动命令
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态清点；未安装依赖、未运行代码、未执行测试。
- 未发现显式 training_entrypoint；训练流程大概率由 jobs/*.sh、patchprot/PROT/main.py 与 trainer 组合触发，但未验证。
- 未见可直接复用的模型权重文件；现有 checkpoint 线索仅是 vendored 的 pretrained 加载/引用代码。
- 大量 CSV/PDB/OUT/Notebook 可能是数据或运行产物，但其生成链和完整性无法从静态清点证明。

## 仍未知

- 各数据集的原始来源、再分发条件与数据许可未能从 frozen inventory 单独确认。
- data/validation 与 data/benchmarking 中的许多结果文件是否为真实运行产物，或仅为示例静态结果，未知。
- vendored ESM 子树与上游版本的精确对应关系、是否带本地补丁，未知。
- 大文件与 LFS/ promisor 内容是否存在未完全展开的权重或附属资产，未知。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
