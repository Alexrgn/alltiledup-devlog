Newest entries first.

---

## v1.9.0 — 2026-09-21 — Voxel, paint depth, and Pro that means something

**Voxel is a real block world.** Chunked storage and meshing, orbit camera, save slots, stamps, selection masks, copy / rotate / scale, and inspect that opens and closes cleanly. Water behaves like a liquid — sources, falls, mist. Fire has a lifetime with Eternal / Pause / Stoke / Extinguish / Douse. Explosions throw micro-voxels. Dynamic bodies can be placed, dragged, and reset with the map. ISO maps extrude into voxel with terrain bands that keep their textures. Texture resolution is a control — 16 / 32 / 64 / 128. Phones run on a GPU budget so the mode stays playable. Hardness holds and block light (0–15) give dig and build real weight.

**The coast is a place you can read.** Dock planks, pilings, cleats, ladders, bait buckets, wells, barrels, signs, cottage framing, glowing windows, chimney smoke, mill vanes, clothesline, carts, beach fires, cave mouths, tide pools, crabs, fish, wakes, gulls, wet sand, and shoreline foam. A dinghy sits on the water; a fisherman stands on the pier. West lighthouse with stairs and beam, walkable cliff caves, cliff waterfalls, teal water with waves. Props place as stamps with undo and export at object scale. Meshing stays greedy and packed; shadows freeze between edits; lamp clusters share lights; work pauses when the tab is hidden.

**Paint and 2.5D are built for real maps.** A full 16-piece wall tileset, per-cell deco, castle buildings with connecting walls, optional doors in wall gaps, an HD stamp palette, stamps that stack on tiles, a format dropdown, dockable HUD, and rail stamps. Phone HUD is laid out for two thumbs. Maps HUD docks to the edges as one sheet. Zoom and pan stay smooth mid-gesture. Generate respects cave and dungeon wall / floor materials. ISO adjust picks the raised face you aim at. Undo covers water and path; chunks keep history; Generate overrides stick; atlas exports ship with real tiles.

**Materials have their own signatures.** Distinct structure per family. Canvas cloth, bark, and hemp resolve to the right architecture. Canvas sails, bark logs, and straw thatch read as canvas, bark, and straw. Hex 64 and Iso Ground sit in the format list with every other format. The picker shows what Free can use — no leftover PRO badges on free formats — and Dirt Path is out of the library.

**Pro is the door out.** Free keeps the full editor — every format, paint, preview. Pro unlocks exports and voxel: atlases, map and bucket JSON, detector packs, character downloads, procedural tiles, 3D screenshots, voxel exports, and voxel entry itself (tab, shortcut, saved restore).

**On Android, Free can earn one export.** At an export gate you can watch a short rewarded ad for a single successful download, or go Pro. The credit is one download. Ads do not open voxel. Pro is ad-free, with unlimited exports and full voxel, **$4.99** one-time on Play. Privacy covers optional Free ads, Play and itch purchases, and that Pro has no ads. Artwork stays on your device.

**Desktop on itch.** Demo and Pro Windows builds share the same product code. The app can check for updates on launch and from Settings and open the itch page when a newer build is ready; itch-app installs still update through itch’s channel updater.

## v1.6.0 — 2026-07-26

**A big decal-identity pass.** Continuing the same "give it a real structural signature instead of a recolored clone" work the textures got last round, this time on over 30 small decal/prop shapes — acorns, beetles, bells, berries, bolts, soap bubbles, bullet holes, charcoal, coins, crystals, dents, embers, eyes, fairy rings, flint, fossils, gears, gems, glyphs, lichen, lilies, mushrooms, nails, portal rifts, potion stains, rings, scrap, shards, skulls, stars, and sticks. Each one now varies its actual silhouette per stamp instead of just repositioning the same shape — the soap bubble, for one example, went from a static circle with two fixed highlight dots to per-instance wobble, refraction shading, and a real iridescent thin-film ring. The grass/moss material family (jungle floor, fungal mat, autumn grass, bamboo grove, sea grass, winter grass, meadow grass, flowering meadow, mossy rock, and more) went through the same treatment, and the Conveyor Belt material was fixed to actually respond to its frequency and seed dials instead of rendering the same shape regardless of what they're set to.

