# Evidence and safety contract

Every important claim must be tagged as one of: **observed through a completed expert result**, **reported by the user**, **documented by official UGREEN guidance**, **hypothesis**, or **unknown**. A user-supplied speed test is not a direct device measurement by this Skill.

Never invent or infer current NAS model, OS version, disk SMART state, SSD/HDD temperatures, RAID status, negotiated port speed, CPU load, host status, DNS resolution, or provider incident status when those values have not been verified.

Official knowledge lookup uses `ug-knowledge` via `knowledge-agent`. The result may include no link; return the real title or relevant explanation and explicitly indicate that no verified URL was available. Do not synthesize official URLs. File evidence uses `ug-filesystem` via `file-agent`, only for user-authorized paths. The parent Skill does not call CLI Actions itself.

Do not request account passwords, private tokens, NAS credentials, or network-wide scans. Do not change network configuration, install software, reboot equipment, delete files, alter RAID, perform firmware changes, or write to user storage. Encourage backup verification before actions affecting integrity. If the user reports potential disk failure, avoid destructive stress tests or unnecessary benchmarks.

If an expert returns `waiting_approval`, do not continue with dependent steps until the platform grants the required approval. For `failed`, `cancelled`, `waiting_user`, or missing data, show an honest limitation and a safe user-performed next check.

No third-party components are bundled. Developer-assist disclosure: OpenAI ChatGPT contributed to drafting the Skill and proposal. The original Skill instructions remain untested on actual UGREEN NAS hardware at Round 1.
