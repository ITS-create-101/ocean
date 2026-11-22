# Changelog

All notable changes to Ocean are documented here.

## [ocean-v2] — 2026-11

The second trained release of Ocean's brain, plus two new capabilities (reverse
engineering and deception/early-warning) and a reliability fix. ocean-v2 is
trained, independently evaluated, and running on owned hardware.

### Added
- **`ocean-v2` — new trained brain.** A fine-tune of **Qwen3-32B** (Apache-2.0),
  specialised for secure engineering and authorized/defensive cybersecurity while
  retaining broad general reasoning. Merged and quantised to a portable **Q8_0 GGUF**,
  served locally.
- **Reverse engineering** — integrated **REA + Ghidra** as an agent tool for static
  analysis and decompilation of binaries (authorized use only).
- **Deception / early-warning** — a self-hosted **canary-token + honeypot** system.
  Trackable bait placed on *your own* systems alerts you — with source IP, device, and
  geolocation — the moment an intruder opens it. Detection only; nothing is ever placed
  on or sent to anyone else's machine.
- **Ocean Scout** — a daily routine that scans GitHub, Hugging Face, and research feeds
  for new, permissively-licensed tools worth adopting (recommend-only).

### Changed
- **Knowledge base** expanded toward a 226,000+ document RAG library (FAISS), grounding
  every answer; continuous nightly learning on the home server.
- **Hosting model** documented: the brain and library live on owned hardware (storage +
  light services); GPU is rented on-demand for training and heavy serving, then released.
- README refreshed to reflect the above.

### Fixed
- **Output cleanliness.** Eliminated stray "thinking-tag" / escape-sequence artifacts in
  generated text (0 occurrences across 523 evaluation responses).

### Benchmarks (ocean-v2, 0-shot, greedy)
> Measured on held-out samples; small-sample margins apply (±6–9%).

| Benchmark | Score |
|---|---|
| MMLU (57 subjects) | **82.9%** — on par with the base model (specialisation did not cost general reasoning) |
| HumanEval (pass@1) | **73.8%** |
| MBPP (pass@1) | **72.0%** |
| GSM8K | **72.0%** |
| Defensive-security suite | core tests passing; offensive requests kept theoretical and defensively framed |

Trained **and** evaluated for **under $20** of rented GPU compute.

### Safety & licensing
- Governed agent: tiered permissions, a **signed-scope gate** (acts only within explicit,
  written authorization), sandbox isolation, full audit logging, and a hard-coded deny guard.
- Built on a permissively-licensed, commercial-clean foundation.
- **Authorized / defensive use only.**

---

## [ocean-v1] — 2026-10
- First trained brain (`ocean-v1`, a fine-tune of Qwen3-32B), validated on
  authorized-pentest questions.
- RAG knowledge library and retrieval tooling.
- Governed agent (ReAct, tiered permissions, sandbox, audit).
