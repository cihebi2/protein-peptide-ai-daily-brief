# ABILiLab/DegradeMaster

- **仓库：** [https://github.com/ABILiLab/DegradeMaster](https://github.com/ABILiLab/DegradeMaster)
- **固定 commit：** `aa149beaf067a051e070b3b281f7dba43c2f3e90`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 17

## 仓库摘要

仓库提供 DegradeMaster 的 PROTAC 降解预测代码、数据与权重，但冻结清单未见 LICENSE，且仅做静态审查，未验证可运行性或复现结果。

## 可复用模块与资源

### checkpoints

- `checkpoint/2000/model_EGNN_2000.pth`
  - 能力：训练后权重
  - 用途：保存训练得到的模型参数。
  - 复用状态：blocked；类型：model_weight
- `checkpoint/1000/model_for_case_study.pth`
  - 能力：案例研究权重
  - 用途：支持 case study 的推理或演示。
  - 复用状态：blocked；类型：model_weight
- `model/test.pt`
  - 能力：测试/演示模型
  - 用途：存放测试或演示时使用的模型文件。
  - 复用状态：blocked；类型：model_weight

### datasets

- `data/PROTAC/features/protac_feature.npy`
  - 能力：训练用 PROTAC 特征包
  - 用途：保存 PROTAC、E3 与 target 的特征数组及名称映射。
  - 复用状态：blocked；类型：unknown
- `data/case_study/processed/feature.pt`
  - 能力：案例研究预处理缓存
  - 用途：保存 case study 的预处理图/张量缓存与标签。
  - 复用状态：blocked；类型：unknown
- `data/case_study/target_pocket/BRD4_O60885.pdb`
  - 能力：结构与对接输入/结果
  - 用途：提供靶标口袋、E3 口袋、ligand 与 PROTAC 的原始结构或对接产物。
  - 复用状态：unknown；类型：unknown

### evaluation

- `log/test.log`
  - 能力：测试日志
  - 用途：记录测试阶段输出、指标或运行摘要。
  - 复用状态：blocked；类型：unknown
- `runs/test/events.out.tfevents.1737682383.LDQX0X3W97Q.65294.0`
  - 能力：TensorBoard 测试轨迹
  - 用途：存放测试阶段的 TensorBoard 曲线与标量记录。
  - 复用状态：blocked；类型：unknown
- `eval/PROTAC_demo_saved.npy`
  - 能力：评估结果缓存
  - 用途：保存 demo 评估或预测结果数组。
  - 复用状态：blocked；类型：unknown

### inference

- `case_study.py`
  - 能力：案例推理脚本
  - 用途：对案例集合执行预测与筛选式推理。
  - 复用状态：blocked；类型：code_entry
- `main.py`
  - 能力：通用推理入口
  - 用途：作为命令行或主入口式预测脚本的候选。
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `model.py`
  - 能力：模型架构
  - 用途：定义核心预测网络与前向计算逻辑。
  - 复用状态：blocked；类型：code_entry
- `prepare_data.py`
  - 能力：数据处理与构建
  - 用途：生成特征缓存、处理输入并组织数据集。
  - 复用状态：blocked；类型：code_entry
- `tokenizer/tokenize_3d.py`
  - 能力：分子与蛋白辅助工具
  - 用途：提供分子三维 tokenization 与相关辅助表示转换。
  - 复用状态：blocked；类型：code_entry
- `utils/chem_utils.py`
  - 能力：化学/结构工具
  - 用途：支持分子化学处理、结构辅助和通用工具函数。
  - 复用状态：blocked；类型：code_entry

### training

- `train_and_test.py`
  - 能力：训练与测试循环
  - 用途：承载训练、验证与测试流程。
  - 复用状态：blocked；类型：code_entry
- `config/config.yml`
  - 能力：训练配置
  - 用途：提供默认超参、数据路径与运行配置。
  - 复用状态：blocked；类型：config

## 使用限制

- 仅做静态审查，未执行仓库代码。
- 未安装依赖，无法验证环境与运行路径。
- 未运行测试，不能把文件存在视为可复现证明。
- 大量 data/.pdb/.mol2/.npy/.pt 资产的来源与生成链条未被内容级确认。
- 冻结清单未发现 LICENSE 文件，复用边界不清。

## 仍未知

- `case_study.py` 与 `main.py` 是否为正式推理入口，仍需读代码确认。
- `train_and_test.py` 是否同时覆盖训练、验证与测试，静态清单不足以证明。
- `data/case_study/target_pocket` 与 `ligase_ligand` 中若干结构/对接结果是否来自第三方工具或外部数据库，未被内容级确认。
- `checkpoint/*.pth` 与 `model/test.pt` 是否对应论文主结果，未在本次静态审查中验证。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
