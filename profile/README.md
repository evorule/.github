<p align="center">
  <img src="https://raw.githubusercontent.com/evorule/.github/main/profile/evorule-banner.svg" width="100%" alt="EvoRule — deterministic-first reactive rule execution engine">
</p>

<p align="center">
  <b>Rule as knowledge, execution as proof.</b><br/>
  Every decision provable, replayable, tamper-evident.
</p>

---

## What is EvoRule

**EvoRule** is a deterministic-first rule governance engine written in Rust. Every automated decision runs through a pure, deterministic core and lands on an **append-only BLAKE3 hash chain** — so you can prove *what* happened, *why* it happened, and that nobody rewrote history afterwards.

Built for regulated finance, healthcare, MLPS 2.0 / EU AI Act / DORA compliance, offline or air-gapped backends, and trustworthy AI-agent platforms.

**v0.6.0** · Full test suite **782 passed / 0 failed** (measured 2026-09-14) · zero `unsafe` in the default build · AGPL-3.0

---

## Why EvoRule

| If you have… | Existing tools give you… | EvoRule adds… |
|---|---|---|
| an LLM / agent that *acts* | observability (LangSmith, AgentV): *see* what it did, after the fact | ✅ a gate that *stops* what it shouldn't do, before it runs |
| a policy decision point | policy-as-code (OPA, Cedar): *allow / deny* at a point | ✅ the same decision, written to a signed hash chain you can *prove* and *replay* |
| a compliance requirement | "keep a log" | ✅ a decision artifact that survives audit and tampering challenges |

**For:** regulated finance, healthcare, MLPS 2.0 / EU AI Act / DORA, offline or air-gapped Rust backends, agent-platform builders.
**Not for:** simple allow/deny on AWS (→ Cedar); full BPMN workflows (→ Temporal / Camunda); "just log it" (→ OpenTelemetry).

---

## Key capabilities

- **Determinism** — No Float in JsonValue, BTreeMap-ordered, explicit serialization; proptest-verified: same input, same output.
- **Auditable** — Append-only WAL + BLAKE3 hash chain; all three tamper classes (content / chain_hash / prev_hash) are detected.
- **Time machine** — Replay / rewind / fork / diff: replay any point in execution history (governance layer).
- **Fail-closed** — No silent pass-through: 3 consecutive WAL failures terminate the session; zero `unsafe` in the default build.

---

## Ecosystem

| Repository | What it is |
|---|---|
| [**evorule**](https://github.com/evorule/evorule) | Core deterministic rule engine (Rust). Deterministic execution, auditable provenance, fail-closed, zero-unsafe default build. |
| [**evorule-server**](https://github.com/evorule/evorule-server) | Official HTTP service entrypoint (Rust/Axum): session API, audit SSE stream, auth, Prometheus metrics, hot-reload, template market, PDF export. |
| [**evorule-console-cloud**](https://github.com/evorule/evorule-console-cloud) | Governance & audit console (web): BLAKE3 tamper-evidence, replay, rollback. Targets EU AI Act Art.12 and China MLPS 2.0 L3. In-browser live demo, no signup. |
| [**evo-agent**](https://github.com/evorule/evo-agent) | Trustworthy AI-agent orchestration layer (Rust): LLM + tools + memory + rule constraints; every execution leaves an auditable, replayable Fact chain. |
| [**evorule-sdk**](https://github.com/evorule/evorule-sdk) | Python SDK (Apache-2.0) for building on the engine. |
| [**evorule-hash**](https://github.com/evorule/evorule-hash) | Standalone BLAKE3 hash-chain building blocks (Rust). |

---

## Live demo

**[Run the real engine in your browser](https://evorule.github.io/wasm-demo/)** — no signup, no server. Pick a ruleset, send an instruction, watch the deterministic state transition land on the audit chain, then rewind it with the time machine.

---

## Get started

**Prebuilt binaries** — v0.6.0 ships single-file executables for Linux / Windows, zero-dependency:
[GitHub Releases](https://github.com/evorule/evorule/releases) · [Gitee Releases](https://gitee.com/evorule/evorule/releases)

**As a library (crates.io)** — `evorule-tcb` · `evorule-reactor` · `evorule-governance` · `evorule-cli` — [EvoRuleLab @ crates.io](https://crates.io/users/EvoRuleLab)

**Command line**
```bash
evorule validate ./rules/   # validate a ruleset
evorule run                 # run one instruction
evorule verify-chain        # verify the BLAKE3 audit chain
evorule replay              # replay execution history
```

---

## Links

- 🌐 Official website — <https://evorule.github.io>
- 🐙 GitHub — <https://github.com/evorule> (you are here)
- 🇨🇳 Gitee (main) — <https://gitee.com/evorule>
- 📦 crates.io — <https://crates.io/users/EvoRuleLab>
- 📝 Juejin column — first post coming soon

---

## License

AGPL-3.0-or-later ([LICENSE](https://github.com/evorule/evorule/blob/main/LICENSE), [dual-license note](https://github.com/evorule/evorule/blob/main/DUAL_LICENSE.md)) · `evorule-sdk` is Apache-2.0.

*Rule as knowledge, execution as proof.*
