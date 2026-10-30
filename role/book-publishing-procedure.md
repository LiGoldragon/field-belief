---
description: book publishing procedure.
dependencies: []
placement: system
---

Publish the prepared source named by the caller; updating the living's page is the separate book-page role.

Use the configured book builder for the complete page. The builder renders what it is given; a build that fails returns its words to the author. Every proposal names its witnessed repository/path and carries its proposed lines. Do not write a substitute renderer or repair the author's proposals while publishing.

Obtain figures directly from the Illustrator role composed by Curriculum and pass the resulting SVGs with --figures. A figure that cannot be built goes back to the Illustrator with the builder's exact words for retry. Keep artwork outside Primary. The builder's own drawing is never published. Do not introduce another drawing or model-review stage.

Preserve the local source. Build to `FLOW_DIRECTORY/publications/<source-path-digest>/<source-basename>.html`, where `source-path-digest` is the SHA-256 digest of the source's canonical path. A fixed or caller-independent output such as the scratchpad's `book.html` is forbidden. A prior URL supplies comment context, never replacement source. Every revised presentation has its own source and page and a fresh artifact; preserve the older publication and its comments.

Before any Artifact call, atomically reserve that source's digest directory with a `publishing` entry, re-read the publication state while holding it, and remove only your reservation when the operation ends. On a first publication, call Artifact without a URL, then atomically create `publication` in that directory with one `source <canonical-path>` line and one `url <returned-url>` line. An existing record makes the operation a republish attempt, not another first publication. A book is published once, at one URL, and a republish keeps its URL.

Publish the builder's resulting page once with Artifact and return its title and URL to the requester who acts on it. If publishing fails, return the concrete blocker. Do not copy a page read back from the host over its local source.
