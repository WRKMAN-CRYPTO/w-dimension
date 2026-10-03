# Builder-0.7: Square Maze

## Pre-registered hypothesis

Before observing the experiment, the user predicted:

> In a maze of squares, W-NULL will win by brute force.

This prediction is recorded before field testing.

## Design

Builder-0.7 restores the live paired-world view so agent behavior can be observed directly.

- W-LIVE above
- W-NULL below
- same seed and initial agents
- same source and sink
- same W dynamics
- same steering mechanics
- identical square-cell maze in both worlds
- maze is symmetric around the horizontal centerline
- agents receive no obstacle sensor, map, avoidance rule, maze instruction, or reward shaping
- walls are collision geometry only
- wall contacts are counted observationally

The purpose is exploratory but the prediction is explicit: NULL is expected to outperform LIVE through brute-force traversal of rectilinear corridors and corners.

A batch replication should follow only after confirming the live maze behaves as intended.


## Apparatus check — 0.7

The first live field test produced zero deliveries in both worlds and millions of repeated wall contacts. Agents formed horizontal lines against the first barriers.

Cause: every rectangle collision used the same horizontal reflection (`angle = π - angle`), even when an agent struck a horizontal face. The apparatus therefore could not support meaningful rectilinear maze traversal.

This run is retained as an apparatus failure, not evidence for or against the pre-registered NULL hypothesis.

## 0.7.1 collision correction

Collision response is now face-aware:

- entering through a vertical rectangle face reflects the x component
- entering through a horizontal rectangle face reflects the y component
- ambiguous corner entry reverses direction

Agents still receive no obstacle sensing, map, avoidance rule, route information, or maze-specific behavior. The original pre-registered prediction remains unchanged.


## Apparatus correction — 0.7.2

The 0.7/0.7.1 obstacle layout was rejected before hypothesis testing because it was a sequence of barriers rather than a meaningful maze.

0.7.2 replaces the layout with a rectilinear branching field containing:

- staggered gates
- upper and lower route choices
- square pockets and false approaches
- dead-end shelves
- a horizontally centered source and sink
- geometry mirrored around the horizontal centerline where practical to avoid a simple top/bottom gift

A grid flood-fill now checks source-to-sink connectivity at boot. The UI reports `route verified` only when a traversable path exists.

The face-aware collision correction from 0.7.1 remains. Agents still receive no obstacle awareness or maze-specific behavior. The original NULL hypothesis remains pre-registered and unchanged.


## Builder-0.8 — generated perfect maze

The hand-authored obstacle layouts from 0.7 through 0.7.2 are retired as apparatus-development failures. They are not maze-test evidence.

Builder-0.8 generates a 12 × 9 cell perfect maze from fixed maze seed `0x4D415A45` using a randomized depth-first backtracker. The generator begins with every cell isolated and repeatedly carves passages to unvisited neighboring cells, producing a spanning tree of the grid.

Consequences of the construction:

- every maze cell is reachable
- there are genuine corridors, turns, junctions, and dead ends
- there is exactly one cell-path between any pair of cells
- the middle-left cell is the entrance and the middle-right cell is the exit
- the remaining cell boundaries become collision rectangles
- both W-LIVE and W-NULL receive the identical generated maze

A separate graph traversal verifies that the entrance cell reaches the exit cell before the UI reports `route verified`.

Agents receive no maze graph, wall sensor, pathfinding rule, avoidance behavior, or navigation hint. Face-aware collision physics from 0.7.1 remains.

The original pre-registered prediction remains: **W-NULL wins by brute force.**


## Builder-0.8.1 — seal the exterior highway

The first 0.8 field observation exposed another apparatus flaw: although the generated structure was a real maze, its outer frame sat inside the simulation bounds. Agents could travel around the top or bottom of the maze and reach the sink without traversing it.

Observed 0.8 delivery counts are therefore contaminated and are not maze-navigation evidence.

0.8.1 changes only the apparatus boundary:

- maze top is coincident with the simulation top boundary (y = 0.08)
- maze bottom is coincident with the simulation bottom boundary (y = 0.92)
- the generated internal maze and fixed maze seed remain unchanged
- legal entrance remains on the left middle row
- legal exit remains on the right middle row
- a separate physical-space flood test searches specifically for a source-to-sink route that stays outside the maze interior
- the UI reports `exterior sealed` only when the maze graph is connected and the exterior bypass test fails to find a highway

The original pre-registered prediction remains unchanged: **W-NULL wins by brute force.**


## Builder-0.8.2 — hard simulation seal

Field observation of 0.8.1 suggested agents could exploit a microscopic numerical/rendering seam along the bottom boundary, travel laterally outside the intended maze, and re-enter near the sink. The coarse exterior flood validator did not detect this path.

0.8.2 stops relying on visual rectangle contact for the maze's top and bottom containment. After every movement/collision step, agent state is constrained directly to the maze's vertical domain:

- minimum legal y = `MY + WT`
- maximum legal y = `MY + MH - WT`
- crossing either limit clamps the agent back inside and reflects its vertical heading component
- these hard constraints are simulation rules, independent of canvas pixels and rectangle seams

The generated maze, maze seed, agent mechanics, entrance, exit, W behavior, and pre-registered hypothesis are otherwise unchanged.

0.8.1 remains an apparatus-development run and is not counted as maze evidence. The UI reports `HARD SEALED` when the graph route, exterior check, and hard-bound configuration all pass.


## Builder-0.9 — crossover trace instrumentation

Builder-0.9 freezes the 0.8.2 maze and agent mechanics and adds observation only.

Motivation: in the first hard-sealed 0.8.2 field run, W-NULL reportedly opened an approximately 40–0 delivery lead, then W-LIVE caught it, crossed over, and maintained a small lead. A later screenshot showed LIVE 324 vs NULL 310. This observation motivates measuring performance as a time series rather than only a final count.

Instrumentation:

- sample cumulative LIVE and NULL deliveries every 1,000 simulation ticks
- compute Δ = LIVE − NULL at each sample
- render Δ over time around a zero baseline
- record the first sampled negative/non-positive → positive crossover
- reset clears samples and crossover state

No steering, W dynamics, collision rules, maze geometry, maze seed, agent seed, source/sink behavior, or hard-seal rules are changed by this version.
