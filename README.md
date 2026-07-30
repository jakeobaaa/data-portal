# data-portal

The public front page at <https://spinellajake.com>, served by GitHub Pages from this repository's
`main` branch.

It began as a download page for the Secure File Transfer desktop app. As of 2026-07-30 it is the
front door for all of Seiler Geospatial's technical services: a tile per service, plus the desktop
app download that the page has always carried.

## What is here

| File | Purpose |
|---|---|
| `index.html` | The whole page. Self contained, inline CSS, no scripts, no external assets |
| `CNAME` | `spinellajake.com`. Deleting this breaks the custom domain |
| `robots.txt` | Currently disallows all crawlers, matching the `noindex` tag in the page |

## Things to know before editing

**The download link points at a release asset in this repository.** It is
`releases/download/v7.0.0/SecureFileTransfer_Lite_Setup.exe`, and it has been downloaded 39 times,
so customers have used it and may have the page bookmarked. Do not remove or rename that link
without putting a replacement in its place. To ship a new desktop version, publish a new release
here and update the one link and the version number in `index.html`.

**The page is deliberately not indexed by search engines.** Both `robots.txt` and a `noindex` meta
tag say so, inherited from when this was a private download page. That is a one line change in each
file whenever the services are ready to be found publicly. Worth doing deliberately rather than by
accident: once a page is indexed and cached, taking it back out is slow.

**Only link services that are genuinely ready.** Live tiles are anchors, everything else is a plain
tile marked coming soon. A tile linking to a service with no customers on it invites sign ups nobody
is ready to serve.

## Deploying

Commit to `main` and push. GitHub Pages rebuilds automatically, usually within a minute. HTTPS is
enforced.

## Related

The service this page was built for lives in `D:\03_Scripts\SEILER-TRANSFER`. The wider picture,
including which services exist and what stage each is at, is in `D:\03_Scripts\SEILER-CONSOLE`,
whose `STATUS.md` is the program status board.
