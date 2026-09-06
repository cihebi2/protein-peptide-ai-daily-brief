# jianzhang-xynu/hybridDBRpred

- **仓库：** [https://github.com/jianzhang-xynu/hybridDBRpred](https://github.com/jianzhang-xynu/hybridDBRpred)
- **固定 commit：** `429f91eb1e6ff0054a9a56a42ce684f73273e518`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 1

## 仓库摘要

该仓库静态上包含 HybridDBRpred 的模型结构、训练/验证/测试特征与标签、特征生成与推理脚本族、示例输出和一份权重文件；但未见 LICENSE、训练入口或可执行评估流程，因此只能判断资产存在，不能证明可复现或可直接复用。

## 可复用模块与资源

### reusable_assets

- `Models.py`
  - 能力：模型架构
  - 用途：定义预测模型的核心结构。
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态审查，未执行代码、未安装依赖、未运行测试。
- 未见训练入口或评估入口，无法证明端到端复现。
- 代码许可缺失，直接复用受阻。
- 路径存在不等于数据集、权重或脚本可用。
- 大文件可能仅为 promisor / 占位，不保证完整可读。

## 仍未知

- `serverScript/*.pl` 与 `forWebUse.py` 的真实调用链未验证，推理是否可独立运行未知。
- `final_model/model_weights.dat` 是否为完整可用 checkpoint、是否与当前代码版本匹配未知。
- `data/features/*` 与 `data/labels/*` 是否为完整训练/验证/测试集或仅冻结样例未知。
- `example/DNAgenie/results.csv` 是否来自真实评估还是演示输出未知。
- 是否存在未显式识别的第三方代码/数据来源未知。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
