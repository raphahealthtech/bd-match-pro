# Changelog · 更新日志

All notable changes to BD Match Pro will be documented here.
The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/) and the project adheres to [Semantic Versioning](https://semver.org/).

本项目所有重要更新记录在此。遵循 [Keep a Changelog](https://keepachangelog.com/en/1.1.0/) 和 [Semantic Versioning](https://semver.org/)。

---

## [Unreleased]

### Planned · 计划中
- ⭐ **Expand DEALS_DB → 500+ deals** (top community-contribution priority)
- Tunable comp-blend weight slider (currently fixed at 50/50)
- Side-by-side scenario comparison · 双场景并列对比
- PDF / one-pager export · PDF / 一页报告导出
- Save/load asset profiles via URL hash · 通过 URL hash 保存与分享方案
- Stage-conditional WACC defaults · 分阶段默认 WACC

---

## [1.0.1] · 2026-04-29

### 🔧 Comp-blended valuation + honest disclosure

#### Added · 新增
- **`compImpliedValue()`** — similarity-weighted regression on `DEALS_DB` with stage / modality / territory corrections
- **50/50 blend** of parametric rNPV and comp-implied terms when N ≥ 3 similar deals exist
- **Reconciliation strip** in valuation panel showing both paths plus the blended P50
- **Transparency banner** at the top of the methodology panel
- **Inline methodology anchors** throughout (one click jumps to the panel)
- **Live `DEALS_DB.length` placeholders** (`.deal-count-n`) populated on page load — no more hardcoded marketing numbers

#### Changed · 调整
- `findComps()` similarity gate tightened — requires real indication-or-modality match, not just stage adjacency
- Methodology panel rewritten with full formulas, weighting rules, and known limitations
- README's Methodology section rewritten to match the in-app explainer
- Roadmap (#2): "Expand DEALS_DB to 500+" promoted to v1.1 top priority

#### Fixed · 修正
- Marketing copy throughout the UI no longer references the inflated "1,196" figure — replaced with live database count (currently 53 hand-curated cross-border deals)
- The previously-cosmetic "Comps panel" now reflects the real database size

---

## [1.0.0] · 2026-04-28

### 🎉 First public open-source release · 首个公开开源版本

#### Added · 新增
- 🎯 Buyer matching across 380+ global strategic acquirers (portfolio fit, geography, recent deals)
- 🧮 Risk-adjusted NPV with full parameter exposure (PoS, WACC, peak sales, margin, ramp, patent runway)
- 💼 Curated comparable-deal database (53 disclosed-economics cross-border transactions, 2024-11 → 2025-12)
- 🧬 Separate biosimilar model with biosim-specific parameters
- 🌐 Bilingual UI (中文 / English) with stage-conditional parameter display
- 📐 Single-file architecture — no build, no backend, no dependencies
- 📊 90+ subdivided indications across oncology, CNS, rare disease, autoimmune, etc.
- 🎨 Editorial hero with reimagined "Creation of Adam" — DNA helix + brain anatomy SVG art
- 📜 MIT license, bilingual README, CONTRIBUTING, CODE_OF_CONDUCT, SECURITY, DISCLAIMER

#### Note on this entry
The original v1.0.0 release claimed "1,196 comparable deals" in marketing copy; this changelog entry has been updated post-hoc to reflect what the codebase actually shipped — see [v1.0.1](#101--2026-04-29) for the patch that aligned model behavior and copy.

#### Open-sourced under · 开源协议
- MIT License — see [LICENSE](LICENSE)

[Unreleased]: https://github.com/raphahealthtech/bd-match-pro/compare/v1.0.1...HEAD
[1.0.1]: https://github.com/raphahealthtech/bd-match-pro/releases/tag/v1.0.1
[1.0.0]: https://github.com/raphahealthtech/bd-match-pro/releases/tag/v1.0.0
