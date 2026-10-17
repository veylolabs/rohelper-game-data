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

Adopt Me currently includes notebook support only. No pet or trading values are
invented. A sourced catalog can be published independently later.

The manifest is at
`https://raw.githubusercontent.com/veylolabs/rohelper-game-data/main/manifest.json`.
