# markuswenzel/xai-proteins

- **仓库：** [https://github.com/markuswenzel/xai-proteins](https://github.com/markuswenzel/xai-proteins)
- **固定 commit：** `4f5e7efababa41f1a2a2cf5891bc7f0151866aa3`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 11

## 仓库摘要

该仓库是 xai-proteins 的静态快照，围绕 EC 与 GO 两个蛋白功能预测子任务，包含数据预处理、Transformer/Integrated Gradients 解释、评估与脚本化提交入口；未见训练入口、checkpoint 或仓库级许可证，只能做路径级盘点。

## 可复用模块与资源

### datasets

- `ec/download_swissprot.sh`
  - 能力：外部数据下载器（SwissProt/GO，非打包数据）
  - 用途：拉取训练/评估所需外部数据；仓库未见 bundled data
  - 复用状态：blocked；类型：code_entry

### evaluation

- `ec/metrics.py`
  - 能力：EC 评估与统计分析
  - 用途：EC metrics、annotation eval、统计汇总
  - 复用状态：blocked；类型：code_entry
- `go/evaluate_go.py`
  - 能力：GO 评估与统计分析
  - 用途：GO evaluation、annotation eval、Jaccard/统计后处理
  - 复用状态：blocked；类型：code_entry

### inference

- `ec/prot_ec.py`
  - 能力：EC 预测/解释模型族
  - 用途：EC protein function prediction 相关模型实现；同目录含 `prot_ec_esm.py`、`prot_ec_mod.py`、`prot_ec_pretrained_shuffled.py` 与提交脚本
  - 复用状态：blocked；类型：code_entry
- `go/prot_go.py`
  - 能力：GO 预测/解释模型族
  - 用途：GO prediction 相关模型实现；同目录含 `prot_go_esm.py`、`prot_go_mod.py`、`prot_go_pretrained_shuffled.py` 与提交脚本
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `ec/processing.py`
  - 能力：EC 数据预处理/读取
  - 用途：整理 EC 子任务输入数据
  - 复用状态：blocked；类型：code_entry
- `go/processing.py`
  - 能力：GO 数据预处理/读取
  - 用途：整理 GO 子任务输入数据
  - 复用状态：blocked；类型：code_entry
- `ec/integrated_gradient_helper.py`
  - 能力：Integrated Gradients 辅助函数
  - 用途：解释归因计算的公共函数；GO 侧有同名实现
  - 复用状态：blocked；类型：code_entry
- `ec/transformer_pooling.py`
  - 能力：Transformer pooling 聚合
  - 用途：Transformer 表征池化/聚合；GO 侧有同名实现
  - 复用状态：blocked；类型：code_entry
- `ec/sites_helper.py`
  - 能力：位点/残基辅助处理
  - 用途：位点级分析辅助；GO 侧有同名实现
  - 复用状态：blocked；类型：code_entry
- `go/prosite_parser.py`
  - 能力：GO 术语/Prosite 解析
  - 用途：解析 GO 相关注释/规则输入，并与 `obtain_go_terms.py` 配套
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态路径盘点，未执行任何代码。
- 依赖未安装，无法验证运行时行为。
- 未发现 tracked checkpoint/weights，不能证明训练或推理可复现。
- 仓库未发现许可证文件，直接复用受阻。

## 仍未知

- `download_swissprot.sh`、`download_go.sh` 实际指向哪些外部数据源以及其许可，未核实。
- `go/envs/*.yml`、`*.txt` 只是环境描述，未验证是否可重建全部依赖。
- `submit_*.sh` 是否只是集群包装脚本、是否依赖外部资源，未执行。
- README 中的实验范围和结果细节未展开核验。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
