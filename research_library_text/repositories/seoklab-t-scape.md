# seoklab/T-SCAPE

- **仓库：** [https://github.com/seoklab/T-SCAPE](https://github.com/seoklab/T-SCAPE)
- **固定 commit：** `2331694a4237861b97cdb5a0008cd3a2c7244dac`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** found
- **资产记录数：** 30

## 仓库摘要

该冻结仓库更像一个以推理为中心的实现包：能静态确认 3 个模型定义、若干 I/O 与工具模块、CSV 推理入口，以及示例输入/输出和 MHC pseudo 参考表；未见训练入口、评估入口或 checkpoint，因此不能从静态证据证明训练或复现权重。

## 可复用模块与资源

### datasets

- `example/inputs/p_im.csv`
  - 能力：example input data
  - 用途：示例 p_im 输入
  - 复用状态：ready_for_review；类型：unknown
- `example/inputs/pmhc_ba.csv`
  - 能力：example input data
  - 用途：示例 pMHC binding affinity 输入
  - 复用状态：ready_for_review；类型：unknown
- `example/inputs/pmhc_ba_I.csv`
  - 能力：example input data
  - 用途：示例 MHC class I binding affinity 输入
  - 复用状态：ready_for_review；类型：unknown
- `example/inputs/pmhc_ba_II.csv`
  - 能力：example input data
  - 用途：示例 MHC class II binding affinity 输入
  - 复用状态：ready_for_review；类型：unknown
- `example/inputs/pmhc_ba_II_modified.csv`
  - 能力：example input data
  - 用途：示例 MHC class II binding affinity 修改版输入
  - 复用状态：ready_for_review；类型：unknown
- `example/inputs/pmhc_ba_I_modified.csv`
  - 能力：example input data
  - 用途：示例 MHC class I binding affinity 修改版输入
  - 复用状态：ready_for_review；类型：unknown
- `example/inputs/pmhc_im.csv`
  - 能力：example input data
  - 用途：示例 pMHC immunogenicity 输入
  - 复用状态：ready_for_review；类型：unknown
- `example/inputs/pmhc_im_modified.csv`
  - 能力：example input data
  - 用途：示例 pMHC immunogenicity 修改版输入
  - 复用状态：ready_for_review；类型：unknown
- `example/inputs/ptcr_ba.csv`
  - 能力：example input data
  - 用途：示例 pTCR binding affinity 输入
  - 复用状态：ready_for_review；类型：unknown
- `example/outputs/p_im_output.csv`
  - 能力：example output data
  - 用途：示例 p_im 预测输出
  - 复用状态：ready_for_review；类型：unknown
- `example/outputs/pmhc_ba_II_output.csv`
  - 能力：example output data
  - 用途：示例 MHC class II binding affinity 预测输出
  - 复用状态：ready_for_review；类型：unknown
- `example/outputs/pmhc_ba_I_output.csv`
  - 能力：example output data
  - 用途：示例 MHC class I binding affinity 预测输出
  - 复用状态：ready_for_review；类型：unknown
- `example/outputs/pmhc_im_output.csv`
  - 能力：example output data
  - 用途：示例 pMHC immunogenicity 预测输出
  - 复用状态：ready_for_review；类型：unknown
- `example/outputs/ptcr_ba_output.csv`
  - 能力：example output data
  - 用途：示例 pTCR binding affinity 预测输出
  - 复用状态：ready_for_review；类型：unknown
- `MHC_classI_pseudo.csv`
  - 能力：MHC pseudo reference tables
  - 用途：MHC class I pseudo-sequence 参考表
  - 复用状态：unknown；类型：unknown
- `MHC_classII_pseudo.csv`
  - 能力：MHC pseudo reference tables
  - 用途：MHC class II pseudo-sequence 参考表
  - 复用状态：unknown；类型：unknown

### inference

- `inference_csv.py`
  - 能力：CSV inference entrypoint
  - 用途：批量读取 CSV 并驱动推理流程
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `src/model_el.py`
  - 能力：model architecture
  - 用途：EL 分支模型定义，供推理阶段加载或组合
  - 复用状态：ready_for_review；类型：code_entry
- `src/model_fused.py`
  - 能力：model architecture
  - 用途：融合模型结构，供多分支特征合并与推理
  - 复用状态：ready_for_review；类型：code_entry
- `src/model_mlm.py`
  - 能力：model architecture
  - 用途：MLM 分支模型定义，供推理阶段使用
  - 复用状态：ready_for_review；类型：code_entry
- `src/layers.py`
  - 能力：shared layers
  - 用途：共享神经网络层与基础模块
  - 复用状态：ready_for_review；类型：code_entry
- `src/io_utils_el.py`
  - 能力：I/O utilities
  - 用途：EL 任务数据读写与预处理辅助
  - 复用状态：ready_for_review；类型：code_entry
- `src/io_utils_fused.py`
  - 能力：I/O utilities
  - 用途：融合任务数据读写与预处理辅助
  - 复用状态：ready_for_review；类型：code_entry
- `src/io_utils_mlm.py`
  - 能力：I/O utilities
  - 用途：MLM 任务数据读写与预处理辅助
  - 复用状态：ready_for_review；类型：code_entry
- `src/utils_el.py`
  - 能力：utility functions
  - 用途：EL 任务辅助函数
  - 复用状态：ready_for_review；类型：code_entry
- `src/utils_fused.py`
  - 能力：utility functions
  - 用途：融合任务辅助函数
  - 复用状态：ready_for_review；类型：code_entry
- `src/utils_mlm.py`
  - 能力：utility functions
  - 用途：MLM 任务辅助函数
  - 复用状态：ready_for_review；类型：code_entry
- `src/aa_index.py`
  - 能力：sequence encoding resources
  - 用途：氨基酸索引或编码常量
  - 复用状态：ready_for_review；类型：code_entry
- `src/constants.py`
  - 能力：constants
  - 用途：全局常量定义
  - 复用状态：ready_for_review；类型：code_entry
- `mhc_pseudo_matching.py`
  - 能力：MHC pseudo matching helper
  - 用途：MHC pseudo 匹配辅助模块
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态清单审查，未执行仓库代码
- 依赖未安装
- 测试未运行
- submodule 未初始化
- 大于 5MiB 的 blob 可能仅为 promisor 内容
- 路径存在不等于可复现性证明

## 仍未知

- LICENSE 正文未解析，无法确认 SPDX 或代码/数据/模型是否有不同许可边界
- 未见训练、评估或 checkpoint 入口，无法判断是否依赖清单外脚本或外部权重下载
- MHC_classI_pseudo.csv 与 MHC_classII_pseudo.csv 的来源与许可无法从冻结清单确认
- 示例 CSV 的字段语义与生成流程仅能从文件名推断

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
