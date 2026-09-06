# bleach366/molpif

- **仓库：** [https://github.com/bleach366/molpif](https://github.com/bleach366/molpif)
- **固定 commit：** `dae95cd665f6c3c76290728372eddfb9f34713f5`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 0

## 仓库摘要

MolPIF 的静态代码仓库快照，含模型实现、PDBBind 数据加载、训练/采样/评估脚本和示例结构，但未见 checkpoint 或 LICENSE。

## 可复用模块与资源

- 未发现可公开描述的结构化资产。
## 使用限制

- 仅做静态审查，未运行代码、未安装依赖、未执行测试。
- 未发现 checkpoint 或模型权重文件，无法验证可复现推理。
- 仓库未见 LICENSE，代码与数据的直接复用受限。
- 示例数据与 `fpscores.pkl.gz` 的来源、完整性和许可边界未被静态清单核实。

## 仍未知

- `PDBBind` 具体版本、划分策略与预处理细节未从冻结清单中确认。
- `sample_for_pocket.py` 是否依赖外部下载器或运行时资源，静态清单无法确认。
- `core/evaluation/utils/fpscores.pkl.gz` 是否确为 RDKit 相关 vendored 资源及其上游许可未核实。
- `example/AMY3_*` 是否为项目自带示例还是外部样本，静态证据不足。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
