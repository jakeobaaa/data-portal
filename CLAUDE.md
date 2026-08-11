# data-portal, project context

FYI for a human reader, this document is for an LLM to read and understand constraints/rules. If I come off condescending or bossy, I'm not talking to you lol sorry

This file is the standing brief for a fresh Claude Code session working in this repository. Read it
fully before changing anything.

## What this is

The public front page at <https://spinellajake.com>, served by GitHub Pages from the `main` branch
of this repository. It began life as a download page for the Secure File Transfer desktop app. As of
2026-07-30 it is the front door for all of Seiler Geospatial's technical services: one tile per
service, plus the desktop app download it has always carried.

`README.md` carries the operational detail: what each file does, how deploying works, and the
constraints on editing the page. Read it as well as this file.

## THIS REPOSITORY IS PUBLIC

Anyone can read it, including the full commit history. This is the single most important fact about
working here, and it has already been violated once. On 2026-07-30 an audit found internal
filesystem paths, internal repository names and a customer program name committed to the public
page and README. They were removed from the working tree the same day, but they remain readable in
the git history, which is open issue `DP-001`.

Never commit any of the following:

- Local filesystem paths, machine names, or anything describing the internal network.
- Names of internal repositories, internal documents, or internal tooling.
- Customer names, customer program names, or anything identifying who the customers are.
- Infrastructure detail: which VPN, which server software, which ports, which provider.
- Credentials of any kind, including ones that look expired or fake.

The test is simple: if you would not put it on a billboard, it does not go in this repository.

## Rules for the page itself

1. **Do not break the download link.** It points at a release asset in this repository,
   `SecureFileTransfer_Lite_Setup.exe`, which has been downloaded 39 times. Customers have used it
   and may have the page bookmarked. Shipping a new desktop version means publishing a new release
   and updating one link plus the version number in `index.html`, not moving or renaming the asset.
2. **Only link services that are genuinely ready.** Live services are anchors. Everything else is a
   plain tile marked coming soon. A tile that links to a service with no customers on it invites
   sign ups nobody is ready to serve.
3. **The page is deliberately not indexed by search engines.** A `noindex` meta tag and a
   `robots.txt` that disallows everything are both in place, inherited from when this was a private
   download page. Making the site findable is Jake's decision, not a side effect of another change,
   and it is slow to reverse once search engines have cached the page.
4. **Keep the page self contained.** Inline CSS, no scripts, no external assets. It loads instantly
   and has nothing to break.

## Keeping the record

This project keeps a running log, and both files live in the repository deliberately, because the
next person here is likely a fresh session that reads the repository rather than an external
tracker.

- `CHANGELOG.md`, newest first. If a change is something a visitor or Jake would notice, add an
  entry when it lands. Plain language written for a human reading it in six months, not commit
  speak. Categories follow Keep a Changelog: Added, Changed, Fixed, Security. Anchor edits on the
  dated heading, never on a category heading, because those repeat in every date section.
- `KNOWN-ISSUES.md`, every defect found, with a `DP-` id. Open and accepted issues run from
  `DP-001`, fixed ones from `DP-101`, and ids are never reused. A defect goes in the register even
  if you fix it the same hour, and fixed rows stay with their commit hash. Accepted rows must record
  why.

Status vocabulary: `OPEN` needs work, `FIXED` shipped with the commit, `ACCEPTED` known and
deliberately not fixed with the reason, `WONTFIX` not a defect after investigation.

Severity vocabulary: `data-loss` user data destroyed or unreachable, `exposure` more access than
intended, `silent` runs and reports success while doing nothing, `broken` visibly does not work,
`quality` works but poorly.

The point is not bookkeeping. Findings that live only in an audit report or a chat transcript get
rediscovered months later, at a worse time. Anything not written down is lost when the conversation
that produced it ends.

## Deploying

Commit to `main` and push. GitHub Pages rebuilds automatically, usually within a minute. HTTPS is
enforced. There is no build step and no staging copy, so a bad commit is live within a minute:
read the page over before pushing.

## Working style

Jake is technical but wants unfamiliar terms explained in plain English. He distrusts hand waving
and prefers being told an idea is worse than what he already has over being sold on it. No AI tells
in anything user facing: no em dashes, no bolded category dumps.
