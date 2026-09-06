# AI4ChemS/Eunomia

- **仓库：** [https://github.com/AI4ChemS/Eunomia](https://github.com/AI4ChemS/Eunomia)
- **固定 commit：** `06ca595bfebae15d21534e2449a24023c0bb1751`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 9

## 仓库摘要

该仓库是一个以 MIT 许可发布的 Python 包，主线更像文献信息抽取/LLM 应用工具与示例集合，而不是可见的训练型机器学习工程。静态清单只显示了一个随仓数据文件、若干示例 notebook、pytest 测试和核心库模块；未见训练入口、正式推理脚本、模型 checkpoint，数据与序列化测试资源也未见独立许可声明。

## 可复用模块与资源

### datasets

- `data/case-study-3-ground-truth.csv`
  - 能力：case study ground truth
  - 用途：随仓真值/标注表，像是 case study 3 的参考数据，可用于示例或回归检查。
  - 复用状态：partial；类型：unknown

### evaluation

- `tests/test_docs.py`
  - 能力：pytest 文档/工具回归
  - 用途：静态文档相关回归测试，与 `tests/test_eunomia.py`、`tests/test_tools.py` 一起构成 smoke / regression 线索。
  - 复用状态：partial；类型：code_entry
- `tests/test_eunomia.py`
  - 能力：pytest 核心库回归
  - 用途：检查核心包行为的测试入口。
  - 复用状态：partial；类型：code_entry
- `tests/test_tools.py`
  - 能力：pytest 工具回归
  - 用途：检查工具层接口与辅助逻辑。
  - 复用状态：partial；类型：code_entry

### inference

- `examples/Extracting_materials_information.ipynb`
  - 能力：示例推理 notebook
  - 用途：演示如何用仓库工具做材料信息抽取。
  - 复用状态：partial；类型：unknown
- `examples/Applying_other_LLMs.ipynb`
  - 能力：示例推理 notebook
  - 用途：演示如何接入其他 LLM 做同类文献处理任务。
  - 复用状态：partial；类型：unknown
- `examples/chemical_structure.ipynb`
  - 能力：示例推理 notebook
  - 用途：演示与化学结构相关的应用流程。
  - 复用状态：partial；类型：unknown
- `examples/other_application.ipynb`
  - 能力：示例推理 notebook
  - 用途：演示其他应用场景的调用方式。
  - 复用状态：partial；类型：unknown

### reusable_assets

- `eunomia/eunomia.py`
  - 能力：核心 Python 包 / agent 流程
  - 用途：主入口样式的包代码，结合 `agents.py`、`parser.py`、`prompts.py`、`tools.py` 组织文献抽取与工具调用流程。
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态清单审查，未执行代码、未安装依赖、未运行测试。
- 未读取仓库文件正文；对方法细节、输入输出与示例行为只能依据路径名和库存描述推断。
- `tests/test_files/test_vector_store.pkl` 更像测试夹具/序列化资源，不应直接等同于可复用模型 checkpoint。
- 数据文件与测试夹具没有看到独立数据许可，跨边界复用存在不确定性。

## 仍未知

- `data/case-study-3-ground-truth.csv` 的来源、生成方式和授权范围未明。
- 示例 notebooks 是否可无外部依赖直接运行未验证。
- 仓库与论文内容的一致性只来自元数据直连，未做实证核对。
- 没有发现正式训练入口，因此是否存在隐藏的生成式训练流程无法从静态清单确认。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
