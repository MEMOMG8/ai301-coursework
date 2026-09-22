# Rubric: is this a good first issue?

Seven checks across five families: the maintainer is alive, the repo is in
use, the scope fits a newcomer, nobody else is already on it, and the
repo's policy allows the way I work. Five checks are `required` and gate
the verdict. Two are `preferred`: they never change a verdict and exist
only to rank the issues this rubric accepts.

**Reference date for every recency threshold below.** In eval mode, the
`captured:` date at the top of the bundle. In live mode, today. A
threshold is never measured against the wrong clock.

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| `maintainer-active` | The dates in the `last 5 default-branch commits` list in the Repo facts block (live: the commit list on the repo front page). | The most recent default-branch commit is dated 180 days or fewer before the reference date. | required |
| `repo-in-use` | The `archived:` flag on the repo line, the `latest release` line, and the `last push to any branch` line in Repo facts. | The repo is not archived, AND at least one of these holds: a release dated 180 days or fewer before the reference date, or a push to any branch 180 days or fewer before the reference date. A repo that publishes no releases at all is not penalised — commit and push activity carry liveness on their own. | required |
| `scope-bounded` | The issue body and the full comment thread in the bundle (live: the issue page and its thread). | Passes by default, and fails only when one of these is present: (a) the issue describes itself as an umbrella, tracking, meta, or mega issue, or its sub-items are separate linked issues, or the change spans an indefinite number of sites in the codebase ("across the codebase", "every module", "all call sites") — a detailed implementation plan for a single deliverable does not fail here, even when it names several files to change; (b) the thread shows the design is still being debated and no maintainer has settled it; (c) a maintainer states the fix touches core internals; (d) the issue is a usage or support question rather than a request for a change; (e) the issue requests a new feature and nobody from the project has endorsed it — it was not filed by a maintainer, no owner, member, or collaborator comment endorses it, and it carries no accepted-feature or roadmap label. Bug reports and documentation tasks are never graded on (e). A terse body, a bare checklist, or a bug report without reproduction steps does not fail this check — the size of the work being asked for is what is graded, not the polish of the writeup. | required |
| `unclaimed` | The `assignees:` and `linked PRs:` fields on the `this issue:` line in Repo facts, plus every claim comment in the Comments section and any PR mentioned there. | Fails if an assignee is set, or if any linked or thread-mentioned PR is open. A claim comment ("I'll take this", "working on this") fails the check only when it is dated 180 days or fewer before the reference date, or when its author has commented again since; an older claim with no subsequent activity from its author is treated as abandoned and does not block the issue. Where the sidebar fields and the thread disagree, the thread is believed. | required |
| `ai-policy-allows` | The `contribution policy` line in Repo facts (live: `CONTRIBUTING.md` in the repo root or `.github/`, any contributor docs it links to, a dedicated `AI_POLICY.md`, and PR or issue templates). | Fails only when the policy bans AI-generated contributions outright. Passes when the policy is silent, and passes when it sets conditions — disclosure, personal understanding, testing, human review of AI output — because conditions are terms to follow, not reasons to walk away. | required |
| `maintainer-responsive` | The `maintainer first-response sample` in Repo facts: five recently updated issues with days to the first owner, member, or collaborator comment. | At least 3 of the 5 sampled issues received a first maintainer comment within 30 days. | preferred |
| `newcomer-labelled` | The `labels:` list on the issue's opening line. | The issue carries a `good first issue` label, or an equivalent newcomer label the repo uses in its place. | preferred |

## Verdict rule

**Accept when every `required` check is graded `pass`. Otherwise reject.**

A `required` check graded `fail` rejects the issue. A `required` check
graded `unclear` also rejects it: `unclear` counts as `fail` throughout
this rubric, because a signal I could not verify is not a signal I can
lean on for a first contribution. The one place absent evidence is not
punished is written into `repo-in-use` as a disjunction rather than left
to `unclear` — a repo with no releases can still pass on commit activity.

`preferred` checks never change a verdict. They cannot rescue a rejected
issue and cannot sink an accepted one. Report their grades, and use them
to rank accepted candidates: among issues this rubric accepts, one in a
repo that answers its issues within 30 days and carries a newcomer label
outranks one with neither.
