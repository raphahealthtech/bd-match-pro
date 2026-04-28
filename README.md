<div align="center">

# BD Match Pro

### *Where does your asset belong?*
### 你的资产，该卖给谁？

**AI · China Assets · Global Markets**
**AI · 中国资产 · 全球市场**

[![Live demo](https://img.shields.io/badge/🌐_demo-live-d4af37?style=flat-square)](https://raphahealthtech.github.io/bd-match-pro/)
[![License: MIT](https://img.shields.io/badge/license-MIT-1a3a5c?style=flat-square)](LICENSE)
[![v1.0.0](https://img.shields.io/github/v/release/raphahealthtech/bd-match-pro?style=flat-square&color=0d0c0a)](https://github.com/raphahealthtech/bd-match-pro/releases)
[![Stars](https://img.shields.io/github/stars/raphahealthtech/bd-match-pro?style=flat-square&color=d4af37)](https://github.com/raphahealthtech/bd-match-pro/stargazers)
[![Discussions](https://img.shields.io/github/discussions/raphahealthtech/bd-match-pro?style=flat-square&color=1a3a5c)](https://github.com/raphahealthtech/bd-match-pro/discussions)

[**🌐 Try the live tool · 立即体验**](https://raphahealthtech.github.io/bd-match-pro/) · [**🐙 Source**](https://github.com/raphahealthtech/bd-match-pro) · [**🗺️ Roadmap**](https://github.com/raphahealthtech/bd-match-pro/issues/2) · [**💬 Discussions**](https://github.com/raphahealthtech/bd-match-pro/discussions)

</div>

---

## 🇨🇳 中文

**BD Match Pro** 是一个开源的、AI 驱动的跨境医药授权交易匹配与估值引擎。它针对医药 BD 工作的"第一公里"——*这个品种应该卖给谁？值多少钱？怎么个卖法？*——提供数据化、参数化、可解释的初步答案。

### 它能做什么

1. **匹配买家**——基于 380+ 全球战略买家的组合策略、地理偏好、近期交易动作，对一个具体品种打分排序，给出**最契合的对手方清单 + 公开联系方式**。
2. **估值与交易结构**——并行运行 **rNPV 风险调整模型** 与 **1,196 笔可比交易回归**，给出首付款、里程碑、销售提成的合理区间，并推荐 License-out / NewCo / 联合开发 / 区域分割 等交易结构。
3. **参数全开放**——成功率（PoS）、贴现率（WACC）、峰值销售、毛利率、爬坡曲线、专利期等核心参数全部可由用户自由调整，**实时**看到不同假设下的估值变化。
4. **方法学透明**——所有公式、参数默认值、买方权重逻辑均在源代码与方法学面板中公开，欢迎挑战、修改、改进。

### 为什么开源

医药 BD 长期是少数大行与精英咨询的"黑箱"。本项目想做一件简单的事：**把第一步的方法论开放出来，让中国生物医药资产更高效地走向全球市场**。

> *交易是艺术，不是模型。* 真实成交逻辑与任何预测都可能大相径庭。但只要在 BD 的第一公里，AI 能让大家少走点弯路、提升一点效率，就已经有用了。

---

## 🇬🇧 English

**BD Match Pro** is an open-source, AI-powered cross-border licensing engine for pharmaceutical assets. It tackles the first mile of biotech business development — *who would buy this asset, at what price, and via which deal structure?* — with data-driven, fully parametric, and transparent first-pass answers.

### What it does

1. **Match buyers** — score and rank 380+ global strategic acquirers against your asset, based on portfolio fit, geographic preference and recent deal activity. Output includes **buyer profile, financial snapshot, recent transactions and public contact details**.
2. **Value & structure** — run **risk-adjusted NPV** and **1,196-deal comparable regression** in parallel; size upfront / milestones / royalty ranges; recommend License-out, NewCo, Co-development or Regional split structures.
3. **Fully parametric** — every input (PoS, WACC, peak sales, margin, ramp curve, patent runway, etc.) is **user-adjustable** and the valuation re-renders in real time.
4. **Transparent methodology** — every formula, default parameter and weight is documented in the methodology panel and in the source. Challenge it, fork it, improve it.

### Why open-source

Pharma BD has long been the black box of a handful of bulge-bracket banks and elite consultancies. This project does one simple thing: **open up the first-pass methodology so that Chinese biopharma assets can find their way to global markets more efficiently.**

> *Deals are art, not models.* Real-world outcomes diverge from any forecast. But if AI can save practitioners a few wrong turns at the very first mile, it has already earned its keep.

---

## 🚀 Quick start · 快速开始

### Run locally · 本地运行

```bash
git clone https://github.com/raphahealthtech/bd-match-pro.git
cd bd-match-pro
# Just open index.html in any modern browser
open index.html              # macOS
xdg-open index.html          # Linux
start index.html             # Windows
```

The entire app is a **single self-contained `index.html` file** — no build step, no backend, no dependencies. All logic lives in plain JavaScript modules within the file.
整个应用是**单一的 `index.html` 文件**——零构建、零后端、零依赖，所有逻辑都用纯 JavaScript 写在文件里。

### Live demo · 在线体验

→ **[https://raphahealthtech.github.io/bd-match-pro/](https://raphahealthtech.github.io/bd-match-pro/)**

---

## 🧮 Methodology · 方法学

### Risk-adjusted NPV (rNPV) for new drugs

```
rNPV = Σ [ PoS_cumulative(t) × CashFlow(t) × (1 - tax) × (1 + WACC)^(-t) ] − DevCost_pv
```

- **PoS_cumulative** — cumulative probability of success from the asset's *current* clinical stage to approval (defaults: Preclinical 5% → Phase I 10% → Phase II 17% → Phase III 52% → NDA 88% → Approved 100%)
- **CashFlow(t)** — peak licensed-territory sales × ramp[t] × net margin × modality premium × competition multiplier
- **WACC** — default 11% (user-adjustable)
- **Patent runway** — default 10 years post-approval; ramp curve covers ramp-up, peak, and LOE decline

### Biosimilar valuation

A separate model with biosim-specific PoS (higher), WACC (lower, 9%), gross margin (~55%), share-of-originator ramp curve, and discount-vs-originator parameter.

### Buyer matching

Each buyer carries vectors over: therapeutic-area portfolio, modality preference, geographic split, recent dealmaking activity, financial firepower (cash + market cap). Matching is a weighted cosine score with explainable per-axis contribution.

### Comparable-deal pricing

1,196 publicly disclosed licensing transactions, indexed by indication × stage × modality × buyer-tier, drive the upfront / milestone / royalty regression bands.

**Full methodology panel is in the running app, and all parameters are visible & editable in the source (`index.html`).**
**完整方法学在运行中的应用方法学面板里，所有参数都在源码 `index.html` 中可见、可改。**

---

## 🤝 Contributing · 参与贡献

We welcome:
欢迎以下贡献：

- 📊 **Better default parameters** — newer industry data on PoS, WACC, peak sales, ramp curves
  **更准的默认参数**——更新的行业数据（PoS / WACC / 峰值 / 爬坡）
- 💼 **Buyer database updates** — new pipeline portfolios, recent deals, contact corrections
  **买方数据库更新**——新管线组合、近期交易、联系方式修正
- 🧠 **Methodology improvements** — better risk-adjustment math, biosim modelling, NewCo structures
  **方法学改进**——更好的风险调整、生物类似药建模、NewCo 结构
- 🌍 **Indication / TA expansion** — finer subdivisions, regional adjustments
  **适应证 / 治疗领域扩充**——更细分类、地域调整
- 🎨 **Design & UX** — accessibility, mobile, internationalisation
  **设计与体验**——可达性、移动端、国际化
- 🐛 **Bug reports & corrections**
  **Bug 反馈与修正**

### How to contribute · 如何参与

1. **Open an Issue** to discuss the change first (especially for methodology changes).
   先开 Issue 讨论（尤其是方法学改动）。
2. **Fork → branch → PR.** Keep PRs focused; explain *why* in the description.
   Fork → 开分支 → 提 PR；保持改动聚焦，描述里说清**为什么**。
3. **Comment thresholds in the code** if you change a default constant — readers need to know what changed and why.
   修改默认常量请在代码里加注释，让读者知道改了什么、为什么。

---

## 📜 License · 许可

Released under the [MIT License](LICENSE). You may use, modify, distribute, and even commercialise this software freely, provided you retain the copyright notice.
基于 [MIT 协议](LICENSE) 发布。任何人都可以自由使用、修改、分发，甚至商用，只需保留版权声明。

**⚠️ Not investment advice.** Outputs are research-grade estimates. See [DISCLAIMER](DISCLAIMER.md) for the full notice.
**⚠️ 不构成投资建议。** 输出仅为研究级估算，完整免责声明见 [DISCLAIMER](DISCLAIMER.md)。

---

## 💬 Contact · 联系我们 <a id="contact"></a>

**Rapha Health Investment Technology Limited · 睿孚健康投资科技有限公司**
Hong Kong · 香港

- 📞 Mainland China · 中国大陆: **+86 13632302814**
- 📞 Hong Kong · 香港: **+852 96602635**
- 🌐 Live tool: [raphahealthtech.github.io/bd-match-pro](https://raphahealthtech.github.io/bd-match-pro/)
- 💡 Feedback / Collaboration / Custom builds: **open an [Issue](https://github.com/raphahealthtech/bd-match-pro/issues)** or **start a [Discussion](https://github.com/raphahealthtech/bd-match-pro/discussions)**

---

<div align="center">

*From China to the World — the first mile, in the open.*
*中国资产 · 全球市场——第一公里，公开可见。*

</div>
