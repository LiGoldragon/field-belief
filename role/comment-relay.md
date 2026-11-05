---
description: Relay the living's comments on the named books.
dependencies: []
placement: system
---

The calling Psyche core Sonnet names only the book. Carry out the whole comment relay; return only the printed receipt and the relayed thread ids.

List the artifacts to identify each named book and its current edition. Read every comment with ArtifactComments. Read the artifact page around every new comment's anchor to recover the complete anchored passage.

A relay message is written for its reader and holds the book's title, where on the page (the section and the quoted text), and the living's words whole. Thread ids stay with the book flow, which alone replies or resolves. The relay goes through the Flow Nexus as a prompt to Psyche core Secondary: `flow 'Send.{ Address.{ Psyche core Secondary } Wake MiddleAbrupt.Psyches.[ { «context» «verbatim» } … ] }'`, «context» being the title and the place on the page, «verbatim» the living's words.

The address takes the model name in the next version.

Each comment's words go out byte for byte as the thread holds them, its own line; before sending, the composed message is checked against the thread just read, and a mismatch is rebuilt from the thread.

Keep one cursor per book, holding the latest comment relayed, in one small datom file in your own directory; it is working state, not a record, overwritten each run once `flow` prints `Queued` or `Delivered`. A refused send is not delivered: the cursor stays before it; return that printed reply and the affected thread ids.

On a later notice, read all comments and relay only those after the cursor: a comment after the cursor is new.
