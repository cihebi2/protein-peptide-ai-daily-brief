# 论文声明 GitHub 仓库对应关系核验表（2026-09-17）

> 范围：新批次 183 篇论文声明的 26 个仓库。核验维度：克隆有效工作树 + 静态审计完成。

**克隆且审计齐全 22/26**；最终未获取 4 个（3 个网络节流 + 1 个上游已删）。

| 仓库 | 关联论文 | 克隆 | 审计 |
|---|---|---|---|
| hicai-zju/plmeae | 10.1038/s41467-025-56751-8 | ✓ | ✓ |
| tjgu/mitar | 10.1038/s42256-024-00836-4 | ✓ | ✓ |
| priorlabs/tabpfn | 10.1038/s41586-024-08328-6 | ✓ | ✓ |
| a-healey/r570scripts | 10.1038/s41586-024-07231-4 | ✓ | ✓ |
| grantlandwehr/accelerated-enzyme-engineering | 10.1038/s41467-024-55399-0 | ✓ | ✓ |
| shibhansh/loss-of-plasticity | 10.1038/s41586-024-07711-7 | ✓ | ✓ |
| bowang-lab/agile | 10.1038/s41467-024-50619-z | ✓ | ✓ |
| ml4bio/rhodesign | 10.1038/s43588-024-00720-6 | ✓ | ✓ |
| haichengyi/acpdl | 10.1016/j.fmre.2024.04.021 | ✗ | — |
| ntranoslab/esm-variants | 10.1038/s41588-023-01465-0 | ✓ | ✓ |
| oxpig/calm | 10.1038/s42256-024-00791-0 | ✓ | ✓ |
| rosettacommons/rfantibody | 10.1038/s41586-025-09721-5 | ✓ | ✓ |
| xcompass-ai/genecompass | 10.1038/s41422-024-01034-y | ✗ | 跳过 |
| felixjwong/antibioticsai | 10.1038/s41586-023-06887-8 | ✗ | 跳过 |
| chemprop/chemprop | 10.1038/s41586-023-06887-8 | ✓ | ✓ |
| cedergrouphub/chgnet | 10.1038/s42256-023-00716-3 | ✓ | ✓ |
| a96123155/utr-lm | 10.1038/s42256-024-00823-9 | ✓ | ✓ |
| instadeepai/nucleotide-transformer | 10.1038/s41592-024-02523-z | ✓ | ✓ |
| jianing-qiu/awesome-healthcare-foundation-models | 10.1109/jbhi.2023.3316750 | ✓ | ✓ |
| songlab-cal/gpn | 10.1073/pnas.2311219120 | ✓ | ✓ |
| biofam/mofa | 10.1186/s43556-025-00340-0 | ✓ | ✓ |
| irinagain/slide-paper | 10.1186/s43556-025-00340-0 | ✓ | ✓ |
| yangzi4/inmf | 10.1186/s43556-025-00340-0 | ✗ | 跳过 |
| rosettacommons/rfdiffusion | 10.1101/2025.09.29.678898 | ✓ | ✓ |
| hive-uoft/prodcarl | 10.48550/arxiv.2602.00157 | ✓ | ✓ |
| zhenchengfang/metaprobiotics | 10.1093/bib/bbae085 | ✓ | ✓ |

## 未获取原因
- felixjwong/antibioticsai（Nature MRSA 论文）：GitHub 经代理克隆多次 curl 56 中断——**代码存在但网络不可达**，可手动浏览器下载 zip 补齐
- xcompass-ai/genecompass：同上（大仓网络中断）
- yangzi4/inmf：同上
- haichengyi/acpdl：上游 Repository not found（已删除或改名）——论文代码声明失效