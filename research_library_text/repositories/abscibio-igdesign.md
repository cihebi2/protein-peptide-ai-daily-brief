# AbSciBio/igdesign

- **仓库：** [https://github.com/AbSciBio/igdesign](https://github.com/AbSciBio/igdesign)
- **固定 commit：** `70431eef0afaf0496d7d84e22dfdc1980ec9e70e`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 9

## 仓库摘要

该仓库是 IgDesign 的静态冻结实现：包含 antibody inverse folding 的模型、数据/特征管线与 `predict.py` 推理入口，并附带示例 PDB、YAML 配置、CSV 结果表和 sensorgram PDF；未见训练入口、评测脚本或 tracked checkpoints，因此只能确认静态资产与许可边界，不能证明可复现执行。

## 可复用模块与资源

### datasets

- `data/Afasevikumab-IL17A.csv`
  - 能力：实验结果/抗体设计 CSV 表
  - 用途：包含 Afasevikumab、Bimagrumab、Eculizumab、Osocimab、Spesolimab、Tezepelumab、Utomilumab 以及 blinded Ravagalimab 的结果表。
  - 复用状态：partial；类型：unknown
- `data/Sensorgrams/Afasevikumab-IL17A.pdf`
  - 能力：sensorgram / 验证 PDF
  - 用途：存放实验传感曲线或验证图，支撑湿实验结果。
  - 复用状态：partial；类型：unknown

### inference

- `predict.py`
  - 能力：CLI 推理/采样
  - 用途：加载模型并输出设计结果的主要运行入口。
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `src/igdesign/model.py`
  - 能力：核心模型与封装
  - 用途：定义 IgDesign 的 antibody inverse folding 核心模型与包装层。
  - 复用状态：ready_for_review；类型：code_entry
- `src/igdesign/features/feature.py`
  - 能力：特征构造与序列/结构编码
  - 用途：构建输入特征、tokenization、embedding 和生成流程。
  - 复用状态：ready_for_review；类型：code_entry
- `src/igdesign/data/datasets/pdb_antibody.py`
  - 能力：PDB/抗体数据解析与结构分析
  - 用途：读取 PDB、组织 antibody 数据集并做结构分析。
  - 复用状态：ready_for_review；类型：code_entry
- `predict.py`
  - 能力：推理入口
  - 用途：命令行推理与候选序列生成的入口。
  - 复用状态：ready_for_review；类型：code_entry
- `configs/1n8z.yaml`
  - 能力：示例配置
  - 用途：为 1n8z 和 5ngv 示例定义推理参数与运行配方。
  - 复用状态：ready_for_review；类型：config
- `examples/1n8z.pdb`
  - 能力：示例结构输入
  - 用途：提供 1n8z 与 5ngv 的结构样例，供配置文件配套使用。
  - 复用状态：unknown；类型：unknown

## 使用限制

- 仅做静态清点；未执行代码、未安装依赖、未运行测试。
- 冻结清单中未见 tracked checkpoint 文件；`download_ckpts.sh` 仅提示可能依赖外部权重，不能证明已具备可运行模型。
- 数据、示例结构与 sensorgram PDF 未见独立许可声明，不能默认沿用 MIT。
- 仓库存在 `data/Blinded/` 等实验结果文件，但缺少对应评测脚本，无法从静态证据验证论文结果链。

## 仍未知

- `examples/1n8z.pdb` 与 `examples/5ngv.pdb` 的具体来源是否为外部 PDB 条目或项目自建，静态路径不足以确认。
- `data/Sensorgrams/*.pdf` 的内容是原始记录、截图还是处理后图，未读取文件内容前无法区分。
- `download_ckpts.sh` 获取的模型权重是否与论文最终结果完全一致，未见可核实的 checkpoint 清单。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
