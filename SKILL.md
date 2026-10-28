---
name: nas-guardian
description: Five-way NAS troubleshooting and verified next steps when a user asks why their NAS, internet, local link, storage or externally hosted app is slow, down, or unreachable.
---

# Goal

Help an owner determine which layer is most likely responsible for a slow, unavailable, or unreliable UGREEN NAS workflow, without confusing internet connectivity, the local link to the NAS, NAS software, NAS hardware, or a separate hosted server/service. Produce a five-domain evidence table, safe next checks, uncertainty, and relevant official guidance. Prefer a useful diagnosis over a generic documentation summary.

Read [diagnostic decision tree](references/diagnostic-decision-tree.md), [evidence and safety contract](references/evidence-and-safety.md), and [finalist validation plan](references/validation-plan.md) before diagnosing.

# Required input

Ask what is failing (file transfers, NAS web UI, local share, remote access, or an application hosted on the NAS or elsewhere); whether the user is accessing it on the same LAN or remotely; the symptom; and, only if necessary, the intended endpoint and approximate onset. Accept optional user-supplied ping, traceroute, local-vs-remote results, speed measurements, router information, SMART diagnostics, NAS system information, screenshots, or logs. Never require secrets or collect credentials. Ask no more than one discriminating question at a time when evidence is missing. Do not assume the user owns a specific NAS model.

# Generation-time capability evidence

- `ug-knowledge` → `knowledge-agent`
- `ug-filesystem` → `file-agent`

Both CLI families and their single registered expert mappings are listed in the official public Uliya capability catalog. Available read actions relevant to this Skill include official knowledge lookup and, for user-authorized file paths only, file listing, metadata, and checksums. No public capability is assumed for direct SMART, CPU, temperature, internet-speed, network-port, model-identification, or remote-cloud telemetry. Absence of access must be reported clearly.

# Workflow

1. Establish the exact scenario: local NAS shares versus NAS remote access versus an independent external hosting origin. Record the five candidate fault domains. Use [diagnostic decision tree](references/diagnostic-decision-tree.md) to select a safe, discriminating comparison; do not guess from the phrase 'NAS is slow'.
2. Request model- or symptom-relevant official guidance from the registered knowledge expert: `delegate --target knowledge-agent --instruction 'Using ug-knowledge official knowledge lookup, find relevant UGREEN/UGOS guidance for the user-reported NAS symptom and confirmed model/version, if known. Return actual documentation titles/URLs only when present in tool results; give caveats when not available. Do not invent URLs, capabilities or a model identity. Read-only.'` The expert, not this Skill, chooses and invokes its registered CLI Actions.
3. If the user supplies an authorized folder or file path and the diagnosis requires file evidence, request: `delegate --target file-agent --instruction 'For the exact user-authorized NAS file or folder path and reported problem, use only registered read-only ug-filesystem capabilities (such as ls, stat, or checksum) that are necessary and permitted. Report exact results or lack of access. Do not enumerate outside the scope, delete, move, edit, benchmark, or claim SMART/CPU/network hardware readings.'` Skip this delegation if there is no such path or consent.
4. If the user offers a diagnostic report stored on the NAS and the supported knowledge capabilities can access it, ask: `delegate --target knowledge-agent --instruction 'For the exact user-authorized report path, use supported read-only evidence collection to summarize observations relevant to connectivity, services, or hardware. Attribute findings to the report and distinguish them from live measurements; do not modify or save data.'` Skip if a report or usable path is unavailable.
5. Synthesize a five-domain differential: (A) internet/ISP/public path, (B) local network/NAS link, (C) NAS OS/application/service, (D) physical NAS hardware/storage, (E) external hosting/origin/cloud provider. Identify evidence **for**, evidence **against**, and **unknowns** for each; assign 'supported', 'plausible', 'unlikely', or 'undetermined', not invented confidence percentages. Treat multiple simultaneous faults as possible.
6. Recommend one safe comparison at a time: local-vs-remote access, another device on LAN, alternate site, link negotiation or transfer test supplied by user, service-specific status, or a hardware report supplied by user. Mark instructions requiring admin tools or physical access as user-performed and conditional. Provide official links only when returned by an expert. Do not present hypothetical sample outputs as observed results.
7. Present result: affected function, five-domain matrix, most likely explanation **if evidence supports one**, discriminating next test, safety cautions, and official source references. Explicitly indicate if only a theoretical or user-supplied diagnosis is possible.

# Completion and failure

- `completed`: use returned facts only, citing tool output or user-provided evidence; distinguish measurements from educated hypotheses.
- `failed`: show that the requested check did not complete and suggest a non-destructive user-performed alternative.
- `cancelled`: stop this branch; do not mark it successful.
- `waiting_user`: request the single missing input or result needed to continue.
- `waiting_approval`: stop dependent work pending actual platform approval; never imply approval was granted.
- For empty or partial expert results, preserve verified partial facts, label the rest unknown, and stop steps dependent on missing evidence. Never invent sensor readings, benchmark results, official links, source availability, cloud outages, or safe-to-repair claims.
- No destructive NAS actions, network changes, firmware updates, RAID rebuilds, credential access, or configuration changes are authorized by this Skill. Hardware warnings must prioritize verified backups and official service procedures.

# Third-party components and development disclosure

This Skill consists of original Markdown orchestration instructions and references written for the 2026 UGREEN AI NAS Hackathon. It embeds no third-party libraries or code. It uses only Uliya's published expert and CLI interfaces as runtime dependencies, subject to that platform's availability and permissions. OpenAI ChatGPT was used to help draft and review the proposal, Skill text, and workflow; no coding agent or external service has been demonstrated as executing this Skill on NAS hardware. Any links to vendor documentation must come from real lookup results, not hard-coded invented references.

If an expert returns no results or an empty result, report that plainly and stop its dependent branch without silently searching unrelated data or expanding scope.
