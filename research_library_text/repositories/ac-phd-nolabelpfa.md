# AC-PHD/NoLabelPFA

- **仓库：** [https://github.com/AC-PHD/NoLabelPFA](https://github.com/AC-PHD/NoLabelPFA)
- **固定 commit：** `f5741143bc7b732d675a77ef6e798ba5d4d82e68`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** not_found
- **资产记录数：** 20

## 仓库摘要

仓库主要是 No_label_PFA 的静态代码与分析笔记本，覆盖输入准备、principal feature selection、mutual information、DBSCAN/HDBSCAN、UMAP/t-SNE 和解释脚本；未发现 LICENSE、可识别 checkpoint 或可验证的数据加载/训练产物，`Test_Files.zip` 与 `src.zip` 仅能从文件名确认存在，内容未展开。

## 可复用模块与资源

### datasets

- `No_label_PFA/Test_Files.zip`
  - 能力：示例/测试输入
  - 用途：静态压缩包；推测用于测试或示例输入，但未解包，内部内容未确认
  - 复用状态：unknown；类型：unknown

### evaluation

- `No_label_PFA/src/no_label_pfa/compare_dbscan_labels.py`
  - 能力：聚类结果比较
  - 用途：比较 DBSCAN 标签/结果
  - 复用状态：blocked；类型：code_entry
- `No_label_PFA/src/no_label_pfa/alt_compare_dbscan_labels.py`
  - 能力：聚类结果比较
  - 用途：DBSCAN 结果的替代比较路径
  - 复用状态：blocked；类型：code_entry
- `No_label_PFA/src/no_label_pfa/compare_hdbscan_labels.py`
  - 能力：聚类结果比较
  - 用途：比较 HDBSCAN 标签/结果
  - 复用状态：blocked；类型：code_entry
- `No_label_PFA/src/no_label_pfa/find_cluster_differences.py`
  - 能力：簇差异分析
  - 用途：分析簇间差异
  - 复用状态：blocked；类型：code_entry
- `No_label_PFA/src/no_label_pfa/find_cluster_differences_HDB.py`
  - 能力：簇差异分析
  - 用途：分析 HDBSCAN 簇间差异
  - 复用状态：blocked；类型：code_entry
- `No_label_PFA/src/no_label_pfa/validate_feature_selection.py`
  - 能力：特征选择验证
  - 用途：验证特征选择结果
  - 复用状态：blocked；类型：code_entry

### inference

- `No_label_PFA/src/no_label_pfa/execute_PFA.py`
  - 能力：推理/批处理执行
  - 用途：对输入数据执行 No_label_PFA 流水线并产出结果
  - 复用状态：blocked；类型：code_entry

### reusable_assets

- `PrepareSeurat2PFAinput.R`
  - 能力：数据准备
  - 用途：将 Seurat 输入整理为 PFA 可用格式
  - 复用状态：blocked；类型：code_entry
- `No_label_PFA/01_File_Preparation_Script.ipynb`
  - 能力：文件准备
  - 用途：准备输入文件与预处理步骤
  - 复用状态：blocked；类型：unknown
- `No_label_PFA/src/no_label_pfa/execute_PFA.py`
  - 能力：核心流水线
  - 用途：执行 No_label_PFA 主流程
  - 复用状态：blocked；类型：code_entry
- `No_label_PFA/src/no_label_pfa/find_relevant_principal_features.py`
  - 能力：特征选择
  - 用途：筛选相关 principal features
  - 复用状态：blocked；类型：code_entry
- `No_label_PFA/src/no_label_pfa/get_mutual_information.py`
  - 能力：互信息排序
  - 用途：计算 mutual information 用于特征排序
  - 复用状态：blocked；类型：code_entry
- `No_label_PFA/src/no_label_pfa/dbscan.py`
  - 能力：聚类
  - 用途：DBSCAN 聚类
  - 复用状态：blocked；类型：code_entry
- `No_label_PFA/src/no_label_pfa/hdbscan.py`
  - 能力：聚类
  - 用途：HDBSCAN 聚类
  - 复用状态：blocked；类型：code_entry
- `No_label_PFA/src/no_label_pfa/umap.py`
  - 能力：降维
  - 用途：UMAP 可视化/降维
  - 复用状态：blocked；类型：code_entry
- `No_label_PFA/src/no_label_pfa/tsne.py`
  - 能力：降维
  - 用途：t-SNE 可视化/降维
  - 复用状态：blocked；类型：code_entry
- `No_label_PFA/src/no_label_pfa/tree_explanation.py`
  - 能力：解释
  - 用途：树模型解释
  - 复用状态：blocked；类型：code_entry
- `No_label_PFA/src/no_label_pfa/shaply_explanation.py`
  - 能力：解释
  - 用途：SHAP 解释
  - 复用状态：blocked；类型：code_entry

### training

- `No_label_PFA/02_No_label_PFA.ipynb`
  - 能力：训练/拟合入口
  - 用途：运行主分析流程；可能承担拟合/生成中间结果，但未见独立模型权重输出
  - 复用状态：blocked；类型：unknown

## 使用限制

- 仅做静态清单审查，未执行代码、未安装依赖、未运行测试
- 未发现可验证的模型 checkpoint/权重文件
- `Test_Files.zip` 与 `src.zip` 仅能确认存在，内容未展开
- `.pyc` 文件存在但不作为可复用源码证据
- 仓库未见明确数据下载器或数据来源说明

## 仍未知

- `No_label_PFA/Test_Files.zip` 是否为测试集或示例输入尚不确定
- `No_label_PFA/src.zip` 更像源码打包件，但未解包，不能确认其内部构成
- `02_No_label_PFA.ipynb` 是演示、批处理还是主入口，单靠清单无法完全确定
- 未见明确的外部数据许可与来源记录

> 许可证缺失或不明确：不要将其中代码、数据或模型作为可直接复用资源。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
