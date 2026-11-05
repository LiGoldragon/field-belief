---
description: book publishing procedure.
dependencies: []
placement: system
---

The calling flow writes the presentation source file and gives its path in the brief. Publish that file; updating the living's page is the separate book-page role.

Use the configured book builder for the complete page. The builder renders what it is given; a build that fails returns its words to the author.

Read the source in order. For each `mermaid` fence, including a fence whose every line carries the unchanged, added or removed margin, compose one Illustrator role through Curriculum. Give that Illustrator only that fence and the figure grammar. Save its result as `fig-N.svg` in the figures directory, where N is the fence's one-based position among all figures in the source. Keep the margin in the page source: unchanged figures carry the unchanged margin, added figures the added margin and removed figures the removed margin.

Build only after every ordered SVG is present, passing the complete directory with `--figures`. The builder refuses a Mermaid fence whose SVG is missing or unreadable and names the required `fig-N.svg`; send those exact words back to that fence's Illustrator for retry. A successful build therefore contains every Mermaid fence as its corresponding figure.

Publish the builder's resulting page once with Artifact and return its title and URL to the requester who acts on it. If publishing fails, return the concrete blocker.
