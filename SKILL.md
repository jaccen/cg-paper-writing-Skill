---
name: cg-paper-writing
description: >-
  Academic paper writing skill for 3D vision, computer graphics, CAD, and 3D understanding.
  Covers NeRF, 3D Gaussian Splatting, multi-view stereo, SLAM, point cloud processing,
  3D shape understanding/generation, CAD modeling, reverse engineering, 3D scene understanding.
  Use when the user asks to write, refine, or polish academic papers in CG/3D vision venues
  (CVPR, ICCV, ECCV, SIGGRAPH, EG, PG, TVCG, CGF) or doctoral dissertations.
  Provides domain terminology conventions, reviewer concern analysis, experiment design guidance,
  and venue-specific writing patterns. Trigger on: paper writing, draft refinement, rebuttal,
  introduction/related work/methodology/experiment sections, abstract, contribution summary.
name_cn: 三维视觉与计算机图形学论文写作
description_cn: 三维视觉/计算机图形学/CAD方向论文写作辅助，涵盖NeRF、3DGS、点云处理、3D形状理解/生成、CAD建模、逆向工程、3D场景理解、SLAM等，支持CVPR/ICCV/SIGGRAPH等顶会及博士论文
---

# 三维视觉与计算机图形学论文写作

面向三维重建、计算机图形学、CAD建模、3D理解与生成方向的学术写作辅助，覆盖从摘要到结论的全流程。

## 核心领域术语规范

详细术语对照表与易错点见 [references/terminology.md](references/terminology.md)，以下为速查。

### 渲染与重建通用术语

| 中文 | 英文 | 备注 |
|---|---|---|
| 新视角合成 | Novel View Synthesis (NVS) | 首字母大写 |
| 三维高斯泼溅 | 3D Gaussian Splatting (3DGS) | 首次出现写全称 |
| 神经辐射场 | Neural Radiance Field (NeRF) | 首次出现写全称 |
| 体密度 | Volume density | σ，勿与opacity混用 |
| 不透明度 | Opacity | α |
| 透射率 | Transmittance | T = ∏(1-α) |
| α合成 | Alpha compositing | 渲染管线核心操作 |
| 运动恢复结构 | Structure from Motion (SfM) | 初始化步骤 |
| 多视角立体视觉 | Multi-View Stereo (MVS) | 传统重建范式 |
| 遮挡关系 | Occlusion | 多视角几何核心问题 |

### CAD与逆向工程术语

| 中文 | 英文 | 备注 |
|---|---|---|
| 边界表示 | Boundary Representation (B-rep) | CAD核心表示 |
| 构造实体几何 | Constructive Solid Geometry (CSG) | 布尔运算建模 |
| 参数化建模 | Parametric modeling | 草图约束→3D |
| 逆向工程 | Reverse engineering | 点云/网格→CAD |
| 草图约束 | Sketch constraint | 2D草图→3D建模 |
| 拉伸/旋转/扫掠 | Extrude / Revolve / Sweep | 基本体素操作 |
| 布尔运算 | Boolean operation | 并集/交集/差集 |
| 特征识别 | Feature recognition | 从网格/点云提取CAD特征 |
| 自由曲面 | Freeform surface | NURBS/Bézier曲面 |
| 容差分析 | Tolerance analysis | 工程精度 |

### 3D形状理解术语

| 中文 | 英文 | 备注 |
|---|---|---|
| 点云分割 | Point cloud segmentation | 语义/实例/部件级 |
| 点云配准 | Point cloud registration | ICP及其变体 |
| 法线估计 | Normal estimation | 局部几何特征 |
| 形状补全 | Shape completion | 部分观测→完整形状 |
| 3D目标检测 | 3D object detection | 点云/体素/鸟瞰图 |
| 紧凑表示 | Compact representation | 压缩/编码/量化 |
| 部件分割 | Part segmentation | 按语义部件分解 |

### 3D生成与编辑术语

| 中文 | 英文 | 备注 |
|---|---|---|
| 文本到3D | Text-to-3D | 大模型驱动 |
| 图像到3D | Image-to-3D | 单/多视角 |
| 3D生成模型 | 3D generative model | GAN/Diffusion/Flow |
| 形状编辑 | Shape editing | 变形/风格迁移/局部编辑 |
| 纹理生成 | Texture generation / synthesis | UV映射 + 纹理合成 |
| 3D感知扩散模型 | 3D-aware diffusion model | 2D扩散模型的3D扩展 |
| 几何先验 | Geometric prior | 深度/法线/表面法 |
| 体素化 | Voxelization | 点云/网格→体素网格 |

### 3D场景理解术语

| 中文 | 英文 | 备注 |
|---|---|---|
| 语义分割 | Semantic segmentation | 逐点/逐面片分类 |
| 实例分割 | Instance segmentation | 区分同类不同个体 |
| 场景重建 | Scene reconstruction | 室内/室外/城市级 |
| SLAM | Simultaneous Localization and Mapping | 实时位姿估计与建图 |
| 深度估计 | Depth estimation | 单目/双目/多目 |
| 鸟瞰图 | Bird's Eye View (BEV) | 自动驾驶常用表示 |
| 3D占用网格 | 3D occupancy grid | 体素级语义占据 |
| 场景流 | Scene flow | 3D运动场估计 |

## 写作流程

### 摘要（Abstract）

结构：问题 → 不足 → 本文方法（一句话）→ 核心机制（1-2句）→ 实验结果（带数据）。

- 字数：CVPR/ICCV 150-250词；SIGGRAPH 200-300词；博士论文 500-800字
- 禁止：未定义缩写、引用、"we"以外的主语
- 必须包含：方法名称、核心指标数值、对比baseline

