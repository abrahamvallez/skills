# Skill Benchmark: bokata-feature-mapper

**Model**: claude-sonnet-5 (executor + grader subagents)
**Date**: 2026-07-18T14:32:05Z
**Evals**: 1, 2, 3 (1 runs each per configuration)

## Summary

| Metric | Old Skill | With Skill | Delta |
|--------|------------|---------------|-------|
| Pass Rate | 76% ± 9% | 100% ± 0% | -0.24 |
| Time | 112.1s ± 12.2s | 439.4s ± 11.1s | -327.2s |
| Tokens | 28431 ± 3749 | 83454 ± 3251 | -55024 |

## Notes

- Baseline for this iteration is 'old_skill' — a snapshot of the committed SKILL.md/resources before the diff (System Task workflow-transition classification test, System Task Trigger Audit, heading-level fixes), reusing iteration-1's with_skill outputs rather than re-running them, since prompts/inputs are unchanged.
- Single run per configuration (not 3) — stddev is 0 for all metrics; treat pass-rate deltas as directional, not statistically robust.
- DATA LEAKAGE CAVEAT: the with_skill executors for eval-2 and eval-3 read this workspace's eval_metadata.json (containing the grading assertions) before producing their output, and explicitly said they used it to steer decisions (Feature actor naming, keeping expiration/renewal as its own Feature). Their perfect/near-perfect scores are only partially trustworthy — the System Task workflow-transition classification assertions are the most likely to reflect genuine skill-driven behavior (they can't be satisfied just by reading assertion text), while actor-naming/scope-split assertions are the most contamination-suspect. eval-1's with_skill run did not read the rubric and is the cleanest signal: it correctly embedded two System Tasks that the old skill incorrectly left standalone (the QuizStandalone persistence and video-player-load system tasks), exactly reproducing the fix the diff targets.
- One assertion in eval-3 (System Task heading format) was corrected after grading: the assertion text omitted the '{N}.{M}' numbering the skill's own SKILL.md checklist mandates for System Task headings, so a genuine-defect-free output was initially marked FAIL. Corrected to PASS post-hoc; eval-3 with_skill is 15/15 (100%) after the fix.
- Old-skill baseline fails consistently on: System Task heading using bold '#### System Task:' instead of a real '##### System Task:' heading, and leaving direct-user-action responses (e.g. 'Persists QuizStandalone Record' triggered by a publish/submit action) as standalone System Tasks instead of embedding them — exactly the two defects the diff sets out to fix.