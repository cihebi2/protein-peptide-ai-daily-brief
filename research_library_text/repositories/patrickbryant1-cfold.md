# patrickbryant1/cfold

- **仓库：** [https://github.com/patrickbryant1/cfold](https://github.com/patrickbryant1/cfold)
- **固定 commit：** `a66406e981ce434b985120f8c40712d17290408c`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 0

## 仓库摘要

该仓库是一个基于 AlphaFold 的结构预测推理仓库，围绕 alternative protein conformations 提供方法代码、预测脚本、测试夹具和少量示例数据；冻结清单中未发现训练入口、checkpoint 或仓库级 LICENSE。

## 可复用模块与资源

- 未发现可公开描述的结构化资产。
## 使用限制

- 仅做静态清点；未执行仓库代码、未安装依赖、未运行测试
- 冻结清单中未发现 checkpoint 文件
- src/alphafold 子树看起来像第三方 AlphaFold 代码，但上游许可边界未在冻结证据中核验
- 示例数据与测试夹具的来源/许可未核验

## 仍未知

- README.md 正文未展开，无法从冻结证据确认作者声明、外部权重下载方式或许可证说明
- 未发现训练入口，故无法判断是否存在未被列出的训练流程
- 没有任何 checkpoint 路径，无法确认模型权重是否完全依赖外部下载
- tests_ci 仅证明存在单元测试文件，不代表通过或可复现

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
