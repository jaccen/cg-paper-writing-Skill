

# 各方向主流基线方法与核心指标

## 新视角合成 (NVS)

### 经典基线（必须对比）

| 方法 | 年份 | PSNR (Blender) | PSNR (Mip-NeRF360) | 特点 |
|---|---|---|---|---|
| NeRF | 2020 | ~31 dB | ~25 dB | 体渲染基线 |
| Mip-NeRF 360 | 2022 | ~33 dB | ~27.5 dB | 反锯齿基线 |
| 3DGS | 2023 | ~33 dB (7K) | ~27.2 dB (30K) | 实时基线 |
| Instant-NGP | 2022 | ~31 dB | ~25 dB | 速度基线 |

### 2024-2025 高频/边界增强方法

| 方法 | 年份 | 发表 | 方向 |
|---|---|---|---|
| FreGS | 2024 | CVPR | 频域正则化 |
| NegGS | 2025 | Inf. Sciences | 负颜色基元 |
| 3D-HGS | 2024 | arXiv | 半高斯核 |
| SignGS | 2025 | — | 符号高斯（本文） |
| 6DGS | 2025 | ICLR | 方向感知增强 |
| Spec-Gaussian | 2024 | NeurIPS | 各向异性外观 |

### 压缩/加速方法

| 方法 | 年份 | 发表 | 压缩率 | FPS |
|---|---|---|---|---|
| CompressedGS | 2024 | CVPR | — | — |
| LightGaussian | 2024 | NeurIPS | 15x | 200+ |
| CompGS | 2024 | ACMMM | — | — |

## 常用数据集

### 合成数据集（NeRF Synthetic / Blender）

- 场景：Chair, Drums, Ficus, Hotdog, Lego, Materials, Mic, Ship
- 来源：NeRF原论文 + Blender数据集
- 评估：PSNR, SSIM, LPIPS
- 训练：100-200张，测试：8个固定视角
- 标注：完整GT深度+法线

### 大尺度数据集（Mip-NeRF 360）

- 场景：Bicycle, Garden, Stump, Room, Counter, Kitchen, Bonfire, Flowers, Treehill
- 来源：智能手机拍摄
- 评估：PSNR, SSIM, LPIPS
- 训练/测试按相机编号划分
- 挑战性：无界场景、大运动、反射表面

### Tank & Temples

- 场景：Truck, Train, Church (medium); Meetingroom, Playroom (advanced)
- 评估：仅定性（无GT），需人工对比
- 特点：真实室外大场景

### Deep Blending

- 场景：DrJohnson, Playroom, Room
- 评估：PSNR, SSIM, LPIPS
- 特点：室内精细场景

### Shiny Blender

- 场景：Car, Ball, Helmet, Teapot, Toaster, Coffee
- 来源：高光/反射材质数据集
- 评估：PSNR, SSIM, LPIPS
- 特点：镜面反射、透明物体

## 消融实验设计要点

必须逐一验证的模块：
1. 核心机制（如符号高斯 → 正高斯对比）
2. 每个损失项的贡献（加 vs 不加）
3. 关键超参数敏感性（通常1-2个核心超参）
4. 与最相关工作的组件级对比（如替换合成规则）

可选加分消融：
- 不同基元初始化策略
- 不同训练调度
- 不同损失权重配比

## CAD/3D 方向补充

CAD建模、3D形状理解/生成、3D场景理解的详细基线与数据集见 [cad-3d.md](cad-3d.md)。

