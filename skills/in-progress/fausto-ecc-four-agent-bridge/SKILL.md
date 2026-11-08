---
name: fausto-ecc-four-agent-bridge
description: Stage and verify a shared ECC-inspired capability registry for four existing MCP agents, preserving original services and requiring separate authorization for device writes.
disable-model-invocation: true
---

# FAUSTO ECC four-agent bridge

Status: experimental specification in a draft PR. The separately authorized local Suite integration and common MCP entries have been installed and backend-tested; this repository is not a running cloud coordinator.

## Scope

Keep four existing agents independent. Route only explicitly authorized work to a named agent, with a read-only default. Share versioned schemas, allowed skills, source links, and audit evidence using a private Google Drive registry. Store no credentials, tokens, user data, or executable secrets in this repository.

Do not claim Drive is an active compute service. Do not move a live SQLite database into Drive. Do not assume that ChatGPT projects or chats automatically synchronize with the registry.

## Source and attribution

ECC upstream: https://github.com/affaan-m/ECC, MIT license. Review pinned commit d2ef2680594f9a17526a6e1a2e18b3d242c5d17b and retain upstream copyright notices for copied source. This staging skill adopts workflow patterns rather than installing or copying ECC executables.

Relevant ECC skills:
- agent-architecture-audit for layer-by-layer assessment
- agent-security-hardening for trust boundaries and explicit action approval
- agent-runtime-gateway-smoke-test for isolated recovery-ready probes
- content-hash-cache-pattern for idempotent content and evidence checks

## Invocation policy

This is user-invoked only. Never execute Windows commands, change Cloudflare routes, grant new permissions, restart services, stop agents, or publish data merely because this skill was read.

## Protocol

1. Identify the target agent, device, role, and current state with current read-only probes.
2. Consult MEMORIA_IA as historical context, verify source evidence and classify unresolved matters explicitly.
3. Check a private registry manifest version and pinned ECC source revision.
4. Validate task envelope: request_id, exact target, capability allowlist, read_only=true, parameters and payload hash. Reject unknown fields.
5. The isolated queue worker allows only health.read, contract.verify and ecc.skills.inspect on a test agent. The separately authorized Suite diagnostic workflow uses a fixed allowlist of real read tools across four existing clients and one explicit provisional-memory write; these two allowlists are not interchangeable.
6. Validate the request before constructing any path, including the replay path. Reject links/reparse points at queue boundaries, duplicate JSON keys and oversized envelopes. Apply per-request exclusive locks and atomic no-overwrite publication. Preserve bytes and modification time for an identical replay; reject a reused request_id with different content. A stale lock is recovery-required, never success. Verify stored response metadata before accepting a replay.
7. To invoke any production tool, require that tool's existing authentication and per-action approval. Never promote the staging allowlist into unrestricted execution.
8. Verify a new output by reading back and checking source, status, expected contents, and provenance. Mark missing access BLOCKED.
9. Compare memory usage at a consistent workload before and after any subsequent migration. Do not infer memory savings from moving text/configuration into Drive.
10. Do not pause or replace original MCPs unless an independent health, operation, rollback and full tool-parity test succeeds and the user approves the exact change.

## Acceptance gates

- Four distinct agents in manifest; every original service remains unchanged.
- ECC source revision pinned with valid SHA, no installation of unreviewed upstream scripts.
- Test accepts three allowed read-only messages and rejects shell.execute.
- Replayed messages yield duplicate_preserved without modifying original responses.
- Private Drive JSON manifests are valid and separately retained.
- Separate acceptance is required for live network exchange, remote PC main participation, memory reduction, process persistence and actual operation through each agent.
- A command or HTTP response from a proxy never substitutes for demonstrated end-to-end work on the target Windows host.

## Rollback and limits

All tests live in a dedicated staging folder on a single authorized PC and a new private Drive subtree. Neither service restart nor process termination is part of staging. Remove the staging only after dependency review. If remote device or connector is unreachable, report that limitation rather than using an untrusted alternate route.

## Current status

A candidate extends the existing Suite State and authenticated workflow API to four MCP clients. It preserves all 111 original catalog entries and adds five restricted entries. The hub remains separate from ECC; no second coordinating daemon or scheduler was introduced.

