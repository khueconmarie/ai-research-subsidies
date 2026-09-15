# Input Supply and the Design of AI Research Subsidies

**Replication materials · Hyunkyu Lee · Kyung Hee University**

[Paper on SSRN](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=7444980) · [Current manuscript](https://github.com/khueconmarie/ai-research-subsidies/releases/tag/v2026.09.15-text1) · [Numerical package](https://github.com/khueconmarie/ai-research-subsidies/releases/tag/v2026.09.15) · [ORCID](https://orcid.org/0000-0001-9134-1748)

The paper compares compute-only and common-rate wage/compute research subsidies in a dynamic general equilibrium model. It separates matching baseline expenditure targets from learning the input-supply responses needed to compare temporary policies. The quantitative rankings are conditional numerical results, not an empirical identification of the best US AI policy.

## Download

| Material | Release | File |
|---|---|---|
| Current manuscript | [v2026.09.15-text1](https://github.com/khueconmarie/ai-research-subsidies/releases/tag/v2026.09.15-text1) | `Manuscript.pdf` |
| Current online appendix | [v2026.09.15-text1](https://github.com/khueconmarie/ai-research-subsidies/releases/tag/v2026.09.15-text1) | `Online_Appendix.pdf` |
| Current editable manuscript and appendix | [v2026.09.15-text1](https://github.com/khueconmarie/ai-research-subsidies/releases/tag/v2026.09.15-text1) | `LaTeX_Source.zip` |
| Complete numerical code, inputs and results | [v2026.09.15](https://github.com/khueconmarie/ai-research-subsidies/releases/tag/v2026.09.15) | `Replication_Package.zip` |

The `text1` revision standardizes authorial prose to an impersonal style. Equations, parameter values, numerical results, numerical table entries and figures are unchanged. The numerical archive and its citation remain at `v2026.09.15`. See [CHANGELOG.md](CHANGELOG.md).

**The full numerical package is the attached `Replication_Package.zip` in the numerical release.** GitHub's green Code button and automatic Source code ZIP/TAR downloads contain this repository's documentation only. Each release supplies its own checksums; [SHA256SUMS.txt](SHA256SUMS.txt) here lists the current manuscript files and the numerical archive together.

## Reproduce

Unzip `Replication_Package.zip`, open a terminal in the extracted package directory, and use Python 3.12:

```sh
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements-numerics.txt
python run_reproduction.py
```

On Windows, activate `.venv\Scripts\activate` instead. The reference environment was macOS ARM64; other platforms have not been verified.

The quick start reconstructs the 24 core table rows, checks accounting for 40 saved policy paths and 17 baselines, performs 40 BGP root calculations for the target-information audit, and regenerates the new table and figure assets. It does **not** reoptimize all stored policies. Commands for fresh policy optimization, their acceptance criteria, and the evidence boundaries are in [REPRODUCTION.md](REPRODUCTION.md) and inside the numerical archive.

For the manuscript, unzip `LaTeX_Source.zip` and run `python3 build.py` with TeX Live installed. The verified output has a 40-page manuscript and a 68-page appendix.

No global optimality or unique crossing is claimed. Underlying third-party microdata and external authors' replication packages are not redistributed. The published inputs are documented in the manuscript and package.

## Cite

Lee, Hyunkyu (2026). *Replication materials for Input Supply and the Design of AI Research Subsidies*. Version 2026.09.15. GitHub. https://github.com/khueconmarie/ai-research-subsidies/releases/tag/v2026.09.15

Machine-readable citation metadata are in [CITATION.cff](CITATION.cff). Please also cite the related paper when using its model or findings. An editorial manuscript revision does not change the version of the numerical evidence.

## Version and rights

The numerical release corresponds to the 14 September 2026 research revision, the 15 September selection-anchor clarification, and submission preparation. The `text1` manuscript revision changes prose only. These releases do not indicate journal acceptance.

No DOI has been assigned to these GitHub releases. No open-source or Creative Commons reuse license has been assigned; public access does not grant an additional reuse license. Third-party material retains its respective rights.

Contact: richardhk2@khu.ac.kr
