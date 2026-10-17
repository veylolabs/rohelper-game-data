# RoHelper game data

Public, versioned game content maintained by **Veylo Labs**. RoHelper downloads
these catalogs independently of application releases. No accounts, cookies,
inventory ownership, notes, tags or personal progress are stored here.

## Publishing an update

Each immutable `game-<id>-<digest>.json` contains a game's name, search aliases,
Roblox place IDs, declarative notebook fields, catalogs, source links and evidence.
Upload the new pack first, then update `manifest.json` with its exact SHA-256.
Keep old immutable packs available. Publish a new manifest revision for each change.
Existing installations check on startup and every six hours, or on manual refresh.

Game IDs and catalog item IDs must stay stable. Never reuse an old ID for a new
item. Unknown facts stay null. Preserve individual source dates and attribution.
Game content is not account data: updating defaults must never create progress
records, reset values or mark an account as playing a game.

The data format is versioned separately from the application. Engine version 1
supports text, number and checkbox fields. Adding compatible games, fields, items,
events and reference facts needs a catalog update only. Brand-new types of UI or
game logic require an application update; remote executable code is not loaded.

## Sources and artwork

The initial SAB data is a previously checked public reference snapshot. Its records
retain their original verification dates; publication is not a fresh fact check.
SABRValues is the primary artwork source, SABExistCount is second, and the SAB
Fandom wiki is the final fallback. Exact source artwork URLs and evidence links
are retained. Artwork belongs to its respective creators and is not relicensed.

Adopt Me includes a public pet, egg and item catalog, separate categories, current
growth task tables, currencies and official event helpers. AMTV item IDs remain
stable (`amtv-<source ID>`); wiki-only entries retain `wiki-<article slug>` IDs.
Artwork uses the exact published AMTV item URL, an exact wiki table/infobox image,
or an exact official update image. Missing artwork stays unknown. Wiki-derived
facts are attributed to Adopt Me Wiki and its original Fandom authors under
CC BY-SA 4.0; artwork rights remain with the respective owners.

`tradeValues` is an AMTV community snapshot in Ride Potions (RP), checked on the
record's `valueCheckedOn` date, not euros or real sale prices. The twelve pet
variants are Normal, R, F, FR, N, NR, NF, NFR, M, MR, MF, MFR; non-pets have only
one value. The source's numerical units are divided by 250 (one Ride Potion).
Growth and friendship adjustments remain unknown. Never infer prices from rarity.
Source evidence and coverage limitations are retained in the Adopt Me pack.

The manifest is at
`https://raw.githubusercontent.com/veylolabs/rohelper-game-data/main/manifest.json`.

## Game layouts and shared events

`navigation` is an ordered tree of `{id, name, icon, view}` tabs or `{id, name, children}` groups. IDs stay stable; labels and order may change. Built-in views: `overview`, `servers`, `notebook`, `reference`, `events`, `event-helpers`, `sab-overview`, `sab-inventory`, `sab-catalog`, `sab-compare`, `sab-checklist`, `adopt-overview`, `adopt-inventory`, `adopt-catalog`. Adopt Me inventory tabs declare a `category` ID. `accountTabs` configures SAB's `sab-rebirth`, `sab-inventory`, `sab-index` views. Reference catalogs contain `sections` and human-readable `entries`. Unknown view types need a newer app; packs never contain executable code.

`helpers` configures names/types/catalog keys for rewards, fuses, crafting, collection and islands. `inventoryEngine: "sab"` enables SAB ownership and reward-to-base actions; `inventoryEngine: "adopt-me"` enables Adopt Me reward ownership, account checklists and add-to-inventory actions. Other games remain reference-only until they have an inventory engine. Never display egg tiers or treat conditional reported fuse maxima as personalized probabilities.

`events` contains stable IDs, titles, start wall times, IANA zones, duration minutes, recurrence, provenance and confirmation state. Use null times/durations and `scheduleConfirmed: false` where unknown; optional `dateStart`/`dateEnd` represent date-only references. Never invent midnight start times or one-hour end times. Label community schedules and estimated ends. Per-device personal timers and per-field overrides are never published. Updates must not initialize or change account progress.

SAB gear reference names are included separately from brainrot base slots. Source metadata and CC BY-SA 4.0 attribution are in `catalogs.gear`; unknown artwork, values and availability remain unasserted. User quantities and notes never enter this repository.

## Inventory helpers and mutation previews

SAB `catalogs.mutationEffects` contains declarative filter palettes, textures, glow, tone tables and color cycles. The app supplies a bounded renderer; no remote executable scripts are loaded. Mutation colors and menu/index order are in the mutation records; traits carry their own menu order. Gold, Diamond and Rainbow remain last in mutation menus, while index tabs start Normal, Gold, Diamond, Rainbow.

`catalogs.gear` retains stable gear IDs, exact artwork references and per-entry acquisition evidence. Cash gear shop, Robux offers, event wheels, fishing, codes and other event sources are distinct. Speculative or unfinished gear is marked unconfirmed. CDN rejection is recorded without substituting unrelated artwork.

Adopt Me `catalogs.items.hatchPools.pools` maps egg IDs to verified current pet IDs and source evidence. Previously obtainable pools are excluded; conditional pets retain their rotation conditions. A hatch is a local account inventory action, consuming one egg and adding one normal newborn pet. Non-pet stacks retain distinct saved metadata.

Currency definitions are public defaults only. All account balances, inventories, ownership and progress stay local. Account and item notes are never published.
