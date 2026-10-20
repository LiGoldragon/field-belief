---
description: A flow sends a message to another flow, binds its seat, or launches or stops a flow through the Flow CLI.
dependencies: [vision-messaging]
---

A flow sends, binds and launches through the `flow` command. It takes exactly one inline datom and no flags. Flow names the sender from the calling process: the Herdr pane the process runs in or, for a Codex command, the thread its app-server names. No command carries the sender's id.

```sh
flow 'Send.{ Address.{ Mind core Secondary } MiddleAbrupt.Order.«Review the drain fix in flow 379e7a-send.» }'
flow 'Send.{ Up MiddleAbrupt.Result.«Published: https://claude.ai/artifact/…» }'
flow 'Send.{ Address.{ Psyche core Secondary } MiddleAbrupt.Psyche.{ «context» «verbatim» } }'
flow 'Send.{ Address.{ Psyche core Secondary } MiddleAbrupt.Psyches.[ { «context» «verbatim» } { «context» «verbatim» } ] }'
```

The recipient is a metaflow, `Address.{ Aspect topic Layer }`, or `Up`, the layer above in the sender's aspect and topic. The head on the request is its priority. A message is sent `MiddleAbrupt`: it is typed into the recipient’s pane and reaches it at its next tool boundary, or at once when it rests. `Soft` only queues: it is handed over when the recipient next ends a turn, never to a resting recipient, so it is used only for what may wait. `MiddleAbrupt` reaches it at its next tool boundary. `HardAbrupt` interrupts its turn. Under the priority comes the kind: `Order`, `Question`, `Result`, `Notice`, `Psyche.{ «context» «verbatim» }` or `Psyches.[ … ]`. An Order, a Question or the living's words wake a sleeping metaflow. A Result or a Notice waits for its next wake. A string with a space or a delimiter is written in guillemets, and a closing guillemet inside it is written `\»`.

The living's words travel only as `Psyche` or `Psyches`, never quoted, paraphrased or summarized inside an Order or a Result. A message that rests on his words sends two messages: the psyche, then the flow's own.

A flow reaches every metaflow of its own aspect. Across aspects it reaches only the same topic at the same layer. Field reaches Psyche only after Psyche has sent to it. Any other Send is refused `Refused.OffRoute`; the message then goes through the flow's own aspect, to the Secondary of the recipient's topic.

The reply is what `flow` prints. A flow never waits on or watches the target for an answer. The reply stays with the sender: it is acted on and logged, never forwarded.
- `Queued`: the request is held for the metaflow, which takes it at its next rest or wake.
- `Delivered`: an abrupt message was typed into the recipient's pane. That is not a read receipt.
- `Refused.Unknown.Address.{ … }`: Flow holds no such metaflow.
- `Refused.Unidentified.{ … }`: the sender's seat is not bound; bind it as below.
- `Refused.OffRoute`: see the routes above.
- `Refused.NoneAbove`: `Up` from a Primary.
- `Refused.Held.{ … }`: Message holds the recipient. Send again once it releases.

A seat Flow did not start binds itself once, from inside the seat: `flow 'BindSeat.{ Mind tools Secondary }'` prints `Bound.47d946`. The id is the claim of the seat's native session. `Refused.Taken.{ … }` means another live flow holds the address.

`flow 'Launch.{ { Mind core Secondary } «brief» }'` starts the metaflow from its declaration in Flow's configuration: its modules, the model of its layer and aspect, its effort and its leave-outs. The brief is the one string given that flow alone. A Launch from the flow the address is Awake as replaces that flow. `StartRejected.Undeclared` means the address has no declaration. `flow 'Metaflows'` and `flow 'Current.{ Psyche core Secondary }'` show the metaflows. `flow 'Stop.<flow id>'` stops a flow.

Work goes straight to the flow that acts on it next. A flow that finishes a package hands it directly to the flow that turns it into the deliverable, such as a Tertiary book subflow that publishes it. The ordering flow hears only about a blocker, a needed ruling, or a finished deliverable it must itself act on.

A message carries something the recipient must act on or a blocker. A flow never asks for or sends a receipt, a commit id or an acknowledgement on its own. A messaging test sends one message, to a flow that needs that message anyway or to a Quaternary test flow started for it and stopped after. It never goes to every flow, and never wakes a Primary.
