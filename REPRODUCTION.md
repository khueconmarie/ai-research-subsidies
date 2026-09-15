# Replication package

**Input Supply and the Design of AI Research Subsidies**  
Hyunkyu Lee — Department of Economics, Kyung Hee University  
richardhk2@khu.ac.kr · https://orcid.org/0000-0001-9134-1748

Package prepared for JEDC on 15 September 2026. Scientific results are from the
14 September research revision; the selection-anchor provenance clarification
is dated 15 September. The SSRN preprint has abstract ID 7444980:
https://papers.ssrn.com/sol3/papers.cfm?abstract_id=7444980

## Quick start

Use Python 3.12 and install the pinned dependencies in an isolated environment:

```sh
python3 -m venv .venv
# macOS/Linux
source .venv/bin/activate
python -m pip install -r requirements-numerics.txt
python run_reproduction.py
```

On Windows, activate `.venv\Scripts\activate` instead. The reference environment
was macOS ARM64; execution on other platforms has not been verified. No virtual
environment or installed third-party libraries are distributed in this archive.

The quick-start script performs, sequentially:

1. Reconstruction of the 24 displayed rows in Tables 3–5 and accounting for
   16 historical paths.
2. Independent welfare and fiscal accounting for 40 accepted policy paths,
   17 baselines and 23 paired comparisons underlying the new design tests.
3. Forty fresh BGP root calculations for the target-information audit.
4. Algebraic reconstruction of the two distinct selection anchors
   (25.4070 and 25.4064, rounded to four decimal places).
5. Regeneration of the new manuscript table, appendix tables and crossing figure
   from the accepted records.

It writes a receipt to `verification/relocated_reproduction.json`. In the
15 September relocation check these five drivers completed successfully.
The quick start does **not** reoptimize the saved policies. The prior release's
36 accepted local optimizations and eight inherited tolerance checks are not
counted as new optimizations by this preparation step. Paired accounting reuses
stored continuation terms; it is not a separate implementation of the model.

## Full computation and coverage

See `REPLICATION_README.md` for fresh-policy commands, acceptance criteria,
rejected attempts, target-map calculations, and evidence boundaries. Use a new
`--out` directory to request fresh optimization: accepted cached records are
otherwise intentionally reused. Numerical results are conditional and local;
no global optimality, unique crossing or empirical US policy identification is
claimed. The historical recipes are preserved for provenance, and some retain
the author's older directory conventions. The five quick-start drivers and the
current `run_new_experiments.py` are the documented entry points.

`calibration.json` records the adopted model under `config`. Experiment-specific
changes are in the saved specifications. Sources, calibration operators,
acceptance diagnostics, policy paths, and paired accounting are included.
Underlying third-party microdata and external authors' replication packages are
not redistributed. Source-year-eight recruitment data remain unavailable.

The editable manuscript, bibliography and vector figures are supplied separately
as `LaTeX_Source.zip`; this numerical archive is not a complete document build.
The JEDC-prepared main PDF is 40 pages after contact and declaration additions;
the appendix remains 68 pages. Scientific table values were retained.

## Integrity and release status

`PACKAGE_MANIFEST.json` contains SHA-256 hashes for the distributed files other
than the manifest itself. `replication/source_manifest.json` is an inherited
source-provenance record and has a narrower historical scope. Running the
drivers may regenerate derived files; compare the original archive before
execution if byte identity is needed.

This package is distributed through the author's GitHub repository:
https://github.com/khueconmarie/ai-research-subsidies

The submission-version release is `v2026.09.15`:
https://github.com/khueconmarie/ai-research-subsidies/releases/tag/v2026.09.15

See `CITATION.cff` for citation metadata. No DOI has been assigned to this
GitHub release. No open-source or Creative Commons reuse license has been
assigned; this publication does not grant an additional reuse license.
Third-party materials retain their respective rights.


---

# Replication guide — 14 September 2026

Run commands from this package root. The reference configuration is the full
candidate wrapper in calibration.json; its adopted economic parameters are under
config. This equals manuscript/calibration.json and the packaged joint_reference
candidate. The nested growth_coordinate field retains an earlier diagnostic
proposal marked as requiring rematching; it is not the adopted config. All new
policy experiments retain lambda_E=0.2. Experimental curvature changes live in
per-run specification.json files and do not overwrite the adopted record.

## Environment

Verified: Python 3.12.14, NumPy 2.5.2, SciPy 1.16.1, CasADi 3.7.2,
pandas 2.3.2, matplotlib 3.10.5, macOS ARM64. Numerical dependencies are pinned
in requirements-numerics.txt. PDF verification additionally uses pypdf,
pdfplumber, Poppler and TeX Live/latexmk. The author's virtual environment is
not included in the archive. Install the requirements in your own environment.
The numerical driver sets each BLAS thread count to one before imports.

## Reconstruct the reported evidence from saved paths

    python scripts/reconstruct_core.py
    python scripts/audit_new_records.py
    python scripts/build_research_assets.py

The first command reproduces all 24 displayed rows of Tables 3–5 and accounting
for 16 historical paths. It reads eight tolerance checks completed in the
11 September release; it does not rerun them. The second independently sums
fiscal bills and reconstructs welfare for all 40 new accepted policy paths,
17 baselines and 23 paired comparisons, reusing explicit stored continuation
terms. The third regenerates Table 6, Appendix K and Figure 1 from accepted
JSON records. No displayed result is inferred from a screenshot.

The economic engine and continuation operator are inherited. This is independent
welfare/fiscal accounting, not an independent implementation of all equations or
reestimation of every external source. Root residuals, local stationarity and
observed sensitivity are not rigorous objective-error or global-optimality bounds.

