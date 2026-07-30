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
The internal filesystem paths, internal repository names and the customer program name were removed
from the working tree on 2026-07-30, but this repository is public and every one of those strings is
still readable in the commit history. An older commit also describes the previous desktop app as
being powered by a named VPN stack, which is no longer accurate and was never meant as a public
statement about the infrastructure.

Removing it from the tip does not remove it from history. Three options, and the choice is Jake's
because each has a real cost:

1. Rewrite the history and force push. Cleanest result. It breaks any existing clone, and GitHub may
   retain unreferenced objects for a period, so it is not an instant guarantee.
2. Delete this repository and recreate it from the current tree. Equally clean, and it loses the
   download counts on the existing release and breaks the release asset URL that customers hold.
   That URL has 39 downloads against it, so this option needs the release republished and the page
   updated in the same move.
3. Accept it. The material is low sensitivity: a program name, some Windows paths, and the name of a
   VPN protocol. Nothing here is a credential, and the audit confirmed all 37 commits are clean of
   secrets.

Recommendation on file: option 3 unless Jake considers the customer program name sensitive, in which
case option 1. Not a decision to make on his behalf.

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

### DP-101 · FIXED · exposure · internal paths and a customer program name were published
The rewrite of this page on 2026-07-30 carried internal material onto a public site: local Windows
paths and internal repository names in the README, and a customer program name in one of the service
descriptions. It was live for roughly half an hour before a program-level audit caught it.

The cause was straightforward and worth recording. The page was written inside a private working
repository and moved into this public one without anyone re-reading it as a public document. Fixed
by removing the material and by adding an explicit statement to the README of what must never be
committed here, so the check does not depend on somebody remembering. The historical copies are
tracked separately as `DP-001`.
