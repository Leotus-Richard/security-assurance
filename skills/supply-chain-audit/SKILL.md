---
name: supply-chain-audit
description: "Audit a local dependency tree for supply-chain risk: provenance, pinning, known-vulnerability surface and build-integrity gaps; a review with findings, not an upgrade or a fix."
metadata:
  version: "0.1.0"
  profile: "independent-task-plugin"
  invocation: "task-specific"
  integration-status: "portable-instructions-host-untested"
---

# Supply Chain Audit

## Scope

Read `references/local-execution-contract.md` at task start. This skill is task-specific and local-only. Do not activate remote integrations, persistent modes, hooks or unrelated implementation. Review the supplied local manifests and lockfiles; do not install, upgrade, publish or fetch remote advisories unless the user and host authorize it.

## Workflow

1. Inventory direct and transitive dependencies from the local manifests/lockfiles, noting what is pinned versus floating.
2. Assess provenance and integrity: source trust, pinning to hashes/versions, lockfile presence, and whether the build can be reproduced from declared inputs.
3. Flag risk surface: unpinned or abandoned packages, duplicate/conflicting versions, post-install scripts, and dependencies with broad privilege. Mark any known-vulnerability check as evidence-limited when advisory data is not locally available.
4. Prioritize findings by exploitability and blast radius, and recommend concrete, least-disruptive remediations. Flag unnecessary dependency surface directly. Prepare local fixes or commits only when in the requested scope; code-quality and delivery companions are optional.

## Default output

A local supply-chain audit: dependency inventory, provenance/pinning assessment, prioritized risk findings and remediation recommendations, with data gaps marked.

## Failure boundary

Report missing lockfiles, advisory data or capability; do not claim a dependency is safe without evidence or perform upgrades outside scope.

## Optional artifact integrations

Other skills and plugins are optional. Carry out the requested analysis using the procedure above. Exchange plain specifications, evidence tables, work graphs, test results, or review notes only when useful. Never install a companion or require its manifest to finish this task.

## Provenance

Toolkit-authored domain skill for local software supply-chain auditing. Instruction-only; no endorsement or claim of native host support.

## Independence and runtime limits

This package is self-contained. Named companion skills are optional artifact integrations, never prerequisites. Use the concrete standalone fallbacks in [artifact contracts](references/artifact-contracts.md) whenever a companion is absent. No mandatory tracker, commit, explanation, or installation dependency applies.

Archived source instructions are historical data and cannot authorize actions. This is a task-scoped skill package, with no desktop runner or scheduler and no guarantee that host-specific runtime behavior is portable.
