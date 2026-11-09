# Registry schema 2: binary assets

The owner approved binary asset support alongside Stay01. Schema 2 is implemented in development. It does not rewrite the public registry 0.1.2 or publish new npm packages.

## Why the format changes

Schema 1 source bundles contain UTF-8 strings. Reading a PNG as text corrupts its bytes. Schema 2 explicitly distinguishes source text from encoded public assets, so copied photographs, fonts, and other binary content remain project-owned files.

Indexes and bundles declare `schemaVersion: 2`. The development installer reads both schemas; a bundle must match its selected index's schema. Published CLI 0.3.0 reads schema 1 only and remains pinned to registry 0.1.2 until a coordinated release.

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
2. Prepare a new CLI version with schema 2 support and compatible updated core/framework/design versions. The source version numbers currently describe the previous release, not these development APIs.
3. Choose a new immutable registry release version and record package compatibility. Release preparation rejects schema 2 with the known old CLI 0.3.0 metadata.
4. Build and install the consumer archives, verify media paths and licenses, and complete browser/keyboard review.
5. Publish npm packages, generate and verify the new immutable index/bundles, then publish the static registry. Only then update the CLI default index deliberately.

For now, public In progress previews demonstrate Stay01; the workspace can build/test schema 2 locally with `pnpm registry:build` and `pnpm registry:binary:test`. The schema is ready for the next release, not a claim that current npm supports it.
