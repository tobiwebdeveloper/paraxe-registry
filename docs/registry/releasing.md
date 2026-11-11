# Registry and npm release — 9 November 2026

The current coordinated update is [published release 0.3.0](release-0.3.0.md), with 24 layouts, 48 bundles, Calendar, and all work through Booking01. Use the [current publishing commands](publishing-commands.md). The details below record the verified 0.2.0 baseline; its bundles and older CLI default remain immutable.

## What ships

| npm package | Published update | Previous release |
| --- | --- | --- |
| @paraxe/core | 1.5.0 | 1.4.0 |
| @paraxe/design | 1.9.0 | 1.8.0 |
| @paraxe/vue | 1.4.0 | 1.3.0 |
| @paraxe/react | 0.3.0 | 0.2.0 |
| @paraxe/cli | 0.4.0 | 0.3.0 |

All five updated versions were published by the maintainer and verified against their exact archive integrity on 9 November 2026. See [release status](../reference/release-status.md). Never republish changed contents under an existing version.

Registry **0.2.0** uses schema 2, with eighteen experimental layouts and thirty-six framework bundles. It adds exact binary-asset copying. Nine recipes ship in the CLI/design packages. Registry **0.1.2** remains immutable and usable by CLI 0.3.0. No preparation tool publishes npm packages; deployment checks that required npm versions exist first.

## Registry hosting

Public release repository: https://github.com/tobiwebdeveloper/paraxe-registry

GitHub Pages destination: https://tobiwebdeveloper.github.io/paraxe-registry/

The main Paraxe repository stays private. Only generated release material and client previews are pushed to the public release repository. Hosting is independent of Codex and ChatGPT. The abandoned Sites project was never deployed and is not a registry dependency.

The versioned index is `r/v0.2.0/index.json`. It records compatible package versions and a SHA-256 for each framework bundle. Bundles contain editable source, explicit text/base64 encodings, file destinations, decoded-byte hashes, and license text. `integrity.json` covers the complete release. Hashes detect corruption against the chosen index; they are not publisher signatures.

## Consumer installation

After npm publication and registry deployment, use CLI 0.4.0:

```sh
npx @paraxe/cli@0.4.0 list
npx @paraxe/cli@0.4.0 add product-page-01 --framework vue --dry-run
npx @paraxe/cli@0.4.0 add product-page-01 --framework vue
```

Use `--framework react` for React, `--dir` to select a project directory, and `--registry` to select another trusted HTTPS index. HTTP localhost is allowed for local testing. Node 22 or newer is required by the CLI.

The installer copies source into `blocks/<name>/`, assets into `public/`, and full license text into `.paraxe-licenses/`. It prints package dependencies to install or upgrade separately. It never runs registry scripts or package installs. Preflight checks reject path traversal, protected paths, duplicate destinations, corrupt hashes and existing directory links. Existing files are refused unless `--force` is explicitly supplied. A failed write attempts to restore files already changed by that install.

## Edit in the IDE

Installed blocks are ordinary project files, not remotely rendered pages. Edit a ProductPage01 entry to add shared QuantityInput and Button components, wire your cart, or change its layout. Your app owns those changes. Defaults such as read-only stock display remain examples rather than a complete checkout.

Updates do not silently overwrite or merge local changes. Compare a fresh bundle or use a separate directory and manually merge. `--force` replaces files; it is not a merge operation. Keep token references so recipes and independent preset axes keep working.

## Reproduce artifacts

```sh
pnpm install --frozen-lockfile
pnpm release:pack
pnpm --filter playground-vue build --base=./
pnpm --filter playground-react build --base=./
pnpm registry:release
pnpm release:verify
```

`release:pack` builds all five packages, packs them with workspace references converted to published versions, and writes archives, checksums, logs, and `publish.ps1` to ignored `releases/npm/`. Cleaning generated core/CLI output before building prevents deleted APIs from surviving inside tarballs. The design package now emits the `index.js` promised by its manifest, and its style entry points to `style.css`.

The registry release command validates sources/tokens, produces immutable bundles under `registry/dist/releases/v0.2.0`, and generates the static site under `registry/site/public/`. Previews use relative Vite assets; only deployed fixture-image paths are adapted to the GitHub Pages project prefix. Source bundles keep their normal application-root image paths.

`release:verify` installs all five archives in a fresh consumer outside the monorepo, overrides the unpublished core dependency with its exact prepared archive, verifies versions and all nine recipe exports, copies all thirty-six registry bundles through the packed CLI, verifies every installed byte/hash, produces Vue and React production builds, and checks consumer TypeScript/Vue declarations. Logs stay in the recorded consumer directory. It writes `releases/npm/verification.json` only on success. Repacking invalidates that record; the publishing helper requires a matching manifest hash.

Changing an existing versioned bundle is rejected: bump `registry/release.json` for the next release and update the CLI's pinned default URL when appropriate. Preserve old release directories on the host.

## Publish npm archives yourself

From the workspace root, after the prepared archive checks and clean-consumer checks pass:

```powershell
Set-Location "C:\Users\tobio\paraxe"
& .\releases\npm\publish.ps1 -DryRun
& .\releases\npm\publish.ps1
```

Use the exact verified archives; avoid rebuilding between verification and publication. npm authentication and any two-factor step remain with the maintainer. Existing npm versions are immutable; the prepared versions were checked against npm before preparation. The same command is saved in the [product direction document](../product-direction.md).

## Publish or update registry files

`pnpm registry:deploy` clones or updates only the dedicated public release repository under ignored `releases/registry-publish`, copies reviewed generated files, commits them, and pushes normally without force. It does not stage or commit the main working tree. GitHub Pages serves the public repository's `main` branch at `/`; `.nojekyll` preserves static assets.

For a host migration, copy the static files and retain all versioned paths, then use `--registry` or publish a new CLI default URL. The npm packages and copied application blocks do not depend on the website remaining online at runtime.

## Verification limits

Package tests, framework typechecks, registry tests, archive inspection, and a clean tarball consumer establish release consistency. Check anonymous HTTP access to the deployed index/bundles and run the prepared CLI against that URL before calling it live. Browser visual review remains pending; all blocks stay experimental.

## PowerShell helper

Run from any folder using the full script path, or from the workspace root:

```powershell
& .\releases\npm\publish.ps1 -DryRun
& .\releases\npm\publish.ps1
```

The helper uses one native `pnpm.cmd` launcher with resolved argument values. It publishes the already-verified tarballs to the npm registry rather than publishing the workspace folders. `--no-git-checks` allows those checksum-verified archives to be published while the source workspace has uncommitted changes. It checks all archive SHA-256 values before publishing, skips packages marked already published in the release manifest, and stops on the first npm failure. `-DryRun` forwards npm's dry-run option and publishes nothing. The canonical helper is `scripts/publish-release.ps1`; packing copies it next to the archives.

The publish helper can resume after a partial release: it checks npm for each remaining version and skips it only when the published SHA-512 integrity matches the prepared archive. A differing published archive stops the release for review. Authentication failures still stop publication; complete the fresh npm login/OTP prompt before retrying.

The copyable PowerShell commands are saved separately in [Publishing commands](publishing-commands.md), including the working directory, dry run, and preview deployment.
