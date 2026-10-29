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

`helpers` configures names/types/catalog keys for rewards, fuses, crafting, collection and islands. `inventoryEngine: "sab"` enables SAB ownership and reward-to-base actions; `inventoryEngine: "adopt-me"` enables Adopt Me reward ownership, account checklists and add-to-inventory actions. The collection engine supports the additional games described below. Never display egg tiers or treat conditional reported fuse maxima as personalized probabilities.

`events` contains stable IDs, titles, start wall times, IANA zones, duration minutes, recurrence, provenance and confirmation state. Use null times/durations and `scheduleConfirmed: false` where unknown; optional `dateStart`/`dateEnd` represent date-only references. Never invent midnight start times or one-hour end times. Label community schedules and estimated ends. Per-device personal timers and per-field overrides are never published. Updates must not initialize or change account progress.

SAB gear reference names are included separately from brainrot base slots. Source metadata and CC BY-SA 4.0 attribution are in `catalogs.gear`; unknown artwork, values and availability remain unasserted. User quantities and notes never enter this repository.

## Inventory helpers and mutation previews

SAB `catalogs.mutationEffects` contains declarative filter palettes, textures, glow, tone tables and color cycles. The app supplies a bounded renderer; no remote executable scripts are loaded. Mutation colors and menu/index order are in the mutation records; traits carry their own menu order. Gold, Diamond and Rainbow remain last in mutation menus, while index tabs start Normal, Gold, Diamond, Rainbow.

`catalogs.gear` retains stable gear IDs, exact artwork references and per-entry acquisition evidence. Cash gear shop, Robux offers, event wheels, fishing, codes and other event sources are distinct. Speculative or unfinished gear is marked unconfirmed. CDN rejection is recorded without substituting unrelated artwork.

Adopt Me `catalogs.items.hatchPools.pools` maps egg IDs to verified current pet IDs and source evidence. Previously obtainable pools are excluded; conditional pets retain their rotation conditions. A hatch is a local account inventory action, consuming one egg and adding one normal newborn pet. Non-pet stacks retain distinct saved metadata.

Currency definitions are public defaults only. All account balances, inventories, ownership and progress stay local. Account and item notes are never published.


## Shared collection engine (RoHelper 0.6.0)

Grow a Garden, Grow a Garden 2, Fisch, Pet Simulator 99, Blox Fruits, Bee Swarm Simulator and Murder Mystery 2 declare `inventoryEngine: "collection"`. Their `catalogs.collection` holds stable entries/categories, item field definitions (number, text, checkbox, select and multiple choice), optional variants, source facts, currencies and verified recipes. The built-in `collection-overview`, `collection-inventory`, `collection-search`, `collection-catalog`, `collection-index`, `collection-planner` and `collection-helpers` views render these data. Existing SAB and Adopt Me packs retain their original inventory engines.

All balances, saved item copies, indexes, goals, hive positions and timers are account-local. A catalog refresh never fills ownership or resets a balance. Indexes are catalog acquisition checklists, not promises of exact in-game reward eligibility or totals. Unsupported views require a newer app; catalogs contain no remote executable scripts.

Pet Simulator 99 uses official BIG Games public collection/RAP endpoints and Roblox asset thumbnails. Variant/shiny/tier matching is exact; unrecognized RAP configuration flags are excluded instead of guessed. RAP snapshots are diamonds, never euro prices. Murder Mystery 2 uses exact wiki article IDs/artwork and direct Supreme Values snapshots in SV units, never inferred from rarity. All values retain source and check dates and are not guaranteed trades.

Other new game facts/artwork are attributed to Grow a Garden Wiki, Grow a Garden 2 Wiki, Fisch Wiki, Blox Fruits Wiki, Bee Swarm Simulator Wiki, Murder Mystery 2 Wiki and their original Fandom authors under CC BY-SA 4.0 where applicable. Artwork rights stay with the respective creators. Images are exact published source URLs; missing artwork stays unknown. Grow a Garden 2 refers to Strawberreh Squad’s verified current Roblox place, not an old unavailable listing.

