# xiaodiyangpku/multimodalppi

- **仓库：** [https://github.com/xiaodiyangpku/multimodalppi](https://github.com/xiaodiyangpku/multimodalppi)
- **固定 commit：** `28c00645a2d701e98d1c27645e18979ec9cafea7`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 0

## 仓库摘要

该仓库是一个面向 human-herpesvirus PPI 预测的静态实验仓库，包含编码、特征融合、训练/测试与多组数据切分，但未发现 LICENSE 或可验证 checkpoint，直接复用边界不清。

## 可复用模块与资源

- 未发现可公开描述的结构化资产。
## 使用限制

- 仅做静态审查，未执行仓库代码或测试。
- 依赖未安装，submodules 未初始化。
- 未发现 LICENSE，直接复用边界不清。
- xaa 至 xat 等无扩展名文件的实际内容与来源未核实。
- 结果 txt 与数据切分文件是否为作者生成、转录或外部基准拷贝，均无法仅凭路径确认。

## 仍未知

- `script/3_train_test.py` 具体是训练入口、测试脚本还是二者合一，只能从文件名推断。
- `script/GO/*.txt` 与 `script/Net/*.txt` 的生成方式、版权和外部来源未核实。
- `DeepViral_dataset`、`TransPPI_dataset`、`table2_dataset`、`sample` 内文件是否为原始数据、整理切分或实验副产物不明确。
- `xaa` 到 `xat` 的 16 个无扩展名文件是否为数据分片、模型中间产物或其他文本块不明。
- README 是否声明了额外许可或数据使用条件，当前未做内容级核验。

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
