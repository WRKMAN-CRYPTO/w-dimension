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
