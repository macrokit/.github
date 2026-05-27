# Macrokit community macro registry

This directory hosts the canonical list of community-published macro packages for [Macrokit](https://macrokit.dev). Anyone can publish a Macrokit macro package — registry listing is the path to ecosystem discovery.

## The registry file

`registry.json` is a single JSON file. Each entry describes one published npm package. The file is small on purpose; if it ever grows past a few hundred entries we'll split it.

### Entry schema

```jsonc
{
  "name": "macrokit-macros-paper-triage",
  "npm": "https://www.npmjs.com/package/macrokit-macros-paper-triage",
  "repo": "https://github.com/some-org/macrokit-macros-paper-triage",
  "vertical": "Academic paper triage",
  "surfaces": ["arxiv.org API", "Semantic Scholar API", "OpenAlex"],
  "macros": 7,
  "author": "Jane Doe (Some Organization)",
  "license": "Apache-2.0",
  "addedAt": "2026-07-12"
}
```

Fields:

| Field | Type | Required | Notes |
|---|---|---|---|
| `name` | string | yes | npm package name. Should follow `macrokit-macros-<vertical>` or `@scope/macrokit-macros-<vertical>` (see [CONTRIBUTING_MACROS.md](https://github.com/macrokit/core/blob/main/CONTRIBUTING_MACROS.md#naming-convention)). |
| `npm` | URL | yes | Public npm registry URL. |
| `repo` | URL | yes | Public source repo. Reviewers spot-check this. |
| `vertical` | string | yes | Short human-readable vertical name. "Academic paper triage", "GitHub maintainer ops", "Internal RFP intake". |
| `surfaces` | array of strings | yes | What systems the macros drive — API names, web apps, file formats, etc. At least one entry. |
| `macros` | integer | yes | Number of macros exported. Should match the package's actual export count. |
| `author` | string | yes | Maintainer name + optional org. "Jane Doe", or "Jane Doe (Acme Inc)". |
| `license` | string | yes | SPDX identifier. Only `Apache-2.0` or `MIT` are listed. |
| `addedAt` | ISO date | yes | Date the entry was added (`YYYY-MM-DD`). Maintainers fill this in on merge. |

The entry shape is intentionally rigid so the registry is easy to render as a table on the docs site without per-entry JSON gymnastics.

## How to get your package listed

1. **Make sure your package qualifies.** Run `macrokit lint --pkg <path/to/your/package>` and address every finding. The package must also have at least 5 benchmark tasks committed to its repo. The full requirements are in [`core/CONTRIBUTING_MACROS.md`](https://github.com/macrokit/core/blob/main/CONTRIBUTING_MACROS.md#minimum-requirements-for-a-valid-macro-package).

2. **Open a PR against `github.com/macrokit/.github`** that adds your entry to `community/registry.json`. Insert your entry in package-name alphabetical order. Leave `addedAt` blank (or use the current date — a reviewer will set it on merge).

3. **PR title format:** `community: add <package-name>`. That's it.

4. **What reviewers check** (intentionally a short list):
   - `npm` URL resolves to a published package.
   - `repo` URL is public.
   - `macrokit lint --pkg` passes against the published version.
   - License is `Apache-2.0` or `MIT`.
   - No outbound calls to maintainer-controlled domains in the macro handlers (a spot-check, not exhaustive).
   - README meets the minimum bar.

5. **Approval is fast.** Usually within a few days. Listing does not imply endorsement of the workflows themselves, only that the package meets the structural bar.

6. **If rejected,** the review comment names the specific failed check. Fix it and re-open.

## Updates and removals

- **Version bumps in your package** require nothing here — the npm link resolves to whichever version is published.
- **Maintainer changes, scope changes, surface changes** — open a PR editing your existing entry.
- **Sunsetting a package** — open a PR removing your entry. Don't silently un-publish from npm without removing the registry entry; that leaves dead links in the docs.
- **Maintainers may remove entries** if a package starts shipping telemetry, becomes a credential exfiltration vector, or is reported as malicious. Removal in those cases happens without a PR; the reason is logged in the commit message.

## What this registry is NOT

- It is not a marketplace. There is no rating system, no download counts, no "featured" tier. Packages are listed alphabetically.
- It is not a quality endorsement. Listing means the package meets the structural minimum, not that the workflows it encodes are correct, secure, or appropriate for any specific deployment.
- It is not exhaustive. The `macrokit-macros` GitHub topic catches packages that haven't been listed (yet or ever). The registry is the curated subset.

## Questions

Open an issue on [`github.com/macrokit/core`](https://github.com/macrokit/core/issues) with the `community` label.