Verified Bee Swarm Blender/equipment recipes and Blox Fruits weapon upgrades are reference plans. They compare only manually recorded inventory/currency and never simulate crafting or consume items. Event dates, probabilities, cooldowns and other missing facts remain unknown unless verified.


## Unified catalogs and gear artwork (0.6.3)

SAB and Adopt Me browsing tabs are named Catalog. All supported catalogs present All items before their item types; SAB combines Brainrots and Gear. The acquisition index remains separate. Six missing gear images are verified and embedded for reliable loading: Roblox developer-product icons for Flying Bee/Waverider, and exact Skibidi Games gear images for Bat/Rainbow Hammer/Christmas Coils/Demon’s Head. Gear artwork may use any clear, exact verified source, with per-entry URL/provider/hash provenance. The separate brainrot artwork source order is unchanged. Unverified, generated illustrations and tiny promotional cover crops are not used. Four remaining gear images stay unknown. No account ownership or personal data is included.


## Activity achievements (RoHelper 1.0)

The optional top-level `manifest.achievements` descriptor points to an immutable JSON file and its full SHA-256 digest. RoHelper 1.0 downloads and validates this data with the game catalogs, caches it in local AppData, and uses the bundled definitions when offline. Older clients ignore this optional field.

Each definition has a stable `id`, `name`, `description`, `group`, numeric `target`, supported `metric`, XP `points`, and an `icon` containing a hex color and SVG path data. Supported metrics: `combinedMs`, `wallActiveMs`, `sessions`, `peakAccounts`, `longestSessionMs`, `activeDays`, `bestStreak`, `antiAfkInputs`, `macroCycles`, `uniqueAccounts`, `savedMacros`, `trackedGames`, and `catalogedItems`. The catalog contains declarative data only, never scripts. New conditions using existing metrics need only a catalog update; adding a new measured metric requires app support.

The initial set contains 53 achievements. Runtime months mean 30 days and years mean 365 days. Calendar-day goals and streaks use UTC. Completed macro cycles count when a script reaches its end. Statistics, account identities, pinned trophies and unlock states stay local and are never uploaded. Unlocks retain a local definition snapshot, so changing or retiring a definition does not remove an earned achievement.


### Achievement expansion — October 29, 2026

100 new definitions bring the catalog to 153 achievements. All original 53 IDs, conditions, names, XP and icons are unchanged. The expansion works with RoHelper 1.0.0 through its normal game-content refresh; no app installation is required.

New Presence achievements measure observed real-world active time, with parallel accounts counting once. New Roster achievements count distinct saved accounts observed over time, without requiring simultaneous clients. More milestones cover combined runtime, concurrent accounts, session counts and lengths, active days, streaks, anti-AFK inputs, macro cycles, saved macros, games and inventories. Each chain is ordered by its target. Existing recorded progress can qualify for the new milestones, while earned unlocks remain local and permanent.

## Events and cooldown timers (RoHelper 1.0.1)

All nine supported games have sourced event references and timer presets: 26 event records and 38 timers reviewed October 29, 2026. Exact schedules are enabled only where supported; date-only, random and disputed schedules remain unconfirmed. This is verified coverage, not a claim that every possible server event is predictable.

Optional `timerPresets` records contain stable IDs, titles, duration seconds, account/server/global scope, clock type, source links, check dates, notes and optional duration variants or UTC phase offsets. Shared clocks predict timing, never live stock or guaranteed rewards. Community references are labeled. Online timers measure only a detected account while RoHelper is open; players must pause them outside the relevant game. Started timers, pauses, notifications and account/server bindings remain local in AppData and retain their duration across catalog updates. Older app versions ignore timer presets. Existing event IDs, local overrides, inventory records and achievement definitions are preserved.
