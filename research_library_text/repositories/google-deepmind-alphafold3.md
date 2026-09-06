# google-deepmind/alphafold3

- **仓库：** [https://github.com/google-deepmind/alphafold3](https://github.com/google-deepmind/alphafold3)
- **固定 commit：** `c0f97eda2f1f482fd94d3a38bece18c7069b4a5c`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** Apache-2.0
- **资产记录数：** 35

## 仓库摘要

该冻结仓库主要是 AlphaFold3 的静态推理与数据管线代码快照：可见推理入口、模型网络、结构读写、MSA/模板处理和 CI 测试；同时包含 13 个 examples JSON、测试 fixture 和采样数据库，但未见训练入口或真实模型 checkpoint，权重仅受单独条款约束。

## 可复用模块与资源

### datasets

- `examples/barnase_barstar.json`
  - 能力：蛋白-蛋白示例输入
  - 用途：官方示例输入之一，用于展示复合物 folding
  - 复用状态：ready_for_review；类型：config
- `examples/kras_g12c_sotorasib.json`
  - 能力：蛋白-小分子示例输入
  - 用途：展示蛋白与配体联合建模输入
  - 复用状态：ready_for_review；类型：config
- `examples/modified_rna.json`
  - 能力：RNA 修饰示例输入
  - 用途：展示修饰 RNA 场景的输入模板
  - 复用状态：ready_for_review；类型：config
- `examples/ubiquitin_monomer.json`
  - 能力：单体蛋白示例输入
  - 用途：最小化蛋白单体示例
  - 复用状态：ready_for_review；类型：config
- `src/alphafold3/common/test_data/alphafold_input.json`
  - 能力：测试输入 JSON
  - 用途：单元测试和输入格式回归样例
  - 复用状态：ready_for_review；类型：config
- `src/alphafold3/common/test_data/test_template.mmcif`
  - 能力：模板结构 fixture
  - 用途：模板对齐与结构解析测试样例
  - 复用状态：ready_for_review；类型：unknown
- `src/alphafold3/test_data/featurised_example.json`
  - 能力：特征化示例
  - 用途：预处理后特征的测试样例
  - 复用状态：ready_for_review；类型：config
- `src/alphafold3/test_data/miniature_databases/uniprot_all__subsampled_1000.fasta`
  - 能力：采样蛋白数据库片段
  - 用途：缩小版序列数据库，用于离线测试与示例运行
  - 复用状态：partial；类型：unknown
- `src/alphafold3/test_data/miniature_databases/rfam_14_4_clustered_rep_seq__subsampled_1000.fasta`
  - 能力：采样 RNA 数据库片段
  - 用途：缩小版 RNA 库，用于测试和示例检索
  - 复用状态：partial；类型：unknown
- `src/alphafold3/test_data/miniature_databases/pdb_mmcif/5y2e.cif`
  - 能力：采样结构数据库片段
  - 用途：PDB/mmCIF 结构样本，用于离线测试
  - 复用状态：partial；类型：unknown

### evaluation

- `.github/workflows/ci.yaml`
  - 能力：CI 工作流
  - 用途：定义自动化测试与检查流程
  - 复用状态：ready_for_review；类型：config
- `run_alphafold_test.py`
  - 能力：端到端回归测试
  - 用途：验证推理主流程与回归输出
  - 复用状态：ready_for_review；类型：code_entry
- `run_alphafold_data_test.py`
  - 能力：数据管线测试
  - 用途：验证数据/特征生成子系统
  - 复用状态：ready_for_review；类型：code_entry
- `src/alphafold3/common/folding_input_test.py`
  - 能力：输入格式单测
  - 用途：检查输入解析与验证逻辑
  - 复用状态：ready_for_review；类型：code_entry
- `src/alphafold3/structure/test_utils.py`
  - 能力：结构测试工具
  - 用途：支撑结构相关测试与断言
  - 复用状态：ready_for_review；类型：code_entry
- `src/alphafold3/test_data/alphafold_run_outputs/run_alphafold_test_output_bucket_default.pkl`
  - 能力：黄金回归输出
  - 用途：作为回归测试的 golden output
  - 复用状态：partial；类型：unknown
- `src/alphafold3/test_data/alphafold_run_outputs/run_alphafold_test_output_bucket_1024.pkl`
  - 能力：黄金回归输出
  - 用途：作为另一组回归测试的 golden output
  - 复用状态：partial；类型：unknown

### inference

- `run_alphafold.py`
  - 能力：推理入口
  - 用途：驱动端到端结构预测推理
  - 复用状态：ready_for_review；类型：code_entry
- `src/alphafold3/model/model.py`
  - 能力：推理模型主干
  - 用途：构造并执行核心预测模型
  - 复用状态：ready_for_review；类型：code_entry
- `src/alphafold3/test_data/model_config.json`
  - 能力：推理配置样例
  - 用途：提供测试/示例级模型配置 recipe
  - 复用状态：ready_for_review；类型：config
- `src/alphafold3/model/params.py`
  - 能力：模型参数装配
  - 用途：组织与加载推理所需参数引用
  - 复用状态：partial；类型：code_entry
- `src/alphafold3/model/network/diffusion_transformer.py`
  - 能力：扩散式结构生成模块
  - 用途：实现扩散/变换器式结构生成核心
  - 复用状态：ready_for_review；类型：code_entry
- `src/alphafold3/model/post_processing.py`
  - 能力：结果后处理
  - 用途：将模型输出整理为最终结构与附加字段
  - 复用状态：ready_for_review；类型：code_entry

### reusable_assets

- `run_alphafold.py`
  - 能力：命令行推理入口
  - 用途：启动一次完整 folding / inference 流程
  - 复用状态：ready_for_review；类型：code_entry
- `fetch_databases.sh`
  - 能力：外部数据库下载/预取脚本
  - 用途：获取运行所需的外部序列/结构数据库；不是 bundled data
  - 复用状态：partial；类型：code_entry
- `src/alphafold3/common/folding_input.py`
  - 能力：输入对象解析
  - 用途：解析、校验并规范化 folding 输入
  - 复用状态：ready_for_review；类型：code_entry
- `src/alphafold3/data/pipeline.py`
  - 能力：序列特征生成管线
  - 用途：构建特征并串接 MSA、模板与结构相关预处理
  - 复用状态：ready_for_review；类型：code_entry
- `src/alphafold3/data/templates.py`
  - 能力：模板处理
  - 用途：模板检索、对齐与模板特征组装
  - 复用状态：ready_for_review；类型：code_entry
- `src/alphafold3/data/tools/msa_tool.py`
  - 能力：MSA 工具封装
  - 用途：封装外部 MSA 工具调用，服务于序列检索与对齐
  - 复用状态：ready_for_review；类型：code_entry
- `src/alphafold3/data/msa.py`
  - 能力：MSA 数据结构与处理
  - 用途：MSA 读写、过滤与内部表示转换
  - 复用状态：ready_for_review；类型：code_entry
- `src/alphafold3/model/model.py`
  - 能力：模型主干组装
  - 用途：组装核心模型前向过程与推理调用
  - 复用状态：ready_for_review；类型：code_entry
- `src/alphafold3/model/network/atom_cross_attention.py`
  - 能力：原子级交互注意力模块
  - 用途：建模原子级跨实体交互
  - 复用状态：ready_for_review；类型：code_entry
- `src/alphafold3/model/confidences.py`
  - 能力：置信度计算
  - 用途：生成结构置信度与相关评分
  - 复用状态：ready_for_review；类型：code_entry
- `src/alphafold3/model/scoring/scoring.py`
  - 能力：几何与立体化学评分
  - 用途：对齐、几何与 stereo 相关评分辅助
  - 复用状态：ready_for_review；类型：code_entry
- `src/alphafold3/structure/mmcif.py`
  - 能力：结构 mmCIF 读写
  - 用途：结构结果的 mmCIF 序列化与解析
  - 复用状态：ready_for_review；类型：code_entry

## 使用限制

- 仅做静态清点，未执行代码、未安装依赖、未运行测试
- 路径存在不等于功能可复现或结果已验证
- 冻结快照未给出真实模型 checkpoint，无法从静态证据确认权重分发与加载链路
- 部分 miniature_databases 可能源自第三方数据库，具体再分发许可需要人工复核

## 仍未知

- 未见训练入口或训练模块，无法判断是否存在未冻结的预训练/微调流程
- 未见实际权重文件（如 .ckpt/.safetensors/.npz 等），仅看到权重使用政策
- examples 与 test_data 的部分内容可能是项目定制或第三方样本，来源边界未完全展开

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
