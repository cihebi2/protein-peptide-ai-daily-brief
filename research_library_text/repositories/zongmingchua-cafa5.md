# zongmingchua/cafa5

- **仓库：** [https://github.com/zongmingchua/cafa5](https://github.com/zongmingchua/cafa5)
- **固定 commit：** `7624af166acd44c88a9624f5b7cacd09887a21fa`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 14

## 仓库摘要

静态清点表明该仓库是 PROTGOAT 的蛋白功能预测代码库：包含模型、GO hierarchy/ontology、PLM/abstract embedding、训练、推理与提交/测试流程；未见 bundled 数据集或 checkpoint，许可证为 MIT，数据与权重边界未在仓库内建立。

## 可复用模块与资源

### evaluation

- `tests/test_config.py`
  - 能力：validation and CI suite
  - 用途：回归测试与接口验证，覆盖 config/data/hierarchy/model/ontology/pipeline/shards/submission
  - 复用状态：partial；类型：config

### inference

- `src/protgoat/predict.py`
  - 能力：inference entrypoint
  - 用途：载入模型并生成功能预测
  - 复用状态：partial；类型：code_entry
- `src/protgoat/submission.py`
  - 能力：submission formatting
  - 用途：整理推理输出并生成提交文件
  - 复用状态：partial；类型：code_entry

### reusable_assets

- `src/protgoat/model.py`
  - 能力：protein function prediction model architecture
  - 用途：定义预测网络结构与输出头
  - 复用状态：partial；类型：code_entry
- `src/protgoat/hierarchy.py`
  - 能力：GO hierarchy propagation
  - 用途：处理 GO 父子层级与传播逻辑
  - 复用状态：partial；类型：code_entry
- `src/protgoat/ontology.py`
  - 能力：GO ontology utilities
  - 用途：载入与规范化 GO 本体术语
  - 复用状态：partial；类型：code_entry
- `src/protgoat/embeddings/plm.py`
  - 能力：protein PLM embeddings
  - 用途：生成蛋白语言模型表征
  - 复用状态：partial；类型：code_entry
- `src/protgoat/embeddings/abstracts.py`
  - 能力：abstract embeddings
  - 用途：生成文本摘要表征
  - 复用状态：partial；类型：code_entry
- `src/protgoat/configs/default.yaml`
  - 能力：task config recipes
  - 用途：default、bpo、cco、mfo 的配置模板入口
  - 复用状态：ready_for_review；类型：config

### training

- `src/protgoat/train.py`
  - 能力：training entrypoint
  - 用途：训练入口，组织优化循环与参数更新
  - 复用状态：partial；类型：code_entry
- `src/protgoat/data.py`
  - 能力：training data loader
  - 用途：读取与整理训练/验证样本
  - 复用状态：partial；类型：code_entry
- `src/protgoat/embeddings/plm.py`
  - 能力：protein PLM embeddings for training
  - 用途：训练阶段生成蛋白语言模型表征
  - 复用状态：partial；类型：code_entry
- `src/protgoat/embeddings/abstracts.py`
  - 能力：abstract embeddings for training
  - 用途：训练阶段生成文本摘要表征
  - 复用状态：partial；类型：code_entry
- `src/protgoat/configs/default.yaml`
  - 能力：training config recipes
  - 用途：训练超参数模板与任务配置
  - 复用状态：ready_for_review；类型：config

## 使用限制

- 仅做静态清点；未执行代码、未安装依赖、未运行测试。
- 冻结清单未包含 bundled data 或 checkpoint，无法据此确认可复现训练/推理。
- 仓库存在归档 notebook，但其是否仍代表当前流程无法从静态路径名确认。
- 外部下载器、预训练资源与数据许可未在冻结清单中完整展开。

## 仍未知

- CAFA5/GO 数据集的具体来源、拆分与下载方式未从冻结清单中直接读出。
- 训练是否实际产出并保存 checkpoint 无法从静态路径存在性推出。
- `notebooks/archive/*` 的当前用途与维护状态不明。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
