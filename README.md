# All Tiled Up — Devlog

Development log for All Tiled Up, a procedural tileset generator and map painter for game devs (and tabletop VTT map makers). Newest entries first.

---

## 2026-07-13 — Water that finally looks like water, VTT export, and a big ISO/3D upgrade

A big chunk of work landed recently. Highlights:

**Water rendering, rebuilt from the ground up.** The old model had pinched, shallow-looking edges everywhere. Now there's a real depth model: one flat sea level per connected water body (computed via flood fill, not once for the whole map), with the seabed sinking beneath it the further out it goes — matches how a real coastline actually looks. Two unconnected ponds in the same area can sit at different heights, and water lines up correctly across chunk boundaries.

**Universal VTT export.** Maps now export as `.uvtt` files that drop straight into Foundry VTT's Universal Battlemap Importer or Roll20's UniversalVTTImporter — wall and line-of-sight data included. If you run tabletop games, your maps are playable the moment they're exported.

**ISO and 3D views caught up to platformer.** Right-click any cell in ISO or 3D (via raycasting) to reseed its texture, swap between two active materials, or set a ramp — the same per-cell control platformer mode already had. Picks persist through save/reload now too.

**A toolbar you can actually rearrange.** Drag-and-drop reordering, rebuilt on pointer events so it works on touch, not just desktop mouse — plus a real stash (ToolBox) for anything you don't want cluttering the bar.

**Smaller stuff that adds up:** per-cell notes and custom properties, shareable preset codes for a seed/variation/biome combo, Aseprite import alongside PNG/JPG/WEBP/GIF, a visual autotile rule-table editor, pointy-top hex as a second orientation, a Present mode for popping the map out to a second monitor, and an ASMR paint sound that's honestly pretty satisfying.

**Fixed:** a nasty 3D-paint bug where only the first stroke of a session rendered — every stroke after it stayed invisible until you paused painting (a debounce that kept cancelling itself under fast input, now a proper throttle). Also a batch of smaller polish and performance fixes from a full codebase audit — icon consistency, export-file encoding cleanup, Android back-button handling, touch target sizing, and more.

More soon — say hi on Discord if you want to follow along or try things out early.
