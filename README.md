# mta-sts

Hosts the [MTA-STS](https://datatracker.ietf.org/doc/html/rfc8461) policy for `lyrebirdsyntax.com` via GitHub Pages at `https://mta-sts.lyrebirdsyntax.com/.well-known/mta-sts.txt`.

- DNS (CNAME `mta-sts`, TXT `_mta-sts`, TXT `_smtp._tls`) lives at Squarespace.
- Policy starts in `mode: testing`. After ~2 weeks of clean TLS-RPT reports (mailed daily to admin@), edit `.well-known/mta-sts.txt` to `mode: enforce` and `max_age: 604800`, commit, **and bump the `id=` value in the `_mta-sts` TXT record** (e.g. to the new date) so senders re-fetch the policy.
- `_config.yml` makes GitHub Pages (Jekyll) serve the dot-directory `.well-known`.
