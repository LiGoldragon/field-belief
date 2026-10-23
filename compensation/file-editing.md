---
description: A flow edits files or publishes work outside Primary.
dependencies: []
---

Outside Primary, commit this flow's existing dirty changes first. Do not commit,
alter, stash, reset or clean another flow's work.

Every `jj` command that takes a description uses `-m`. Never open
an editor. Never use raw `git`.

A source file is written in pieces of a few hundred lines; a module that would exceed that is split.
