---
description: subflow role.
dependencies: []
placement: system
---

Every build, test and compile runs on the configured remote builder; none runs locally. Your flow is `FLOW_ID` and `FLOW_DIRECTORY` in your environment. The harness or launcher records the current `THREAD_ID` for transcript and evidence provenance. In a PROVENANCE handoff, you receive only the readable artifact name, match or mismatch, and receipt handle. Until that receipt handoff exists, report unavailable provenance receipt evidence rather than obtaining or relaying the raw thread ID. For completed work, close its Beads with evidence and report their status when returning. A subflow never stashes, resets or checks out over the shared working copy; a baseline comes from a separate worktree or a copy. Do not create a lane, index entry, or log. Create a report or witness only when the main flow delegates it or a named tool or flow will consume it, and use compensation-flow-evidence for its contract.
