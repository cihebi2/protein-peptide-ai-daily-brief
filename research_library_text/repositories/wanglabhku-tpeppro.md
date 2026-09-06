# wanglabhku/TPepPro

- **仓库：** [https://github.com/wanglabhku/TPepPro](https://github.com/wanglabhku/TPepPro)
- **固定 commit：** `fae7337ca275ac6711ffebc94e105ad98b7ffdc5`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 9

## 仓库摘要

仓库冻结快照包含 TPepPro 的模型代码、预处理脚本、样例数据和一个保存的 GAT checkpoint；未见显式 LICENSE，且未执行代码或测试。

## 可复用模块与资源

### checkpoints

- `test_sample_model/save_model_pkl/TPepPro_receptor-peptide(train 19187 pairs)_GAT.pkl`
  - 能力：已保存模型参数
  - 用途：GAT 模型 checkpoint，可能用于示例推理或复现实验状态
  - 复用状态：blocked；类型：unknown

### datasets

- `data/receptor-peptide.actions.tsv`
  - 能力：主受体-肽相互作用数据
  - 用途：主数据表/样本边界，配合 `data/receptor(14374)-peptide(9594)_dictionary.xlsx` 形成训练数据资源
  - 复用状态：blocked；类型：unknown
- `test_sample_model/data/actions/sample_cmap.actions.tsv`
  - 能力：样例 contact-map 评估包
  - 用途：样例/测试运行所需的 contact-map 元数据与配套 npz、embedding 资源
  - 复用状态：blocked；类型：unknown

### evaluation

- `test_sample_model/my_main_test.py`
  - 能力：样例 smoke test
  - 用途：在 sample data 上运行模型的测试/演示流程，不等同于正式 benchmark 评测
  - 复用状态：blocked；类型：code_entry

### inference

- `data pre-processing/generate_embeddings.py`
  - 能力：特征生成与推理预处理
  - 用途：为模型推理/评估生成嵌入与 contact map 输入
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `model/TAGlayer.py`
  - 能力：核心模型架构模块
  - 用途：实现 TAG/GAT 风格层、图加载、序列编码与通用工具，构成主模型的核心代码边界
  - 复用状态：blocked；类型：code_entry
- `data pre-processing/generate_contact_map.py`
  - 能力：contact map 与 embedding 预处理
  - 用途：生成 contact map 和 embeddings 的预处理流程，可作为推理前特征构建模块
  - 复用状态：blocked；类型：code_entry
- `dgl_cu101-0.6.1-cp37-cp37m-manylinux1_x86_64.whl`
  - 能力：vendored 第三方运行依赖
  - 用途：打包的 DGL 轮子文件；属于第三方依赖边界，不应按项目原创资产处理
  - 复用状态：blocked；类型：unknown

### training

- `model/my_main.py`
  - 能力：训练/验证流程
  - 用途：训练驱动与验证循环入口；冻结清单未显示独立 training entrypoint
  - 复用状态：blocked；类型：code_entry

## 使用限制

- 仅做静态清点，未安装依赖、未运行训练/测试、未验证 checkpoint
- 主数据来源/授权未在冻结清单中说明
- 训练入口与评估流程更多表现为模块/样例脚本，未见完整可复现流水线
- test_sample_model 中存在与主目录重复的代码，不能视为独立贡献

## 仍未知

- sample_cmap 与 `TPepPro_receptor-peptide(train 19187 pairs)_GAT.pkl` 的生成关系未验证
- data/receptor(14374)-peptide(9594)_dictionary.xlsx 是否为原始数据、派生表或外部资源不明
- vendored `dgl_cu101` wheel 的准确许可证和再分发条件未核实
- README 是否描述额外下载步骤/外部数据依赖，冻结清单未体现

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
