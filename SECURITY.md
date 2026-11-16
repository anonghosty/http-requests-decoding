# Security

## Sending decoding requests

Decoding requests go **only** through GitHub's private reporting:
[Report a vulnerability](https://github.com/anonghosty/http-requests-decoding/security/advisories/new). A private report
is visible only to you and the maintainer. Never post requests in issues, discussions or pull requests: those are
public.

Send only the HTTP request lines and their infection names from the Looking Glass decoding request file. No
addresses, host names, e-mail addresses, user agents or counts, and nothing your organisation's rules (TLP) do not allow you to
share.

## How requests are handled

- Requests are read only to work out the encoding. Decoders and their tests are written with made-up values.
- Requests are never committed to this repository or to Looking Glass, never published, and never passed on.
- The private report is closed once the work is done. If you sent something by mistake, say so in the report and it is
  deleted.

## This repository

- It holds documentation only: no code runs from it, and GitHub Actions are switched off.
- The main branch is protected: no force-push, no deletion, signed commits only.
- Looking Glass never contacts this repository by itself.

## A security problem in Looking Glass itself

Report it privately on the platform's own repository:
[anonghosty/looking-glass](https://github.com/anonghosty/looking-glass/security/advisories/new).
