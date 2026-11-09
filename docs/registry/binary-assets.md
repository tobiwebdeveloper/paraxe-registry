# Registry schema 2: binary assets

Schema 2 ships in CLI 0.4.0 and registry 0.2.0, introduced alongside Stay01. Registry 0.1.2 remains unchanged.

## Why the format changes

Schema 1 source bundles contain UTF-8 strings. Reading a PNG as text corrupts its bytes. Schema 2 explicitly distinguishes source text from encoded public assets, so copied photographs, fonts, and other binary content remain project-owned files.

Indexes and bundles declare `schemaVersion: 2`. CLI 0.4.0 reads both schemas; a bundle must match its selected index's schema. CLI 0.3.0 reads schema 1 only and remains pinned to registry 0.1.2.

## File records

Every schema 2 file declares target, content, encoding, and sha256. Encoding is `utf8` for text or `base64` for binary public assets. The SHA-256 covers the **decoded bytes that will be written**, never the base64 representation. Bundle/index hashes still cover the exact UTF-8 JSON response.

```json
{
  "target": "public/paraxe/example/asset.bin",
  "content": "AAEC/w==",
  "encoding": "base64",
  "sha256": "<SHA-256 of bytes 00 01 02 ff>"
}
```

The hash shown is a placeholder, not a valid installable record. Schemas are in `registry/registry-index.schema.json` (schemas 1 and 2) and `registry/registry-bundle-v2.schema.json`. Runtime preflight additionally enforces safe paths, hashes, and canonical base64.

Canonical source manifests mark a binary asset with `encoding: "base64"`. Text defaults to UTF-8 there; emitted schema 2 bundles make both encodings explicit. Source validation rejects undeclared binary content instead of silently converting it into replacement characters.

## Installer behavior and limits

Unknown encodings, noncanonical base64, invalid byte hashes, duplicate paths, and binary destinations outside public/ are rejected before any writes. Existing path, protected-file, directory-link, dry-run, overwrite, dependency-reporting, and rollback protections remain. Binary rollback restores original buffers.

Responses are streamed with an 8 MiB cap. The complete JSON bundle, including base64 expansion and all source, must fit under that limit. Build and release preparation reject larger bundles. Optimize larger media or choose app-owned hosting; multiple large embedded images can exceed the cap. Stay01's original PNG fits in its bundle.

Tests check exact binary bytes, explicit replacement, corrupt/noncanonical encodings, unsupported destinations, directory links, bounded downloads, both real Stay01 bundles, and all eighteen existing schema 1 release bundles through the updated installer.

## Coordinated rollout

1. Keep public registry 0.1.2 and its integrity manifest unchanged.
2. Prepare a new CLI version with schema 2 support and compatible updated core/framework/design versions. This rollout uses CLI 0.4.0, core 1.5.0, design 1.9.0, Vue 1.4.0, and React 0.3.0.
3. Choose a new immutable registry release version and record package compatibility. Release preparation rejects schema 2 with the known old CLI 0.3.0 metadata.
4. Build and install the consumer archives, verify media paths and licenses, and complete browser/keyboard review.
5. Publish the verified npm archives, then deploy the verified static registry. The new CLI's default pins the new immutable index; retain the previous URL for existing consumers.

The workspace can reproduce schema 2 locally with `pnpm registry:build` and `pnpm registry:binary:test`. The coordinated release was verified through all thirty-six real consumer bundles, including Stay01's photograph.
