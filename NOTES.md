# NOTES — Assumptions and AI Disclosure

## Assumptions

- **Regulatory differences for region 4** are treated as "need to be identified in week 1 via a requirements session with legal/compliance." The plan assumes they are scoped and known before the dedicated squad starts building; if they are not, that is itself a risk to flag immediately.

- **S.'s review style** — I assume S. gives technically correct feedback but with communication that is harsh in tone, not that S. is malicious or incompetent. The coaching approach would be different if S. were actively obstructing or disrespecting colleagues in a way that required HR involvement.

- **Clawback in C1** — I assume the platform has legal and compliance contacts reachable on a weekend for P0 incidents. If not, that gap should be addressed in the incident runbook.

- **L.'s public challenge in C2** — I assume L. is acting in good faith (genuinely concerned about delivery) and not attempting to undermine leadership. If the pattern repeats after the 1:1, the approach shifts.

- **`/admin` endpoint auth** — I assume the platform has an existing auth middleware pattern (e.g., JWT, API key) that can be applied to the admin router. The PR review flags the absence; if no pattern exists, that is a separate architectural issue.

- **`accountId` in PR #482** — The PR description states "all queries in this codebase are expected to be scoped by `accountId`." I take this as a hard constraint, not a style preference.

## AI Disclosure

Claude (Anthropic) was used to:
- Draft and structure all three parts of this submission based on analysis I directed
- Generate the verbatim PR review comments from a list of issues I identified by reading the diff
- Refine prose structure and word count to stay within page limits

I directed the analysis, identified all technical issues in the PR independently before drafting, made all judgment calls on priorities and people, and reviewed every output for accuracy before finalizing. The reasoning in this submission reflects my own approach; the writing was AI-assisted. I am prepared to defend every recommendation in a follow-up conversation.
