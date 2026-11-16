# HTTP Requests Decoding

Encoded HTTP requests that [Looking Glass](https://github.com/anonghosty/looking-glass) could not decode, sent in by
CSIRTs so that a future release can decode them automatically.

This repository is kept apart from the platform on purpose: no code from here runs in Looking Glass, and nothing in
Looking Glass sends anything here by itself. A CSIRT analyst decides what to share, and shares it by hand.

## What to send

Only the HTTP requests, as the sinkhole recorded them. In Looking Glass: **Findings → Requests Looking Glass could not
decode → Send to the Looking Glass creator → Download the decoding request**. The file holds up to five request lines,
each with the infection name it is filed under, and nothing else. Only the value that could not be decoded is
kept; every other parameter's value reads `<value>` and any address reads `<address>`:

```json
{
 "looking_glass_decoding_request": 2,
 "made": "2026-11-16T08:00:00Z",
 "requests": [
  {"infection": "example.family", "request": "GET /example/path?id=<value>&k=ENCODED-VALUE HTTP/1.1"}
 ]
}
```

Never send:

- an IP address, host name or e-mail address of a constituent or a device;
- the C2 host, the user agent or any count from your own reports;
- anything your organisation's rules (TLP) do not allow you to share.

Decoded, an encoded value may hold the device's own data (a MAC address, a hardware ID, a CPU id). Treat every request
as sensitive.

## How to send it: privately

1. Open **[Report a vulnerability](https://github.com/anonghosty/http-requests-decoding/security/advisories/new)**
   (the **Security** tab of this repository). GitHub keeps the report private: only you and the maintainer see it.
2. Title: `Decoding request`.
3. Paste the contents of the downloaded file into the description, inside a code block. Leave the other fields as
   they are.
4. Submit. When a decoder is added, the release notes of Looking Glass say so, without your requests in them.

Public issues are switched off for requests: please do not post requests anywhere public, including discussions,
pull requests or other projects.

## What happens next

The maintainer works out the encoding offline, writes a decoder and its tests with **made-up** values only, and ships
it in a Looking Glass release. Your requests are never committed to this repository or to Looking Glass, and the
private report is closed once the work is done.

## Security

See [SECURITY.md](SECURITY.md).
