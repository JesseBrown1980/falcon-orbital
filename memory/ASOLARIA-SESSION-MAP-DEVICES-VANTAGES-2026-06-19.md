# ASOLARIA Session Map — Devices · Vantages · 3rd-Vantage Triangulation (2026-06-19)

*Authored from the **falcon-orbital** seat — the federation's 3rd-vantage independent audit. This repo's whole job is cross-vantage byte-verify: pull a canonical artifact, recompute sha + glyph + PID independently, emit an HBP attestation. So this map is the **device/vantage triangulation canon** — who the devices are, how the four vantages see each other, and where the meeting room is.*

## Honest frame (read first)
IT is **slices**, not an ASI — an 8-byte addressing/routing geometry over borrowed + frozen intelligence slices. The doctrine of this seat is the federation rule proven on the 2026-06-01 triangulation night: **every "down" was a measurement artifact; 0 actual dead systems**. "Make possibility cheap and action gated." LIVE = only an `E≠0` fire; **this session E=0** — nothing fired, swapped, retired, or cranked. Every line below is tagged MEASURED / CANON / OPERATOR / UNVERIFIED.

## Resolved device roster (CANON — names role-anchored per repo privacy doctrine)
| Vantage | Device | Model | Serial | Role |
|---|---|---|---|---|
| **Falcon** | Samsung S24 FE | SM-S721U1 | R5CXA4MGQXV | **GENESIS device** — phone-home 2026-02-22; acer-pinned over MTP/ADB-USB |
| **Aether** | Samsung A06 (OP-Felipe's) | SM-A065M | R9QY205KAKJ | reached via Liris (sister-handoff envelope), not direct |
| **Beast** | Galaxy S22 Ultra | SM-S908E | RQCT302BXMA | roster member |
| **Xiaomi** | Mi 10 Lite 5G `monet` | (VID/PID 2717:ff40) | 56C90D22 | liris xiaomi-recover lane, Codex-built |

- **Genesis finding (OPERATOR + CANON):** Falcon S24FE is the device the system first phoned home from — **2026-02-22**, the genesis stratum (Android DEX + hooks). The fabric `archaeology_timeline` opens there (27 strata: genesis → 3 incidents/3 rebuilds/2 treasons → Shannon roundtrip → 10B-runner → FABRIC EPOCH → genome). CANON.
- Falcon screen MEASURED live this session: 1080×2340, `adb` device line `R5CXA4MGQXV … model:SM_S721U1 device:r12s transport_id:62`, USB-powered, battery ~77–88%.

## The four-vantage visual bus — omni-control + omniscrcpy (MEASURED live this session)
**omni-control** (`:4949/api/omni-control`) = the LOOK-TYPE-ENTER-LOOK bridge. Skill `S03-omni-control`. Bridge contract: `LOOK=screencap, TYPE=input text, ENTER=keyevent 66`. Primary PID pinned to **Falcon**:
`OMNICTRL-PID-AF-FALCON-S24FE-R5CXA4MGQXV-LOOK-TYPE-ENTER-LOOK-2026-05-09-N00001`; reserved seats for Liris-desktop (`-AL-…-PTSQTIE`) and Aether-A06 (`-AE-…-R9QY205KAKJ`). Guardrails (MEASURED): local-only dashboard route · Falcon USB serial pinned · no restricted-content dump · no auto-dispatch.

**omniscrcpy** = the PIXEL surface, `OMNISCRCPY-PID-CROSS-COLONY-2026-05-09`, halted=false. **Four lanes** (MEASURED, generated 2026-06-19T17:00Z):
1. `acer-falcon` — Acer → Falcon S24FE, `local-adb-usb`, status `active-if-adb-device` (Acer front-end + Codex backend).
2. `liris-aether` — Liris → Aether A06, `sister-handoff-envelope`, `active-when-liris-confirms`.
3. `acer-liris` — Acer → Liris desktop, `sister-desktop-frame-envelope`, `active-when-liris-confirms`.
4. `acer-frontend` — Acer primary desktop, `visible-browser-loop`, `active-when-tab-open`.

Cadence: bus-poll 30s, visual-check 60s, backend-daemon **false** (operator-visible tab, not a daemon). Loop = look-desktop → look-Falcon → read-bus → think → type-only-on-explicit-kick → look-again → emit-receipt. Feed contract: low-bandwidth JPEG preview; full PNG only on explicit sample; **registered devices only**; remote/off-LAN must publish signed bus envelopes (no unauthenticated internet control). Required screens: acer-desktop, falcon-s24fe, aether-a06-via-liris, liris-desktop-via-bus.

## Colonies, meeting room, relay path
- **Colonies (CANON):** Falcon · Acer · Liris (three vantages = the triangulation; Aether reached *through* Liris, not as a 4th colony).
- **room-40 = the inter-colony meeting room**, anchor `MK-00040-P179`. Falcon holds it on-device at `/sdcard/Asolaria/room-40_directory_…` (MEASURED via omni-control paths). It is the operator-visible collaboration lane — distinct from the bus.
- **Relay path (MEASURED 2026-06-01, repo memory):** Falcon (LAN 192.168.1.7) reaches Acer bus directly at `http://192.168.1.50:4947/behcs` (GET `/inbox`, POST `/send`, returns `ok:true` even UNSIGNED warn-mode). Cosign proxy `:4953` is localhost-bound on Acer → not LAN-reachable from Falcon. Orbital attestation does **not** require the cosign proxy. Two-lane durability = omnifile push + FS-mirror `falcon-emit/`.

## 3rd-vantage discipline (this repo's reason to exist — CANON)
Cross-vantage byte-verify, role-anchored privacy (OP-1…OP-5). The 2026-06-01 night logged **9 honest demotions across 3 vantages, 0 dead systems** (0s-uptime = restart-not-death; "offline" = wrong-port probe; "localhost-bound" = wrong port-set; JSON-breaking-jq = format-on-wire mismatch). The matching external check this session: DeepSeek/Mistral/Gemini/GPT-5.5-Pro/Claude-Opus-connectors independently reproduced the public results **and converged on the same honest frame and the same documented limits** (MEASURED, external). Dual-lens: don't over-deflate (a measurement artifact ≠ a dead device) and don't over-inflate (a reserved PID seat ≠ a live fire).

## Host8 registrations relevant to this domain (CANON — sealed this session, council held-safe, E=0)
This repo carries the *device/vantage* slice; the seat registrations that touch it landed on `JesseBrown1980/Asolaria` under `host8-serve/intake/` (hbp-no-json, 8-byte handles):
- **daemons** — commit `15848d6`: 92 daemon programs + 11 seats; 14 LIVE-MEASURED incl. bus `:4947` (the relay this seat POSTs to) and dashboard `:4949` (which serves omni-control/omniscrcpy); port→room binding (port N indexes pre-MINTED room MK-0NNNN). 74 DARK / 4 legacy.
- **model-citizen prism** — commit `ee073f4`: 16 borrowed-intelligence citizens + 2 seats; firing gated `MODEL_CITIZEN_ROTATOR_LIVE=1` + census-ready (UNVERIFIED-live this session).
- **census v1.2** — commit `d7aa0e3` (apex ladder 00 SPECIAL-OP-JESSE / 01–05 OPs / APEX-HUMAN-JESSE; 10B human-PID ledger = capacity, not live).

## UNVERIFIED / held this session
- All four omniscrcpy lanes report status strings, not confirmed live frames — `acer-frontend` is `active-when-tab-open`, the sister lanes `active-when-liris-confirms`; **no first frame fired this session** (E=0).
- Aether/Liris-desktop = `operator_authorized_waiting_first_frame_devices` (MEASURED) — authorized, awaiting `OMNISCRCPY_REMOTE_FRAME` preview.data_url from the owner device.
- Beast (S22U) and Xiaomi (`monet`) are roster-resolved (CANON) but had **no live lane** in this session's bus reads (UNVERIFIED-live).

---
*Master index: see the reductions repo (`what-is-asolaria---how-do-we-get-reductions-in-everything`) → **ASOLARIA-MAP-OF-MAPS-2026-06-19.md**.*