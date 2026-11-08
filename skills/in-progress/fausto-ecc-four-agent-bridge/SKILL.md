---
name: fausto-ecc-four-agent-bridge
description: Stage and verify a shared ECC-inspired capability registry for four existing MCP agents, preserving original services and requiring separate authorization for device writes.
disable-model-invocation: true
---

# FAUSTO ECC four-agent bridge

Status: experimental skill, not installed or promoted. This is a specification and test harness, not a running cloud coordinator.

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

This is a bounded diagnostic workflow with a provisional memory write, not unrestricted agent delegation or a permanent autonomous schedule. Production promotion and a Suite-only restart require the user's explicit approval and backup verification. Cloudflare sessions can expire. Complete tool parity, reboot persistence, stronger remote host attestation and controlled RAM/CPU savings remain unverified. The legacy FAUSTO router read still fails ValueError/invalid_request; this work extends the separately accessible existing Suite. Keep this PR as a draft.
