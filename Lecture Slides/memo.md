# 10-708 PGM 备忘录

## Lecture 进度

| Lecture | Topic | Status |
|---------|-------|--------|
| 1  | Introduction | |
| 2  | Directed Graphical Models | |
| 3-4 | Undirected Graphical Models | |
| 5  | Exact Inference | |
| 6-7 | Belief Propagation | |
| 8  | Graph Neural Networks | |
| 9  | MCMC Introduction | |
| 11 | Advanced MCMC | |
| 13 | Variational Inference | |
| 15 | EM Algorithm | |
| 16 | VAE + BBVI | |
| 17 | GAN | |
| 18 | GAN Applications | |
| 19 | Score Matching | |

## 后半学期 Dependency 图 (期中 cutoff: L9)

```
MCMC 线:        L9 (基础MCMC) ──→ L11 (高维 + multimodality + mixing time)
                                       ↑ 相对独立

VI → 生成模型线:  L13 (VI) ──→ L15 (EM) ──→ L16 (VAE) ──→ L17 (GAN) ──→ L18 (GAN应用)
                     ↑ 主线，层层递进               ↑ GAN 从 VAE 缺陷出发

Score 线:        L19 (Score Matching / EBM)
                     ↑ 独立分支，回到 partition function 问题，绕开 Z
```

- **三条线之间关系**: MCMC 线和 VI 线平行；GAN 线从 VAE 延伸；Score Matching 独立
- L17 的动机: VAE 生成模糊 (KL(p||q) 导致 mode averaging) → 不用 likelihood，改用 adversarial
- L19 的动机: MLE 训练 EBM 需要算 ∇log Z (需要 MCMC 采样) → score matching 完全绕开 Z
- **建议学习顺序**: L13 → L15 → L16 → L17 → L18 → L11 → L19

## TODO

- [ ]

## 重点 / 易混淆概念

-

## 解释风格

- Assume minimal background，每个术语第一次出现时都要定义
- 先讲直觉/动机，再上公式
- 不要跳步
- LaTeX 中英夹杂：中文行文 + 英文 terminology，风格贴近对话

## 考试相关

-
