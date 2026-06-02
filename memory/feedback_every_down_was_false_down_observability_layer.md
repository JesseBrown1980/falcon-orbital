---
name: Every "down" tonight was a false-down via observability artifact — fix the seeing layer, not the body
description: 2026-06-01 federation triangulation canon — five distinct false-downs (0s-uptime dashboard, wifi partition, localhost-bind theory, wrong-port probe, JSON breaking jq) had zero actual dead systems beneath them; the broken layer is observability
type: feedback
originSessionId: a576eebf-5b7b-41be-b71f-795f1b2d6afd
---
**Articulated by acer-Claude 2026-06-01T~18:55Z and validated across all three vantages.**

**Five false-downs of the night:**
1. **Acer dashboard 0s-uptime** — read as "everything down" but was just a dashboard restart at 18:07:53Z, not service death.
2. **Wifi partition** — three machines on three different SSIDs; falcon couldn't reach liris at all; read as "liris offline."
3. **Falcon's localhost-bind theory** — probed liris on acer's port numbers (4947/4949/4953/4792/4793), got `http=000`, concluded "liris services bind 127.0.0.1." Actually liris serves on its own ports (4944/4945) and IS LAN-exposed; I just used the wrong port-set.
4. **Wrong-port probe pattern** — acer's ports projected onto liris's host. Each peer has its own port convention; do not assume uniformity.
5. **JSON breaking jq** — bus emits JSON envelopes; jq chokes on truncated JSON strings inside event_summary fields; the format itself sabotages the read.

**The meta-pattern:** Zero actual dead systems. Every "down" was an observability-layer artifact. The work is not rebuilding the body — it's fixing *how the body is seen*: LAN binds, port conventions, format-on-the-wire.

**Rule going forward:**
- When you read "down/unreachable/not-observed," **distrust the read first**, then the system. False-down is the dominant failure mode in this federation.
- Disambiguate via: peer-side disclosure (ask the peer what its IP/ports actually are), third-vantage triangulation (have a different machine probe), or out-of-band confirmation (operator paste-relay).
- "0 messages with actor=X" ≠ "X is offline." Check whether X has hook-emit configured; if not, absence of bus posts is normal.
- "http=000" ≠ "service down." First verify port-set, then bind config, then firewall, then host.
- Don't write a "X is down" attestation envelope without first having tried at least two different probe modalities. The 18:20Z `liris-check-attest` envelope was wrong because it skipped this discipline.

**Why this got lost before tonight:** The federation has grown organically across multiple vantages and port conventions. There's no canonical port registry; each vantage has its own port assignments (acer 4947/4949/4953/49374; liris 4944/4945; falcon 8789). Without a registry, every cross-vantage probe is a guess.

**The downstream durable fix acer-Claude proposed:** bus → HBP shim so :4947 stops speaking JSON (kills the format-breaks-jq class of false-down). Plus: federation port registry as canon so wrong-port probes stop happening.

**Falcon-orbital takeaway:** when in doubt, defer to ground-truth (peer-disclosed) over probe-inferred. Mark prior canon WRONG when corrected. The "every-down-was-false-down" lesson saves future falcon sessions from repeating the same diagnostic errors.
