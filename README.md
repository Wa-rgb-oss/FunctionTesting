# Gradari Ground Operations

Standalone, browser-based movement prototype for Gradari Mireris. An angled orthographic 2.5D view with original procedural visuals, inspired by colony simulators and top-down military games.

## Run

Serve this directory using VS Code Live Server, or `python3 -m http.server 8080`, then open http://localhost:8080. No dependencies or build step. ES modules require HTTP rather than opening index.html directly.

For GitHub Pages: repository Settings → Pages → Deploy from a branch → main → /(root) → Save. Once deployed, the expected address is https://wa-rgb-oss.github.io/FunctionTesting/. Pages must be enabled by the repository owner; committing these files does not activate hosting.

## Controls

* WASD / arrow keys: direct movement with solid obstacle collision.
* Shift: run.
* Click / tap clear ground: route around obstacles and walk to the destination.
* E / Interact button: enter a nearby facility.
* Wheel or + / −: zoom.
* Space / Pause: pause simulation.
* R: reset the deterministic outpost and objectives.

Visit the three facilities to complete the field survey. Two NPCs patrol the outpost. Progress is temporary and resets on reload.

## Integration direction

`game.js` keeps simulation coordinates separate from the projection. `findPath` uses a four-neighbor breadth-first search over the tile occupancy grid, suitable for this small map. Rendering uses scaled terrain, building height and depth ordering to produce an angled view without a 3D engine. This is 2.5D rather than true 3D.

A future Gradari integration could map each strategic hex to a surface scene, load its facilities as obstacles and interaction points, and use the authenticated character as the operative. This prototype has no Supabase connection, multiplayer, combat, persistent economy or production changes. Authoritative multiplayer and permissions would need a separate implementation before integration.
