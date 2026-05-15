# WR10 古诗词认知负荷写作能力 HLM 分析项目

## 项目简介

本项目实现"古诗词认知负荷对写作能力提升的跨年级预测分层线性回归模型构建研究"的完整数据分析流程, 基于 1920 名 3-6 年级学生为期一年的纵向追踪数据, 通过三层线性混合效应模型 (HLM) 探究认知负荷三维度对写作能力发展的预测机制。

## 研究设计

- **样本**: 1920 名学生 × 4 时点 = 7680 次观测
- **嵌套结构**: 学生 (L1, N=1920) ⊂ 班级 (L2, K=48) ⊂ 学校 (L3, J=12)
- **测量时点**: T1 (2024-09) → T2 (2024-12) → T3 (2025-03) → T4 (2025-09)
- **分析方法**: 三层线性混合模型、潜变量中介、跨层调节、二次生长曲线、10折交叉验证

## 项目架构

```
WR10_HLM_Project/
├── README.md                   # 本文件
├── requirements.txt            # Python依赖
├── config.py                   # 全局配置与论文参考值
├── run_all.py                  # 一键运行所有分析
├── data/                       # 数据目录
│   ├── 数据集.xlsx             # 19-Sheet主数据文件
│   └── WR10_Codebook_数据字典.pdf
├── src/                        # 核心分析模块
│   ├── __init__.py
│   ├── data_loader.py          # 数据加载
│   ├── descriptive.py          # 描述性统计 (复现 Table 1-2)
│   ├── reliability.py          # 信效度 (复现 Table 4)
│   ├── correlation.py          # 相关矩阵 (复现 Table 3)
│   ├── hlm_models.py           # HLM分析 (复现 Table 5-6)
│   ├── mediation_moderation.py # 中介+调节 (复现 Fig 9)
│   ├── prediction.py           # 预测模型 (复现 Table 6 + Fig 10)
│   ├── robustness.py           # 鲁棒性检验 (复现 Table 7)
│   ├── visualization.py        # 数据可视化 (复现 Fig 4,6-10)
│   └── utils.py                # 工具函数
├── analysis/                   # 分析脚本(顺序执行)
│   ├── 01_run_descriptive.py
│   ├── 02_run_reliability.py
│   ├── 03_run_correlation.py
│   ├── 04_run_hlm.py
│   ├── 05_run_mediation_moderation.py
│   ├── 06_run_prediction.py
│   ├── 07_run_robustness.py
│   └── 08_run_visualization.py
└── results/                    # 输出结果
    ├── tables/                 # CSV/Excel 表格
    └── figures/                # PNG/PDF 图像
```

## 环境要求

- Python ≥ 3.10
- 依赖见 `requirements.txt`

## 快速开始

### 方式1: 一键运行
```bash
cd WR10_HLM_Project
pip install -r requirements.txt
python run_all.py
```

### 方式2: 分步运行
```bash
cd analysis/
python 01_run_descriptive.py        # Table 1, 2
python 02_run_reliability.py        # Table 4
python 03_run_correlation.py        # Table 3
python 04_run_hlm.py                # Table 5, 6
python 05_run_mediation_moderation.py
python 06_run_prediction.py         # Table 6, Fig 10
python 07_run_robustness.py         # Table 7
python 08_run_visualization.py      # Fig 4, 6-10
```

## 输出说明

### `results/tables/`
| 文件 | 对应论文 | 说明 |
|---|---|---|
| Table1_Sample_Characteristics.csv | Table 1 | 样本基本特征 |
| Table2_Descriptive_Statistics.csv | Table 2 | 主要变量描述统计 |
| Table3_Correlation_Matrix.csv | Table 3 | T4数据相关矩阵 |
| Table4_Reliability_Validity.csv | Table 4 | 信效度指标 |
| Table5_Null_Model_Variance.csv | Table 5 | 零模型方差分解 |
| Table6_Path_Estimates.csv | Table 6 | 路径估计与建模目标 |
| Table7_Robustness_Tests.csv | Table 7 | 鲁棒性检验 |

### `results/figures/`
| 文件 | 对应论文 | 说明 |
|---|---|---|
| Fig4_Sample_Distribution.png | Figure 4 | 样本分布特征 |
| Fig6_Writing_Trajectories.png | Figure 6 | 各年级写作发展轨迹 |
| Fig7_CFA_Results.png | Figure 7 | 验证性因子分析 |
| Fig8_Growth_Models.png | Figure 8 | 生长模型比较 |
| Fig9_Mediation_Effects.png | Figure 9 | 跨层交互与中介效应 |
| Fig10_Prediction_Performance.png | Figure 10 | 预测模型性能 |

## 引用

Shi, P., & Zheng, L. (2025). Construction of a Hierarchical Linear Regression
Prediction Model for Classical Chinese Poetry Writing Ability Development.
*Heze University.*

## 联系方式

- 通讯作者: 史培根 (Peigen Shi)
- Email: 972593080@163.com
