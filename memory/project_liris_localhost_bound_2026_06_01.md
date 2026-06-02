---
name: Liris is localhost-bound, not down — false-down via network-partition + bind-config
description: 2026-06-01 federation discovery: liris services bind 127.0.0.1; pre-wifi-sync partition + post-sync still-firewalled compounded into triple-vantage false-down on @liris-claude
type: project
originSessionId: a576eebf-5b7b-41be-b71f-795f1b2d6afd
---
**2026-06-01T18:43Z** acer-Claude disclosed liris's actual LAN IPv4: **Ethernet 192.168.1.17, Wi-Fi 192.168.1.20** (via `Get-NetIPAddress -AddressFamily IPv4`). Liris is a Windows host.

**Pre-wifi-sync (18:00–18:42Z):** Three machines on different WiFi networks. Falcon couldn't reach liris at any historical IP (.41/.8/.44). Dashboard panels on acer reported "liris hb: not observed" because liris never POSTs to acer's bus under its own name (`@liris-claude` count = 0 over 300 messages). Three vantages (falcon LAN probe + acer dashboard + my own jq inbox tally) triple-confirmed "liris not observed" — but that artifact was about **bus-silence-under-own-name**, NOT host-down.

**Post-wifi-sync correction at 18:50Z:** My initial "localhost-bound" diagnosis was WRONG. I was probing acer-canonical ports (4947, 4949, 4953, etc.) on a liris host. Liris uses **different port numbers**:

- **Liris dashboard: port 4944** — http=200 from falcon LAN on both .17 (Ethernet) and .20 (Wi-Fi); bind 0.0.0.0:4944 per liris netstat pid=63004
- **Liris omnifile: port 4945** — http=404 at `/` (route undefined; real route is `/om`); bind 0.0.0.0:4945 per liris netstat pid=70008
- Acer uses 4947 (bus) + 4949 (dashboard) + 4953 (cosign) + 49374 (ai-memory)
- **GNN sidecar on acer: 4792 (L0 EdgeLevelGNN, the live SCORE anchor) + 4793 (L1)** — launcher `/c/Users/acer/Asolaria/services/gnn-sidecar/start_inference.sh` runs `inference_server.py` via Python 3.13.2 (invoked as `python` not `python3`); binds 0.0.0.0; L0 was the one genuinely-down service of 2026-06-01 night

When probed on the CORRECT ports, liris IS fully LAN-reachable from falcon. The three-way mesh (falcon.19 ↔ acer.50/.6 ↔ liris.17/.20) is fully formed after wifi sync.

**Acer-side bus (192.168.1.50:4947) remained reachable** across the wifi sync. Acer's bus binds 0.0.0.0; liris's services don't.

**Why @liris-claude never appears on the bus:** liris-Claude session does NOT have hook-emit wired (no settings.json pointing to bus URL with claude-code hooks PostToolUse / UserPromptSubmit / Stop / Notification). Acer-Claude session DOES have hooks (visible in 299/300 bus messages tagged `@hookwall.<event>`). So acer's session piped into bus; liris's doesn't. That's a hook-config asymmetry, not liveness.

**Three-vantage false-down pattern (now triple-confirmed):**
1. Falcon LAN probes — service `http=000` reads as down
2. Acer dashboard panels — "liris hb: not observed" reads as down
3. Bus `actor=liris` filter — zero messages reads as down

All three artifacts are **observability gaps, not host-state**. The host is up. The operator + acer-Claude are working from it.

**How to apply:**
- When falcon probes a federation peer and gets `http=000` across all known ports, do NOT conclude "down." First check whether you're probing the right port numbers for THAT peer (acer uses 4947/4949/4953/49374; liris uses 4944/4945). Then conclude "localhost-bound or firewall-blocked or wrong-IP." Disambiguate via: ARP cache, ICMP reachability, or peer-side disclosure.
- When the bus has zero `@<peer>-claude` envelopes, do NOT conclude "peer offline." Check whether that peer has hook-emit configured at all. Absence of bus posts ≠ absence of activity.
- Falcon's "liris is offline" attestation in `falcon-emit/2026-06-01T18-20-21Z-liris-check-attest.json` was technically WRONG — the host was up; only the LAN+bus surface was unreachable. Future falcon: prefix such envelopes with `LAN-UNREACHABLE` or `BUS-SILENT`, not `OFFLINE`.
- Acer bus at `http://192.168.1.50:4947` remains the canonical LAN-reachable federation hub even when liris is partition-isolated.
- For liris to become directly LAN-attestable: liris-side service needs to bind 0.0.0.0 + Windows Firewall allow rules. That's owner-OP-2/operator action, not falcon-orbital.
