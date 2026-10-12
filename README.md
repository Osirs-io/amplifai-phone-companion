# AMPLIFai Phone — Intel Mac support

This branch adds an **x86_64 Mac build based on Jeff's published RC23 source**. It targets Intel Macs running macOS 14 or later. It preserves the current collection fixes and all 102 Python dependency versions while building the missing Intel encryption dependency from verified source.

- [Build and release handoff for Jeff](docs/INTEL-MAC-HANDOFF.md)
- [Verification results and remaining device checks](docs/INTEL-VERIFICATION.md)
- [Native Intel build workflow](.github/workflows/macos-intel.yml)
- [Exact RC23 source provenance](docs/rc23-source-baseline.json)

The workflow produces a separate ad-hoc signed Intel candidate, matching source inputs, checksums and test receipts. Developer ID signing, notarization, a normal downloaded installation and a real Intel Mac/iPhone/account test are separate release requirements. Read the verification record for the observed results; this branch does not claim a finished customer release.

## For Jeff

Build this branch directly, or apply the focused changes after imported RC23 baseline commit `81ecfb5` to the matching published source layout. The baseline came from the verified RC23 source ZIP because the upstream `main` branch was older. If the current collector has advanced, reconcile the changes individually rather than replacing newer collector code.

The changes do not deploy a website, modify accounts, publish to the canonical updater, or change the existing Apple-silicon installer. Intel update checks remain disabled until an appropriate signed Intel feed is qualified. The website must also expose the Intel installer and permit the Intel setup/pairing path; the handoff names those integration points.

## Source and licensing

The project-authored companion is Copyright (C) 2026 OSIRS LLC and licensed under **GPL-3.0-or-later**. See [COPYRIGHT](COPYRIGHT), [LICENSE](LICENSE), and [THIRD-PARTY-NOTICES.txt](THIRD-PARTY-NOTICES.txt). The separate private website/backend source is not included.

`source/` contains the RC23 Swift/Python companion, tests, locked dependencies, logos and build scripts, plus the Intel changes. The repository retains the independently versioned Android source.

The large, unchanged third-party source package is in [Jeff's RC23 release](https://github.com/JmooreOsirs/amplifai-phone-companion/releases/tag/macos-2026.10.12-rc23-release), identified by URL and SHA-256 in the provenance receipt. Successful Intel candidate releases attach the additional exact Intel Python, OpenSSL and cryptography/Rust source inputs and notices alongside the corresponding authored source. No byte-for-byte reproducible-build claim is made.
