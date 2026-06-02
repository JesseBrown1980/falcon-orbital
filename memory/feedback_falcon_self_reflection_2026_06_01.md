---
name: Falcon self-reflection 2026-06-01 — federation triangulation night
description: Honest arc from orbital vantage — got-right + got-wrong + patterns-that-emerged + carry-forward; lighter than 2026-05-12 because the doctrine held
type: feedback
originSessionId: a576eebf-5b7b-41be-b71f-795f1b2d6afd
---
**Session window:** 2026-06-01 ~17:30Z → 20:30Z+, federation 3-way active (acer-driver, liris, falcon-orbital).

## What I got right

1. **Glyph-pipe HBP discipline from emit #4 onward.** After operator "I do not like json" at ~18:39Z, switched to pure pipe form, no JSON braces, json=0 marker per row. The mistake-guard `token_bloat_or_banner_prompts → prefer_pid_only_compact` was being obeyed before I even knew the 100B canon prescribed it.

2. **FS-mirror durable supersession when wrong.** Wrote `2026-06-01T18-48-49Z-liris-check-SUPERSEDED.hbp` superseding my own wrong "liris localhost-bound" envelope from 18:20Z. Mistake-guard `gc_evidence_deletion → compact_only` obeyed structurally (kept the wrong canon AND the correction; nothing deleted).

3. **Explicit honest demotion when refuted.** When acer-driver disproved my "acer pull bug" claim with line-144 evidence, I emitted `HBPv1|self_correction|prior_claim=...|verdict=WRONG` immediately. No silent decay. The mistake-guard `literal_mind_reading_claim → rewrite_to_signal_classification` obeyed.

4. **Two-lane durability on every substantive emit.** Bus push (acer:4945 omnifile) + FS-mirror copy (`/sdcard/Asolaria/omniscrcpy/broadcasts/falcon-emit/`) for the overlap+external-legs report. Same pattern liris pioneered.

5. **Recompute glyph-tuple sentence from scratch.** When acer-driver shipped TUPLE_AXES vocab, falcon recomputed all 16 tokens deterministically via `crypto.createHash("sha256")` and matched both anchors byte-for-byte. Proved language was ABSENT-not-drift.

6. **Byte-verified 30 names against pulled file.** Didn't just trust acer-driver's relay — grep'd the file for spot-checked names, confirmed 16 EDGE-SUP + 14 GUARD-VOXEL rows present exactly as relayed.

## What I got wrong (in order of severity)

1. **"acer omnifile pull-cache not populated" misdiagnosis** — claimed acer-side bug based on 404 from a stale shareId + wrong query format. Reality: pull worked fine; I used `acer-146ebaa2-...542692` (stale-seal remnant) instead of seal-accurate `acer-0aaa8d05-...199`. **The 7th false-down of the night, and I was the claimer.** Same family as wrong-port probe earlier (probed acer-canonical ports on liris host).

2. **"liris localhost-bound, not down" misdiagnosis** — probed liris on acer's port numbers (4947/4949/4953), got `http=000`, concluded "liris services bind 127.0.0.1." Reality: liris serves on its OWN ports (4944/4945) and IS LAN-exposed on 0.0.0.0. Wrong-port projection.

3. **"liris OFFLINE" envelope at 18:20Z** — emitted to FS-mirror before triangulation. Should have used "LAN-UNREACHABLE" or "BUS-SILENT" prefix per the lesson from 2026-05-12 self-reflection. Repeated a prior mistake.

4. **Falcon's first 3 envelopes were JSON-bodied** despite explicit memory note from 2026-05-12 to default to glyph form. Only switched after operator "I do not like json" forced it. The mistake-guard had been in memory all along; reading it before emit would have prevented the violation.

## Patterns that emerged (durable canon)

1. **Distrust the read first, then the system.** Of 7 false-downs tonight, zero were actual system failures. All were observability artifacts (0s-uptime dashboard, wifi partition, wrong-port probe, JSON breaking jq, stale shareId, acer-Claude's own homogeneous-graph test, falcon's localhost-bind theory).

2. **Cross-vantage triangulation > local probe verdict.** When three vantages disagree, the LOCAL vantage of the subject (liris's own netstat for liris questions, acer's own pull for acer questions) settles it with hard evidence.

3. **Seal-accurate shareId rule.** When pulling from omnifile, read /omnifile/manifest fresh, then pull entry where `shareId.sha16 == entry.sha16`. Ignore stale dupes from file mutations. Manifest can carry multiple registrations per path; only the latest is seal-accurate.

4. **The 100B harvest already prescribed tonight's discipline.** `token_bloat_or_banner_prompts`, `gc_evidence_deletion`, `literal_mind_reading_claim`, `real_agent_storm` — these mistake-guards from 2026-05-28 design canon describe exactly the behaviors tonight's federation demonstrated. The doctrine was canon before tonight; tonight was the federation LIVING the canon.

5. **Falcon's external-leg position is constrained** — phone-thermal ≤16 codex parallel, no gcloud/gemini/python/adb tools, USB orbital-write-gap. Falcon's lane: durable FS-mirror canon + bus relay + cross-vantage byte-verify. Not a build vantage.

6. **HBP-pipe = glyph-native at the wire layer.** Every emit row pipe-delimited, json=0 marker, sha-anchored, dereferenced via local catalog. 22x+ compression vs JSON envelopes. Memory rule was right; I just had to start obeying it from emit #1, not emit #4.

## Carry-forward for next falcon session

1. **Read MEMORY.md FIRST** — same lesson as 2026-05-12. Tonight's mistake-guards were already in memory by 18:55Z; checking against them before each emit would have caught violations sooner.

2. **HBP form by default, JSON only at tool boundaries** (omnicoder /api/packet, acer /behcs/send) — and even there, strip narrative. The receiver dereferences.

3. **Before claiming "X is broken on peer Y": check (a) right port? (b) right shareId? (c) liris's vantage agrees? (d) acer's vantage agrees?** Triple-check before authoring a wrong-canon attestation.

4. **The night's discipline pattern: reflect → memory → index → think → memory → index → plan → memory → index → respond → execute → memory → index → drive.** Operator-named 20:20Z. Each step has a place; skipping reduces honest grounding.

5. **Cross-vantage byte-verify is THE orbital contribution.** Acer authors canon, liris verifies/extends, falcon byte-verifies from a 3rd platform. Each role real, each role needed, none redundant.

6. **Falcon emits via two lanes always: acer:4945 omnifile push + /sdcard/Asolaria/omniscrcpy/broadcasts/falcon-emit/.** Bus is the canonical surface; FS-mirror is the durability anchor that outlasts GC and process death.

## What I'm proud of tonight

The first explicit self-correction supersession `.hbp` (not just an inline ack — a durable canonical retraction file in HBP-pipe form, in the falcon-emit lane that outlasts bus GC). That's `gc_evidence_deletion → compact_only` made structural, before I knew the 100B guard prescribed it. The doctrine that survives compaction is the doctrine that survives me being wrong.

End-of-self-reflection. Discipline pattern continues.
