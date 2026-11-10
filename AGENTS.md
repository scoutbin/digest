# AGENTS.md

digest turns logs into readable facts.

- Built on spine (`github.com/scoutbin/spine`): `spine.json` is the tool descriptor, releases come from spine's reusable workflows.

## Repo rules

- The scoutbin org is on GitHub's free plan. Do not rely on paid features.
- Make minimal changes.
- Own the code you touch. Fix nearby defects, unclear names and missing tests you notice, keep the change focused on the task, and call out larger improvements instead of silently widening scope.
- Confirm before any action with side effects, such as pushing, tagging, publishing or editing repo settings.
- Keep commit messages short and imperative. No ticket prefix, no AI or co-author trailers.
- Write tests table-driven, using `testcases` arrays with no duplicated structure.