**Hex and Tiled export fix.** Tiled's TSX export was slicing every isometric tile in half — it was sizing tiles off the map's grid footprint instead of the actual atlas cell size. Hex maps also had their Tiled "stagger axis" backwards: pointy-top and flat-top were swapped from what Tiled's own convention expects. Both fixed, with new automated coverage so they can't quietly regress again.

**Decals in isometric maps were silently invisible.** Not a rendering glitch — decals were being placed and saved into the map correctly, they just never got painted, for as long as iso decal stamping has existed. The iso render path calls its own terrain function and returns before ever reaching the decal-paint step meant to run afterward. Fixed by moving decal painting into the function iso actually renders through.

**Materials hotfix.** Six materials (Mortar, Noir Cobble, Tundra Gravel, Mosaic Tile, Crumbled Mosaic, a Dirt Dry Dusty gravel variant) crashed the materials panel outright — leftover references from a mid-refactor. Two more (Baked Clay, Dirt Dry Dusty) rendered as flat solid black instead of erroring, from a bug that silently turned a coordinate into "not a number" rather than failing loudly. All fixed and checked against every material in the library.

**Smaller stuff:** the chunk map panel gained a delete-current-chunk button; the PATH tool's toolbar button was mislabeled "RAMP" since ramps got folded into it as automatic behavior — renamed, and Generate now actually respects the material you pick for it instead of randomizing; a real fullscreen toggle, a clear-map action, seamless tile export, and Tiled (.tmx) world export were added to Paint; Platformer levels can use imported parallax backdrop images out of the box.

**In progress, not shipped yet:** a real voxel block-world format is taking shape behind the scenes — chunked storage, a hidden-face-culling mesher, and a read-only 3D test view. Early and not exposed in the released app, but it's the foundation for true 3D block editing down the line.

---

## v1.5.0 — 2026-07-21

**Platformer levels can now have real hazards and moving parts.** A new level-entity system adds moving platforms (ping-pong back and forth on whichever axis and distance you set, rendered as a real one-way ledge you can ride), hand-drawn spike strips, and breakable blocks with their own crack patterns — all riding through save/load, undo, and chunk baking like everything else, plus a generic JSON export for scripting them into your own engine. The test sprite rides platforms properly (no tunnelling through on a fast fall), dies on spikes, and breaks blocks bumped from below. Decals can now ride along on top of a moving platform too, instead of floating in place while it moves out from under them.

**Parallax backdrops.** Import your own image, stack multiple layers with independent scroll speed (locked to the screen, or moving with the world) and tiling, and it renders behind the level with the sky left transparent. A new spawn point (auto-placed by Generate, or set by hand) marks exactly where test-play starts, and platformer levels can now generate a ceiling with climbable ladder-islands instead of always being open-air.

**Cross-chunk platformer generation.** Adjacent chunks now generate floors, ceiling openings, and drop-through pits that actually line up at the seam in all four directions, instead of every chunk being generated in isolation.

**Hex format grew into a full hexcrawl toolkit.** Coordinate labels, a curated point-of-interest picker (village, watchtower, ruins, portal, and more), GM fog-of-war with a separate reveal-only view for a second-screen Present mode, and rivers/roads that route along hex edges and centers with organic wobble. Also new: edge tiles (paint a material onto a specific hex edge, auto-mirrored onto the shared neighbor, with a mismatch checker and its own tile-set export), and a Layered hex mode that renders elevation as real extruded, shaded stacked tiers instead of flat color bands.

**Test-play, actually playable on your phone.** New on-screen touch controls — a D-pad and jump button, both resizable and repositionable — drive test-play using the same input the keyboard already does, including double-tap-and-hold to run and down+jump to drop through a one-way platform. Getting this working on a real phone surfaced (and fixed) a run of real bugs: test-play's toggle button was accidentally dev-only and never actually reachable in any real build; a 2-finger pinch or pan could race against placing an entity or decal and place one by accident; tapping an existing moving platform now opens its settings instead of stacking a new one on top; a mobile bug where hiding UI during test-play could permanently shrink the rendered viewport for the rest of that session; the zoom slider could make the sprite (and camera) jump to a different spot on the map instead of staying anchored where it actually was; and middle-mouse-drag panning would snap right back to the sprite a moment after you let go of it instead of actually holding your new view. Also added a speed slider for test-play (separate from zoom), and widened the touch/pinch-recognition window after live testing showed a real pinch gesture needs more room than a synthetic one to be told apart from a paint stroke.

