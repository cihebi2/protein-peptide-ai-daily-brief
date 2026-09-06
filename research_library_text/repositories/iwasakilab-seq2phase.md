# iwasakilab/seq2phase

- **仓库：** [https://github.com/iwasakilab/seq2phase](https://github.com/iwasakilab/seq2phase)
- **固定 commit：** `4fb01c9e8d238a1a4bd271c991abe77b4f92f6b9`
- **审计批次：** addendum
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** MIT
- **资产记录数：** 20

## 仓库摘要

仓库是一个面向 LLPS client 预测的静态分析流水线：包含 nn_model.py、train_model.py、seq2phase.py，以及 ESM2 嵌入、特征筛选、超参调优、GO enrichment、UMAP、跨物种和区域分析的 notebooks；未见可核实的 checkpoint 或模型权重。

## 可复用模块与资源

### datasets

- `data/drllps_client_clstr_Homo_sapiens.fasta`
  - 能力：人类 DrLLPS 正样本集
  - 用途：训练/评测中的正样本序列集合
  - 复用状态：unknown；类型：unknown
- `data/swiss_prot_human_220916.fasta`
  - 能力：人类 Swiss-Prot 背景蛋白集
  - 用途：背景 proteome/负样本候选来源
  - 复用状态：unknown；类型：unknown
- `experiment/fig1/result/drllps_client_clstr_Homo_sapiens.fasta`
  - 能力：派生聚类结果集
  - 用途：下游分析中使用的聚类后客户端序列集合
  - 复用状态：partial；类型：unknown
- `experiment/fig5/result/qhuman_sMus_musculus.tsv`
  - 能力：跨物种查询结果表
  - 用途：跨物种命中/过滤结果的表格化输出
  - 复用状态：partial；类型：unknown

### evaluation

- `experiment/fig2/fig2bcS2_predict_vs_conventional.ipynb`
  - 能力：与传统特征对比
  - 用途：比较本方法与 conventional features 的表现
  - 复用状态：partial；类型：unknown
- `experiment/fig2/fig2cdefS2_vs_PSP_PScore.ipynb`
  - 能力：与 PSP/PScore 对比
  - 用途：与 PSP/PScore 等基线比较
  - 复用状态：partial；类型：unknown
- `experiment/fig4/fig4_umap.ipynb`
  - 能力：降维可视化
  - 用途：对 embedding 或预测空间做 UMAP 展示
  - 复用状态：partial；类型：unknown
- `experiment/fig6/fig6_score_distribution.ipynb`
  - 能力：分数分布分析
  - 用途：分析预测分数分布及阈值行为
  - 复用状态：partial；类型：unknown
- `experiment/fig7/fig7_region_wise.ipynb`
  - 能力：区域级分析
  - 用途：分析序列不同区域的贡献或得分
  - 复用状态：partial；类型：unknown

### inference

- `seq2phase.py`
  - 能力：批量推理
  - 用途：对新序列生成预测分数或类别
  - 复用状态：ready_for_review；类型：code_entry
- `experiment/fig2/fig2a_predict_client.ipynb`
  - 能力：客户端预测笔记本
  - 用途：执行 client protein 预测流程
  - 复用状态：partial；类型：unknown
- `experiment/fig5/fig5_cross-species_new.ipynb`
  - 能力：跨物种推理笔记本
  - 用途：对不同物种序列做推理并整理结果
  - 复用状态：partial；类型：unknown

### reusable_assets

- `nn_model.py`
  - 能力：模型结构定义
  - 用途：定义序列分类网络结构，供训练与推理复用
  - 复用状态：ready_for_review；类型：code_entry
- `train_model.py`
  - 能力：训练入口
  - 用途：执行模型训练、参数更新与保存流程
  - 复用状态：ready_for_review；类型：code_entry
- `seq2phase.py`
  - 能力：推理脚本
  - 用途：对输入蛋白序列进行预测/打分
  - 复用状态：ready_for_review；类型：code_entry
- `experiment/fig3/fig3_go_enrichment.ipynb`
  - 能力：功能富集分析笔记本
  - 用途：对预测客户端做 GO enrichment
  - 复用状态：partial；类型：unknown
- `experiment/fig5/fig5_cross-species.ipynb`
  - 能力：跨物种分析笔记本
  - 用途：进行跨物种同源过滤与预测分析
  - 复用状态：partial；类型：unknown

### training

- `train_model.py`
  - 能力：训练主流程
  - 用途：从标注序列训练分类模型
  - 复用状态：ready_for_review；类型：code_entry
- `experiment/fig2/for_fig2cdef_param_tune.ipynb`
  - 能力：超参调优
  - 用途：模型参数搜索与比较实验
  - 复用状态：partial；类型：unknown
- `experiment/fig2/table1_model_comparison_param_tune.ipynb`
  - 能力：模型对比调参
  - 用途：不同模型/配置的比较与调参
  - 复用状态：partial；类型：unknown

## 使用限制

- 仅做静态盘点，未执行代码、notebooks 或测试。
- dependencies 未安装，无法验证训练/推理链路是否可运行。
- 未见 tracked checkpoint/weight 文件，无法核实可复用模型产物。
- 第三方数据（如 DrLLPS、Swiss-Prot、PhaSepDB 相关文件）未见独立许可字段，复用需回溯上游条款。

## 仍未知

- nn_model.py、train_model.py 与 seq2phase.py 的具体网络结构、损失函数和 CLI 参数未读文件内容，无法确认实现细节。
- 数据文件是否为上游完整镜像、是否与原始数据库版本完全一致，静态证据不足。
- 部分 result/ 与 .dmnd 产物是否可由当前仓内输入完整重建，未实际运行无法确认。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
