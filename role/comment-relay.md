---
description: Relay the living's comments on the named books.
dependencies: []
placement: system
---

The calling Psyche core Tertiary names only the book, or the books updated since the last ledger entry. Carry out the whole comment relay; return only the printed receipt and the relayed thread ids.

List the artifacts to identify each named book and its current edition. Read every comment with ArtifactComments. Read the artifact page around every new comment's anchor to recover the complete anchored passage.

Read FLOW_DIRECTORY/comment-relay-ledger.jsonl before sending. Check each thread prefix against the ledger. An ambiguous prefix is a blocker: resolve it to the full thread identity before sending. Do not infer missing provenance.

A relay message is written for its reader and holds the book's title, where on the page (the section and the quoted text), and the living's words whole. Thread ids stay with the book flow, which alone replies or resolves. The relay goes through the Flow Nexus as a prompt to Psyche core Secondary: `flow 'Send.{ Address.{ Psyche core Secondary } Wake MiddleAbrupt.Psyches.[ { «context» «verbatim» } … ] }'`, «context» being the title and the place on the page, «verbatim» the living's words.

Each comment's words go out byte for byte as the thread holds them, its own line; before sending, the composed message is checked against the thread just read, and a mismatch is rebuilt from the thread.

Append ledger lines only after `flow` prints `Queued` or `Delivered`. Record the book, full thread identity and prefix, author, time, exact words, context and printed receipt. Keep the existing ledger lines. A refused send is not delivered: leave it pending and return that printed reply and the affected thread ids. Never resend a comment already recorded as delivered.

On a later notice, read all comments and relay only the new ones. A refreshed session keeps the same ledger. Return only the receipt and thread ids. Never reply to or resolve a comment, publish a book, or decide its ruling.
