---
description: The change lands in Nix.
dependencies: [vision-nix-builds]
---

Model services declaratively with typed options.
Pin portable inputs in the lock file.
Build and deploy reproducible source.
Keep `flake.nix` readable as an index.
Keep substantial check and build implementations and long shell programs out of `flake.nix`.
Ask Nix or source.
Any part of an environment already owned by Nix, CriomOS, or CriomOS-home is fixed, updated, and maintained through that owning declarative source.
Keep local overrides transient.
Run Nix evaluations and builds independently.
Test with binaries and scripts packaged by Nix.
A Rust runtime has its own Rust-only repository, holding only what compiling its executable or library needs; mutable data and content live in separate data inputs or repositories, so Rust compilation stays cached across data changes. A Rust executable repository holds Rust alone; everything else changes in its own repository.
Treat managed output as evidence; change it at its source.
Keep evaluation and activation evidence separate.
A check of the Prometheus builder goes through the nix daemon as the build user; a direct ssh probe costs a penalty that drops live builds.
