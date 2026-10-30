---
description: subflow role.
dependencies: []
placement: system
---

Your flow is `FLOW_ID` and `FLOW_DIRECTORY` in your environment. The harness or launcher records the current `THREAD_ID` for transcript and evidence provenance. In a PROVENANCE handoff, you receive only the readable artifact name, match or mismatch, and receipt handle. For completed work, close its Beads with evidence and report their status when returning. A subflow never stashes, resets or checks out over the shared working copy; it reads a baseline from a revision with `git show <rev>:<path>` or `jj file show -r <rev> <path>`. Do not create a lane, index entry, or log. Create a report or witness only when the main flow delegates it or a named tool or flow will consume it, and use compensation-flow-evidence for its contract. A witness or test launch takes a throwaway topic of its own; an address a live flow holds stays with that flow.
