## Part A - 90-Day Plan
### 1. Diagnosis
Three root patterns, not eleven separate incidents.

**Pattern 1: No enforcement layer for money correctness.**

Incidents #1 (idempotency), #4 (float arithmetic), and patterns in #5-9 all passed review before reaching production. PR #482 on day 9 repeats all three. The codebase has the right conventions but nothing enforces them - convention without enforcement is just advice.

**Pattern 2: Single points of failure in people, not systems.**
S. is the sole wallet engine expert → bottleneck for all payment reviews. T. is the sole pipeline owner → incidents #10-11 happen when T. is out. Region-3 config was copy-pasted with no checklist. Knowledge lives in individuals, not process.

**Pattern 3: No automated safety net for money flows.**
2 QA for 20 engineers (1:10 ratio) cannot scale. Manual QA catches regressions late. No automated regression suite for critical money paths. Without automation, every release risks repeating incidents #1 and #4.

### 2. Priorities and Trade-offs

**Incident prioritization:** We cannot retroactively fix past incidents, but we prevent new ones. Incidents #1, #4, #5-9 are preventable with the checklist and automation. Incidents #2, #3, #10-11 need operational fixes (runbook, knowledge transfer). CEO saw incident #1 - money-impacting incidents are the non-negotiable priority.

**Do in this quarter, in order:**

**Weeks 1-2: Stabilize + build safety net**
- Payment PR checklist: S. defines, I enforce. Prevents incidents like #1, #4.
- Incident process: on-call rotation, P0 runbook, CEO comms template.
- Start QA automation: QA1 begins automated suite for critical money flows (deposit, withdrawal, cashback) - 5 scenarios by week 3.
- Team training: L. facilitates 90-min session for leads/mids on how people issues cascade to delivery. Sets shared language before individual coaching.

**Weeks 3-10: Region-4 launch + scale QA**
- Launch squad: S., D., one mid, one junior, QA1. S. anchors launch, not org-wide review.
- QA contractor: hire for launch period to bridge 1:10 → 1:7 ratio. Start week 3.
- Automation expands: 15 scenarios by week 6, runs on every payment PR.
- Add QA to open reqs: target fill week 8, permanent hire post-launch.

**Explicitly not doing this quarter:**
- Codebase refactor, tech stack changes, new tooling platforms.
- Attempt to fix S.'s review style via confrontation (long-arc coaching only).
- Block launch on filling both BE headcounts (start pipeline, don't block).

Reasoning: Everything deferred doesn't help region-4 ship or prevent money incidents. Everything we do addresses at least one.

### 3. Process Changes

**P1: Payment PR Checklist - Week 1.** 
Six-item checklist in PR template, auto-triggered for wallet/payment files: accountId scoping; idempotency (DB + app); DECIMAL/bignumber; transaction boundary; structured logging; admin auth. S. authors, author self-certifies, reviewer verifies. Success: zero money-impacting incidents from reviewed code in 60 days.

**P2: Automated Money Regression Suite - Weeks 2-6.** 
QA1 builds E2E tests: deposit idempotency, withdrawal, cashback, cross-brand isolation. 5 scenarios by week 3, 15 by week 6, runs on every payment PR. Success: suite catches at least one issue before it reaches manual QA within 30 days.

**P3: Incident On-Call + P0 Runbook - Weeks 1-2.** 
Weekly on-call rotation, I back-stop P0. Runbook: freeze payouts → page S. → notify CEO in 15 min with template. Success: every incident has owner, MTTR tracked from first alert.

**P4: QA Shift-Left - Week 2.** 
QA in Payments planning from day one. Payment stories need written acceptance criteria before coding starts; QA signs off on criteria. Success: regression count at QA stage decreases.


### 4. Metrics

| Metric | Why | Target |
|---|---|---|
| **Money-impacting incidents / month** | Board-level commitment. CEO saw incident #1. If not zero, nothing else matters. | 0 for quarter |
| **Automated test coverage for money paths** | Manual QA doesn't scale. Automation is the only way to prevent #1, #4 from repeating at scale. | 15 scenarios by week 6, 100% pass rate |
| **MTTR for P0/P1** | Trending up. Clearest leading indicator of org health we can move. | 50% reduction in 60 days |
| **Region-4 launch gates on time** | Delivery leading indicator. Gates: integration tests (week 6), config review (week 8), soft launch (week 9). | Reviewed weekly |

Not measuring: story points, velocity, PR count. These are gamed and reveal nothing about correctness.

### 5. People

**Team-wide (week 2):** L. runs 90-min session for all leads/mids: "How people issues cascade to team goals" - using recent incidents as case studies. Shared language before 1:1s.

**S.:** Author the payment checklist + anchor region-4. Checklist pre-filters PRs, reducing S.'s review load.

**T.:** Pair with one mid week 1 for pipeline knowledge transfer. Not sole on-call.

**2 open BE headcounts:** Financial/transactional background. Pipeline starts week 1, offer week 6, onboard post-launch.

**QA capacity:** 1:10 ratio is unsustainable (industry standard 1:5–1:7). Fix: (1) shift-left (P4), (2) contractor for launch weeks 3–10, (3) permanent QA hire targeting week 8. Fallback if hiring slips: QA writes manual test cases, juniors execute under QA guidance - distributes load without sacrificing coverage. Automation (P2) is the long-term answer.
