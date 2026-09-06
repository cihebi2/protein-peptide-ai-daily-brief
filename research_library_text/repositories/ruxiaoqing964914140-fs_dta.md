# ruxiaoqing964914140/fs_dta

- **仓库：** [https://github.com/ruxiaoqing964914140/fs_dta](https://github.com/ruxiaoqing964914140/fs_dta)
- **固定 commit：** `373adfc66e78d6569038e233969cb51b861b46a6`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 14

## 仓库摘要

该仓库主要是DTA亲和力预测的特征处理、训练与评测代码/数据集合，包含Davis与KIBA数据和若干实验Notebook，但未见许可证、模型权重或独立推理入口。

## 可复用模块与资源

### datasets

- `data/NerLTR-DTA-main/NerLTR-DTA/data/Davis/davis_binding_affinity.txt`
  - 能力：Davis benchmark dataset
  - 用途：DTA亲和力训练/测试数据，连同fold与相似度文件一起构成Davis实验集
  - 复用状态：unknown；类型：unknown
- `data/NerLTR-DTA-main/NerLTR-DTA/data/KIBA/kiba_binding_affinity_v2.txt`
  - 能力：KIBA benchmark dataset
  - 用途：DTA亲和力训练/测试数据，连同fold文件构成KIBA实验集
  - 复用状态：unknown；类型：unknown

### evaluation

- `IFS/test_model.py`
  - 能力：test_harness
  - 用途：测试与结果汇总
  - 复用状态：blocked；类型：code_entry
- `data/NerLTR-DTA-main/NerLTR-DTA/code/emetrics.py`
  - 能力：metric_implementation
  - 用途：评价指标实现
  - 复用状态：blocked；类型：code_entry
- `Evaluation criteria/CI_MSE.ipynb`
  - 能力：evaluation_notebook
  - 用途：误差/评测标准分析
  - 复用状态：blocked；类型：unknown

### reusable_assets

- `IFS/train_model.py`
  - 能力：training_entrypoint
  - 用途：训练主入口与模型定义
  - 复用状态：blocked；类型：code_entry
- `IFS/test_model.py`
  - 能力：evaluation_entrypoint
  - 用途：测试/评估入口
  - 复用状态：blocked；类型：code_entry
- `Feature processing method/xgb_p_afterVT.py`
  - 能力：feature_processing
  - 用途：XGBoost特征处理/建模脚本
  - 复用状态：blocked；类型：code_entry
- `data/Train_test.ipynb`
  - 能力：training_module
  - 用途：训练与测试流程Notebook
  - 复用状态：blocked；类型：unknown
- `data/NerLTR-DTA-main/NerLTR-DTA/code/data processing.py`
  - 能力：data_loader
  - 用途：DTA数据读取、切分与预处理
  - 复用状态：blocked；类型：code_entry
- `data/NerLTR-DTA-main/NerLTR-DTA/code/emetrics.py`
  - 能力：evaluation
  - 用途：评价指标实现
  - 复用状态：blocked；类型：code_entry

### training

- `IFS/train_model.py`
  - 能力：training_entrypoint
  - 用途：训练入口
  - 复用状态：blocked；类型：code_entry
- `Feature processing method/davis_d_lasso.py`
  - 能力：feature_selection_training
  - 用途：Davis特征筛选与训练前处理
  - 复用状态：blocked；类型：code_entry
- `data/Train_test.ipynb`
  - 能力：training_notebook
  - 用途：训练/测试流程编排
  - 复用状态：blocked；类型：unknown

## 使用限制

- 仅做静态盘点，未运行代码、未安装依赖、未执行测试。
- 未见独立模型权重或checkpoint文件，无法证明存在可复现训练产物。
- 未见明确LICENSE文件，直接复用代码/数据存在许可不确定性。
- `data/NerLTR-DTA-main/...` 看起来像外部项目或数据的捆绑副本，来源与授权需单独确认。
- `RankLib-2.16.jar` 与 `ranklib.zip` 属于第三方二进制/压缩包，许可边界不明。
- 未见独立推理入口，`test_model.py` 更像测试/评测脚本而非完整部署推理服务。

## 仍未知

- Davis/KIBA 文件是原始镜像、改写副本，还是项目自建数据集，静态清单无法确认。
- `IFS/train_model.py` 的具体模型结构与超参需要阅读源码或运行后才能完整确认。
- `RankLib` 相关二进制是否与仓库代码同许可未知。
- Notebook 是否包含隐藏输出、硬编码路径或本地环境依赖，静态清单无法确认。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
