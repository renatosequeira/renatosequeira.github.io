# renatosequeira.github.io

Static site hosting WebAuthn Relying Party metadata for the
[67Radar](https://github.com/renatosequeira/67radar) Android admin
unlock flow.

## What's here

- `.well-known/assetlinks.json` — Digital Asset Links file that binds the
  `com.sixseven.radar` Android package to this domain as a valid WebAuthn
  Relying Party. Without this file, Google Play Services blocks every
  passkey / hardware-security-key request issued by the app for `rp.id =
  renatosequeira.github.io`.

The SHA-256 fingerprint listed is the **debug** signing key. The release
fingerprint must be appended to the array before the Play Store build
ships.

## Why this domain

`renatosequeira.github.io` is the GitHub Pages user-pages origin (served
at the root, no project subpath). WebAuthn requires the RP id to be a
bare domain that serves `/.well-known/assetlinks.json` at its root, and
Supabase project URLs cannot serve that path — so a separate static host
is required.

If a custom domain is registered later (e.g. `admin.67radar.app`), this
file should be re-hosted there and every admin WebAuthn credential will
need to be re-registered against the new RP id (credentials are bound to
the RP id at creation time).
