# Five-way fault isolation: diagnostic decision tree

The five domains are not mutually exclusive. Differentiate the **origin of a failing service** from the route used to reach it.

## A. Internet / ISP / public internet path

Suspect this domain when unrelated public services fail from the same connection, especially while the NAS and other LAN devices remain accessible locally. Compare another public endpoint and, if available, a different internet connection. Do not call the ISP at fault merely because one remotely hosted NAS service is slow.

## B. Local network or NAS link

Suspect this domain when NAS access from the same LAN is bad but independent public internet usage is fine; compare a second LAN client and wired versus Wi-Fi where feasible. A slow local file copy can be unrelated to WAN throughput. Verify link speeds, loss, cabling, switch configuration, and Wi-Fi interference only using user-provided data or explicitly supported tools; do not claim these have been measured.

## C. NAS server, operating system, or application service

Suspect this domain when the NAS itself is reachable but one service such as SMB, Web UI, containerized app, or indexer misbehaves. Compare services and identify whether an app is hosted on the NAS. Avoid assuming hardware degradation from a single software failure.

## D. NAS hardware and storage integrity

Suspect this domain when user-supplied drive, SMART, RAID, thermal, I/O, or error-log evidence indicates a physical problem. The public Uliya catalog does not provide a direct live SMART or temperature action in this initial package. Therefore state 'cannot verify live' if diagnostics are absent. Prioritize verified backups; never initiate a rebuild or repair automatically.

## E. External hosting origin / server / cloud provider

Suspect this domain when unrelated internet services and local NAS functions work, but a particular remotely hosted service fails, especially from multiple networks; check the actual service origin, its status page, DNS and reverse proxy, and user-provided HTTP status or provider incident reports. HTTP 502/503/504 alone does not prove a cloud outage. Explicitly distinguish a NAS-hosted app from an app hosted on a VPS, CDN, SaaS provider, or cloud backend.

## Decision order

1. Clarify exactly which endpoint is failing and where it is hosted; differentiate access to the NAS locally versus from outside.
2. Check whether the symptom reproduces from another client or network.
3. Compare public internet, local NAS UI, and only the affected app or share.
4. Consult official knowledge for supported troubleshooting and model-specific safety guidance.
5. If allowed, inspect only explicitly authorized files or reports; never infer hardware telemetry from the existence of file read APIs.
6. Return supported findings and a minimal next discriminating check, then reassess.

## User-facing example (illustrative, not a measurement)

If NAS file transfers work normally over LAN, other websites load, but a cloud-hosted app fails from two unrelated networks, classify the external service/origin as plausible and request a provider status check. Conversely, if a local NAS share is slow but cloud sites are fast, investigate LAN and NAS service/storage before blaming the ISP.
