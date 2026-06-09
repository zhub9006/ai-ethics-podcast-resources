# 📚 AI Fairness & Ethics — Open-Source Project Directory

> Curated by the *"Who Gets to Define Bias?"* podcast research team.
> Last updated from live GitHub data. Projects are ordered by community activity.

---

## 🔬 Fairness Measurement & Mitigation Toolkits

### 1. [fairlearn/fairlearn](https://github.com/fairlearn/fairlearn)
![Stars](https://img.shields.io/github/stars/fairlearn/fairlearn) · Python · MIT License

**What it does:** Microsoft-backed Python package for assessing and improving fairness of ML models. Provides `MetricFrame` for disaggregated metric evaluation, plus mitigation algorithms (reductions, post-processing thresholders).

**Why it matters for the podcast:** Fairlearn is *explicitly opinionated* — it defines fairness in terms of **harms to people**, not statistical properties of data. It deliberately avoids the words "bias" and "debiasing." This philosophical stance is baked into every API decision and is a source of ongoing community debate.

**Key concepts:** Demographic Parity, Equalized Odds, Bounded Group Loss, `MetricFrame`, `ExponentiatedGradient`, `ThresholdOptimizer`

**Active debates:** See [DEBATES.md](./DEBATES.md) — Issues #430, #756, #971, PR #997

**Links:**
- 📖 Docs: https://fairlearn.org
- 🐛 Open Issues (131): https://github.com/fairlearn/fairlearn/issues
- 🔀 Open PRs: https://github.com/fairlearn/fairlearn/pulls

---

### 2. [Trusted-AI/AIF360](https://github.com/Trusted-AI/AIF360)
![Stars](https://img.shields.io/github/stars/Trusted-AI/AIF360) · Python/R · Apache 2.0

**What it does:** IBM's AI Fairness 360 — a comprehensive toolkit with 70+ fairness metrics and 11 bias mitigation algorithms spanning pre-processing, in-processing, and post-processing. Supports both Python and R.

**Why it matters for the podcast:** AIF360 takes the *opposite* philosophical stance from fairlearn — it *embraces* the language of "bias" and "debiasing," and includes data-level interventions (Reweighing, Disparate Impact Remover, Optimized Preprocessing). The contrast between AIF360 and fairlearn's approach is a microcosm of a deeper debate: **do you fix bias in the data, or do you measure and mitigate harm in the output?**

**Key concepts:** Disparate Impact, Statistical Parity Difference, Equal Opportunity Difference, Reweighing, Adversarial Debiasing, Calibrated Equalized Odds

**Active debates:** See [DEBATES.md](./DEBATES.md) — Issue #97 ("Reconsider use of 'bias' in README"), Issue #154, Issue #241

**Links:**
- 📖 Docs: https://aif360.res.ibm.com
- 🐛 Open Issues (157): https://github.com/Trusted-AI/AIF360/issues
- 📄 Paper: https://arxiv.org/abs/1810.01943

---

### 3. [jphall663/awesome-machine-learning-interpretability](https://github.com/jphall663/awesome-machine-learning-interpretability)
![Stars](https://img.shields.io/github/stars/jphall663/awesome-machine-learning-interpretability) · Curated List

**What it does:** The most comprehensive curated list of responsible ML resources (4,000+ stars). Covers fairness, interpretability, explainability, model debugging, and AI security. Maintained by Patrick Hall (formerly H2O.ai, now BNH.ai).

**Why it matters for the podcast:** This is the de facto "where do I start?" resource for practitioners. Its curation choices reveal community consensus on what counts as "responsible AI" — and what gets left out. The line between interpretability and fairness is blurry here, which is itself a debate.

**Links:**
- 🌐 https://github.com/jphall663/awesome-machine-learning-interpretability

---

### 4. [aws/amazon-sagemaker-clarify](https://github.com/aws/amazon-sagemaker-clarify)
![Stars](https://img.shields.io/github/stars/aws/amazon-sagemaker-clarify) · Python · Apache 2.0

**What it does:** AWS's fairness and explainability library for SageMaker. Detects pre-training and post-training bias, computes SHAP-based feature attributions, and supports the Conditional Demographic Disparity (CDD) metric from Wachter et al.

**Why it matters for the podcast:** A corporate implementation of a legally-motivated fairness metric (CDD, derived from EU non-discrimination law). Represents the **industry operationalization** of academic fairness research — and the tension between legal compliance and genuine fairness.

**Links:**
- 🐛 Issues: https://github.com/aws/amazon-sagemaker-clarify/issues
- 📄 CDD Metric: https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-data-bias-metric-cddl.html

---

### 5. [linkedin/LiFT](https://github.com/linkedin/LiFT)
![Stars](https://img.shields.io/github/stars/linkedin/LiFT) · Scala/Spark · BSD 2-Clause

**What it does:** LinkedIn's Fairness Toolkit — built for **large-scale** ML workflows on Spark. Measures fairness at the scale of LinkedIn's production systems (job recommendations, talent search, feed ranking).

**Why it matters for the podcast:** LiFT represents the **production reality** of fairness measurement — not a research prototype, but a system measuring bias in recommendation engines that affect millions of job seekers. The choice to build in Scala/Spark rather than Python reveals assumptions about who uses fairness tools and at what scale.

**Links:**
- 🌐 https://github.com/linkedin/LiFT
- 📄 Paper: https://arxiv.org/abs/2008.07433

---

## 📐 Fairness Metrics — Quick Reference

| Metric | What It Measures | Mathematical Requirement | Key Tension |
|--------|-----------------|--------------------------|-------------|
| **Demographic Parity** | Equal positive prediction rates across groups | P(Ŷ=1\|A=0) = P(Ŷ=1\|A=1) | Ignores actual outcome differences |
| **Equalized Odds** | Equal TPR *and* FPR across groups | Equal error rates for both outcomes | Mathematically incompatible with calibration when base rates differ |
| **Calibration** | Predicted probabilities match actual outcomes | P(Y=1\|score=s,A=a) = s | Incompatible with equalized odds (Chouldechova 2017) |
| **Individual Fairness** | Similar individuals treated similarly | d(x,x') ≈ 0 → \|f(x)-f(x')\| ≈ 0 | Who defines "similar"? |
| **Counterfactual Fairness** | Same outcome regardless of protected attribute | P(Ŷ_{A←a}\|x,a) = P(Ŷ_{A←a'}\|x,a) | Requires causal model of the world |
| **Conditional Demographic Disparity (CDD)** | Disparity conditional on legitimate factors | From Wachter et al. / EU law | Can be gamed; contested operationalization |

> ⚠️ **The Impossibility Result**: Chouldechova (2017) and Kleinberg et al. (2016) proved that demographic parity, equalized odds, and calibration *cannot all be satisfied simultaneously* when base rates differ between groups. Every fairness toolkit is implicitly taking a side in this mathematical impossibility.

---

## 📰 Essential Reading

| Title | Authors | Year | Why Read It |
|-------|---------|------|-------------|
| [Fairness and Machine Learning](https://fairmlbook.org) | Barocas, Hardt, Narayanan | 2023 | The textbook — free online |
| [Why Fairness Cannot Be Automated](https://arxiv.org/abs/2005.05906) | Wachter, Mittelstadt, Russell | 2020 | EU law vs. algorithmic operationalization |
| [Dissecting Racial Bias in an Algorithm Used to Manage the Health of Populations](https://www.science.org/doi/10.1126/science.aax2342) | Obermeyer et al. | 2019 | Real-world harm from calibration choice |
| [Gender Shades](http://gendershades.org) | Buolamwini, Gebru | 2018 | Audit methodology that sparked industry change |
| [The (Im)possibility of Fairness](https://dl.acm.org/doi/10.1145/3290607.3310418) | Friedler et al. | 2021 | Structural vs. individual worldview |
| [Datasheets for Datasets](https://arxiv.org/abs/1803.09010) | Gebru et al. | 2018 | Documentation as accountability |
| [Model Cards for Model Reporting](https://arxiv.org/abs/1810.03993) | Mitchell et al. | 2019 | Transparency standard now widely adopted |

---

## 🏛️ Policy & Regulatory Resources

- **EU AI Act** (2024): https://artificialintelligenceact.eu — First binding AI regulation; defines "high-risk" systems
- **NYC Local Law 144** (AEDT): https://legistar.council.nyc.gov — Requires bias audits for automated employment decision tools
- **NIST AI RMF**: https://www.nist.gov/system/files/documents/2023/01/26/AI%20RMF%201.0.pdf — US voluntary risk management framework
- **FTC AI Guidance**: https://www.ftc.gov/business-guidance/blog/2021/04/aiming-truth-fairness-equity-ftcs-approach-artificial-intelligence — Enforcement perspective

---

*🔄 This file is updated as new projects and resources are identified. Submit a PR to add something we missed.*
