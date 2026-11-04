# Standby Packs

Content packs for **Standby** (App Store name: *Emergency*), an offline-first
iOS survival and preparedness app. The app downloads this repository's
`manifest.json`, and users install packs from it on demand — each pack lands in
the app's fast reading and search format, never as a raw document.

This repository contains **content only** — no app source code.

## Packs

| Pack | Guides | Source | Licence |
|---|---|---|---|
| `ready-gov-plan-kit` | 2 | Ready.gov (FEMA) | Public domain (U.S. government work) |
| `ready-gov-disasters` | 6 | Ready.gov (FEMA) | Public domain (U.S. government work) |
| `army-survival` | 8 | U.S. Army FM 3-05.70, *Survival* | Public domain (U.S. government work) |

## Structure

- `manifest.json` — the list of available packs (`id`, `name`, `description`,
  `guideCount`, `sizeKB`, `version`, `url`). Pack URLs are relative to the
  manifest, so this repository works unchanged from raw.githubusercontent.com
  or any mirror.
- `<pack-id>.json` — one file per pack: metadata, licence (kind, attribution,
  source URL) and guides. Each guide is front-matter fields plus a markdown
  body in a deliberately tiny subset: `#`/`##` headings, single-level `-`
  bullets, `1.` steps, `> ⚠️` warnings, `**bold**`/`*italic*`. No tables, no
  nested lists, no links, no images.

## Sourcing policy

Only openly licensed or public-domain sources, per-pack:

- **Public domain**: U.S. federal government works (17 USC §105) — Ready.gov,
  CDC, U.S. Army field manuals. Verbatim, attribution as good practice.
- **OGL v3.0**: gov.uk, HSE, Environment Agency — verbatim, with the required
  attribution line: *"Contains public sector information licensed under the
  Open Government Licence v3.0."*
- **CC BY-SA 4.0**: Wikipedia-derived packs only, clearly badged share-alike.
- **Never** verbatim: NHS, British Red Cross, AHA/BHF, WHO — facts only,
  rewritten and cited.

## Adding a pack

1. Author `<pack-id>.json` (validate with `python3 -m json.tool`).
2. Add its entry to `manifest.json` with the correct `guideCount` and `sizeKB`.
3. Commit to `main`. Installed apps pick it up the next time the user opens the
   pack list — no app release needed.
4. Bump a pack's `version` when its content changes.
