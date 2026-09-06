# borgwardtlab/multimodalamr

- **仓库：** [https://github.com/borgwardtlab/multimodalamr](https://github.com/borgwardtlab/multimodalamr)
- **固定 commit：** `6d2d5fe8c9ca8444e7a31ab44c864b79e6897f90`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 0

## 仓库摘要

仓库是面向 DRIAMS 的多模态 AMR 预测代码与派生数据包，含训练、基线比较和特征构造，但未见 LICENSE、checkpoint 或独立推理入口。

## 可复用模块与资源

- 未发现可公开描述的结构化资产。
## 使用限制

- 仅做静态清点，未运行代码、未安装依赖、未验证可复现性。
- 未见 tracked checkpoint/model weight 文件，不能从静态证据确认任何已训练权重。
- processed_data/ 及 plot_*.csv 更像派生特征/结果，不等同原始数据。
- 仓库未见独立 inference 入口，推理可能嵌在训练或评估脚本中。

## 仍未知

- 原始 DRIAMS 数据与各派生表之间的上游来源、数据协议和版权边界未完全明示。
- `dd_experiments/graph2vec/2_embedding/graph2vec.py`、部分 R 脚本是否为 vendored third-party 代码，仅凭静态文件名无法确认。
- `README.md` 与脚本未足以确认所有 data/ 与 processed_data/ 文件的确切生成顺序。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
