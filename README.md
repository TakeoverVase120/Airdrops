# Airdrops v1

Configurable supply drops, landmark encounters and rewards for **Minecraft Paper 26.2 with Java 25**. Race to Common, Rare, Epic and Legendary drops, complete encounters, hold your claim and collect the loot.

Public release name: **v1**. The plugin reports **1.0.0** in the server console. Earlier preview numbers were development builds.

[Download v1](https://github.com/TakeoverVase120/Airdrops/releases/tag/v1) · [Resource packs](https://github.com/TakeoverVase120/airdrops-resource-packs/releases/tag/v1) · [Report an issue](https://github.com/TakeoverVase120/Airdrops/issues)

## Choose your download

| Download | Use it for |
|---|---|
| [AirDrops-v1.jar](https://github.com/TakeoverVase120/Airdrops/releases/download/v1/AirDrops-v1.jar) | The plugin itself; replace your existing Airdrops JAR while the server is stopped. |
| [AirDrops-v1-Full.zip](https://github.com/TakeoverVase120/Airdrops/releases/download/v1/AirDrops-v1-Full.zip) | Installation documentation, plugin, matching source, optional expansions, companion content and resource packs. |
| [AirDrops-v1-Upgrade.zip](https://github.com/TakeoverVase120/Airdrops/releases/download/v1/AirDrops-v1-Upgrade.zip) | Upgrade package; read its instructions and preserve existing settings and player data. |
| [AirDrops-v1-source.zip](https://github.com/TakeoverVase120/Airdrops/releases/download/v1/AirDrops-v1-source.zip) | Matching plugin source. GitHub's automatically generated “Source code” archives contain this documentation repository instead. |
| [SHA256SUMS.txt](https://github.com/TakeoverVase120/Airdrops/releases/download/v1/SHA256SUMS.txt) | Checksums for the release downloads. |

## What Airdrops can do

- Automatic scheduled drops, countdowns, manual tests and a live player tracker.
- Four rarity tiers with configurable chances, loot pools, roll counts, expiry times, effects and messages.
- Falling reward crates, timed claiming and cancellation when the claimant moves too far away.
- Small tier structures, with a switch to retain them around falling crates.
- Larger landmarks with staged objectives, patrols, waves and boss encounters, according to the installed content.
- Configurable YAML bosses and events, event-locked rewards and boss encounter history.
- Remote call-in items, limited-charge attraction beacons and placeable/recoverable trophies.
- Optional exchange menus, tradable encounter items, transaction history, achievements, reward inboxes, weekly challenges and exclusive gear crafting/recycling.
- Optional Eclipse night events and a themed shop.
- Optional Java and Bedrock resource packs for supported item and delivery visuals.
- An owner menu, backed-up content editing, configuration reloads and durable terrain recovery.

**A fresh core installation does not automatically enable every expansion.** The Full download contains seven optional content packs: Gear, Landmarks, Encounters, Rewards, Exchange, Eclipse and Visuals. Install and enable the features you want. Server PvP rules and protection plugins still determine where players can fight.

## Requirements and optional integrations

| Component | When you need it |
|---|---|
| Paper 26.2 and Java 25 | Release target. |
| WorldEdit | Pasting schematic structures and landmarks. Use a build compatible with your Paper server. |
| CreatorRuntime | Resolving the supplied Creator item rewards. The Full download includes companion content and 12 Airdrops item definitions. |
| Vault and a supported economy provider | Content that uses economy rewards or costs. SimpleBank is a separate plugin; native Airdrops core does not require it. |
| Geyser/Floodgate, as appropriate to your crossplay setup | Bedrock access; matching packs and custom mappings are also needed for custom Bedrock visuals. |
| WorldGuard / GriefPrevention | Optional protection integration when installed. |

Creator Studio and CreatorBridge are authoring tools, not requirements for normal core gameplay. Optional content is configuration/content, not seven additional plugin JARs.

## Install or upgrade

1. For an existing server, clear an active drop with `/airdrop clear` and check that cleanup succeeded. Stop the server normally.
2. Back up the affected worlds and plugin data together. Keep this matching recovery set.
3. Put **one** Airdrops JAR in `plugins/`. Move the old JAR outside that folder. Preserve the existing `plugins/Airdrops/` directory, player progress, ledgers and recovery journal.
4. Start the server and check that Airdrops enables as `1.0.0`. A fresh data folder selects core content; existing installations retain their settings.
5. Stop before installing selected expansions. For a compact layout, copy missing files from `optional-content/ready-for-compact/<pack>/Airdrops/` into `plugins/Airdrops/`. Compare and merge any existing files rather than replacing them wholesale.
6. Install the dependencies for those expansions, then restart and check the console. Test a drop, claim, cleanup and any enabled encounter/reward features.

For legacy layouts, use the logical paths in each content ZIP's `expansion.json`. Do not install both layouts. A `content-layout-v1.done` file identifies the compact layout; keep that marker.

JAR upgrades, Geyser mappings and pack changes require a normal restart. `/airdrop reload` is for supported configuration/content edits. Avoid generic plugin hot-reload tools.

## Player commands

These permissions are **enabled for players by default**. A server's permissions plugin can override them. Menu commands are used in game; features also need their content installed and enabled. `<value>` means required; `[value]` means optional. Do not type the brackets.

| Command | What it does | Permission |
|---|---|---|
| `/addrops` | Opens the live schedule and active-drop tracker. | `airdrop.overview` |
| `/airdropachievements` or `/adachievements` | Opens achievements and progress. | `airdrop.achievements` |
| `/adrewards` | Opens the reward inbox/menu. | `airdrop.achievements` |
| `/adrewards weekly` | Shows weekly challenges/progress. | `airdrop.achievements` |
| `/adrewards recycle confirm` | **Consumes the eligible exclusive armour piece in your main hand** for fragments. Applies to recognised Dawnkeeper/Starforged pieces; use deliberately. | `airdrop.achievements` |
| `/adexchange` or `/airdropexchange` | Opens the exchange menu. | `airdrop.exchange` |
| `/adexchange tradables` | Opens the tradable-item catalogue. | `airdrop.exchange` |
| `/adexchange history` | Opens your exchange transaction history. | `airdrop.exchange` |
| `/adeclipse` or `/adeclipse shop` | Opens the Eclipse shop. | `airdrop.eclipse` |
| `/adeclipse status` | Shows Eclipse status and relevant player shop information. | `airdrop.eclipse` |
| `/advisuals` or `/advisuals refresh` | Refreshes recognised inventory item visuals when Visuals is enabled; retains stats and abilities. | `airdrop.visuals` |
| `/discord` or `/dc` | Shows the configured Discord information if the feature is enabled. Configure your own server's destination. | No separate player permission declared. |

Players claim drops by interacting with the landed crate and following its prompts. They do not need `/airdrop test` or any administrative give command. Defaults are a 10-second claim with a 5-block maximum distance; the server can change these.

## Admin and OP commands

`airdrop.admin` defaults to **OP**. It grants the entire `/airdrop` command, the admin panel and the administrative actions below. Do not grant it merely to let players claim drops. Administrative actions under player command roots still need that root's permission if you explicitly denied it.

| Command | Purpose / important behaviour |
|---|---|
| `/airdrop` | Displays command help. |
| `/airdrop start` | Starts the airdrop countdown. |
| `/airdrop stop` | Stops automatic drops/countdown and attempts to clear the active drop. |
| `/airdrop clear` | Clears the active drop/arena while retaining the automatic schedule. Cleanup safety checks still apply. |
| `/airdrop info` | Reports the active drop, including its location. |
| `/airdrop reload` | Reloads supported settings/content. Check console validation messages. |
| `/airdrop test <common|rare|epic|legendary>` | Attempts a test drop using loaded terrain and configured distance limits; see the placement section. Requires at least one online player. |
| `/airdrop landmarks [rarity]` | Lists installed landmark IDs and whether landmarks are enabled. |
| `/airdrop landmark <id>` | In-game only: attempts that landmark near the command sender. Needs available schematic, enabled structures and suitable loaded ground. |
| `/airdrop history [id-prefix|boss-type]` | Shows up to ten matching boss-history entries, outcomes and rankings. |
| `/airdrop utility <remote|beacon|trophy> [player]` | Gives a utility item. Target must be online and have inventory space. Console must name a player. |
| `/airdrop loot list <rarity> [page]` | Lists loaded loot entry IDs. |
| `/airdrop loot give <rarity> <entry-id> [player]` | Gives a specific loaded loot entry; needs inventory space. Console must name a player. |
| `/airdrop loot roll <rarity> <1-54> [player]` | Gives random rolls from the selected loot pool; needs inventory space. Console must name a player. |
| `/airdrop boss spawn <boss-id>` | In-game only: tests an installed boss near the player. |
| `/airdrop event start <event-id>` | In-game only: starts an installed event at the player's location. |
| `/adadmin` | In-game owner control panel. |
| `/adadmin edit <file> <key> <value>` | In-game: edits an existing allowed content value with a backup. Review and reload content afterward. |
| `/advisuals refresh <player>` | Refreshes an online player's recognised item visuals. |
| `/adexchange history <online-player|UUID>` | Reviews another player's exchange history; offline lookup uses UUID. |
| `/adexchange give <player> <currency-or-landmark-ID> <1-2304>` | Gives recognised exchange items to an online player with room. |
| `/adrewards give <player> <common|rare|epic|legendary> <1-100>` | Credits packs to an online player's reward inbox. |
| `/adrewards givegear <player> <dawnkeeper|starforged> <helmet|chestplate|leggings|boots>` | Delivers exclusive gear or saves it to the reward inbox. Existing pending rewards must be collected first. |
| `/adrewards fragments <player> <1-10000>` | Credits an online player's fragments. |
| `/adrewards review <player>` | Shows pending reward/receipt and recycling-review state. |
| `/adrewards resetachievements confirm` | **Resets all achievement progress and achievement claims**, with a backup. Retains inventories, bank, salvage, packs and weeklies. |
| `/adeclipse start [world] [variant]` | Starts an Eclipse event. Console must specify a world; specify world before variant. Bypasses chance/cooldown only. |
| `/adeclipse stop [world]` | Ends an Eclipse event. Console must specify a world. |
| `/adeclipse reload` | Reloads Eclipse settings and ends active Eclipse events. |
| `/adeclipse give <player> <shard|item-id> <1-64>` | Gives Eclipse items to an online player; gear must be given one at a time. |

`/discord reload` (also `/dc reload`) uses **`airdrop.discord.admin`**, which defaults to OP, rather than `airdrop.admin`. It is in-game only and can reload the configuration even when the Discord feature is disabled.

Use installed definition IDs for bosses/events and tab completion where provided. Optional companion commands such as `/creatoritem` belong to CreatorRuntime and have their own permissions/help; they are not Airdrops player commands.

## Why `/airdrop test common` may not work where you are

**The test command does not promise a drop beside you.** In this release it uses the **first online player's world**, which may differ from the sender's world on a multiplayer server. It then searches already-loaded chunks within the configured distance band.

In `plugins/Airdrops/config.yml`:

```yaml
airdrop:
  location:
    min-distance: 500
    max-distance: 3000
```

These distances are measured horizontally from **world X:0, Z:0**, not from the command sender or a relocated world spawn. They form a distance band, not independent X and Z limits. Moving `/setworldspawn` does not move this search centre.

For example, an open site at X:1000, Z:0 is within the default band. A player millions of blocks away does not make their nearby terrain eligible. Also, previously generated terrain is not necessarily currently loaded.

If the console says **“Could not find a safe airdrop location”**:

1. Confirm which online player's world is being selected. For a controlled test, use a single tester in the intended world. Nether drops are disabled.
2. Load open, suitable terrain within the configured band, then retry. Standing in the band helps load candidate chunks but does not guarantee a successful search.
3. Check min/max settings, terrain and relevant protections. On a dedicated test world you can deliberately lower the minimum, then reload; preserve your production limits unless you intend to change them.
4. For a nearby utility test, use a beacon and remote through their normal interaction path. For a named landmark, use `/airdrop landmarks` followed by `/airdrop landmark <id>` on open ground.
5. Check the actual spawn/landing log and `/airdrop info`. The test command's generic “spawned” reply alone is not proof of successful placement.

Automatic scheduled drops use an asynchronous location search; `/airdrop test` uses the loaded-chunk search. A failed test is not by itself proof that automatic drops have stopped. Recovery warnings are a separate issue—see below.

## Structures, landmarks and falling delivery

Small tier structures and landmarks are separate features. A landmark has its own encounter/objectives. When a landmark cannot fit, Airdrops can fall back to a smaller tier structure.

To keep small structures around a falling crate, merge these **root-level** keys into `plugins/Airdrops/delivery.yml`:

```yaml
enabled: true
keep-small-structures: true
```

Put `keep-small-structures` alongside `enabled`, `height` and `duration-ticks`—**not inside `visual:`**. Keep your existing visual settings. Also enable the master switch in `config.yml`:

```yaml
airdrop:
  structure:
    enabled: true
```

- `keep-small-structures: true`: retains the basic tier structure with falling delivery.
- `keep-small-structures: false` (default): uses crate-only falling delivery, removing the basic structure.
- Landmarks retain their own behaviour; this switch does not disable them.
- Schematic placement needs WorldEdit and the matching files. Landmark settings, catalogue, events, loot and schematics must be installed together.

“Landmark roll could not fit…” means the available landmark could not fit the nearby loaded terrain. Try open, fairly level ground with a clear footprint and headroom. The named landmark test advises a clear 17×17 area. The message can be a normal fallback, not a plugin crash.

## Configuration locations

Paths below are relative to `plugins/Airdrops/`. Keep the layout your installation uses.

| Purpose | Compact layout | Legacy layout |
|---|---|---|
| Main settings, worlds, distances, claiming, schedule, tiers | `config.yml` | Same |
| Falling delivery and small-structure switch | `delivery.yml` | Same |
| Core/extra loot | `content/loot/` | `loot.yml`, `armour-loot.yml`, `legendary-custom.yml`, `loot-additions-3.2.3.yml` |
| Boss and event definitions | `content/bosses/`, `content/events/` | `bosses/`, `events/` |
| Schematics and landmark settings | `content/structures/`, `content/landmarks/` | `structures/`, `landmarks/` |
| Exchange | `content/exchange/` | `exchange.yml`, `exchange-expansion.yml`, `exchange-landmarks.yml` |
| Rewards | `content/rewards/reward-packs.yml` | `reward-packs.yml` |
| Eclipse | `content/eclipse/eclipse.yml` | `eclipse.yml` |
| Visual switches | `content/visuals/` | `resource-pack.yml`, `visual-upgrade.yml`, `mob-cosmetics.yml` |

Configure actual loaded world names under `airdrop.worlds`. Rarity chances, loot rolls, claiming and automatic intervals live in the main config; tier content may override expiry and encounter choices. Event `chance` controls whether an event occurs; pool `weight` controls which event is chosen. A boss defines the enemy; an event defines the encounter and unlocking conditions.

## Java resource pack

Download the [Java pack](https://github.com/TakeoverVase120/airdrops-resource-packs/releases/download/v1/AirDrops-Java-v1.zip). While stopped, merge into `server.properties`:

```properties
resource-pack=https://github.com/TakeoverVase120/airdrops-resource-packs/releases/download/v1/AirDrops-Java-v1.zip
resource-pack-sha1=5120ff1dc8be44fec3ea6ee81009a9e7e302861b
resource-pack-id=d4f3891d-a816-55a6-b798-da5a79f6290e
require-resource-pack=false
```

Set `require-resource-pack=true` only if accepting the pack is required for joining your server. If you already distribute a combined server pack, merge assets properly and use that combined file's own hash/identity instead of replacing unrelated artwork.

For the delivery model, merge into `delivery.yml`:

```yaml
visual:
  item-model: 'airdrops:delivery_crate'
  java-pack-id: 'd4f3891d-a816-55a6-b798-da5a79f6290e'
```

Install the Visuals content and enable its `resource-pack.yml`/`visual-upgrade.yml` settings for recognised item artwork. Restart, reconnect and accept the **server-offered** pack. Enabling a pack only in Java Options does not establish the server pack handshake used by delivery visuals. `/advisuals refresh` refreshes recognised items; it does not install a resource pack.

## Bedrock resource pack

1. Download [AirDrops-Bedrock-v1.mcpack](https://github.com/TakeoverVase120/airdrops-resource-packs/releases/download/v1/AirDrops-Bedrock-v1.mcpack) and [airdrops-mapping.json](https://github.com/TakeoverVase120/airdrops-resource-packs/releases/download/v1/airdrops-mapping.json).
2. Put one copy of the MCPACK in `plugins/Geyser-Spigot/packs/` and the combined mapping in `plugins/Geyser-Spigot/custom_mappings/`.
3. Replace superseded Airdrops mappings carefully; do not also load an old delivery-only mapping. Preserve other plugins' mappings and store backups outside the loaded folders.
4. In Geyser's configuration enable `gameplay.enable-custom-content` and `gameplay.force-resource-packs`.
5. Merge this under the existing `visual:` section of Airdrops `delivery.yml`:

```yaml
  bedrock:
    mode: required-pack
    pack-id: '8119bba5-6055-56b2-af5e-1879d599cc5d'
    sha256: 'b9b3c89a65ac65ecb6dec7dd22f7463ead760fc8b4ac6cc4c3b8afb930c551be'
    identifier: 'airdrops:delivery_crate'
```

Restart and reconnect Bedrock, accepting the pack. UUID/hash values must match the exact pack. Geyser serves the Bedrock pack; its public URL is a download for server owners, not a replacement for the Java `resource-pack` setting.

**Known visual limitation:** placed beacons intentionally use a vanilla appearance on Bedrock in v1; Java retains custom artwork. Unknown, old or unacknowledged packs use the vanilla delivery fallback. Custom mob cosmetics have separate switches.

## Troubleshooting and recovery

| Symptom | Explanation / next step |
|---|---|
| Remote disappears after calling a drop | A remote is single-use. A successful call consumes it. |
| Beacon disappears after three drops | The default beacon has three attractions. Check `utility-items.beacon.attractions` if customised. |
| Claim stops when moving away | Intended distance check; default maximum is five blocks. Stay near the crate during the countdown. |
| A landmark chest stays locked | Complete its objectives/encounter first. Check stage messages and remaining enemies. |
| Event reports failure after `/airdrop clear` | Clearing deliberately cancels the active event. Confirm terrain cleanup succeeds afterward. |
| Missing small structure during falling delivery | Check `keep-small-structures`, the master structure switch, WorldEdit and the schematic. |
| Menu says disabled or is unavailable | Install/enable the relevant optional content and check permissions. Core-only installs do not provide every expansion. |
| `/advisuals refresh` says disabled | Install Visuals and enable `visual-upgrade.yml` in the correct layout. Also distribute the resource packs. |
| Creator reward cannot resolve | Check CreatorRuntime and the supplied item definitions. Preserve existing custom definitions when merging. |
| Custom Java delivery stays vanilla | Check server-offered pack acceptance, matching pack UUID and the delivery visual settings; reconnect. |
| Java rendering breaks across the creative menu too | Try a client resource reload/reconnect and test without shaders to distinguish a client renderer issue from a server issue. |

### “Cleanup paused”, “Recovery footprint changed” or a retained journal

Airdrops records temporary terrain in `state/terrain-recovery.bin`. Before restoring a structure it checks the footprint against expected blocks. If a conflicting change is found, cleanup can pause and the journal is retained instead of overwriting unrelated blocks. This can block replacement drops; a persistent startup recovery failure can prevent Airdrops enabling.

**Do not delete the recovery journal to force the next drop.** Keep the journal, affected world and plugin data together. Preserve a backup, inspect the expected/found blocks and coordinates in the log, and investigate the conflict before attempting recovery. Startup retries saved recovery. Verify a successful restoration message before resuming tests.

The current v1 replacement accepts supported natural changes such as leaf distance updates, rail shape updates and grass decaying to plain dirt. Other material replacements remain protected. Identical player-placed dirt cannot be distinguished from natural grass decay.

### Known shutdown limitation

Stopping with an active structure can report `Terrain cleanup incomplete at shutdown ... plugin is not enabled` and retain the journal. A subsequent startup may restore it successfully. To reduce this case, clear the active drop and confirm cleanup before stopping. If recovery still fails, retain the journal and report the logs; do not assume a retained journal means cleanup finished.

## Reporting a problem

Open an [issue](https://github.com/TakeoverVase120/Airdrops/issues) with the plugin build/checksum, Paper and Java versions, enabled expansions/dependencies, exact steps, relevant console messages and whether the problem occurs on Java or Bedrock. Include relevant settings after removing credentials, webhook URLs and other private data.

The bundled `BUILD-VERIFICATION.json` and checksums identify the downloaded build. Public naming remains v1, so include the build identifier or checksum when comparing replacement downloads. This README documents the v1 command handlers and permission defaults; older guides under `docs/` may describe earlier behaviour.
