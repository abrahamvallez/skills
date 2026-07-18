# Skill Benchmark: bokata-feature-slicer

**Model**: claude-sonnet-5 (executor + grader subagents)
**Date**: 2026-07-18T14:32:05Z
**Evals**: 1, 2 (1 runs each per configuration)

## Summary

| Metric | With Skill | Without Skill | Delta |
|--------|------------|---------------|-------|
| Pass Rate | 100% ± 0% | 63% ± 0% | +0.37 |
| Time | 259.4s ± 58.5s | 140.6s ± 0.4s | +118.8s |
| Tokens | 80197 ± 2022 | 39403 ± 577 | +40794 |

## Notes

- First-ever eval setup for this skill — baseline is 'without_skill' (no methodology guidance at all), not a prior skill version.
- Single run per configuration — stddev is 0 for all metrics; treat as directional signal from n=1, not a statistically robust estimate.
- Without-skill baselines both under-covered: eval-1 leaked DB/field names (`credits`, `plan`, `upload_id`) into user-facing descriptions and used priority tags instead of the required '[User Task Name]' tag format; eval-2 only walking-skeletoned 3 of 6 User Tasks, deferring Filter/Sort/Search entirely rather than giving each a minimal option. The with_skill runs covered all tasks in both cases and stayed at user-facing altitude.
- The with_skill eval-1 executor explored the actual clip2coach-api codebase (available as an additional working directory) and grounded its walking skeleton in real existing patterns (e.g. handlers/videos.js) rather than inventing a generic architecture — a plausible but unplanned realism bonus specific to this environment, not something the skill instructs directly.