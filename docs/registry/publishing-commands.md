# Publishing commands

Run these in a **PowerShell terminal**. The helper uses pnpm to publish prepared archives to the npm registry.

## npm packages

```powershell
Set-Location "C:\Users\tobio\paraxe"

# Check the prepared archives without publishing.
& .\releases\npm\publish.ps1 -DryRun

# Publish the same verified archives.
& .\releases\npm\publish.ps1
```

Run the `.ps1` file itself; do not paste its contents into the terminal. Its archive paths depend on PowerShell's `$PSScriptRoot`. The generated helper belongs beside `release-manifest.json` and the `.tgz` archives in `releases/npm/`. The canonical `scripts/publish-release.ps1` is a template, not the copy to run there.

The helper checks archive hashes, skips matching versions already on npm, and stops if a published version has different contents. Authenticate to npm if necessary with `pnpm login`; complete any account or two-factor prompts in your terminal.

These commands publish **the prepared archives**, not whatever source is currently in the workspace. The prepared update is core 1.5.0, design 1.9.0, Vue 1.4.0, React 0.3.0, and CLI 0.4.0, coordinated with registry 0.2.0. Do not repack new source under an already-published version. `pnpm release:pack` builds and packs; after `pnpm registry:release`, `pnpm release:verify` installs the archives in an isolated consumer, copies and checks all thirty-six bundles, builds both frameworks, and checks consumer types. Repacking invalidates that verification. None of those preparation commands publishes npm packages.

## Registry previews

To update the mutable gallery and its In progress previews, without changing installed release bundles:

```powershell
Set-Location "C:\Users\tobio\paraxe"
pnpm --filter playground-vue build --base=./
pnpm --filter playground-react build --base=./
pnpm registry:preview
pnpm registry:deploy
```

For a new installable registry release, review new package versions and `registry/release.json`, build and verify a new immutable release with `pnpm registry:release`, then deploy it. Existing versioned bundles stay unchanged. See [release details](releasing.md).
