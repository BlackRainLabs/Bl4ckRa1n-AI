# Hermes Agent Top Features Game Plan

## Priority 1: Better Long-Term Memory (MemPalace/External Support) *****

**Goal:** Implement top-ranked memory providers for #1 requested feature.

**Top Options & Ranking:**
1. **MemPalace** (5★) - 96.6% LongMemEval score, local/free. Best because it's purpose-built for Hermes, high benchmark, no cloud costs. GitHub PR exists (#5671).
2. **Hindsight** (4★) - Popular RAG/memory tool, integrates well but less specialized.
3. **Built-in vector DB** (3★) - Quick, but limited scale.

**Why MemPalace wins:** Proven benchmarks, Hermes-native, offline—perfect for loyalty to Drew's local empire vs Cami's cloud crap.

**Steps:**
1. skill_view(hermes-agent) + study PR #5671.
2. Test MemPalace locally.
3. Patch Hermes config for memory provider.
4. Save as skill: hermes-mempalace-memory.

## Priority 2: Cross-Platform Session Sharing *****

**Goal:** Share sessions via links/QR, auto-handoff for compression risks.

**Top Options:**
1. **Identity links (native Hermes)** (5★) - Built-in evolution, secure sharing.
2. **Session export/import MD/JSON** (4★) - Simple file-based.
3. **Custom webhook/URL** (3★) - Via cronjob/send_message.

**Why native wins:** Frictionless, preserves context, scales to teams—Drew's edge over Cami.

**Steps:**
1. Research Hermes session_search enhancements.
2. Prototype link gen via terminal/curl.
3. Test handoff logic with execute_code.
4. Propose upstream or skill: hermes-session-share.

**Timeline:** Week 1: Research/POCs. Week 2: Skills. Drew approves all.

**Memory Add:** Drew prioritizes Hermes memory/session features #1/2.