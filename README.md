# UGREEN NAS Doctor

**An evidence-first troubleshooting Skill for UGREEN AI NAS.**

UGREEN NAS Doctor helps users distinguish five different sources of NAS-related performance and availability problems:

1. Internet connection, ISP, or public network route
2. Local network, Wi-Fi, switch, or link to the NAS
3. NAS operating system and application services
4. Physical NAS hardware and storage integrity
5. External hosting origin, cloud provider, or remote service

Rather than blaming the NAS for every slow app, the Skill identifies which domain a symptom supports, where evidence is missing, and the safest next check. It can request model-appropriate official guidance through the registered Uliya knowledge expert and inspect user-authorized file paths through the registered filesystem expert.

## Project status

This repository contains the **Round 1 pre-test Skill and proposal** for the [UGREEN Hackathon 2026 on AI NAS](https://ugreenhackathon.devpost.com/).

- The `SKILL.md` and references passed the bundled Uliya static checker (0 errors, 0 warnings).
- **Not yet executed or verified on a UGREEN NAS.** Round 1 does not provide participants hardware access.
- The public Uliya capability catalog does not currently document direct SMART, NAS temperature, network throughput, CPU usage or external cloud-status readings. These inputs can be user-reported or remain unknown until supported capabilities are provided.
- The project offers diagnosis and safe guidance, not autonomous repairs.

## Files

| Path | Purpose |
| --- | --- |
| [`SKILL.md`](SKILL.md) | Main Uliya Skill entry point and expert orchestration |
| [`references/diagnostic-decision-tree.md`](references/diagnostic-decision-tree.md) | Five-domain diagnostic methodology |
| [`references/evidence-and-safety.md`](references/evidence-and-safety.md) | Evidence provenance, approvals, data safety |
| [`references/validation-plan.md`](references/validation-plan.md) | Tests planned for the finalist NAS session |
| [`docs/Round1-Proposal.pdf`](docs/Round1-Proposal.pdf) | Original 10-question Round 1 proposal |

## Submission packaging

The competition's Skill ZIP contains **only** `SKILL.md` and `references/*.md`; `README.md`, `LICENSE`, and this PDF are not part of the Skill ZIP. Submit the proposal PDF separately in Devpost.

## Tech stack and dependencies

Original Markdown instructions; Uliya registered `knowledge-agent` (`ug-knowledge`) and `file-agent` (`ug-filesystem`). No executable scripts, external libraries, or credentials are included in the Skill. Third-party documentation is queried at runtime through official supported capabilities, not scraped or embedded.

## Development disclosure

Created for the 2026 UGREEN AI NAS Hackathon. OpenAI ChatGPT assisted with drafting and technical review of the original Markdown workflow and proposal. NAS runtime compatibility has not yet been demonstrated.

## License

MIT; see [LICENSE](LICENSE). UGREEN/UGOS/Uliya names refer to the provider's interfaces and remain their respective owners' trademarks.
