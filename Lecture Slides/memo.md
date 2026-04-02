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
| 13 | Variational Inference | 进行中 |
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

## 已学内容 (2026-03-31)

### Prerequisites (notes.tex pp.1-6)
- [x] Inference = 向模型提问（conditional, marginal, MAP, sampling, Z）
- [x] Marginal vs conditional（conditional = 两个 marginal 做除法）
- [x] MAP vs MLE（MAP 找变量 x，MLE 找参数 θ；一个是 inference，一个是 learning）
- [x] Conditional vs posterior（posterior 是 Bayesian update 下的特殊 conditional）
- [x] Bayesian reasoning（prior 是对参数的信念；wrong prior 可纠正，wrong model 不行）
- [x] Partition function（让概率加起来等于 1 的除数；变量多了指数级 intractable）
- [x] Likelihood（给定参数，数据有多可能；分母里藏着 Z）

### L13 Variational Inference (notes.tex pp.7-12)
- [x] 和统计力学的对应（Boltzmann distribution, free energy, entropy）
- [x] Free energy = ⟨E⟩ - TS，ELBO = -F
- [x] 为什么平衡态是 Boltzmann distribution（max entropy under energy constraint）
- [x] Boltzmann machine（用 Boltzmann distribution 作为概率模型的神经网络）
- [x] Gibbs Variational Principle（log Z = max_q [H(q) + E_q[E(x)]]）
- [x] 为什么两项都要（只要 E → MAP，只要 H → uniform）
- [x] GVP 对任何分布成立，但有用性取决于 E(x) 好不好算和 Q 选得好不好
- [x] KL divergence → ELBO 推导
- [x] Evidence = 数据的概率 P(data)，ELBO 是它的 lower bound
- [x] Mean-field approximation（假设变量独立，参数从 2^n 降到 n）
- [x] CAVI（coordinate ascent，一次更新一个 q_i）
- [x] Inner vs outer approximation（下界 vs 上界）

### L13 待继续
- [ ] Slides 后半部分的具体 example（pairwise UGM 上的 CAVI）
- [ ] Outer relaxation 的细节
- [ ] Lagrange multiplier（完全没学懂，之后补）

## TODO

- [ ] 把 prerequisites 部分改写成中英夹杂风格

## 重点 / 易混淆概念

- MAP vs MLE：形式都是 argmax，但 MAP 找 x（inference），MLE 找 θ（learning）
- E_slides = -E_physics（符号约定相反）
- ELBO = -F（negative free energy）
- GVP 永远成立 ≠ GVP 永远有用

## 解释风格

- Assume minimal background，每个术语第一次出现时都要定义
- 先讲直觉/动机，再上公式
- 不要跳步
- LaTeX 中英夹杂：中文行文 + 英文 terminology，风格贴近对话

## 考试相关

- 期中 29/70（25% of total grade → 贡献 10.36%）
- 文件在 `/midterm 1/`：Lex's solution, Bryan's solution, sample exam sol
- 第一道解答题 (Q9) 是 systematic-scan Gibbs，特别 triggering
- 成绩分配：HW 40%, Midterm 25%, Final 35%, Attendance 3% extra
- HW2: 113.5/115（mean 109.25, median 111.5）
- HW1: TBD, HW3: 已交未出分, HW4: 未出
- Midterm review LaTeX 在 `/midterm 1/midterm_review.tex`
- 学期 GPA（另外两门 A+ 和 A）：708 B- → 3.78, B → 3.89, C+ → 3.67
