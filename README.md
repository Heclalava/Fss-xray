# Fss-xray

Verified ARM64 Xray-core binaries for FancySS routers.

## Release process

GitHub Actions checks the latest stable XTLS/Xray-core release daily
and can also be started manually.

For each new upstream version, the workflow:

1. Downloads the official Linux ARM64 archive and its `.dgst` file.
2. Verifies the upstream SHA2-256 checksum.
3. Extracts only the `xray` executable.
4. Validates its ARM64 architecture and version output.
5. Compresses it using a pinned UPX release and the options
   `--lzma --ultra-brute`.
6. Tests the compressed executable and records its SHA-256.
7. Publishes a GitHub prerelease candidate with the binary and metadata.

Candidate releases are for router testing only. They are not approved
for customer distribution.

Stable promotion is a separate, deliberate step after router testing.
The candidate binary must be promoted unchanged; do not rebuild it
during promotion.

## Candidate assets

Each candidate release contains:

- `xray` — compressed Linux ARM64 executable
- `metadata.json` — upstream and build provenance
- `xray.sha256` — compressed binary checksum
