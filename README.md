# Operit Ry Development Updates

This repository hosts development APKs and differential update assets for the
`personal/dev` branch of [CATMIAOZHI/Operit](https://github.com/CATMIAOZHI/Operit).

The `Personal Dev Update` workflow checks `personal/dev` every five minutes and
skips the build when the source commit is already published. It publishes a full
APK for a new update series, then publishes `apkraw-1` differential updates while
keeping the full APK as a fallback.

Development APKs use the package name `com.rainy.operitry.dev`. They must retain
the existing Operit Ry signing certificate with SHA-256 fingerprint:

```text
40:F8:7A:4D:66:EB:70:D0:E2:D1:37:9C:6A:97:DD:DC:0C:ED:D3:BA:87:2E:02:74:50:CA:77:AF:42:EC:5E:74
```

The following repository Actions secrets must contain the same signing values as
the `CATMIAOZHI/Operit` repository:

- `OPERIT_RELEASE_KEYSTORE_BASE64`
- `OPERIT_RELEASE_STORE_PASSWORD`
- `OPERIT_RELEASE_KEY_ALIAS`
- `OPERIT_RELEASE_KEY_PASSWORD`

The workflow uses this repository's scoped `GITHUB_TOKEN` to create releases; no
cross-repository release token is required.

Because the Android build executes code from `personal/dev` while signing, write
access to that branch must remain limited to trusted maintainers. Protect the
branch before granting write access to additional collaborators.