A real autonomous API cycle completed nine tool jobs across all four services. Inventories contained 61, 54, 3 and 5 tools respectively. The memory record was read back and an identical note deduplicated. Replaying the request in a new process returned duplicate_preserved with zero new calls and identical response SHA-256. The API rejected missing session authentication, incorrect Origin and invalid request IDs. Ten existing bridge regression tests passed. Device evidence includes the remote laptop hostname, local execution hostname and OS fingerprints; OS fingerprints alone are not unique host attestation.

The separate isolated worker revision passed eight regression tests locally and on PC_PRIORITY, including concurrent publication. All nine backed-up production source files remain hash-identical. Candidate source, exact backups, patch, release manifest and evidence are retained privately; this repository contains the specification and pinned source lock only.

This is a bounded diagnostic workflow with a provisional memory write, not unrestricted agent delegation or a permanent autonomous schedule. The user approved production promotion and a Suite-only restart. The five-file extension is now installed in the existing Suite after verified backups. Cloudflare sessions can expire. Complete tool parity, reboot persistence, stronger remote host attestation and controlled RAM/CPU savings remain unverified. The legacy FAUSTO router read still fails ValueError/invalid_request; this work extends the separately accessible existing Suite. Keep this PR as a draft.

## Deployment verification — 2026-11-08

The first promotion exposed a Windows/OneDrive read-only attribute on the workflow's owned empty lock directory. Automatic rollback restored the original files and healthy Suite. A restricted cleanup fix clears only that directory's DOS read-only attribute, rejects redirecting/nonempty locks and never changes ACLs or deletes recursively. Four targeted tests and ten bridge regressions passed; a further live cycle passed in OneDrive.

The corrected extension was promoted with a fresh backup. A final UTF-8 note-text correction was backed up and verified separately. The installed Suite completed a fresh nine-job four-MCP diagnostic cycle, verified the provisional memory note and returned the same result hash on a fresh-process replay with zero new calls. All 111 original catalog entries remain within the 116-entry catalog. Credentials, routes and existing agents were not replaced; no permanent schedule was enabled.

Final response SHA-256: b6761cd1469c415dab13fd271fc76ee79616423c2d79bf1e0578f73c2d719919. Before/after resource samples were RAM86.8%/CPU11.0% and RAM88.8%/CPU14.9%, under uncontrolled workload; no resource savings are established. This draft still tracks the skill specification and source lock, not private deployed source or credentials. Full parity and reboot/session persistence remain unverified.


## Common entry deployment — 2026-11-08

The four backend MCP services expose `coordinar_tarea(request_id)` and `consultar_coordinacion(request_id)`. They delegate to the existing authenticated Suite workflow API. Remote entries use the existing local DEV relay; the PC entry uses the existing loopback Suite session. No new coordinating daemon, public route, bearer export or permanent schedule was introduced.

The entry is bounded to the joint diagnostic and provisional memory record. Mentioning a plugin alone does not trigger execution. The assistant selects the tool when the user explicitly asks for that workflow; arbitrary task execution remains out of scope. A current client tool catalog is required.

Backend inventories are 63 FAUSTO, 56 PC_PRIORITY, 5 Jaseris HTTP and 7 MEMORIA_IA tools. Every previous Suite catalog tool remains present; all 54 original PC tool definitions were compared exactly. Installed entry calls from all four backends shared one request ID, completed nine workflow calls, verified memory readback and deduplication, and returned identical results when replayed through every entry. Result SHA-256: c6383395e4998e54cd17b944c0b0cbc1629e4c6f14ab9ebdb0d2a4215f36ab9c.

The test exposed an existing classifier bug: an approval phrase quoted inside historical memory data was treated as a current approval gate. The authorized correction examines direct tool messages while retaining explicit approval statuses, error states and plain-text notices. Eight targeted cases passed. The release manifest was updated with separate authorization after its integrity check correctly rejected the changed source hash.

Exact backups exist for the connector files, classifier and release manifest. Three remote HTTP services were restarted; the existing Suite was restarted separately with authorization. Managed STDIO clients were not terminated. The current chat still advertises its previous tool catalog; refresh/reconnection and the remote managed STDIO chat session remain to be verified. Do not equate backend success with refreshed client availability.

Remote CPU samples were 12% before and 9% after; free RAM was 2538156 and 2494072 KiB. These uncontrolled restart samples establish no resource savings. Full historical-tool execution parity, controlled PC resource comparison, reboot persistence and Cloudflare-session persistence remain unverified. Keep this PR as a draft; private source snapshots, backups and operational evidence stay outside the public repository.
