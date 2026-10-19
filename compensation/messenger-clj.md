---
description: A flow runs an hm-* command, reads its output, or changes messenger-clj.
dependencies: [vision-messaging]
---

The `hm-*` shorthands are provided by the standalone messenger-clj repository under `Repository root`, on its default branch. Use `hm-send` for flow-to-flow messages, never a shell script, paste, or another intercom.

`FLOW_ID=<self> hm-send TARGET BODY` sends one complete machine body as `#msg [sender machine-prose]`. Use `--stdin` in place of `BODY` for a large or multiline body. `FLOW_ID=<self> hm-send TARGET --psyche CONTEXT VERBATIM` sends the living's words, context first, as one `#psyche [sender context whole-verbatim]`; `--psyche CONTEXT --stdin` reads the verbatim from standard input. `FLOW_ID=<self> hm-send TARGET --psyches --stdin` reads one EDN vector of `[context verbatim]` pairs and sends them as one `#psyches` envelope. Pass message fields, never a prebuilt envelope. `hm-send-abrupt` takes the same arguments and interrupts the target's active turn first. Flows refer to one another by the registered, space-separated meta-flow identifier, such as `Psyche core Secondary`. Quote it as one TARGET argument and use its registered topic case. Internal flow IDs are audit keys, not public command targets. The origin of every live `#msg`, `#psyche` and `#psyches` is the sender registration's aspect, topic and layer with spaces, never dots, a model, a guessed title or a truncated native UUID. Missing sender registration or any required metadata refuses the send; missing or ambiguous named TARGET refuses it.

The living's words travel only as psyche, never quoted, paraphrased or summarized inside a `#msg` body. A message that rests on his words sends two messages: the psyche, then the flow's own `#msg`. Write the recipient-facing body only.

Work goes straight to the flow that acts on it next. A flow that finishes a package hands it directly to the flow that turns it into the deliverable, such as a Tertiary book subflow that publishes it. The ordering flow hears only about a blocker, a needed ruling, or a finished deliverable it must itself act on.

Before sending, establish that the recipient holds the work and is live. A Codex delivery is relied on once hm-send prints Presented; nothing more is sought from the recipient.

The typed reply is what hm-send itself prints; a flow never waits on or watches the target for an answer. What hm-send prints stays with the sender: it is acted on and logged, never forwarded. `Transported` is Herdr's acceptance for the checked binding. `Presented` includes the observed reaction of the target. `Held` means nothing was typed and the whole body is pending until an explicit supported delivery action; its printed reason names the refusal. `RepairRequired` means the recorded candidates must be judged and the route repaired with `hm-repair`. `Uncertain` means the envelope may have arrived: inspect the target and never retry blindly. A refused or undelivered send is reported to the sending flow and its route is mended.

`hm-register TARGET AGENT_NAME [--session SESSION] [--native-thread UUID]` validates one exact live Herdr identity and stores its native binding; send readiness is checked separately. TARGET is the quoted registered `Aspect topic Layer` name; AGENT_NAME is the exact Herdr agent name, not a Flow ID. Metadata comes from TARGET. Optional `--aspect ASPECT --topic TOPIC --layer LAYER` flags must be supplied together and match it. A new registration requires the actual claimed runtime identity from the supported launcher; a native UUID or a guessed ID does not establish it. Historical ID-bearing envelopes remain audit evidence.

`FLOW_ID=<self> hm-retire TARGET` takes the registered, space-separated metaflow name as one quoted argument, for example `hm-retire "Psyche core Secondary"`. It validates the recorded route against the exact live Herdr identity and retains retirement evidence. Success prints `Retired.{ «Psyche core Secondary» }`; a refusal prints `RetireRefused.{ «Psyche core Secondary» Reason }` and changes nothing. Registry retirement does not stop or sleep the native flow.

Flow lifecycle controls are separate from messenger retirement. The current Flow contracts expose `Stop.FlowId` and privileged `Retire.FlowId`; they provide no public-name sleep operation. Until a supported public-name control route is supplied, report that missing contract rather than constructing `Sleep.Address` or substituting `hm-retire`.

A message carries something the recipient must act on or a blocker; a flow never asks for, or sends, a receipt, a commit id or an acknowledgement on its own.
