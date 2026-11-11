# Settings01

A complete account-settings layout: a compact identity and section rail, profile fields, locale choices, notification rows, a read-only security overview, and a persistent save/discard bar. It uses Flex, the existing form/typography controls, and semantic colour, density, radius, and surface tokens. Clean is its suggested recipe; it does not introduce a new recipe or embed AppShell.

Try `?preview=settings-01&profile=clean&theme=light` in either playground. Included in registry **0.3.0**, with core **1.6.0**, design **1.10.0**, Vue **1.5.0** or React **0.4.0**, and CLI **0.5.0**. Its shared component improvements ship in these packages. Older immutable registry 0.2.0 does not include this layout.

## Controlled form contract

Import `Settings01` from its React entry or the default Vue entry. `modelValue` is required and contains fullName, email, bio, timezone, language, weeklyDigest, mentions, and productUpdates. React emits `onModelValueChange(value)`, `onSubmit(value)`, and `onDiscard()`; Vue emits `update:modelValue`, `submit`, and `discard`. No account or credentials are fetched automatically.

Optional props: errors (field messages), dirty, pending, feedback ({tone, message}), title, accountLabel, timezones, languages, security, and securityHref. Time-zone/language options are editable value/label lists. Extend the default lists in the copied source or pass your application's supported choices; pass the same lists to validation.

The security overview receives optional twoFactorEnabled, passwordUpdated, and sessionCount values from the app. Missing data is labelled as provider-managed rather than inventing a protection status. The optional Manage security link uses a real application destination. It is unavailable while changes are unsaved or saving, so it cannot silently abandon the draft. Security changes and sessions belong to the identity provider; they are never part of the preferences save payload.

## Save ownership and recovery

The optional `createSettingsController(initial, {persist, timezones, languages})` helper owns a copied draft and saved baseline. Subscribe/getSnapshot work with React's useSyncExternalStore or a Vue shallowRef. Connect update, save, and discard to the controlled events. The block also works with your own state controller.

Validation trims name/email/bio, checks name/email/lengths, checks locale membership, and validates notification booleans. It runs before persistence. Invalid fields have linked messages; a submit focuses the first invalid control. Saving locks duplicate work, edits, and discard. A rejected request or invalid server response preserves the draft and saved baseline. Success updates the baseline from the validated response. Discard restores the last successfully saved values, including after multiple saves.

The preview explicitly uses a sample account and tab memory. Its About this preview controls can make the next save fail to exercise recovery. Reloading resets the sample; it does not change an account, send emails, switch the interface language, or configure security.

For a real integration, provide a persistence function that performs authorization, validation, email-verification requirements, storage, and notification delivery on your server. Add route/unload guards in your application's navigation layer; the block's section links only jump inside the same form. Do not persist passwords or access tokens in this draft.

## Core change

Switch now supports id, name, labelledBy, describedBy, required, and invalid consistently in Vue and React, and omits its unused label span when the label is supplied externally. Settings01 uses native labels and description IDs rather than creating a bespoke toggle. The change is development source until a new package release.

Tests cover validation, custom locale choices, pending locks, failure/retry, invalid responses, saved-baseline discard, native Switch activation and labels, validation focus, both framework renders, and token policy. Browser visual review remains pending when no connected browser is available.
