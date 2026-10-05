# mta-sts

Hosts the [MTA-STS](https://datatracker.ietf.org/doc/html/rfc8461) policy for `lyrebirdsyntax.com` via GitHub Pages at `https://mta-sts.lyrebirdsyntax.com/.well-known/mta-sts.txt`.

- DNS (CNAME `mta-sts`, TXT `_mta-sts`, TXT `_smtp._tls`) lives at Squarespace.
- Policy started in `mode: testing` (2026-08-06) and moved to **`mode: enforce`, `max_age: 604800` on 2026-10-05**. Any policy edit must be followed by **bumping the `id=` value in the `_mta-sts` TXT record** (e.g. to the new date) so senders re-fetch; the id for the enforce flip is `20261005a`.
- Rollback: set `mode: testing`, commit, push, bump the id again — senders cache for at most `max_age` (1 week).
- TLS-RPT reports (JSON, from Google/Microsoft) only arrive on days a reporting sender delivered to the domain over SMTP; Google→Google mail is internal and never generates one.
- `_config.yml` makes GitHub Pages (Jekyll) serve the dot-directory `.well-known`.
