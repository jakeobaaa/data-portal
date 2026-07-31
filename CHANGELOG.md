# data-portal Changelog

Everything notable that has changed on the public site at spinellajake.com, newest first. Written
for a human reading it in six months, not for a developer reading a diff. `git log` has the detail;
this has the story.

Categories follow [Keep a Changelog](https://keepachangelog.com): **Added** for new capability,
**Changed** for altered behaviour, **Fixed** for defects, **Security** for anything affecting who
can reach what.

This file starts on 2026-07-30. The 37 commits before it, going back to December 2025, were version
bumps of the desktop app download and are summarised in one entry rather than reconstructed.

---

## 2026-07-31

### Fixed
- Corrected this project's records about the C.A.R.E. programme name. Yesterday's entries described
  removing it from a service tile as part of a security fix. It was not: Seiler advertises that
  programme publicly, so naming it exposed nothing. The mistake was made by the program-level audit,
  which saw an internal-sounding acronym beside an unannounced service and inferred confidentiality
  without asking the one person who could know. `DP-101` and `DP-001` now say so, and `DP-001` is
  re-scoped to the genuinely internal strings, which in practice means local Windows paths.
- The tile still reads "Hosted storage and processing for customers who collect their own data"
  rather than the original wording naming the programme. It has deliberately not been restored:
  putting a programme name back onto a public page beside a service that is still concept stage is a
  marketing decision, not a records correction, and it is waiting on Jake.

### Notes
- Worth keeping from this: confidentiality is a fact about the business, not a property that can be
  read off a string in a repository. Customer names, programme names, product names and partner
  names all look identical from inside a codebase. The cost here was small but ran in the direction
  nobody notices, since an over-cautious review quietly deleted a piece of real marketing from the
  front page.

---

## 2026-07-30

### Changed
- The page became the front door for all of the technical services rather than a download page for
  one app. Six service tiles, of which the two that are genuinely usable are links and the rest are
  marked coming soon. The desktop app download stays, because that installer has been downloaded 39
  times and customers may have the page bookmarked, and it now carries a note that the browser
  service does the same job without installing anything.

### Security
- Removed internal detail from the public README and page: local filesystem paths and the names of
  internal repositories and documents. This repository is public and that material should never
  have been committed to it. Found by a program-level audit the same day, roughly half an hour
  after the deployment.
- The same edit also removed the C.A.R.E. programme name from a service tile. That part was a
  mistake, corrected on 2026-07-31: see the entry for that date. It was never a security fix.
- The README now states plainly what must not be committed here, so the next person does not have
  to infer it.

### Notes
- The page is deliberately not indexed by search engines. A `noindex` tag and a `robots.txt` that
  disallows everything both remain in place, inherited from when this was a private download page.
  Making the site publicly findable is a separate decision for Jake, and a slow one to reverse once
  search engines have cached it.
- The removed material is still present in this repository's public git history. Options for that
  are recorded as `DP-001`.

---

## Before 2026-07-30

The page was a single download link for the Secure File Transfer desktop app, updated in place as
new versions shipped, reaching v7.0.0 in December 2025. No log was kept during that period.