**Generate no longer places two ramps meeting at a bare peak.** A flat, 2-cell-wide hilltop could get ramps sloping down from both sides with nothing flat left at the top — a knife-edge point instead of a walkable peak. Both Generate and manually painting a path over a height change now always leave a flat cell between two ramps that would otherwise meet.

**Export correctness pass.** LDtk export was rewritten against the real 1.5.3 schema (the old one was fundamentally broken); Godot export fixed hex tile sizing and a missing collision layer; edge-tile export fixed material and orientation bugs; and Universal VTT export now correctly refuses to run on formats it was never built for (iso/hex) instead of producing a broken file.

**Rendering & performance pass** across platformer, hex, iso, and 3D — including lift-aware picking (clicking a tall stack's raised face now resolves to that cell, not whatever flat cell happens to be underneath), eased wheel-zoom, and backdrop layers you can reorder, reposition, resize, and rotate in place.

---

## v1.4.0 — 2026-07-17

**Terrain generation, rebuilt.** Randomize and Generate used to quantize a single noise field into height bands and hope the result looked like a map. Now terrain is built from real, distinct landforms — mountains that scale as an actual tapering peak (not a spike), carved canyons, and water basins placed clear of the mountains so lakes and cliffs never fight for the same ground — with open, walkable field left between features for paths to run through. Materials follow real elevation order too: shore, ground, vegetation, foothill rock, then peak, instead of whatever happened to land in a band. Give a layer a role (Floor, Rock, Peak, etc.) and Randomize, Generate, and World Drift all respect it now — not just World Drift like before.

**Fixed ISO and 3D losing painted terrain on format switch.** Switching a multi-terrain map (Blob, Wang, etc.) to ISO — or viewing it in 3D — could flatten every elevation band down to whichever single material happened to be selected, instead of showing the actual band-assigned materials. Both views now correctly inherit the real terrain.

**Path tool now has its own material picker.** Every path on the map used to render as the same hardcoded material no matter what you painted with. Now you pick the material the path tool paints with directly, and each stretch of path keeps whatever material it was painted with — changing the picker mid-map never rewrites path you already laid down.

**Puddle format lag, fixed.** Every material's blob was being fully rebuilt — full-map canvas, blur, per-pixel noise — on every redraw, including ticks that had nothing to do with Puddle at all (like the water animation). Now it's cached and only rebuilt when something actually changes.

**Toolbox reworked.** It's now a straightforward list of every toolbar tool — click one to show or hide it without it jumping out of the list, drag its handle if you want it placed at an exact spot. Randomize also moved out of the World dropdown and onto the toolbar itself.

**Hindi, Bengali, and Marathi added,** reaching full localization for three of India's most-spoken languages.

---

  ## v1.3.0 - Water Physics Update - 2026-07-17      
                                                     
  **Water now behaves like an actual liquid.** Water 
  placed in height-map worlds flows into nearby      
  basins and fills enclosed spaces up to their lowest
  retaining wall. Break a wall and the water drains  
  into the newly opened area while conserving its    
  volume. Connect two pools and they equalize at one 
  shared surface instead of remaining at conflicting 
  heights.                                           
                                                     
  **New Sponge tool.** The Sponge removes water      
  inside the brush area without damaging terrain,    
  changing materials, or deleting decals.            
                                                     
  **3D water was rebuilt for the new behavior.**     
  Water edges now meet the terrain without gaps,     
  clipping, or z-fighting. Waves respond to water    
  depth, remain below retaining walls, and follow the
  selected flow direction. Painting in 3D can also   
  stack terrain repeatedly instead of raising a cell 
  only once per session.                             
                                                     
  **World generation and stability fixes.** Generated
  roads now route around buildings, and settlement   
  metadata correctly matches the structures shown on 
  the map. Long painting sessions no longer leak 3D  
  billboard materials into GPU memory.               
                                                     
  **Safer imports and desktop builds.** Custom-      
  material imports now enforce a 25 MB per-file limit
  and report failures honestly. External desktop     
  the desktop runtime has been upgraded
  43.

 ## v1.3.0 — 2026-07-13

**Real 3D building models.** The first hand-placed 3D building prop — a mushroom hut — is now in the game: drop it into 3D view, then pick it up and drag it wherever you want, or rotate/scale it, like any other decal. It's the first asset through a new art pipeline for turning custom multi-view artwork into compact, game-ready 3D models, so more of these are coming. Also fixed a couple of real bugs in the process: decal placement didn't actually work in 3D view at all before this (in or out of decal mode, it just painted terrain instead), and adjusting a decal's rotation or size with the scroll wheel was quietly zooming the camera at the same time. Both now behave like their 2D counterparts.

**Water rendering, rebuilt from the ground up.** The old model had pinched, shallow-looking edges everywhere. Now there's a real depth model: one flat sea level per connected water body (computed via flood fill, not once for the whole map), with the seabed sinking beneath it the further out it goes — matches how a real coastline actually looks. Two unconnected ponds in the same area can sit at different heights, and water lines up correctly across chunk boundaries instead of stair-stepping.

**Universal VTT export.** Maps now export as `.uvtt` files for standard tabletop VTT importers — wall and line-of-sight data included. If you run tabletop games, your maps are playable the moment they're exported.

**ISO and 3D views caught up to platformer.** Right-click any cell in ISO or 3D (via raycasting) to reseed its texture, swap between two active materials, or set a ramp — the same per-cell control platformer mode already had. Picks now persist through save/reload and layer switches, not just for the session.

**A toolbar you can actually rearrange.** Drag-and-drop reordering, rebuilt on pointer events instead of native HTML5 drag-and-drop (which turns out to just never fire from a touch gesture on touch devices — so this was silently broken on-device despite working fine with a desktop mouse). Plus a real stash for anything you don't want cluttering the bar, and every toolbox action (randomize, generate water, clear map, save/load) is now a real moveable button instead of being stuck in a fixed dropdown.

**A pass of bug fixes:** undo/redo now covers per-cell notes and properties, Clear Map actually resets everything it should, shift+right-click reliably opens the cell-notes popup on every autotile strategy instead of erasing the cell first, baking a chunk no longer silently drops its notes or texture picks, VTT export now derives wall data from every visible layer, pointy-top hex exports stopped reverting to flat-top metadata, and layered image import now respects hidden/translucent groups.

**Smaller stuff that adds up:** per-cell notes and custom properties, shareable preset codes for a seed/variation/biome combo, layered image import alongside PNG/JPG/WEBP/GIF, a visual autotile rule-table editor, pointy-top hex as a second orientation, a Present mode for popping the map out to a second monitor, and an ASMR paint sound that's honestly pretty satisfying.

**Also fixed:** a nasty 3D-paint bug where only the first stroke of a session rendered — every stroke after it stayed invisible until you paused painting (a debounce that kept cancelling itself under fast input, now a proper throttle). A precision bug that silently capped decal/puddle jitter to half its intended range. And a batch of smaller polish/performance fixes from a full codebase audit — icon consistency, export-file encoding cleanup, mobile back-button handling, touch target sizing, smarter tile-cache eviction, and more.

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

Exponential map size steps, plus an Endless Map community bot. Dynamic UI/font scale resizing and native app-review prompts. Fixed broken GameMaker/Unity/Defold/Godot/LDtk exports and wired up real in-app billing. Fixed material color-parameter edits not affecting rendered output, and replaced flashing tooltip toasts with a dismissible, replayable popover.

## 2026-06-24

Camera snap presets and dynamic water controls in the 3D view, plus 3D OBJ model export. Fixed a grass-tuft render crash, collapsed the layers panel, and expanded the help guide.

## v1.0.9 — 2026-06-17

Fixed mobile boot and settings issues for this release.

## v1.0.1 — 2026-06-17

A design-critique-driven top-bar and brand pass, mobile polish, paint fixes, an update prompt, and a help guide. This was the first closed-testing release.

## The beginning — 2026-06-16

All Tiled Up split off into its own project, growing out of an earlier prototype.

---

Questions, or want to try things out early? Come say hi in the community.
