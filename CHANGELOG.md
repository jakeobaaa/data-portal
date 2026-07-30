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

## 2026-07-30

### Changed
- The page became the front door for all of the technical services rather than a download page for
  one app. Six service tiles, of which the two that are genuinely usable are links and the rest are
  marked coming soon. The desktop app download stays, because that installer has been downloaded 39
  times and customers may have the page bookmarked, and it now carries a note that the browser
  service does the same job without installing anything.

### Security
- Removed internal detail from the public README and page: local filesystem paths, the names of
  internal repositories and documents, and a customer program name that appeared in a service
  description. This repository is public and that material should never have been committed to it.
  Found by a program-level audit the same day, roughly half an hour after the deployment.
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
