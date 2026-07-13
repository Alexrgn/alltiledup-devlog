# All Tiled Up — Devlog

Development log for All Tiled Up, a procedural tileset generator and map painter for game devs (and tabletop VTT map makers). Newest entries first.

---

## In progress — building toward the next release

**Water rendering, rebuilt from the ground up.** The old model had pinched, shallow-looking edges everywhere. Now there's a real depth model: one flat sea level per connected water body (computed via flood fill, not once for the whole map), with the seabed sinking beneath it the further out it goes — matches how a real coastline actually looks. Two unconnected ponds in the same area can sit at different heights, and water lines up correctly across chunk boundaries instead of stair-stepping.

**Universal VTT export.** Maps now export as `.uvtt` files that drop straight into Foundry VTT's Universal Battlemap Importer or Roll20's UniversalVTTImporter — wall and line-of-sight data included. If you run tabletop games, your maps are playable the moment they're exported.

**ISO and 3D views caught up to platformer.** Right-click any cell in ISO or 3D (via raycasting) to reseed its texture, swap between two active materials, or set a ramp — the same per-cell control platformer mode already had. Picks now persist through save/reload and layer switches, not just for the session.

**A toolbar you can actually rearrange.** Drag-and-drop reordering, rebuilt on pointer events instead of native HTML5 drag-and-drop (which turns out to just never fire from a touch gesture on Android — so this was silently broken on-device despite working fine with a desktop mouse). Plus a real stash for anything you don't want cluttering the bar, and every toolbox action (randomize, generate water, clear map, save/load) is now a real moveable button instead of being stuck in a fixed dropdown.

**A pass of bug fixes:** undo/redo now covers per-cell notes and properties, Clear Map actually resets everything it should, shift+right-click reliably opens the cell-notes popup on every autotile strategy instead of erasing the cell first, baking a chunk no longer silently drops its notes or texture picks, VTT export now derives wall data from every visible layer, pointy-top hex exports stopped reverting to flat-top metadata, and Aseprite import now respects hidden/translucent group layers.

**Smaller stuff that adds up:** per-cell notes and custom properties, shareable preset codes for a seed/variation/biome combo, Aseprite import alongside PNG/JPG/WEBP/GIF, a visual autotile rule-table editor, pointy-top hex as a second orientation, a Present mode for popping the map out to a second monitor, and an ASMR paint sound that's honestly pretty satisfying.

**Also fixed:** a nasty 3D-paint bug where only the first stroke of a session rendered — every stroke after it stayed invisible until you paused painting (a debounce that kept cancelling itself under fast input, now a proper throttle). A precision bug that silently capped decal/puddle jitter to half its intended range. And a batch of smaller polish/performance fixes from a full codebase audit — icon consistency, export-file encoding cleanup, Android back-button handling, touch target sizing, smarter tile-cache eviction, and more.

---

## v1.2.0 — 2026-07-11

**Theme overhaul.** Switched the default theme to light, which — surprisingly — fixed doubled Paint toolbar icons as a side effect, and reordered the default toolbar buttons. Fixed invisible/low-contrast text and black-on-dark button text that only showed up once light became the default.

**Platformer improvements.** Wired up the real character sprite with role-aware collision (drop-through ledges) and a traversable level generator. Added real diagonal slope tiles and per-cell tile variant cycling. Fixed staircase interior cells wrongly capped to the edge material.

**Variant/texture randomize system, rebuilt.** Replaced the old footer variant control with a right-click/long-press popup, added tile TYPE choice (diagonal/full/half) and a texture-randomize toggle. Randomize now draws from the full variation range with brightness/hue jitter and reseeds fine-detail noise (flecks, grain, sparkle) that previously never varied — turned out to be the actual root cause of "randomize doesn't look different."

Also fixed example maps not matching their own preview thumbnails.

## v1.1.1 — 2026-07-10

Export now shows an actionable "Upgrade to Pro" dialog instead of a dismissible toast. Full German localization shipped, reaching parity with English and Spanish.

## v1.1.0 — 2026-07-09

Every hardcoded UI string wired through i18n, with Spanish added. Fixed paint-mode map exports being completely ungated when they should have required Pro like every other export path. Plus smaller fixes: corrected mobile UI scale defaults, fixed a Detector-mode crash, fixed stale free-tier text in the help guide.

## v1.0.10 — 2026-07-03

Exponential map size steps, plus an Endless Map Discord bot. Dynamic UI/font scale resizing and native app-review prompts. Fixed broken GameMaker/Unity/Defold/Godot/LDtk exports and wired up real Google Play Billing. Fixed material color-parameter edits not affecting rendered output, and replaced flashing tooltip toasts with a dismissible, replayable popover.

## 2026-06-24

Camera snap presets and dynamic water controls in the 3D view, plus 3D OBJ model export. Fixed a grass-tuft render crash, collapsed the layers panel, and expanded the help guide.

## v1.0.9 — 2026-06-17

Fixed Android boot and settings issues for this release.

## v1.0.1 — 2026-06-17

A design-critique-driven top-bar and brand pass, mobile polish, paint fixes, an update prompt, and a help guide. This was the first closed-testing release.

## The beginning — 2026-06-16

All Tiled Up split off into its own project, growing out of an earlier prototype.

---

Questions, or want to try things out early? Come say hi on Discord.
