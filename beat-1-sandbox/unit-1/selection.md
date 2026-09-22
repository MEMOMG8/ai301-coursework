# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the
wrong label is not graded.

---

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/26

**Verdict output**

**The verdict must record `accept` for this issue.** Choose an issue your own skill
accepts. If your skill rejects every candidate you try, that is a signal about your
rubric rather than about the issues: revise it and re-run — retries are unlimited and a
partial re-run costs about $0.20 — or run the skill on different candidates. Output
recording `reject` for the issue you chose earns no credit for this field.

**Scope check:** `codepath/pathreview-ai301-fa26-s3` matches the repo declared in
`scope.md` — the candidate is inside the scoped source. Path Review house rule noted
(classmates' claim comments do not block); it changes nothing here, since the thread
is empty.

**Reference date:** 2026-09-22 (live mode measures against today).

| Check | Weight | Grade | Evidence |
|---|---|---|---|
| `maintainer-active` | required | **pass** | Last `main` commit 2026-09-16 by `Aburke225`, a human author, 6 days before the reference date |
| `repo-in-use` | required | **pass** | `archived: false`; no releases published, but push to `main` on 2026-09-16 is within 180 days |
| `scope-bounded` | required | **pass** | Maintainer-filed bug naming two files and the supplying method; no umbrella framing, no design debate, no core-internals statement |
| `unclaimed` | required | **pass** | `assignees: none`; 0 comments; repo has 0 PRs open and 0 closed; no cross-reference events |
| `ai-policy-allows` | required | **pass** | `docs/CONTRIBUTING.md`: 0 matches for AI terms; PR template: 0; no dedicated AI policy files — silent policy passes |
| `maintainer-responsive` | preferred | **fail** | 0 of the 5 most recently updated issues received a first owner/member/collaborator comment |
| `newcomer-labelled` | preferred | **pass** | `labels: bug, good first issue, safety, tier-1` |

All five `required` checks pass, so the verdict rule yields **accept**.

One note on the preferred failure, which by the rubric cannot change the verdict:
`maintainer-responsive` fails repo-wide because `Aburke225` *authors* every issue
rather than replying in threads, so there is no first-response latency to measure.
The threshold is measuring the wrong thing in a seeded classroom repo. That is a
defect in the check's shape, and the fix belongs in `rubric.md`, not in this run.

```json
{
  "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/26",
  "checks": [
    {"name": "maintainer-active", "grade": "pass",
     "evidence": "Most recent default-branch commit is 2026-09-16 by Aburke225, a human author, 6 days before the reference date 2026-09-22 and well inside the 180-day threshold."},
    {"name": "repo-in-use", "grade": "pass",
     "evidence": "archived: false; the repo publishes no releases, but the last push to main is 2026-09-16, within 180 days, which the rubric accepts in place of a release."},
    {"name": "scope-bounded", "grade": "pass",
     "evidence": "Maintainer-filed bug (Aburke225, COLLABORATOR) naming exactly two files, api/routes/health.py and safety/monitoring.py, plus the method that supplies the value; no umbrella or tracking framing, no design debate in a thread with 0 comments, no core-internals statement, and not a usage question."},
    {"name": "unclaimed", "grade": "pass",
     "evidence": "assignees: none; 0 comments on the issue; the repo contains 0 pull requests open and 0 closed, and the issue timeline shows no cross-referenced or connected events."},
    {"name": "ai-policy-allows", "grade": "pass",
     "evidence": "docs/CONTRIBUTING.md (189 lines covering branching, commits, PR process, CI and code style) contains no mention of AI, and neither does .github/PULL_REQUEST_TEMPLATE.md; no AI_POLICY.md or AGENTS.md exists. A silent policy passes."},
    {"name": "maintainer-responsive", "grade": "fail",
     "evidence": "In the 5 most recently updated issues (#73, #72, #71, #70, #69), 0 received a first owner, member, or collaborator comment, so the 3-of-5 within-30-days threshold is not met."},
    {"name": "newcomer-labelled", "grade": "pass",
     "evidence": "The issue's labels are bug, good first issue, safety, tier-1."}
  ],
  "verdict": "accept"
}
```

---

## Eval iterations

Quote source text directly in each field below. Paraphrase does not satisfy them.

**Run history**

Five runs, in order:

1. `--limit 3` (smoke) — **2/3**
2. `--only issue-01,issue-05,issue-10` — **3/3**
3. `--only issue-20,issue-09,issue-06,issue-12,issue-14` — **4/5**
4. `--only issue-20,issue-09` — **2/2**
5. Full run, `--save-run eval-run.txt` — **19/20**

The final score, 19/20, is the agreement line in the committed `eval-run.txt`.

Run 1 exposed one disagreement (`issue-01`), which run 2 confirmed fixed while
re-checking `issue-05` and `issue-10` as canaries. Run 3 probed the five cases I
expected to be hardest and found the one I had predicted would fail, `issue-20`.
Run 4 confirmed that fix with `issue-09` as the canary. Run 5 is the full run on
record.

**Issue analysis**

**`issue-15`** (zulip/zulip#19589) — the one disagreement in the committed run.

- My rubric's decision: **accept**
- Gold label: **reject** ("years of design debate and two abandoned PRs behind a
  friendly label")

Every required check passed. `scope-bounded` passed on the reasoning that the
thread showed no umbrella framing, no unsettled design debate, and no maintainer
statement about core internals. The signal gold rejects on is the issue's
*history*: it has been open for years and carries two closed, unmerged PRs
(#20840 and #23123) — abandoned attempts that reveal the real difficulty behind a
`good first issue` label.

My rubric had that evidence in hand and did not use it. `unclaimed` explicitly
recorded both PRs as closed, and correctly declined to block on them, because a
closed PR is not an active claim. No check read the same fact as a difficulty
signal, so nothing failed. The miss is a consequence of a deliberate choice I
made when writing `scope-bounded`: I graded the work being asked for, not the
issue's age or its record of failed attempts.

**Check rationale**

`scope-bounded`, quoted as currently written:

> Passes by default, and fails only when one of these is present: (a) the issue
> describes itself as an umbrella, tracking, meta, or mega issue, or its sub-items
> are separate linked issues, or the change spans an indefinite number of sites in
> the codebase ("across the codebase", "every module", "all call sites") — a
> detailed implementation plan for a single deliverable does not fail here, even
> when it names several files to change; (b) the thread shows the design is still
> being debated and no maintainer has settled it; (c) a maintainer states the fix
> touches core internals; (d) the issue is a usage or support question rather than
> a request for a change; (e) the issue requests a new feature and nobody from the
> project has endorsed it — it was not filed by a maintainer, no owner, member, or
> collaborator comment endorses it, and it carries no accepted-feature or roadmap
> label. Bug reports and documentation tasks are never graded on (e). A terse
> body, a bare checklist, or a bug report without reproduction steps does not fail
> this check — the size of the work being asked for is what is graded, not the
> polish of the writeup.

The check is built as **pass-by-default with named disqualifiers**, not as a
positive specification test. That shape came from the evidence guide's warning
that "short is not the same as unscoped": a terse bug report from a maintainer can
be an ideal first issue, so requiring acceptance criteria would reject good work
for bad writing.

Clauses (a) and (e) are the two I revised in response to eval disagreements.

(a) started as "an umbrella or tracking issue, a list of sub-items meant to be
split into separate work". That wording rejected `issue-01`, a docs task whose
body lists five files to change, because the grader read any bulleted list as an
umbrella. Gold accepts it: the five files are one deliverable. I rewrote (a)
around two signals instead — how the issue *describes itself*, and whether the
work spans an indefinite number of sites — and added the explicit carve-out for a
detailed plan. The guide supports both halves: it says "**explicitly** an umbrella
or tracking issue", and gold calls `issue-10` a "**self-described** megaissue".

(e) did not exist until run 3. `issue-20` passed all five required checks and gold
rejects it. It is a one-line feature wish filed by `cursor[bot]` (association
`NONE`) with "Logo asset TBD", zero comments, and a product decision — whether
Excalidraw wants a company-logo tool — that nobody from the project has answered.
None of my four disqualifiers touched it. (e) generalizes the lesson rather than
patching the case: an unendorsed feature request is wasted work for a newcomer,
because the PR is decided on product grounds before anyone reads the code.

**Trade-offs**

`scope-bounded` gives up the issue's **history** as a difficulty signal, and
`issue-15` is the case I accept it will miss. The evidence guide names that signal
directly — "an issue open for years with several abandoned attempts (closed,
unmerged PRs in its history) is telling you something about its real difficulty" —
and I chose not to encode it. Grading age and failed attempts means rejecting
issues on other people's track record rather than on the work being asked for, and
`issue-09` is the case that made me wary: it is old, carries a claim from 2022, and
gold accepts it. I took a known one-issue cost over a rule I could not aim
precisely.

Both revisions were confirmed against canaries rather than assumed:

- After rewriting (a), I re-ran `--only issue-01,issue-05,issue-10`. `issue-01`
  flipped to accept as intended, and both umbrella rejects held, for 3/3. The two
  halves of the new clause each carried one canary on their own: `issue-05` failed
  on indefinite scope ("no single deliverable, and 12 linked PRs across unrelated
  files"), `issue-10` on self-description ("titled 'Documentation request
  megaissue'... ~120 separate linked issue numbers"). Neither half is dead weight.
- After adding (e), I re-ran `--only issue-20,issue-09`. `issue-20` flipped to
  reject and `issue-09` — the only accepted feature request in the set, where a
  maintainer invited takers — stayed accepted, which is the case (e) was written to
  spare.

One further weakness the full run surfaced, in a `preferred` check rather than this
one: `maintainer-responsive` graded `unclear` on `issue-15` because the bundle
supplied only two of the five sampled response times, and my threshold is phrased
as "3 of the 5". It changed no verdict, since preferred checks cannot, but the
threshold assumes a complete sample that the bundles do not always provide.

---

## Selection rationale

Graded on whether all three are answered, in your own words. Not on how good the
reasoning is, and not on length — a short honest answer to each earns the full marks.
This is also the basis for the claim comment you write in Unit 2.

**Selection rationale**

**1. Fit to my interests and to the time available.**

I am interested in #26 because it combines AI safety monitoring with a backend API
health endpoint, which fits my goals in backend, cloud, and Applied AI. The 2–4 hour
estimate feels realistic, and the task is scoped enough for me to complete carefully.

**2. What the verdict identified correctly, and what I weighed that the rubric could not.**

I agree with the verdict because the issue is clearly defined, unassigned, and has no
open PRs. However, I chose #26 instead of #53 because another student was already
actively investigating #53, even though the rubric still considered it unclaimed.

**3. The anticipated difficulty in claiming it.**

I think it should be relatively easy to claim because the repository has no PRs and
there is no visible work on this issue. The five required CI jobs may take some care,
but they give me a clear way to verify that the change is correct.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
