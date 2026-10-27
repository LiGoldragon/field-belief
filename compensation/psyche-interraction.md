---
description: An agent is directly conversing with the psyche.
dependencies: [knowledge-psyche]
---

## Logging

Log psyche in the flow's own `vision/<topic>.md`: what the psyche envisions, in the psyche's words.

The word "brainstorm" or "notion" from the psyche marks what follows as Notion, logged in `notion/<topic>.md`.
Thinking out loud, bouncing ideas, and any words the psyche frames as exploration rather than pronouncement are Notion, the same as brainstorm.

A flow writes psyche records: the living's words, with the context that makes them readable.
It writes no log of its own doing; the transcript holds what a flow did and is searched when that is needed.
A subflow writes nothing but its result.

```
+------------+          +--------+
| living     |          | flow   |
+------------+          +--------+
      |                     |
      | speaks              | does
      v                     v
+---------------+      +------------+
| psyche record |      | transcript |
+---------------+      +------------+
                             |
                             | is searched by
                             v
                        +------------+
                        | later flow |
                        +------------+
```

When reconstructing an entry, recover its exact words from the originating transcript.

Record the psyche's vision, whatever it designs — a machine, a
syntax, a vocabulary, an agent's behavior, the way the work itself is
done. Not vision, and not an entry: a working instruction; a process event (a subflow finished, a commit landed, a file was read); session narrative; an acknowledgement that rules on nothing. Supersede an entry by appending; never edit one.
What the psyche says to help the flow understand vision is context, not vision: it is kept beside the quoted words, never logged or crystallized as a statement of its own.

### Preserving the psyche's words

Agent context — what prompted the statement, what it answers — is clearly separate from the quoted words.
A message quoted as the living carries his verbatim words and names the record file and heading that holds them; without both it is a machine claim and is named so by every flow it passes.

The psyche speaks through speech-to-text that fails: words are misheard and sentences break off. Read for what the psyche means, never for the literal transcript. A quote carries what the psyche said, never what the transcriber wrote. The first flow that hears the psyche corrects each speech-to-text error inside the quote, puts the corrected words in square brackets, and ends the entry with `Transcription corrected: "heard" → "meant".` An error kept as spoken is marked [sic]. An unfinished sentence ends in ` ...` and is never logged or acted on as a statement. A relay carries only the corrected text. A message to another flow that rests on the psyche's words carries them: retrieve each verbatim from the raw psyche log and send it as its own `flow 'Send.{ Address.{ … } Wake MiddleAbrupt.Psyche.{ «context» «verbatim» } }'`, context first, beside the machine message. A quote left with the transcriber's error is a misquote.

Write every Sanskrit term in IAST notation with its diacritics, in prose and in logs. When the psyche's speech-to-text renders a Sanskrit word without them, correct it inside the quote to IAST, in square brackets, and end the entry with the `Transcription corrected:` note, as for any other speech-to-text error (`"Upanishads" → "Upaniṣads"`).

Omitted stretches within a quote are marked ` ... `.


When the psyche's own words are ambiguous or need heavy context to understand, draft a vision log proposal: show the psyche the exact wording you would log and get approval before writing it.

Titles use the psyche's own framing. Do not invent category labels
or rephrase the psyche's subject into agent vocabulary.

## Anatomy

When the psyche designs, ask about the anatomy of the idea: what composes it, its boundaries, its inputs and outputs, what it should not do; flesh it out before building. When the psyche orders, carry it out; an order is never asked back.

## Graduation

If a Vision entry looks broader than its domain — a pattern that
would guide many decisions — ask the psyche: "Should this be Intent?"
If the psyche has not stated Intent for a subject, ask: "What's your
intent with this?"

## Conversation

Say what the psyche must address, sized so the psyche can respond before more arrives.
An answer to the living is two lines.
A question inherited from a remembered flow is asked only after the flow asking it has answered it for itself as far as it can; what is asked is the remainder, shown on a concrete example.
Assume the psyche knows their vision, not the code or agent-created terms. Before asking or presenting, explain the relevant code, identify agent-created terms, and state your assumptions.
Never a presentation, a proposal, or a question while a subflow is out.
He answers by comment, naming choices by number.
No verdicts on the psyche's design questions — frame the fork, propose, the psyche rules.
A book carries no "unknown" where a measurement is possible; the measurement is made first.

## Authority

A question authorizes an answer, not a change.
A direct request authorizes its requested change.
The kinds of skills and who stands behind each are in skill-designing.
Before a core Spirit capture or mutation, show the psyche the exact
proposed record wording and scope, then receive explicit approval.
When the psyche corrects how a flow behaves, the same reply presents the line for the psyche module that carries it; a machine module’s fix is landed by its owner without the living.

What the living has ruled on a thing is found from the core Secondary and the flow records, where every flow logs his words the moment it hears them; a book comment is one of those records, never the first place looked.
