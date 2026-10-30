---
description: A Nexus is started, deployed, or its next iteration is tested.
dependencies: [knowledge-datom, vision-ethos, compensation-testing]
---

Every Nexus has three slots: testing, next and stable. Each slot holds its own store.

Testing is the raw binary just built, run directly. Its store sits at its canonical testing path and may be deleted at will.

Next is a deployed service with its own canonical store path, where the next iteration runs.

Stable is the deployed service in production use.

The current Flow runs in stable. Its next iteration is built in testing and targets next.

## Stable

Stable is the systemd user unit declared in `The user environment`, `modules/home/profiles/min/<nexus>.nix`. `%t` is the user runtime directory, `%h` the home directory.

| Nexus | Unit | Sockets | Store |
|---|---|---|---|
| Flow | `flow-nexus.service` | `%t/flow/flow.sock`, `%t/flow/flow-meta.sock` | `%h/.local/state/<stateDirectory>/flow.sema`, `<stateDirectory>` being `criomosHome.flow.stateDirectory` |
| Message | `message-nexus.service` | `%t/message/message.sock`, `%t/message/message-owner.sock` | `%h/.local/state/message/message.sema` |
| Orchestrate | `orchestrate-nexus.service` | `%t/orchestrate-nexus/orchestrate.sock`, `%t/orchestrate-nexus/orchestrate-meta.sock` | `$XDG_STATE_HOME/orchestrate-nexus/orchestrate-nexus.sema`, else `%h/.local/state/orchestrate-nexus/orchestrate-nexus.sema` |
| Curriculum | `curriculum-nexus.service` | `%t/curriculum/curriculum.sock` | its context checkouts, `%h/.local/state/curriculum-context` |

Flow requires Curriculum; Message starts, stops and restarts with Flow.

An activation that changes the tools every flow calls, flow and herdr among them, is witnessed before and after from a fresh login shell by flow Metaflows and the herdr pane list, and is rolled back at once on a difference.

```sh
systemctl --user restart flow-nexus.service
systemctl --user restart orchestrate-nexus.service
```

The stable Flow unit runs:

```sh
flow-nexus "{ %t/flow/flow.sock %t/flow/flow-meta.sock %h/.local/state/<stateDirectory>/flow.sema None }"
```

## Where each Nexus reads its paths

Flow reads its sockets and store from its one argument, the Start datom. Its landing watch is `None` or `Some.{ <context-repository> <deploy-executable> }`.

Message reads `HOME` and `XDG_RUNTIME_DIR`. Orchestrate reads `XDG_STATE_HOME`, else `HOME`, and `XDG_RUNTIME_DIR`, and refuses any argument. Curriculum reads `XDG_RUNTIME_DIR`. Each of the three starts with no argument.

## Testing

In the long term, each Nexus declares its canonical testing store path.

Testing runs the just-built package's executable. Flow, in the form its usage line gives:

```sh
flow-nexus '{ «ordinary-socket» «meta-socket» «store-path» None }'
```

A Nexus that reads its anchors starts on testing anchors. This form is inferred from the anchors it reads, unwitnessed as a testing command:

```sh
HOME=<testing-home> XDG_RUNTIME_DIR=<testing-runtime> message-nexus
```

## Next

In the long term, next is `<unit>-next.service` beside stable. `lib/stable-next-service.nix` in `The user environment` lays out its anchors, with clients named `<name>-next…`:

```sh
HOME=%h/.local/state/<name>-next
XDG_RUNTIME_DIR=%t/<name>-next
```

Its sockets sit at `%t/<name>-next/<name>/`. Flow's next store goes in its next Start datom.

## Types

Flow's Start, in `flow-ethos/ethos/library.ethos`:

```
OrdinarySocketPath.String
MetaSocketPath.String
StorePath.String
ContextRepository.String
DeployBinary.String
LandingWatch.{ ContextRepository DeployBinary }
Start.{ OrdinarySocketPath MetaSocketPath StorePath Option<LandingWatch> }
```

The slot, proposed:

```
Library
[]                                      ; imports
[ Slot.[ Testing                        ; types: the three slots
         Next
         Stable ] ]
[ Deployable.[ deployed.[ Boolean ]     ; traits: runs as a deployed service
               disposable.[ Boolean ] ] ] ;   its store may be deleted at will
[ Slot.[ Deployable ] ]                 ; associations: every slot bears it
```

A slot, as a datom:

```
Testing
Next
Stable
```