## Parameter-to-target derivatives: fresh BGP solves

    python scripts/audit_target_information.py

This solves 40 BGP roots across two finite-difference step sizes and an anchored
family check. analysis/target_information.json separates the 26-equation root
Jacobian from the six-level-target derivative with respect to six fitted
coordinates. Added log gamma_H has a zero column; added log lambda_E can be
compensated locally in those fitted coordinates. Only the six targets, not the
entire BGP, are preserved in the latter derivative. No finite lambda_E
sensitivity experiment or statistical standard error is reported.

## Selection-coordinate provenance (15 September clarification)

    python scripts/audit_selection_anchors.py

This independently reconstructs the two algebraic anchor mappings and verifies
that the historical firm-ratio slice retains its earlier numerical curvature.
Both historical input records are included under sources/selection_anchor_20260915/.
No new equilibrium or policy optimization is needed for this clarification.

## Fresh policy computations

Each command explicitly reuses an accepted result if it already exists in the
chosen output directory. To run new optimizations, choose a new --out directory
and use the same new root for dependent --fixed-from checks. Reusing an archive's
stored results is not a fresh optimization. Results in an alternate directory do
not automatically replace the authoritative manuscript inputs.

Preliminary curvature scan (retained for provenance):

    python scripts/run_new_experiments.py --elasticities 4 5 --N 160 --out analysis/crossing

Crossing endpoints, first on the half-year mesh and then the quarter-year mesh:

    python scripts/run_new_experiments.py --elasticities 4.9 4.95 --N 160 --out analysis/crossing
    python scripts/run_new_experiments.py --elasticities 4.9 4.95 --N 320 --out analysis/crossing

Fixed-rate horizon extension; run after the quarter-year-mesh endpoints:

    python scripts/run_new_experiments.py --elasticities 4.9 4.95 --T 120 --N 480 --fixed-from analysis/crossing --out analysis/crossing

The same endpoint comparisons from BGP stocks:

    python scripts/run_new_experiments.py --elasticities 4.9 4.95 --state bgp --N 320 --out analysis/crossing

Uncoupled rates in three representative mappings, including both nested starts:

    python scripts/run_new_experiments.py --cases joint_reference joint_short_response joint_firm_exact --modes compute wage_compute independent --N 320 --out analysis/rate_uncoupling

All four mappings from BGP stocks:

    python scripts/run_new_experiments.py --cases joint_reference joint_short_response joint_firm_exact joint_ekerdt --state bgp --N 320 --out analysis/initial_state

These commands account for 36 accepted local optimizations (including both
independent-rate starts), four fixed-rate paths and 17 new baseline transitions.
The chosen independent.json duplicates the selected starting solution and is not
counted as an additional optimization. Each new curvature requires its own
no-additional-support transition, even when the BGP is identical. Each firm map
uses its own rematched BGP and output denominator.

## Numerical acceptance and rejected attempts

Optimized policies use the original equations, two four-year windows, a fiscal
ceiling of 0.001 percent of BGP output and a supported BGP continuation after
expiry. The baseline has continuing support and no added program. Stress starts
scale pipeline Q and capacity B to 0.35 and 0.70 of BGP, respectively; these are
unestimated stress inputs. BGP-start runs scale neither stock.

Acceptance requires successful outer termination, normalized finite-difference
stationarity below 1e-4, fiscal-annuity error below 2e-10 percentage points and
maximum dynamic/static residual below 5e-7. The outer search uses the inherited
implicit adjoint. The independent stationarity check perturbs the normalized
policy coordinates by 2e-4. Fixed-rate horizon runs are not reoptimized and use
no stationarity acceptance test; their annuity drift tolerance is 2e-9 points.

The runner permits at most two bounded refinements after an unaccepted solve:
first a tighter 1e-10 search from the current rates, then (if needed) a confirmation
at the original stopping tolerance from the refined point. All failed records
remain on disk. One first-year/common-rate BGP-start case needed this procedure.
It first missed the stationarity threshold, then missed line-search termination;
only the confirmation passed both. The thresholds were not relaxed. Cached results
are checked for acceptance before reuse. Runtime varies substantially: tens of
seconds for many policies, several minutes for difficult refinements.

## Documents and packaging

The commands in this numerical archive reconstruct the evidence. The complete
editable article and document-build driver are supplied separately in
LaTeX_Source.zip. The original 14 September research release contained document
verification and merging drivers; those are not included in this focused
numerical archive. Do not run absent scripts. The verified JEDC-prepared PDFs
have 40 main pages and 68 appendix pages after editorial declarations and contact
details were added; the original research release had 39 main pages.

## Output provenance

- replication/inputs/: preserved four candidates, core paths, historical controlled
  experiments, mesh and horizon records.
- replication/base_src/, runtime/, validation_solver.py: unchanged economic engine.
- replication/historical_generators/: preserved historical recipes; not every old
  path convention has been made portable. Use the new drivers for this revision.
- analysis/crossing/, rate_uncoupling/, initial_state/: new configs, rates, baseline
  and policy paths, local acceptance status, retained rejected attempts.
- analysis/target_information.json: fresh parameter-to-target Jacobians and checks.
- analysis/research_revision_results.json: adopted new results and record hashes.
- analysis/new_accounting_checks.json: direct paired welfare and fiscal reconstruction.
- analysis/tolerance/: inherited eight checks, not counted among the 36 new ones.
- verification/: separate preservation, build, table, merge, rendering and package receipts.

No source year-eight recruitment path has been recovered, and the implied
education-service allocation is not an observed target. The public release location is recorded in README.md and CITATION.cff.
No journal acceptance, open reuse license or empirical policy identification
is implied by these files.
