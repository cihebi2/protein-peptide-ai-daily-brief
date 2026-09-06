# arcimboldo-team/vairo

- **仓库：** [https://github.com/arcimboldo-team/vairo](https://github.com/arcimboldo-team/vairo)
- **固定 commit：** `8ddc70072c4e9a83128ecb716fbd1bafafd56c7a`
- **审计批次：** base
- **分析边界：** 仅静态审计和语义盘点；未执行代码、未训练、未复现。
- **许可证：** BSD-3-Clause
- **资产记录数：** 6

## 仓库摘要

该仓库是一个静态可见的 VAIRO 网页应用与分析工具包，核心围绕 AlphaFold、模板、序列、结构与输出可视化；冻结清单未显示训练、评测、数据集或模型 checkpoint。

## 可复用模块与资源

### inference

- `vairo/libs/run_alphafold.py`
  - 能力：AlphaFold 相关推理/运行封装
  - 用途：围绕 AlphaFold 预测流程的调用与编排
  - 复用状态：partial；类型：code_entry
- `vairo/libs/hhsearch.py`
  - 能力：模板检索与匹配辅助
  - 用途：支持模板搜索/匹配以服务推理流程
  - 复用状态：partial；类型：code_entry
- `vairo/app/templates/input.html`
  - 能力：网页交互与结果展示层
  - 用途：呈现输入、输出、参数化与摘要页面
  - 复用状态：partial；类型：unknown

### reusable_assets

- `vairo/app/app.py`
  - 能力：Web 应用入口与页面渲染骨架
  - 用途：提供应用主入口并组织前端页面/交互流程
  - 复用状态：partial；类型：code_entry
- `vairo/libs/bioutils.py`
  - 能力：分析与可视化辅助模块
  - 用途：序列、模板、特征、结构、输出与绘图等通用处理
  - 复用状态：partial；类型：code_entry
- `vairo/binaries/cc_analysis_linux`
  - 能力：打包的分析二进制工具
  - 用途：为结构/接触/hinge 等分析提供本地可执行工具
  - 复用状态：partial；类型：unknown

## 使用限制

- 仅做静态盘点，未执行代码、未安装依赖、未运行测试。
- 冻结清单不等于可复现证明；路径存在只能证明文件存在。
- 仓库中第三方二进制与前端资源的来源/许可未逐文件核验。

## 仍未知

- `vairo/ALEPH` 目录的具体内容和用途未读取。
- `vairo/binaries/` 中的可执行文件是否全部为项目自带、还是外部 vendored 版本，静态清单无法完全确认。
- 未见训练/评测/数据/ckpt 路径，但这只能说明冻结清单未列出，并不等于仓库历史中从未出现。

> 发布边界：路径和摘要来自 commit 固定的静态盘点，不代表代码可运行、训练可复现或许可证兼容。
