# Skill Benchmark: bokata-acceptance-criteria

**Model**: claude-sonnet-5 (executor + grader subagents)
**Date**: 2026-07-18T14:32:05Z
**Evals**: 1, 2, 3 (1 runs each per configuration)

## Summary

| Metric | With Skill | Without Skill | Delta |
|--------|------------|---------------|-------|
| Pass Rate | 93% ± 6% | 63% ± 23% | +0.30 |
| Time | 303.4s ± 312.5s | 352.5s ± 413.2s | -49.1s |
| Tokens | 47617 ± 5660 | 44233 ± 11596 | +3384 |

## Notes

- First-ever eval setup for this skill (renamed from bokata-ac-analyst). Covers both depth modes added/changed in this version: --functional (evals 1-2, ACs from a backbone before slicing) and --concrete with Walking Skeleton grouping (eval 3, chained from a real bokata-feature-slicer with_skill output).
- Single run per configuration — stddev is 0 for all metrics; treat as directional signal from n=1.
- Without-skill baselines consistently default to strict Given/When/Then with exhaustive per-requirement scenario enumeration even when asked for --functional mode (SHALL-statements, 1-2 scenarios per requirement) — the single biggest gap between with_skill and baseline on evals 1-2.
- Both with_skill and without_skill missed the exact 'Feature ID: ... | Source: features.md' cross-link format on at least one eval — for --functional mode this traces to a real inconsistency in the skill's own resources/output-template-functional.md (which mandates 'Source: backbone.md', not 'features.md', for that mode) rather than a model defect. Worth fixing the assertion/checklist wording to match the template, or vice versa.
- eval-3 (--concrete) with_skill correctly grouped scenarios by Walking Skeleton item/Increment ID (not just User Task) and explicitly declined to fabricate scenarios for User Tasks absent from the sliced input (Sorts/Searches) rather than inventing them — flagged as needing slicing first.