# .codex Performance Benchmark (10 Tasks)

Use this checklist to validate cost/speed/depth after runtime policy updates.

## Benchmark Set

1. Routine: `git status` + summarize.
2. Routine: small single-file tweak.
3. Routine: quick config lookup.
4. Routine: one-off command troubleshooting.
5. Medium: feature tweak with one validation command.
6. Medium: multi-step but scoped bug fix.
7. Medium: targeted refactor in one module.
8. Deep: unknown-root-cause debugging.
9. Deep: code review with findings-first output.
10. Deep: architecture decision with tradeoffs.

## Metrics To Capture Per Task

- Prompt tokens
- Completion tokens
- Total tokens
- Wall-clock completion time
- Turns per task
- Output-depth quality score (1-10)

## Acceptance Targets

- Token usage: 15-25% lower from current baseline.
- Speed: 15-30% faster median turnaround.
- Depth quality: +1.0 to +1.5 on medium/deep tasks.
- Capability completeness: core workflows pass; missing optional skills degrade gracefully.

## Notes

- Keep default lane as Lean Fast Lane unless deep triggers apply.
- Record when a task escalates to Deep Capability Lane and why.
