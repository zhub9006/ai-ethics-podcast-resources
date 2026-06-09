# 📚 AI Ethics & Fairness — Open Source Resources

> Curated for the *Technology & Social Justice* podcast. Last updated: June 2026.

This document lists active open-source projects working on algorithmic fairness, bias detection, and AI auditing. These are real tools used by researchers, policymakers, and engineers to interrogate machine learning systems.

---

## 1. 🤖 AI Fairness 360 (AIF360)

**Repository:** [Trusted-AI/AIF360](https://github.com/Trusted-AI/AIF360)  
**Stars:** ⭐ 2,821 | **Language:** Python | **License:** Apache 2.0  
**Maintained by:** IBM Research (Trusted-AI org)  

### What It Does
AIF360 is one of the most comprehensive open-source toolkits for detecting and mitigating bias in machine learning datasets and models. It provides:
- **70+ fairness metrics** spanning individual, group, and causal fairness
- **Bias mitigation algorithms** at pre-processing, in-processing, and post-processing stages
- Support for a wide range of ML frameworks (scikit-learn, TensorFlow, PyTorch)

### Why It Matters for the Podcast
AIF360 is the *de facto* reference implementation for many fairness researchers. Its open issue tracker is a window into live debates about *which* metrics matter, *whose* fairness definitions get encoded, and *who* the tools are really built to serve. It's where the academic rubber meets the real-world road.

### Key Links
- 📖 [Documentation](https://aif360.readthedocs.io/)
- 🐛 [Open Issues](https://github.com/Trusted-AI/AIF360/issues)
- 📄 [Research Paper](https://arxiv.org/abs/1810.01943)

---

## 2. ⚖️ Fairlearn

**Repository:** [fairlearn/fairlearn](https://github.com/fairlearn/fairlearn)  
**Stars:** ⭐ 2,249 | **Language:** Python | **License:** MIT  
**Maintained by:** The Fairlearn Community (originally Microsoft Research)  

### What It Does
Fairlearn is a Python package that empowers AI developers to assess and improve the fairness of their systems. It focuses on **group fairness** — asking which groups of people are at risk of harm from a given model. It offers:
- **Fairness metrics** for comparing models across demographic groups
- **Mitigation algorithms** including ExponentiatedGradient and GridSearch
- A strong community governance model with a published Code of Conduct

### Why It Matters for the Podcast
Fairlearn is explicit about something most tools dance around: *fairness is fundamentally a sociotechnical challenge*, and no set of metrics can capture everything. Its README openly acknowledges that "many quantitative fairness metrics cannot all be satisfied simultaneously" — a statement that opens up enormous philosophical and political questions.

### Key Links
- 🌐 [Website](https://fairlearn.org/)
- 📖 [User Guide on Fairness Definitions](https://fairlearn.org/main/user_guide/fairness_in_machine_learning.html)
- 🐛 [Open Issues](https://github.com/fairlearn/fairlearn/issues)
- 💬 [Discord Community](https://discord.gg/R22yCfgsRn)

---

## 3. 🔍 Aequitas

**Repository:** [dssg/aequitas](https://github.com/dssg/aequitas)  
**Stars:** ⭐ 760 | **Language:** Python | **License:** MIT  
**Maintained by:** Data Science for Social Good (UChicago / Carnegie Mellon)  

### What It Does
Aequitas is a bias auditing and Fair ML toolkit built specifically with **policymakers and public-sector data scientists** in mind. It focuses on:
- **Confusion matrix-based bias auditing** across sensitive demographic attributes
- **Aequitas Flow** — a pipeline for fair ML experimentation (pre-, in-, and post-processing)
- Integration with real-world policy datasets like COMPAS (criminal recidivism) and FolkTables (census data)

### Why It Matters for the Podcast
Unlike tools built primarily for industry ML engineers, Aequitas was designed from the ground up for **high-stakes public-interest decisions** — predictive policing, child welfare screening, hiring. This raises a critical question: should fairness tools be designed differently depending on whether they're used by a tech company or a government agency?

### Key Links
- 🌐 [Project Website](http://dsapp.uchicago.edu/aequitas/)
- 📖 [Documentation](https://dssg.github.io/aequitas/)
- 🐛 [Open Issues](https://github.com/dssg/aequitas/issues)
- 📄 [Fairness Tutorial (KDD/AAAI)](https://dssg.github.io/fairness_tutorial/)
- 📄 [Aequitas Flow Paper (JMLR 2024)](https://arxiv.org/pdf/2405.05809)

---

## 🗺️ How These Projects Relate

```
AIF360          →  Maximum breadth: most metrics, most algorithms, most research citations
Fairlearn       →  Maximum accessibility: best docs, active community, Microsoft-backed
Aequitas        →  Maximum social impact focus: public sector, policy, high-stakes decisions
```

All three are MIT or Apache licensed, Python-based, and actively maintained. Together they represent the current "state of the art" in open-source AI fairness tooling — and all three are wrestling with the same unsolved problems documented in [`DEBATES.md`](./DEBATES.md).

---

*Want to add a project? Open a PR! See [README.md](./README.md) for contribution guidelines.*
