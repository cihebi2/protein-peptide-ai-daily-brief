# anzhang314/PopGo

- **仓库：** [https://github.com/anzhang314/PopGo](https://github.com/anzhang314/PopGo)
- **固定 commit：** `d873a9fadc68987ff572f51e0af4f56eb10219b9`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 7

## 仓库摘要

该仓库的冻结清单显示其核心由 model.py、data.py 和 evaluator/* 组成，但未发现 LICENSE、checkpoint、明确的训练入口或推理入口；data.zip 仅是 tracked path，未被静态清单确认为 bundled data，因此数据内容与许可仍未知。

## 可复用模块与资源

### datasets

- `data.zip`
  - 能力：dataset_archive_candidate
  - 用途：未解包的压缩归档；可能承载训练/评测数据，但 frozen inventory 未将其确认成 bundled_data
  - 复用状态：unknown；类型：unknown

### evaluation

- `evaluator/backend/cpp/include/evaluate.h`
  - 能力：metric/evaluation API
  - 用途：C++ 评测接口声明
  - 复用状态：blocked；类型：unknown
- `evaluator/backend/cpp/include/metric.h`
  - 能力：metric/evaluation API
  - 用途：C++ 指标声明/定义
  - 复用状态：blocked；类型：unknown
- `evaluator/backend/python/metric.py`
  - 能力：metric/evaluation API
  - 用途：Python 指标实现
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `model.py`
  - 能力：model_architecture
  - 用途：推荐/协同过滤模型主体与打分逻辑的核心实现
  - 复用状态：blocked；类型：code_entry
- `data.py`
  - 能力：data_loader
  - 用途：数据读取、切分与预处理逻辑
  - 复用状态：blocked；类型：code_entry
- `setup.py`
  - 能力：build/packaging metadata
  - 用途：依赖声明与安装元数据，便于判断环境需求
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态清点，未安装依赖、未执行代码、未运行测试，因此不能证明可复现性。
- 仓库没有 LICENSE，直接复用代码或评测器前需要单独核验授权。
- `data.zip` 只是 tracked path，未被冻结清单确认是数据集或权重文件。
- 仓库中存在多个未被本次能力清单提升的脚本/包装文件，真实职责仅能按路径推断。

## 仍未知

- `data.zip` 的实际内容、来源、许可与是否包含数据/权重均未知。
- `main.py`、`parse.py` 是否构成训练或推理入口未通过执行确认。
- `evaluator/backend/cpp` 是否含有 vendored 第三方代码，单凭路径无法判断。
- 是否存在外部下载流程、隐藏 checkpoint 或其他未入库资源不可知。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