### 引言（Introduction）

标准结构（适用于所有目标会议）：
1. 领域背景 + 该方向建立的基本范式（1段）
2. 已有工作的分类综述 + 各类方法的共性不足（1-2段）
3. 本文动机：从不足中引出研究问题（1段）
4. 本文方法概述：核心思想 + 2-3个关键设计（1段）
5. 实验总结：主要指标 + 对比优势（1段）

**引言写作禁忌**：
- 不在引言中展开数学公式（最多一个核心公式用于直观说明）
- 不在引言中列举实验细节（具体数字放实验部分）
- 避免通用乐观结尾（"我们相信本研究将推动该领域发展"）

### 相关工作（Related Work）

组织原则：按主题分组，而非按论文逐一罗列。

每个主题段落结构：
1. 该主题的共性方法（2-3句概括）
2. 代表性工作举例（带引用，说明每篇做了什么）
3. **关键**：与本文的区别（最后1-2句）

三维视觉论文常见分组：
- 神经辐射场与新视角合成（NeRF/3DGS及其变体）
- 点云处理与3D理解（分割/配准/检测）
- 3D生成与编辑（文本/图像到3D、形状编辑）
- CAD建模与逆向工程（参数化建模、特征提取）
- 3D场景理解与SLAM（语义重建、位姿估计）
- 高频/边界表达（如有符号方法、频域方法）
- 压缩与加速

### 方法（Methodology）

结构：总体框架图 → 各模块展开。

- 先给出整体pipeline/架构图（图1），后续逐模块引用
- 每个新符号首次出现时必须定义
- 公式编号连续，引用格式：式(1)、式(2)
- 每个模块结尾用1句话总结该模块的作用

### 实验（Experiments）

必须包含的实验：
1. **数据集**：列出全部数据集，说明训练/测试划分
2. **评估指标**：根据方向选择（见下方各方向指标）
3. **基线对比**：至少包含当前SOTA
4. **消融实验**：逐一验证每个核心模块的贡献

**各方向核心评估指标**：

| 方向 | 核心指标 | 补充指标 |
|---|---|---|
| 新视角合成 | PSNR↑ SSIM↑ LPIPS↓ | FPS、基元数量 |
| 3D形状理解 | mIoU↑ mAcc↑ | F1-score、AUC |
| 3D生成 | FID↓、1-NNA-CD↓、1-NNA-EMD↓ | MMD、COV |
| 点云配准 | RMSE↓、Chamfer距离↓ | RRE、RTE |
| CAD重建 | Chamfer距离↓、F-score↑ | 几何精度 |
| 3D场景理解 | mIoU↑ | 查全率、查准率 |

可选加分项：
- 运行效率对比（FPS、训练时间、内存）
- 可视化对比（定性分析图）
- 不同场景难度（室内/室外、简单/复杂）
- 鲁棒性分析（噪声、遮挡、稀疏视角）

## 审稿人关注点

### CVPR/ICCV/ECCV 审稿倾向

| 维度 | 权重 | 常见审稿意见 |
|---|---|---|
| 新颖性 | 高 | "与XXX的区别是什么？" |
| 实验充分性 | 高 | "缺少XXX数据集/基线" |
| 定性可视化 | 中高 | "需要更多视觉对比" |
| 写作清晰度 | 中 | "动机不够清晰" |
| 效率分析 | 中 | "推理速度/内存占用？" |

**常见rebuttal策略**：
- 新颖性质疑：精确指明技术差异，补充对比实验
- 基线缺失：承认遗漏，补充实验或引用
- 效率质疑：补充FPS/内存/参数量表格

### SIGGRAPH/EG/PG 审稿倾向

| 维度 | 权重 | 常见审稿意见 |
|---|---|---|
| 技术深度 | 高 | "数学推导是否严谨？" |
| 理论分析 | 高 | "收敛性/复杂度分析？" |
| 美学质量 | 中高 | "视觉质量是否显著提升？" |
| 方法通用性 | 中 | "能否泛化到其他场景？" |
| 实现细节 | 中 | "超参数敏感性？" |

### 博士论文注意事项

- 每章需独立成体系，包含本章小结
- 创新点声明需在引言末尾明确列出（编号列表）
- 参考文献100篇以上，近3年文献占60%+
- 实验章节需覆盖至少3个不同场景/数据集
- 格式遵循学校模板，注意封面、摘要的中英文版本

## 引用核查规范

核查每条引用时需验证：
1. 作者姓名拼写（特别注意ü、ö等特殊字符）
2. 标题大小写（论文缩写如NeRF、3DGS需大写）
3. 期刊/会议名称准确
4. 年份、卷号、页码/文章号
5. arXiv预印本是否已被正式会议接收（如已接收需更新引用格式）

**高频事实错误**：
- NegGS 的"负不透明度"→ 实为负颜色（opacity仍为非负）
- 6DGS 标注为arXiv→ 已被ICLR 2025接收
- AH-GS → 作者已撤稿
- Ref-NeRF 第一作者 → Verbin D 而非 Barron J T

## 资源

### references/

- [terminology.md](references/terminology.md) — 详细术语对照表与易错点
- [venues.md](references/venues.md) — 各会议/期刊的格式要求与审稿偏好
- [baselines.md](references/baselines.md) — 各方向主流基线方法与核心指标
- [experiments.md](references/experiments.md) — 标准实验设计与常见数据集配置
- [cad-3d.md](references/cad-3d.md) — CAD/3D方向术语、基线与数据集
