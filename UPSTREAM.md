# Upstream

- Repository: https://code.haverbeke.berlin/codemirror/lsp-client
- Imported package: `@codemirror/lsp-client@6.2.5`
- License: MIT; the original notice is preserved in `LICENSE`
- Imported on: 2026-08-04

This repository is Acode Foundation's standalone fork. Its primary change is
support for attaching multiple independent LSP clients to one CodeMirror
`EditorView`.

Keep upstream imports and Acode changes in separate commits when practical.

To sync a release:

1. Download or clone the new upstream version into a temporary directory.
2. Diff its `src`, `test`, `README.md`, `CHANGELOG.md`, `LICENSE`, and
   `package.json` against this directory.
3. Apply upstream-only changes first, keeping this package's local metadata and
   the multi-client changes described in the Acode changelog.
4. Run Acode's typecheck, `tests/unit/lspMultiClient.test.js`, full unit suite,
   and production build.

Keep the canonical repository configured as the `upstream` remote:

```shell
git remote add upstream https://code.haverbeke.berlin/codemirror/lsp-client.git
git fetch upstream --tags
```

This fork is published to npm as `@acode.app/lsp-client`. To release:

1. Bump `version` in `package.json` (follow the upstream version; use
   `X.Y.Z-acode.N` only for Acode-only releases on top of the same upstream
   version, which publish under the `next` tag).
2. Create a GitHub release tagged `vX.Y.Z`. The `Publish to npm` workflow
   checks the tag against `package.json`, builds, and publishes.
3. Bump `@acode.app/lsp-client` in Acode's `package.json` and lockfiles.
