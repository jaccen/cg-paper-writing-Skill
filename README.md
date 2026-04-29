

# cg-paper-writing-Skill

三维视觉与计算机图形学论文写作技能

面向三维重建/计算机图形学/CAD建模与逆向工程、3D形状理解与分析、3D生成与编辑、3D场景理解、3D视觉SLAM等方向的学术写作辅助，目标包括 CVPR/ICCV/ECCV、SIGGRAPH/EG/PG、NeurIPS/AAAI、核心期刊以及博士论文。

## v1.1.0 更新

- SKILL.md: 升级至 v1.1.0，合并双版精华
- 新增：去AI痕迹规则（12条具体模式 + 标准学术用语保留列表）
- 新增：贡献声明指南与模板
- 新增：SLAM/压缩/前馈/生成 等新术语类别
- 新增：rebuttal策略
- baselines.md: +20+ 方法（Mip-Splatting/4DGS/HAC/MVSplat/SLAM方法等）
- baselines.md: +5 新数据集（RealEstate10K/ACID/DL3DV/Replica/Waymo）
- terminology.md: +18个易错术语（含SLAM/压缩/前馈/生成）
- venues.md: +NeurIPS/AAAI 会议指南
- experiments.md: +效率参考值、+SLAM数据集

## 技能概览

| 内容 | 文件 | 说明 |
|------|------|------|
| 主技能文件 | cg-paper-writing/SKILL.md | 触发规则、写作流程、审稿人关注点、去AI痕迹规则、贡献声明 |
| 术语对照表 | references/terminology.md | 数学符号规范、中英术语对照、18个高频易错术语详解 |
| 会议/期刊指南 | references/venues.md | CVPR/ICCV/ECCV/SIGGRAPH/NeurIPS/AAAI/TVCG/CGF 格式与审稿偏好 |
| 基线方法库 | references/baselines.md | NVS/压缩/动态/前馈/SLAM基线、5大类数据集 |
| 实验设计规范 | references/experiments.md | 评估指标用法、效率参考值、SLAM数据集 |
| CAD/3D补充 | references/cad-3d.md | CAD/3D方向术语、基线与数据集 |

## 安装

```bash
# 克隆仓库
git clone https://github.com/jaccen/cg-paper-writing-Skill.git

# 复制到 Agent 技能目录
cp -r cg-paper-writing-Skill/SKILL.md ~/.openclaw/skills/cg-paper-writing/
cp -r cg-paper-writing-Skill/references ~/.openclaw/skills/cg-paper-writing/
```

