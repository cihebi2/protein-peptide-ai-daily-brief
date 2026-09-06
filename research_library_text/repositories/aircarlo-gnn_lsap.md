# aircarlo/GNN_LSAP

- **仓库：** [https://github.com/aircarlo/GNN_LSAP](https://github.com/aircarlo/GNN_LSAP)
- **固定 commit：** `cdeb0ef8dd7c42d83b36ff689b3013c64b6d58e9`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** GPL-3.0
- **资产记录数：** 1

## 仓库摘要

仓库的冻结清单里只确认到 networks.py 这一处模型架构代码和 GPL-3.0 LICENSE；未发现可核实的数据集、训练入口、推理入口、评估脚本或检查点。README 仅在元数据层面出现，无法据此验证完整复现流程。

## 可复用模块与资源

### reusable_assets

- `networks.py`
  - 能力：model_architecture
  - 用途：GNN/LSAP 相关模型结构定义，适合作为静态架构参考
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态清单审查，未执行代码、未安装依赖、未跑测试。
- 冻结清单未标出训练/推理/评估入口，无法确认端到端流程。
- 未发现可核实的数据文件或检查点文件。
- README 仅有声明性元数据，内容未作为可复现证据展开。

## 仍未知

- main.py 与 helper_fn.py 的具体职责未在冻结清单中展开。
- 网络结构是否对应完整论文方法、以及是否存在外部下载数据，均未证实。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
