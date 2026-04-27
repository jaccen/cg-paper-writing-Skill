---
AIGC:
  ContentProducer: '001191110102MAD55U9H0F10002'
  ContentPropagator: '001191110102MAD55U9H0F10002'
  Label: '1'
  ProduceID: '20953b8f-ded4-439a-ab03-01bc3b92d75a'
  PropagateID: '20953b8f-ded4-439a-ab03-01bc3b92d75a'
  ReservedCode1: 'e77ec736-4deb-4deb-b3d4-8be46a2a7a8c'
  ReservedCode2: 'e77ec736-4deb-4deb-b3d4-8be46a2a7a8c'
---

# 标准实验设计与常见数据集配置

## 评估指标使用规范

### PSNR (Peak Signal-to-Noise Ratio)
- 计算范围：整个图像（非裁剪center crop，除非特别说明）
- Blender数据集：通常报告center crop结果（与3DGS原论文一致）
- Mip-NeRF 360数据集：报告全图结果
- 单位：dB，保留2位小数
- 注意：某些方法会报告"不确定性"（±std），需说明是否使用多次随机种子

### SSIM (Structural Similarity)
- 通常报告全局SSIM（非per-pixel SSIM map的平均）
- 范围：[0, 1]，越高越好
- 保留4位小数

### LPIPS (Learned Perceptual Image Patch Similarity)
- 使用VGG网络提取特征
- 范围：[0, 1]，越低越好
- 保留4位小数
- 常用模型：AlexNet版本（lpips_alex）或VGG版本（lpips_vgg）

## 实验表格标准格式

### 定量对比表（Quantitative Comparison）

```
| Method | Chair↑ | Drums↑ | Ficus↑ | Hotdog↑ | Avg↑ |
|--------|--------|--------|--------|---------|------|
| NeRF   | 33.00  | 25.01  | 30.13  | 36.18   | 31.01|
| 3DGS   | 35.82  | 26.17  | 34.83  | 37.67   | 33.30|
| Ours   | **36.15**| **26.89**| **35.21**| **38.02**| **34.07**|
```

- 三指标各一张表（PSNR / SSIM / LPIPS）
- 最优结果**加粗**
- 次优结果用下划线（可选）
- 平均值（Avg）取所有场景的均值
- ↑ 表示越高越好，↓ 表示越低越好

### 效率对比表（Efficiency Comparison）

```
| Method     | Gaussians(K) | Memory(MB) | FPS  | PSNR |
|------------|---------------|-------------|------|------|
| 3DGS       | 307           | 845         | 124  | 27.22|
| LightGS    | 24            | 178         | 203  | 26.85|
| Ours       | 298           | 823         | 118  | **28.03**|
```

## 可视化对比设计

### 定性对比图（Qualitative Comparison）

- 选取3-4个具有代表性的测试视角
- 每个视角排列：GT | Baseline1 | Baseline2 | Ours
- 建议选择：高频细节多的区域、遮挡边界多的区域、大面积平坦区域
- 标注放大区域（用方框圈出）

### 消融可视化

- 展示去掉某个模块后的失败案例
- 常见场景：边缘模糊、颜色偏移、伪影
- 上下排列或左右排列均可

## 训练配置标准写法

论文实验部分必须说明的训练配置：

| 配置项 | 标准写法 |
|---|---|
| GPU | NVIDIA RTX 3090 / 4090 / A100 |
| 训练迭代次数 | 7K / 15K / 30K（3DGS标准） |
| 学习率 | 初始0.016，指数衰减至0 |
| 优化器 | Adam (β₁=0.9, β₂=0.999) |
| 密集化开始 | 500 iter |
| 密集化间隔 | 每100 iter |
| 剪枝间隔 | 每100 iter |
| PSNRMetric | λ_L1 = 0.8, λ_DSSIM = 0.2 |
| SSIM Metric | λ_L1 = 0.2, λ_DSSIM = 0.8 |

## 常见审稿意见与应对

### "缺少XXX基线"
- 应对：补充实验或说明为何不适用
- 如果基线不可复现，引用其原始论文数据

### "仅在XX数据集验证"
- 应对：至少补充一个大尺度真实场景（如Mip-NeRF 360）

### "训练时间/内存占用未报告"
- 应对：补充效率对比表

### "超参数敏感性未分析"
- 应对：对1-2个核心超参数做消融

### "公平对比？"
- 应对：确保使用相同的训练配置、相同的评估视角、相同的SfM初始化

> AI生成