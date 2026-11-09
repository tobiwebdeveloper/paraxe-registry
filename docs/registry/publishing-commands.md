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

These commands publish **the prepared archives**, not whatever source is currently in the workspace. ProductGallery and subsequent development require a newly versioned, built, and verified coordinated release before publication. Do not repack new source under an already-published version. `pnpm release:pack` is the preparation command after package versions and release metadata have been reviewed; it does not publish.

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
