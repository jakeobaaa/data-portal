# Known issues

The defect register for the public site. Every issue found, whether fixed, open, or accepted.

Findings that live only in an audit report or a chat transcript get rediscovered months later. If
you find something, it goes here even if you fix it the same hour: the value is in seeing which
shapes keep recurring.

**Status**: `OPEN` needs work · `FIXED` shipped, with the commit · `ACCEPTED` known and
deliberately not fixed, with the reason · `WONTFIX` not a defect after investigation.

**Severity**: `data-loss` user data destroyed or unreachable · `exposure` more access than
intended · `silent` runs and reports success while doing nothing · `broken` visibly does not
work · `quality` works but poorly.

IDs are prefixed `DP-` and never reused. Open and accepted issues run from `DP-001`, fixed ones
from `DP-101`, following the convention used across the other repositories.

---

## Open

### DP-001 · OPEN · exposure · internal detail remains in the public git history
The internal filesystem paths and internal repository names were removed from the working tree on
2026-07-30, but this repository is public and both are still readable in the commit history.

Re-scoped on 2026-07-31. This issue originally also covered the C.A.R.E. programme name, on the
strength of an audit finding that turned out to be wrong: Seiler advertises that programme publicly,
so nothing was ever exposed by naming it. Only genuinely internal strings remain in scope, which in
practice means the local Windows paths.

A separate matter, listed here because it lives in the same history: an older commit describes the
previous desktop app as powered by a named VPN stack. That is an advertising judgement about
disclosing an infrastructure choice rather than a security question, and it is Jake's call.

Removing it from the tip does not remove it from history. Three options, and the choice is Jake's
because each has a real cost:

1. Rewrite the history and force push. Cleanest result. It breaks any existing clone, and GitHub may
   retain unreferenced objects for a period, so it is not an instant guarantee.
2. Delete this repository and recreate it from the current tree. Equally clean, and it loses the
   download counts on the existing release and breaks the release asset URL that customers hold.
   That URL has 39 downloads against it, so this option needs the release republished and the page
   updated in the same move.
3. Accept it. The material is low sensitivity: some local Windows paths, and separately the name of
   a VPN protocol. Nothing here is a credential, and the audit confirmed all 37 commits are clean of
   secrets.

Recommendation on file: option 3. What remains in the history is a handful of local Windows paths,
which reveal a folder layout and nothing more. The audit confirmed all 37 commits are clean of
credentials. With the C.A.R.E. name correctly out of scope, the case for rewriting history and
breaking the release URL that 39 downloads point at is weaker than it was. Not a decision to make on
Jake's behalf either way.

### DP-002 · OPEN · quality · the page advertises services that are not ready
The page shows a tile for hosted mobile mapping workstations, which is concept stage with no code
written and is gated on a Trimble approval that has not arrived. It also links the route planner,
which is deployed and working but has no customers outside Seiler, against this repository's own
stated rule that a tile linking a service with no customers invites sign ups nobody is ready to
serve.

Both were deliberate at the time and both may be fine: coming soon is an honest label, and the route
planner URL was already public. Flagged because the page now makes public claims about a service
whose existence depends on a third party agreeing to it. Awaiting Jake's decision on what should be
advertised today.

## Fixed

### DP-101 · FIXED · exposure · internal paths were published on the public site
The rewrite of this page on 2026-07-30 carried internal material onto a public site: local Windows
paths and internal repository names in the README. It was live for roughly half an hour before a
program-level audit caught it.

Corrected 2026-07-31. This entry originally also cited the C.A.R.E. programme name as exposed
material. That was wrong, and the error was the audit's rather than this project's: Seiler
advertises the programme publicly, so naming it exposed nothing. The removal of that name was not a
security fix and is tracked separately as `DP-002`. The lesson worth keeping is that confidentiality
is a fact about the business, not a property that can be read off a string in a repository, and an
internal-sounding acronym next to an unannounced service is not evidence of anything.

The cause was straightforward and worth recording. The page was written inside a private working
repository and moved into this public one without anyone re-reading it as a public document. Fixed
by removing the material and by adding an explicit statement to the README of what must never be
committed here, so the check does not depend on somebody remembering. The historical copies are
tracked separately as `DP-001`.
