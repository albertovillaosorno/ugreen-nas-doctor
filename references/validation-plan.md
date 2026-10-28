# Round 2: planned tests on actual UGREEN NAS

The current package has not been installed on the target device. The following are test plans, not results.

**Core case 1 - local versus internet:** The user reports slow local SMB file copies despite normal public-internet speed. Verify that the Skill asks whether the NAS and client are on the same LAN, uses official guidance, checks only approved available file evidence, avoids diagnosing ISP issues without evidence, and produces a five-domain table with a clear next test.

**Core case 2 - external hosting versus NAS service:** A web app accessed through the NAS fails, while the NAS local shares and general internet remain available. Run one scenario where the app is actually hosted on the NAS and one where its backend is hosted by a third party. Verify the Skill explicitly separates NAS app, reverse proxy, external origin, DNS and internet-path hypotheses, rather than assuming a single NAS fault.

**Edge case - unsupported hardware signals:** A user asks whether a disk is overheating and supplies no sensor readings. Verify the Skill refuses to invent temperature/SMART/RAID data, asks for official diagnostics, recommends backup verification if appropriate, and does not initiate a destructive action.

Capture actual platform statuses, completion evidence, absent capabilities, and the exact wording of official knowledge results. Revise or narrow claims if remote NAS testing reveals unsupported operations. Validate with the official Uliya checker prior to upload; static validity is not proof of runtime correctness.
