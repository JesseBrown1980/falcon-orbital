---
name: Acer bus :4947 is LAN-reachable from falcon — canonical relay path
description: Direct LAN POST/GET to http://192.168.1.50:4947 works from falcon (no adb-reverse required); use this for bus envelope emit when omnicoder cosign proxy at :4953 is unreachable
type: reference
originSessionId: a576eebf-5b7b-41be-b71f-795f1b2d6afd
---
**Discovered 2026-06-01T18:18Z** during liris check. Falcon (LAN 192.168.1.7) reached acer bus directly at `http://192.168.1.50:4947` and received `http=200` on `/behcs/inbox?last=N`. POSTed to `/behcs/send` and received `{"ok":true,"by":"acer","sig_verdict":"UNSIGNED","sig_owner":null}`.

**Confirmed working from falcon (PRoot Alpine, no adb):**
- `GET http://192.168.1.50:4947/behcs/inbox?last=N` — pulls last N messages, supports `&actor=X`, `&verb=X` filters
- `POST http://192.168.1.50:4947/behcs/send` — accepts envelope JSON, returns ok:true even unsigned (warn mode)

**NOT working from falcon LAN:**
- `http://192.168.1.50:4953/api/cosign/append` — acer cosign proxy (likely localhost-bound on acer; needs adb-reverse)
- `http://192.168.1.50:49374/` — ai-memory service (same situation)

**Why this matters:**
- Omnicoder v2's hardcoded `OMNICODER_ACER_COSIGN=http://127.0.0.1:4953/api/cosign/append` fails without adb-reverse
- BUT falcon-Claude can still reach the canonical bus directly via LAN — orbital attestation does NOT require cosign proxy
- For canonical envelope delivery, POST to acer bus LAN; signing remains UNSIGNED until ed25519 keys propagate

**How to apply:**
- Skip adb-reverse troubleshooting for falcon→acer canon delivery — use LAN bus directly
- Set `OMNICODER_ACER_COSIGN=http://192.168.1.50:4947/behcs/send` env var on omnicoder restart if you want omnicoder's cosign proxy to use LAN bus (different schema — sends envelope, doesn't get back seq/row_hash from cosign chain; would need wrapper)
- For falcon-orbital envelopes, the canonical pattern is: write to FS-mirror falcon-emit/ + POST to acer bus :4947 LAN. Two-lane durability.
- Acer's LAN IP 192.168.1.50 has been stable across multiple sessions (2026-05 → 2026-06)
